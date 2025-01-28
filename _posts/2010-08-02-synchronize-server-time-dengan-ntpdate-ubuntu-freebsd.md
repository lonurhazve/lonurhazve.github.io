---
title: "Synchronize Server Time Dengan ntpdate Ubuntu/FreeBSD"
date: 2010-08-02
---
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgRGO9QYrfD29hHIahbUDfNmaIqoQDa2vTdUTAZ1ZuRweZfosi0i5grXFNCwyYuQMeLP-s6hyf1dqioACb_C92xMQVSqXy0RZHws9DLy4JRbD4KRiOsSvytCsJtnTemP0MP44_VV0o1OQ/s1600/jampeguin.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="200" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgRGO9QYrfD29hHIahbUDfNmaIqoQDa2vTdUTAZ1ZuRweZfosi0i5grXFNCwyYuQMeLP-s6hyf1dqioACb_C92xMQVSqXy0RZHws9DLy4JRbD4KRiOsSvytCsJtnTemP0MP44_VV0o1OQ/s200/jampeguin.jpg" width="166" /></a></div>
<br />
Tujuannya untuk memastikan waktu pada server kita sama dengan waktu standard sebenar. Kalau malaysia biasanya di synchronize kepada time server ntp.jaring.my.</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
How ( Ubuntu Server )?</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br />
1. Ubah time server dalam<b> /etc/default/ntpdate</b> dan tukarkan NTPSERVERS="ntp.ubuntu.com" kepada&nbsp; <b>NTPSERVERS="ntp.jaring.my".</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #NTPSERVERS="ntp.ubuntu.com"<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #LONURHAZVE<br />
<b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NTPSERVERS="ntp.jaring.my"</b><br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Additional options to pass to ntpdate <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NTPOPTIONS=" </div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
Sekiranya file ini tidak ditukar seperti di atas dengan ntp.jaring.my biasanya ianya akan keluar error berikut :</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>1 Aug 20:47:48 ntpdate[31921]: no server suitable for synchronization found</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
2. Run command <b>#ntpdate ntp.jaring.my</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>1 Aug 21:01:05 ntpdate[12434]: step time server 61.6.32.61 offset -0.986923 sec</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br />
<u>RUN ntpdate Every Day/Boot Menggunakan Cron</u></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
1. Menggunakan editor buat fail baru dalam /etc/cron.daily :</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#vi /etc/cron.daily/ntpdate</b><br />
<br />
&nbsp;&nbsp;&nbsp; -&gt; Tambah ntpdate ntp.jaring.my dlam file tersebut dan simpan</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
2. Buat executable pada file tersebut</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#chmod 755 /etc/cron.daily/ntpdate</b><b>&nbsp;</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
How to ( FreeBSD )?</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
1. Install ntp</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>lonurhazve# pkg_add -rv ntp</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div class="separator" style="clear: both; font-family: Arial,Helvetica,sans-serif; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhXpo57tlzh6icZ6ZOBRiLyRIGLE8U17w5leQfE8HR5R1knjGWau-Wb1pcyHCznlshQE7CDABBGqjjtZy97U-Qf4XVmxa0X_OJ-4pUs_dKzDBT7nEmuJtniANRtKvNxXTdHsm4Pmu_YHw/s1600/ntpfbsd" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhXpo57tlzh6icZ6ZOBRiLyRIGLE8U17w5leQfE8HR5R1knjGWau-Wb1pcyHCznlshQE7CDABBGqjjtZy97U-Qf4XVmxa0X_OJ-4pUs_dKzDBT7nEmuJtniANRtKvNxXTdHsm4Pmu_YHw/s400/ntpfbsd" width="400" /></a></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b></b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b><br />
</b>ATAU '</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>lonurhazve#cd /usr/ports/net/ntp</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>lonurhazve#make; make install</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b> </b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
2. Set date :</div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<b>lonurhazve#ntpdate -v -b ntp.jaring.my</b></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<pre></pre>
3. <u>Run ntpdate masa boot ( tambah dalam rc.conf ) </u>&nbsp; </div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<pre></pre>
<div style="text-align: justify;">
<b>lonurhazve#vi /etc/rc.conf</b></div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
<b>------------------------------------------------------------------------------------------------------------------</b></div>
<div style="text-align: justify;">
<b></b></div>
<div style="text-align: justify;">
<b># -- sysinstall generated deltas -- # Sun Oct 18 16:43:04 2009<br />
# Created: Sun Oct 18 16:43:04 2009<br />
# Enable network daemons for user convenience.<br />
# Please make all changes to this file, not to /etc/defaults/rc.conf.<br />
# This file now contains just the overrides from /etc/defaults/rc.conf.<br />
defaultrouter="10.2.0.10"<br />
hostname="lonurhazve.net"<br />
ifconfig_rl0="inet 10.2.0.20&nbsp; netmask 255.255.255.0"<br />
keymap="us.iso"<br />
linux_enable="YES"<br />
sshd_enable="YES"<br />
ddclient_enable="YES"<br />
ddclient_flags="-daemon 600"<br />
nginx_enable="YES"<br />
mysql_enable="YES"<br />
php_fpm_enable="YES"</b></div>
<div style="text-align: justify;">
#tambah&nbsp; line berikut<b><br />
</b></div>
<div style="text-align: justify;">
<b>ntpdate_enable="Yes"</b></div>
<div style="text-align: justify;">
<b>ntpdate_hosts="ntp.jaring.my"</b></div>
<div style="text-align: justify;">
<b style="font-family: Arial,Helvetica,sans-serif;"><code></code></b><b>----------------------------------------------------------------------------------------------------------------------------</b></div>
<div style="text-align: justify;">
<b><br />
</b></div>
<div style="text-align: justify;">
Save dan Reboot<br />
* PASTIKAN PORT 123 DIBUKA PADA FIREWALL </div>
<b> </b><br />
<pre></pre>
</div>
