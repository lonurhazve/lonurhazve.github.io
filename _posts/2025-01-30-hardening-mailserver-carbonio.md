---
layout: post
title: "Securing Mail Server with Ensures That Only Foreign Attackers Are Blocked To Attempt Logins Safely"
date: 2025-01-30
categories: MailServer
tags: [mail, smtp, fail2ban, carbonio ce, zextras, opensource]
---

Securing Mail Server with Ensures That Only Foreign Attackers Are Blocked To Attempt Logins Safely

In this tutorial, we will set up Fail2Ban with GeoLite2 to block repeated failed SASL authentication attempts and restrict access only to Malaysian IPs. This helps prevent brute-force attacks on your mail server running Postfix on Ubuntu 22.04.

Step 1: Install Fail2Ban and GeoLite2

First, install Fail2Ban and dependencies:

sudo apt update && sudo apt install -y fail2ban iptables mmdb-bin

Download and install the GeoLite2 database:

mkdir -p /usr/share/GeoIP
cd /usr/share/GeoIP
wget -O GeoLite2-Country.tar.gz "https://geolite.maxmind.com/download/geoip/database/GeoLite2-Country.tar.gz"
tar -xzf GeoLite2-Country.tar.gz --strip-components=1 --wildcards "*/GeoLite2-Country.mmdb"
rm GeoLite2-Country.tar.gz

Ensure the GeoLite2-Country.mmdb file is correctly placed in /usr/share/GeoIP/.

Step 2: Configure Fail2Ban

2.1 Create a Custom Jail

Edit or create the file /etc/fail2ban/jail.local:

[sasl-auth-custom]
enabled = true
port = smtp,465,submission
filter = sasl-auth-custom
logpath = /var/log/mail.log
bantime = 604800   # 7 days
findtime = 43200   # 12 hours
maxretry = 3
ignoreip = 127.0.0.1/8 10.0.0.0/8
action = sekat_custom

This configuration monitors SASL authentication failures and bans IPs that exceed 3 failed attempts in 12 hours for 7 days.

2.2 Create a Custom Action

Create the file /etc/fail2ban/action.d/sekat_custom.conf:

[Definition]
actionstart =
actionstop =
actionban = bash -c 'GEO=$(mmdblookup --file /usr/share/GeoIP/GeoLite2-Country.mmdb --ip <ip> country iso_code 2>/dev/null | grep -Eo "[A-Z]{2}" | head -n 1); if [ "$GEO" = "MY" ]; then echo "<ip> is from Malaysia, no ban."; else iptables -A INPUT -s <ip> -j DROP; fi'
actionunban = iptables -D INPUT -s <ip> -j DROP

This script checks the country of the offending IP and only bans it if it is not from Malaysia (MY).

2.3 Create a Custom Filter

Create the file /etc/fail2ban/filter.d/sasl-auth-custom.conf:

[Definition]
failregex = ^.*?warning:\s+(?:unknown|[\w\.-]+)\[<HOST>\]:\d+:?\s+SASL.*?authentication failed: authentication failure, sasl_username=.*$
ignoreregex =

This regex matches failed SASL authentication attempts in the mail log.

Step 3: Restart and Test Fail2Ban

Restart the Fail2Ban service:

sudo systemctl restart fail2ban
sudo systemctl enable fail2ban

Verify if the jail is active:

sudo fail2ban-client status sasl-auth-custom

Step 4: Check Logs and Banned IPs

To check banned IPs:

sudo fail2ban-client status sasl-auth-custom

To manually ban an IP for testing:

sudo fail2ban-client set sasl-auth-custom banip 203.0.113.5

To manually unban an IP:

sudo fail2ban-client set sasl-auth-custom unbanip 203.0.113.5

Example Log Entry

If an attacker attempts multiple failed logins, your log (/var/log/mail.log) might show:

Jan 30 09:28:00 mail postfix/smtps/smtpd[810753]: warning: unknown[197.255.196.83]:65410: SASL LOGIN authentication failed: authentication failure, sasl_username=johndoe

Fail2Ban will then ban the IP if it is not from Malaysia. Feel free to modify the setting with your country code.
