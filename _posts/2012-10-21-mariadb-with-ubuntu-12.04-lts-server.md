---
title: "MariaDB With Ubuntu 12.04 LTS Server"
date: 2012-10-21
---
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
:~# echo -e "# MariaDB repository list - created 2012-06-17 16:25 UTC\n# http://downloads.mariadb.org/mariadb/repositories/\ndeb http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu precise main\ndeb-src http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu precise main" &gt; /etc/apt/sources.list.d/MariaDB.list</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
IMPORT GP KEY</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 1BB943DB</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
INSTALL</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
apt-get update &amp;&amp; apt-get -y install mariadb-server-5.5 mariadb-common mariadb-client</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
SECURE</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
apt-get update &amp;&amp; apt-get -y install mariadb-server-5.5 mariadb-common mariadb-client</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
Enter current password for root (enter for none): yoursecurepassword<br />
Change the root password? N<br />
Remove anonymous users? Y<br />
Disallow root login remotely? Y<br />
Remove test database and access to it? Y<br />
Reload privilege tables now? Y&nbsp;</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
RESTART</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
service mysql restart</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
COMFIRM RUNNING</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
netstat -tap | grep mysql<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
&nbsp;</div>

