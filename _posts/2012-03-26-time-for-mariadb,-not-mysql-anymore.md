---
title: "Time For MariaDB, Not Mysql Anymore"
date: 2012-03-26
---
<code></code><br />
<u><code><b>Installation Mysql Server On Ubuntu 10.04 LTS ( Lucid ) Server</b> </code></u><br />
<br />
<code></code><br />
<code><i>( On root permission or sudo )</i> </code><br />
<br />
<br />
<code></code><br />
<br />
<b><u><code>Langkah 1 : </code></u></b><br />
<br />
<code>Masukkan keyserver to keyserver.ubuntu.com</code><br />
<code>&nbsp;</code><br />
<code>apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1BB943DB</code><br />
<br />
<u><b><code>Langkah 2 :</code></b></u><br />
<code>Buat repository baru sebagaiamana berikut:</code><br />
<code>&nbsp;</code><br />
<code>vi /etc/apt/sources.list.d/mariadb.list</code><code> </code><br />
<br />
<code></code><br />
<u><b><code>Langkah 3 : </code></b></u><br />
<code>Masukkan repo berikut dalam fail mariadb.list dan save: </code><br />
<br />
<code></code><code>deb http://mirror2.hs-esslingen.de/mariadb/repo/5.3/ubuntu lucid main<br />deb-src http://mirror2.hs-esslingen.de/mariadb/repo/5.3/ubuntu lucid main</code><br />
<code></code><br />
<br />
<u><b><code>Langkah 4 :</code></b></u><br />
<code>Upadate dan Install guna apt-get :</code><br />
<code></code><b><code><br /></code></b><br />
<code></code><code>sudo apt-get update</code><code>&nbsp;</code><br />
<code>sudo apt-get install mariadb-server mariadb-client</code><br />
<code><br /></code><br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgN1kuwPGkOfeXahdX28-7zRpOe-QOdpgyeYFSDHLNwULq8RCDdfuy-faODwoySEUZszS-9RX7J74pES1YKD9cOqIwRLrwrJt3XqOurkNIBMY1lEu9dwDOqsaFYWVpSD3qWqmsuwiUzBg/s1600/mdbinstall.jpg" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" height="298" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgN1kuwPGkOfeXahdX28-7zRpOe-QOdpgyeYFSDHLNwULq8RCDdfuy-faODwoySEUZszS-9RX7J74pES1YKD9cOqIwRLrwrJt3XqOurkNIBMY1lEu9dwDOqsaFYWVpSD3qWqmsuwiUzBg/s640/mdbinstall.jpg" width="640" /></a></div>
<code><br /></code>
