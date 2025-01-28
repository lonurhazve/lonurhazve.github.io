---
title: "Installation Owncloud"
date: 2017-04-21
---
<br />
<br />
<br />
<br />
<br />
Install Webserver dan MariaDB<br />
<br />
<b>#apt install apache2 mariadb-server php7.0 php7.0-common libapache2-mod-php7.0 php7.0-gd php-xml-parser php7.0-json php7.0-curl php7.0-bz2 php7.0-zip php7.0-mcrypt php7.0-mysql php7.0-mbstring memcached php-memcached php-redis redis-server</b><br />
<b><br /></b>
<b><br /></b>
<b>Konfigurasi webserver</b><br />
<b><br /></b>
Pastikan index.php berada di hadapan sekali dalam file dir.conf.<br />
<br />
#vi /etc/apache2/mods-enabled/dir.conf<br />
<br />
<b>---------------------------------------dir.conf-------------------------------------------------------------------------</b><br />
<b><ifmodule mod_dir.c=""></ifmodule></b><br />
<b>&nbsp; &nbsp; DirectoryIndex index.php index.html</b><br />
<b></b><br />
<br />
<br />
<br />
<b>Meningkatkan performance apache webserver&nbsp;</b><br />
<b><br /></b>
Edit global configuration apache seper berikut :<br />
<br />
#vi&nbsp;/etc/apache2/apache2.conf<br />
<br />
<b>------------------------------------apache2.conf---------------------------------------------------------------------</b><br />
<b>Timeout 20</b><br />
<b>KeepAliveTimeout 100</b><br />
<b>MaxKeepAliveRequests 200</b><br />
<b><br /></b>
<b><br /></b>
