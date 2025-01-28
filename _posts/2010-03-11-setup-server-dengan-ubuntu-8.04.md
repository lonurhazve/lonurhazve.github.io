---
title: "Setup Server Dengan Ubuntu 8.04"
date: 2010-03-11
---
<div style="text-align: justify;">Download dan Install ubuntu yang paling basic.</div><div style="text-align: justify;">______________________________________________________________________________________</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Update terlebih dahulu server yang baru di install;</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#aptitude</b><b> update &amp;&amp; apt-get dist-upgrade</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Selepas update dan upgrade, reboot server :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#shutdown -r now</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Install openssh-server</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#aptitude</b><b> install openssh-server</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Webserver memerlukan software webserver seperti apache, nginx, lighttpd dsb. Kebanyakan menggunakan apache<b>. </b>Sebagai tambahan<b> </b>webserver juga memerlukan database server seperti MySQL dan server-side language seperti PHP.</div><div style="text-align: justify;">Semua program tersebut perlu di install:</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Semasa proses installation MySQL akan meminta untuk dimasukkan&nbsp; katalaluan untuk root MySQL.Jangan tinggalkan kosong untuk katalaluan tersebut.</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Setelah selesai intallation sebenar kita dah dapat webserver dan database server secara asasnya. Walaubagaimanapun beberapa konfigurasi perlu dibuat.</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Buat konfigurasi pada apache :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#pico /etc/apache2/apache2.conf</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Tukarkan <b>ServerTokens Full </b>kepada <b>ServerTokens Prod<br />
</b>Tukarkan <b>ServerSignature On</b> kepada <b>ServerSignature Off</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b> </b>dan<b> </b>simpan<b> tekan Ctrl O dan Ctrl X</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Konfigurasi pada php.ini</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b># pico /etc/php5/apache2/php.ini</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Tukarkan <b>expose_php</b> = On kepada <b>expose_php = Off</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">dan<b> </b>simpan tekan Ctrl O dan Ctrl X</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Restart apache :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#/etc/init.d/apache2 restart</b></div><div style="text-align: justify;">Ini merupakan konfigurasi asas pada php dan apache.</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Install firewall :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Untuk menutup port2 yang tidak diperlukan firewall diperlukan. Firewall yang boleh digunakan ialah shorewall ( command-line firewall ).</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#</b> <b>aptitude install shorewall</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Setelah selesai install beberapa konfiurasi pada firewall perlu dibuat :</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">copy semua fail berikut&nbsp; /usr/share/doc/shorewall-common/examples/one-interface/* ke dalam /etc/shorewall/</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">buka fail rule pada /etc/shorewall<b> </b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#pico /etc/shorewall/rules</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Tambah rules sebagai berikut untuk menutup semua connection kecuali port 80 (http) dan 22 ( SSH ):</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>HTTP/ACCEPT net  $FW</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>SSH/ACCEPT net  $FW</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">dan<b> </b>simpan tekan Ctrl O dan Ctrl X</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Setelah itu, untuk membolehkan firewall start dan boot konfigurasi pada file shorewall perlu dibuat.</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#pico /etc/shorewall/shorewall.conf</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">tukarkan <b>STARTUP_ENABLED=No</b> kepada <b>STARTUP_ENABLED=Yes</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">dan<b> </b>simpan tekan Ctrl O dan Ctrl X</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Buka fail /etc/default/shorewall</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Tukar <b>startup=0</b> kepada <b>startup=1</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">dan<b> </b>simpan tekan Ctrl O dan Ctrl X</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Restart firewall</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b>#/etc/init.d/shorewall start</b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Itu saja untuk asas webserver.</div>
