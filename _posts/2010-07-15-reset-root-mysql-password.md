---
title: "Reset Root MYSQL Password"
date: 2010-07-15
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGURyaIaxVqgks6RqhyjM86y4mQgWhjYaP11TQPfW4neXAd4XkOHDqXb-anf6tJioQd4U4rgMdzQEs1r8C9VllcQVyLRyrNmRrz6BnQYf4Qm5QCiiuL3dXAE7S3nIXbFhBVMABHekR7g/s1600/logomysql.gif" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="133" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGURyaIaxVqgks6RqhyjM86y4mQgWhjYaP11TQPfW4neXAd4XkOHDqXb-anf6tJioQd4U4rgMdzQEs1r8C9VllcQVyLRyrNmRrz6BnQYf4Qm5QCiiuL3dXAE7S3nIXbFhBVMABHekR7g/s200/logomysql.gif" width="200" /></a></div>
<br />
<u>Stop Service Mysql</u><br />
<br />
<b>lnz@lonurhazve:~# /etc/init.d/mysql stop</b><span style="color: blue; font-size: x-small;">&nbsp;* Stopping MySQL database server mysqld&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="font-size: x-small;"><span style="color: blue;">&nbsp;&nbsp;&nbsp; [ OK ]</span></span> &nbsp; <br />
<b>lnz@lonurhazve:~# mysqld --skip-grant-tables &amp;</b><span style="font-size: x-small;"><span style="color: blue;">[1] 20084</span></span><br />
<span style="font-size: x-small;"><span style="color: blue;">100815 12:21:28&nbsp; InnoDB: Started; log sequence number 0 43675</span><br style="color: blue;" /><span style="color: blue;">100815 12:21:28 [Note] mysqld: ready for connections.</span><br style="color: blue;" /><span style="color: blue;">Version: '5.0.51a-3ubuntu5.5'&nbsp; socket: '/var/run/mysqld/mysqld.sock'&nbsp; port: 3306&nbsp; (Ubuntu)</span></span><b><span style="font-size: x-small;"><br style="color: blue;" /></span></b><br />
<br />
<br />
<u>Login Mysql Tanpa Password</u><br />
<br />
<b>lnz@lonurhazve:~# mysql -u root mysql</b><span style="font-size: x-small;"><span style="color: blue;">Reading table information for completion of table and column names</span><br style="color: blue;" /><span style="color: blue;">You can turn off this feature to get a quicker startup with -A</span><br style="color: blue;" /><br style="color: blue;" /><span style="color: blue;">Welcome to the MySQL monitor.&nbsp; Commands end with ; or \g.</span><br style="color: blue;" /><span style="color: blue;">Your MySQL connection id is 1</span><br style="color: blue;" /><span style="color: blue;">Server version: 5.0.51a-3ubuntu5.5 (Ubuntu)</span><br style="color: blue;" /><br style="color: blue;" /><span style="color: blue;">Type 'help;' or '\h' for help. Type '\c' to clear the buffer.</span></span><br />
<span style="font-size: x-small;"></span><br />
<br />
<u>Reset Password Root</u><br />
<br />
<b>mysql&gt; UPDATE user SET Password=PASSWORD('pass-baru') WHERE User='root'; FLUSH PRIVILEGES; exit;</b><br />
<span style="color: blue; font-size: x-small;">Query OK, 3 rows affected (0.00 sec)<br />
Rows matched: 3&nbsp; Changed: 3&nbsp; Warnings: 0<br />
<br />
Query OK, 0 rows affected (0.00 sec)<br />
<br />
Bye</span><br />
<span style="color: blue; font-size: x-small;"></span><br />
<span style="color: blue; font-size: x-small;"></span><br />
<span style="color: blue; font-size: x-small;"><br />
</span><u>Restart</u><b> </b><br />
<b>lnz@lonurhazve:~# /etc/init.d/mysql restart</b>
