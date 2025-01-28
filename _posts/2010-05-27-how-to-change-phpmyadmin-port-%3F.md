---
title: "How To Change phpmyadmin Port ?"
date: 2010-05-27
---
<div style="text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh087jQGQNCGf5PA6NMEGuy6nx5m5__ILR2D0oteByiWk-2TDYSuwFzJVv38AUEnKiEjnGHIj_3IHGQ6RG7X7XKe_LmB59riwjPFmVY7BDLU0sCLwcVGe8SurA5x7zMA7UyYfwVdxC4GA/s1600/phpmyadmin.gif" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="137" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh087jQGQNCGf5PA6NMEGuy6nx5m5__ILR2D0oteByiWk-2TDYSuwFzJVv38AUEnKiEjnGHIj_3IHGQ6RG7X7XKe_LmB59riwjPFmVY7BDLU0sCLwcVGe8SurA5x7zMA7UyYfwVdxC4GA/s200/phpmyadmin.gif" width="200" /></a>&nbsp;</div>
Installation phpmyadmin pada webserver adalah untuk memudahkan kita mengurus pengakalan data mysql secara web base. Tapi dengan intall phpmyadmin ni mungkin kita akan menghadapi masalah security. Salah satu cara untuk selesai masalah ini ialah dengan menukar port asalnya iaitu 80 kepada port lain.<br />
<br />
<u><b>Langkah-langkahnya adalah sebagaimana berikut (saya nak tukar default port 80 kepada port 7071) : </b></u><br />
<br />
1. Remove fail phpmyadmin.conf di /etc/apache2/conf.d/phpmyadmin.conf<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#rm /etc/apache2/conf.d/phpmyadmin.conf</b><br />
<br />
2. Tambah listen port 7071 pada /etc/apache2/ports.conf<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#vi /etc/apache2/ports.conf</b><br />
<br />
<b>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Listen 80<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Listen 7071<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <ifmodule mod_ssl.c=""><br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Listen 443<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </ifmodule></b><br />
<b></b><br />
3. Buat <b>/ </b>tambah virtual host baru pada /etc/apache2/sites-available/<br />
<b> </b><br />
<br />
<b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #vi /etc/apache2/sites-available/phpmyadmin</b><br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiZ1Ca21TY7NbCZ_4ef1uogJ-PlAeJ1NawQ3HzYCjSxkm8hsBLacR3wRrcTe1Seao1yifYg5Rfq_ZZxaluQTkIXYNLKG5SpnRh75p2ntMTDx59Nct-G6iFJNil5Eil5Hl2TtHQ_TMGhcg/s1600/porthttp" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="192" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiZ1Ca21TY7NbCZ_4ef1uogJ-PlAeJ1NawQ3HzYCjSxkm8hsBLacR3wRrcTe1Seao1yifYg5Rfq_ZZxaluQTkIXYNLKG5SpnRh75p2ntMTDx59Nct-G6iFJNil5Eil5Hl2TtHQ_TMGhcg/s400/porthttp" width="400" /></a></div>
&nbsp; &nbsp; &nbsp; &nbsp; <b>&nbsp; &nbsp;&nbsp; <virtualhost *:7071=""><virtualhost *:7071=""></virtualhost></virtualhost></b><br />
4. Enable site vhost phpmyadmin yang buat tadi<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#sudo a2ensite phpmyadmin --- &gt; </b>Ubuntu<b><br />
</b><br />
<b><br />
</b><br />
5. Buat symbolink kepada directory phpmyadmin<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>#cd /var/www/sqlurus<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #ln -s /usr/share/phpmyadmin/</b><br />
<b><br />
</b><br />
6. Restart semula apache dan cuba access ke <b>http://www.domainaku.com:7071/phpmyadmin</b> ( Pastikan&nbsp;&nbsp;&nbsp; port yang diperlukan dibuka pada firewall )<br />
<br />
<br />
<b>ATAU</b> <br />
<br />
Buka fail /etc/phpmyadmin/apache.conf<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEggw9IHcepYy_Zyo-A2dN3oIAfwv9jIIXv6QXNIoQ7UDtoA-57E7E7lcr_BEyk6_YxeRw3RvJLSGFooj4PzLN-4PTXNgLNkrxxPukX_26onLkyDP6FztmBEofaFp0I8ugVH2Y4i5iJOjQ/s1600/porthttp1" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="400" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEggw9IHcepYy_Zyo-A2dN3oIAfwv9jIIXv6QXNIoQ7UDtoA-57E7E7lcr_BEyk6_YxeRw3RvJLSGFooj4PzLN-4PTXNgLNkrxxPukX_26onLkyDP6FztmBEofaFp0I8ugVH2Y4i5iJOjQ/s400/porthttp1" width="320" /></a></div>
