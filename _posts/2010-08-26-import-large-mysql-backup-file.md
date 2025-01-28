---
title: "Import Large Mysql Backup File"
date: 2010-08-26
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGURyaIaxVqgks6RqhyjM86y4mQgWhjYaP11TQPfW4neXAd4XkOHDqXb-anf6tJioQd4U4rgMdzQEs1r8C9VllcQVyLRyrNmRrz6BnQYf4Qm5QCiiuL3dXAE7S3nIXbFhBVMABHekR7g/s1600/logomysql.gif" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="133" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGURyaIaxVqgks6RqhyjM86y4mQgWhjYaP11TQPfW4neXAd4XkOHDqXb-anf6tJioQd4U4rgMdzQEs1r8C9VllcQVyLRyrNmRrz6BnQYf4Qm5QCiiuL3dXAE7S3nIXbFhBVMABHekR7g/s200/logomysql.gif" width="200" /></a></div>
&nbsp;Perlu configure fail php.ini dan my.cnf mengikut saiz fail yang hendak di import. Cth fail mysql bersaiz 100mb, perkara berikut perlu di ubah :<br />
<br />
<u>php.ini</u><br />
<br />
post_max_size = <b>100M</b><br />
upload_max_filesize = <b>100M</b>max_execution_time = 1000<br />
memory_limit = 128M - Bergantung pada RAM Server<br />
<br />
<br />
<u>my.cnf</u><br />
<br />
max_allowed_packet = <b>100M</b><br />
<b><br />
</b><br />
upload file menggunakan phpmyadmin<b>. </b>Adalah lebih baik menggunakan shell command untuk upload file mysql bersaiz besar sekiranya dapat access shell.<br />
<br />
lonurhazve#<b>mysql -u root -p <i>database_name</i> &gt;dababase_nak_import.sql</b>
