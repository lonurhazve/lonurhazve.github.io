---
title: "ddclient Install dan Configure - FreeBSD"
date: 2010-08-10
---
<div style="text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" /></a></div>
<br />
<b><u>ddclient</u></b> ? - Sekiranya anda tidak mempunyai fixed ip dan hanya menggunakan&nbsp; dinamik ip&nbsp; ( ip sentiasa berubah ) anda masih boleh membangunkan server dengan sentiasa update ip anda pada server dns dinamik. Ini amat berguna sekiranya anda ingin membangunkan server dan ditempatkan dirumah anda sendiri dengan hanya menggunakan talian streamyx biasa yang tidak mempunyai fixed ip. ddclient merupakan opensource dynamic ip update yang boleh digunakan untuk update automatik ip anda setelah bertukar dari masa ke semasa kepada server dns yang digunakan. Server dynamic dns yang biasa digunakan ialah opendns, zoneedit, dynDNS.org dan sebagainya. Anda terlebih dahulu perlu untuk mendaftar akaun pada server dns tersebut.</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Server anda --update ip---&gt; server dns &lt;----domain anda ( lnz.net )---- client</div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
<br />
<b><u>Kaedah Install dan Configure</u></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
FreeBSD </div>
<div style="text-align: justify;">
<br />
<u>Langkah 1: Install ddclient</u></div>
<div style="text-align: justify;">
<br />
<b>lonurhazve#cd /usr/ports/dns/ddclient </b></div>
<div style="text-align: justify;">
<b>lonurhazve#make install clean</b><br />
<br />
@<b> </b><br />
<br />
<b>lonurhazve# pkg_add -r ddclient</b><br />
<b><span style="color: blue; font-size: x-small;">Fetching ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-8.1-release/Latest/ddclient.tbz... Done.<br />
Fetching ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-8.1-release/All/p5-Net-SSLeay-1.36.tbz... Done.<br />
Fetching ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-8.1-release/All/p5-IO-Socket-SSL-1.33.tbz... Done.<br />
<br />
***********************************************************<br />
<br />
Copy<br />
&nbsp;&nbsp;&nbsp; /usr/local/etc/ddclient.conf.sample<br />
to<br />
&nbsp;&nbsp;&nbsp; /usr/local/etc/ddclient.conf<br />
<br />
and edit it to fit your needs.<br />
<br />
If you would like to run ddclient as a daemon add the<br />
following line to /etc/rc.conf<br />
<br />
&nbsp;&nbsp;&nbsp; ddclient_enable="YES"<br />
<br />
***********************************************************</span>&nbsp;</b><br />
<b>lonurhazve# pkg_info -ox ddclient<br />
<span style="color: blue; font-size: x-small;">Information for ddclient-3.8.0:<br />
<br />
Origin:<br />
dns/ddclient</span>&nbsp;</b><br />
<br />
<b>lnz# porteasy -u dns/ddclient<br />
<span style="color: blue; font-size: x-small;">U dns/Makefile<br />
U ddclient/Makefile<br />
U ddclient/distinfo<br />
U ddclient/pkg-descr<br />
U ddclient/files/ddclient.in<br />
U ddclient/files/pkg-message.in<br />
U security/Makefile<br />
U p5-IO-Socket-SSL/Makefile<br />
U p5-IO-Socket-SSL/distinfo<br />
U p5-IO-Socket-SSL/pkg-descr<br />
U p5-IO-Socket-SSL/pkg-plist<br />
U p5-Net-SSLeay/Makefile<br />
U p5-Net-SSLeay/distinfo<br />
U p5-Net-SSLeay/pkg-descr<br />
U p5-Net-SSLeay/pkg-plist<br />
U p5-Net-SSLeay/files/patch-SSLeay.pm</span></b><br />
<br />
<b>lonurhazve#rehash</b><u><br />
</u></div>
<div style="text-align: justify;">
<u><br />
</u><br />
<u>Langkah 2 : Copy fail fail configure ddclient</u><br />
<br />
<b>lonurhazve#cp /usr/local/etc/ddclient.conf.sample /usr/local/etc/ddclient.conf</b></div>
<div style="text-align: justify;">
<br />
<u>Langkah 3 : Configure</u><br />
<br />
Configure File ddclient dalam /usr/local/etc/ddclient.conf :</div>
<div style="text-align: justify;">
( guna zoneedit )<br />
--------------------------------------------------------------------------------------------------------------------<br />
<div style="color: blue;">
<span style="font-size: x-small;">daemon=300&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></div>
<div style="color: blue;">
<span style="font-size: x-small;">syslog=yes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></div>
<div style="color: blue;">
<span style="font-size: x-small;">mail=root</span></div>
<div style="color: blue;">
<span style="font-size: x-small;">mail-failure=root <br />
pid=/var/run/ddclient.pid <br />
ssl=yes&nbsp;&nbsp; </span></div>
<div style="color: blue;">
<span style="font-size: x-small;"><br />
</span></div>
</div>
<div style="color: blue; text-align: justify;">
<span style="font-size: x-small;">## LONURHAZVE<br />
protocol=zoneedit1<br />
use=web, web='http://www.zoneedit.com/checkip.html/', web-skip='Current IP Address:'<br />
server=dynamic.zoneedit.com<br />
login=<username-zoneedit-anda><login-akaun><br />
password=<passwd-akaun><passwd-zoneedit-anda><br />
lonurhazve.net,lnz.net &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </passwd-zoneedit-anda></passwd-akaun></login-akaun></username-zoneedit-anda></span></div>
-------------------------------------------------------------------------------------------------------------------<br />
<br />
<u>Langkah 4 : Setting Autostart ddclient pada rc.conf</u><br />
<br />
<div style="text-align: justify;">
<b>lonurhazve#pico /etc/rc.conf</b><br />
<br />
Tambah dalam fail rc.conf<br />
<br />
<span style="color: blue; font-size: x-small;">ddclient_enable=YES</span><br />
<br /></div>
<div style="text-align: justify;">
Langkah 5 : Start ddclient</div>
<div style="text-align: justify;">
<br />
<b>lonurhazve#/usr/local/etc/rc.d/ddclient start</b></div>
<div style="text-align: justify;">
<br />
-test run ddclient -<br />
<br /></div>
<code class="bash plain"></code><b> </b><br />
<b>lonurhazve#ddclient -daemon=0 -debug -verbose -noquiet . ddclient -daemon=0 -debug -verbose -noquiet</b>
