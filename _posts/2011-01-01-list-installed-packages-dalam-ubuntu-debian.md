---
title: "List Installed Packages Dalam Ubuntu/Debian"
date: 2011-01-01
---
1. List Currently Installed Packages<br />
<br />
<br />
<pre>$ dpkg --get-selections
adduser                                         install
alsa-base                                       install
alsa-utils                                      install
apache2                                         install
apache2-mpm-prefork                             install
apache2-utils                                   install
apache2.2-common                                install
apt                                             install
apt-utils                                       install</pre><pre>&nbsp;</pre><pre>2. dpkg --get-selections | grep php</pre><pre>&nbsp;</pre><pre>3. Tengok Lokasi Fail package yang install</pre><pre>&nbsp;</pre><pre>dpkg -L php5-gd
/.
/usr
/usr/lib
/usr/lib/php5
/usr/lib/php5/20060613
/usr/lib/php5/20060613/gd.so
/usr/share
/usr/share/doc
/etc
/etc/php5
/etc/php5/conf.d
/etc/php5/conf.d/gd.ini
/usr/share/doc/php5-gd
 </pre>
