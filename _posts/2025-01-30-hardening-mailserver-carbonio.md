---
layout: post
title: "Securing Mail Server with Ensures That Only Foreign Attackers Are Blocked To Attempt Logins Safely"
date: 2025-01-30
categories: MailServer
tags: [mail, smtp, fail2ban, carbonio ce, zextras, opensource]
---

# Setting Up Fail2Ban with GeoLite2 to Block SASL Authentication Attacks

We will set up Fail2Ban with GeoLite2 to block repeated failed SASL authentication attempts and restrict access only to Malaysian IPs. This helps prevent brute-force attacks on your mail server running Postfix on Ubuntu 22.04.

## Install Fail2Ban and GeoLite2

First, install Fail2Ban and dependencies:

```bash
sudo apt update && sudo apt install -y fail2ban iptables mmdb-bin
```

Download and install the GeoLite2 database:

```bash
mkdir -p /usr/share/GeoIP
cd /usr/share/GeoIP
wget -O GeoLite2-Country.tar.gz "https://geolite.maxmind.com/download/geoip/database/GeoLite2-Country.tar.gz"
tar -xzf GeoLite2-Country.tar.gz --strip-components=1 --wildcards "*/GeoLite2-Country.mmdb"
rm GeoLite2-Country.tar.gz
```

Ensure the `GeoLite2-Country.mmdb` file is correctly placed in `/usr/share/GeoIP/`.

## Configure Fail2Ban

### Create a Custom Jail

Edit or create the file `/etc/fail2ban/jail.local`:

```bash
vi /etc/fail2ban/jail.local
```

Add the following configuration:

```ini
[sasl-auth-custom]
enabled = true
port = smtp,465,submission
filter = sasl-auth-custom
logpath = /var/log/mail.log
bantime = 604800 # 7 days
findtime = 43200 # 12 hours
maxretry = 3
ignoreip = 127.0.0.1/8 10.0.0.0/8  #tidak block ip local
action = sekat_custom
```

This configuration monitors SASL authentication failures and bans IPs that exceed 3 failed attempts in 12 hours for 7 days.

### Create a Custom Action

Create the file `/etc/fail2ban/action.d/sekat_custom.conf`:

```bash
vi /etc/fail2ban/action.d/sekat_custom.conf
```

Add the following content:

```ini
[Definition]
actionstart =
actionstop =
actionban = bash -c 'GEO=$(mmdblookup --file /usr/share/GeoIP/GeoLite2-Country.mmdb --ip <ip> country iso_code 2>/dev/null | grep -Eo "[A-Z]{2}" | head -n 1); if [ "$GEO" = "MY" ]; then echo "<ip> ini rakyat Malaysia, abaikan dulu" >> /var/log/fail2ban_sekatnegara.log; else echo "<ip> dari $GEO telah disekat" >> /var/log/fail2ban_sekatnegara.log; iptables -I INPUT -s <ip> -j DROP; fi'
actionunban = iptables -D INPUT -s <ip> -j DROP
```

This script checks the country of the offending IP and only bans it if it is not from Malaysia (MY) while logging the actions.

### Create a Custom Filter

Create the file `/etc/fail2ban/filter.d/sasl-auth-custom.conf`:

```bash
vi /etc/fail2ban/filter.d/sasl-auth-custom.conf
```

Add the following content:

```ini
[Definition]
failregex = ^.*?warning:\s+(?:unknown|[\w\.-]+)\[<HOST>\]:\d+:?\s+SASL.*?authentication failed: authentication failure, sasl_username=.*$
ignoreregex =
```

This regex matches failed SASL authentication attempts in the mail log `/var/log/mail.log`.

Example log entry:

```log
Jan 30 09:28:00 mail postfix/smtps/smtpd[810753]: warning: unknown[46.72.252.233]:65410: SASL LOGIN authentication failed: authentication failure, sasl_username=zaim
```

## Restart and Test Fail2Ban

Restart the Fail2Ban service:

```bash
sudo systemctl restart fail2ban
sudo systemctl enable fail2ban
```

Verify if the jail is active:

```bash
sudo fail2ban-client status sasl-auth-custom
```

### Check Logs and Banned IPs

If an attacker attempts multiple failed logins, your logs may show:

```bash
tail -f /var/log/fail2ban.log
```

Example output:

```log
2025-01-30 10:50:52,656 fail2ban.filter         [1513193]: INFO    [sasl-auth-custom] Found 124.101.249.119 - 2025-01-30 10:50:52
2025-01-30 10:50:52,790 fail2ban.actions        [1513193]: NOTICE  [sasl-auth-custom] Ban 124.101.249.119
```

Check Fail2Ban country-specific bans in `fail2ban_sekatnegara.log`:

```bash
tail -f /var/log/fail2ban_sekatnegara.log
```

Example output:

```log
92.37.176.67 dari RU telah disekat
117.253.169.232 dari IN telah disekat
180.7.128.91 dari JP telah disekat
49.124.151.70 ini rakyat Malaysia, abaikan dulu
```

To check all banned IPs:

```bash
sudo fail2ban-client status sasl-auth-custom
```

To manually ban an IP for testing:

```bash
sudo fail2ban-client set sasl-auth-custom banip 203.0.113.5
```

To manually unban an IP:

```bash
sudo fail2ban-client set sasl-auth-custom unbanip 203.0.113.5
```

Fail2Ban will then ban the IP if it is not from Malaysia. Feel free to modify the setting with your country code.
