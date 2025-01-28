---
title: "Checklist dan Kaedah Untuk Hardening Webserver ( Apache + Php )"
date: 2010-03-23
---
<div style="text-align: justify;">Untuk memastikan server yang menggunakan apache berada pada tahap yang memuaskan perkara berikut perlu dilakukan selepas default installation:</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b><span style="text-decoration: underline;">1. Jangan benarkan maklumat server dan apache (spt: version, service yang digunakan/mod ) terdedah kepada umum.</span></b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Langkah :&nbsp; Edit fail security || UBUNTU : /etc/apache2/conf.d/security tukarkan ServerToken dan ServerSignature sebagaimana berikut :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>ServerToken Prod<br />
ServerSignature Off</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Untuk test server anda memaparkan maklumat tersebut cuba guna command :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#telnet &lt;domain anda&gt;&nbsp; 80</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>Trying &lt;domain anda&gt;…<br />
Connected to &lt;domain anda&gt;.<br />
Escape character is ‘^]’.<br />
HEAD / HTTP/1.0            &lt;- after this press 2 times ENTER</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>HTTP/1.1 200 OK<br />
Date: Tue, 23 Mar 2010 03:59:15 GMT<br />
Server: Apache/2.0.55 (Debian) PHP/5.1.2-1+b1 mod_ssl/2.0.55 OpenSSL/0.9.8b<br />
Connection: close<br />
Content-Type: text/html; charset=iso-8859-1<br />
</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">JIKA MAKLUMAT TIDAK DIPAPARKAN IANYA AKAN PAPARKAN SEBAGAIMANA BERIKUT :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>HTTP/1.1 403 Forbidden<br />
Date: Tue, 23 Mar 2010 03:59:15 GMT<br />
Server: Apache<br />
Connection: close<br />
Content-Type: text/html; charset=iso-8859-1</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>Connection closed by foreign host.</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span style="text-decoration: underline;"><b>2. Tidak Membenarkan Browsing pada Directory/file dan Option Yang Tidak Diperlukan </b></span></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Langkah :&nbsp; Edit pada fail httpd ( UBUNTU : default/http ) atau tambah/tukar pada virtual hosting configuration</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Tambahkan "-" Minor pada setiap option yang tidak digunakan</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>-ExecCGI : Jika Tidak Gunakan CGI</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>-Includes :&nbsp; Matikan server side includes</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>-FollowSymLinks</b> : <b>Tidak Membenarkan </b><b>apache follow symbolic links</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>ATAU </b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Turn OFF Semua Option</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>Options None</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>ATAU </b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>Options -Indexes -FollowSymLinks -ExecCGI -Includes<br />
</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span style="text-decoration: underline;"><b>3. Enable Mod Rewrite pada Apache</b></span></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Langkah : <b>UBUNTU#a2enmod rewrite</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">dan</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Elakkan Cross-Site-Tracing attack. Tambahkan code dibawah diantara " <b>&lt;VirtualHost *:80&gt;</b>" :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">4.&nbsp; <b><span style="text-decoration: underline;">Install module Mod Evasive ( libapache2-mod-evasive ) untuk elakkan daripada HTTP DoS, DDoS / Brute Force attack.</span></b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b><span style="text-decoration: underline;">5. Configure php.ini sebagaimana berikut :</span></b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>display_errors = Off<br />
log_errors = On<br />
allow_url_fopen = Off<br />
safe_mode = On<br />
expose_php = Off<br />
enable_dl = Off<br />
disable_functions = system, show_source, symlink, exec, dl, shell_exec, passthru, phpinfo, escapeshellarg, escapeshellcmd</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span style="text-decoration: underline;"><b>6. Pastikan Apache Running Atas Akaun dan Groupnya Sendiri</b></span><br />
<br />
<u><b>7. Install Mod Security Untuk Elakkan Sql Injection</b></u><br />
<br />
<b>lonurhazve#wget http://www.modsecurity.org/download/modsecurity-apache_2.5.12.tar.gz</b><br />
<br />
<b>lonurhazve#aptitude install build-essential gcc g++</b><br />
<b> </b><br />
<b>lonurhazve#tar xzvf modsecurity-apache_2.5.12.tar.gz</b><br />
<br />
<b>lonurhazve#cd modsecurity-apache_2.5.12/apache2</b>/<br />
<br />
<br />
Install&nbsp;<b> </b>apache apxs<b><br />
</b><br />
<b>lonurhazve#apt-get install apache2-threaded-dev</b><br />
<br />
Install libxml2<br />
<b> lonurhazve#apt-get install libxml2-dev</b><br />
<br />
Install libcurl4-gnutls-dev&nbsp; <b><br />
</b><br />
<b>lonurhazve#apt-get install libcurl4-gnutls-dev</b><br />
<br />
Install liblua5.1<b>&nbsp;</b><br />
<b>lonurhazve#apt-get install \<br />
build-essential lua5.1 liblua5.1-0 liblua5.1-0-dev \<br />
liblua5.1-socket2 liblua5.1-socket-dev \<br />
libssl-dev libssl0.9.8</b><br />
<b><br />
</b><br />
Install liblua-sec ( Secara manual bagi ubuntu 8.04 )<br />
<br />
<b>lonurhazve#wget http://mirror.ne.gov/ubuntu/pool/universe/l/lua-sec/liblua5.1-sec1_0.4-3_i386.deb<br />
lonurhazve#dpkg -i liblua5.1-sec1_0.4-3_i386.deb</b><br />
<b><br />
</b><br />
<b> </b><br />
<b>lonurhazve#./configure</b><br />
<br />
<b>lonurhazve#make install</b><br />
<br />
<b>lonurhazve#pico /etc/apache2/mods-available/mod-security2.load</b><br />
<b> </b><br />
<b>Masukkan arahan berikut :</b><br />
<br />
<span style="color: blue; font-size: x-small;"><b>LoadFile /usr/lib/libxml2.so<br />
LoadFile /usr/lib/liblua5.1.so<br />
LoadModule security2_module /usr/lib/apache2/modules/mod_security2.so </b></span><br />
<br />
<b>lonurhazve#a2enmod mod-security2</b><br />
<div style="color: blue;"><span style="font-size: x-small;"><b>Module mod-security2 installed; run /etc/init.d/apache2 force-reload to enable </b></span></div><b>lonurhazve#a2enmod unique_id </b><br />
<b><span style="color: blue; font-size: x-small;">Module unique_id installed; run /etc/init.d/apache2 force-reload to enable.</span></b><br />
<br />
<b>lonurhazve#pico /etc/apache2/conf.d/modsecurity2.conf</b><br />
Masukkan arahan berikut ( file konfigurasi akan diletakkan dalam /etc/modsecurity/&nbsp; ext: .conf:<br />
<span style="color: blue; font-size: x-small;"><ifmodule mod_security2.c=""><br />
&nbsp;&nbsp;&nbsp; Include /etc/modsecurity/*.conf</ifmodule></span><br />
<span style="color: blue; font-size: x-small;"></span><br />
<span style="color: blue; font-size: x-small;"><br />
</span>Buat dir dan fail untuk log<br />
<br />
<b>lonurhazve#mkdir /etc/modsecurity<br />
lonurhazve#mkdir /etc/modsecurity/logs<br />
lonurhazve#touch /etc/modsecurity/logs/modsec_audit.log<br />
lonurhazve#touch /etc/modsecurity/logs/modsec_debug.log</b><br />
<br />
Copy file rules yang ada dalam source mod security yang telah download tadi<br />
<br />
<b>lonurhazve#cp -Rv rules/* /etc/modsecurity/</b><br />
<br />
<br />
<b>lonurhazve#pico /etc/modsecurity/modsecurity_crs_10_config.conf</b><br />
<br />
Tambah arahan berikut :<br />
<br />
<span style="color: blue; font-size: x-small;">S</span><span style="color: blue; font-size: x-small;">ecAuditLog&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /etc/modsecurity/logs/modsec_audit.log<br />
SecDebugLog&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /etc/modsecurity/logs/modsec_debug.log</span><br />
<br />
Restart Apache<br />
<br />
<b>lonurhazve#/etc/init.d/apache2 restart</b><br />
<br />
Test<br />
<br />
<b>lonurhazve#cat /var/log/apache2/error.log | grep ModSecurity</b><span style="color: blue; font-size: x-small;">[Tue Aug 17 02:30:46 2010] [notice] ModSecurity for Apache/2.5.12 (http://www.modsecurity.org/) configured.</span>&nbsp;</div>
