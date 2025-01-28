---
title: "Upgrading Software Install Pada Server ( FreeBSD )"
date: 2010-08-14
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" /></a></div>
<br />
<u><b>Langkah 1&nbsp;</b></u><br />
Untuk mudah, buat satu fail script untuk periksa sama ada software perlu upgrade atau tidak . Cth :<br />
<br />
Pastikan :<br />
a)Fail cvs-supfile dah ada yang mengandungi konfigurasi berikut :<br />
<br />
<span style="color: blue; font-size: x-small;">*default host=cvsup.tw.freebsd.org<br />
*default base=/usr/local/etc/cvsup<br />
*default prefix=/usr<br />
*default tag=RELENG_8_1<br />
*default release=cvs delete use-rel-suffix compress<br />
src-all</span><br />
<br />
dalam cth ni saya letak fail tsbt dalam /root/urus/.cvs-supfile<br />
&nbsp; <br />
b) Pastikan porteasy dan portupgrade ( ports management ) di install<br />
<br />
<u>Tulis script untuk check software perlu upgrade</u><br />
lonurhazve#pico /root/urus/.periksa_software<br />
Masukkan script berikut :<br />
<b><span style="color: blue; font-size: x-small;">#!/bin/sh<br />
# periksa fail .cvs-supfile<br />
&nbsp;</span></b><br />
<b><span style="color: blue; font-size: x-small;">cvsup -L2 /root/.bin /.cvs-supfile</span></b><br />
<b><span style="color: blue; font-size: x-small;"><br />
# Download index port terbaru dan check pada software yang dah install<br />
&nbsp;</span></b><br />
<b><span style="color: blue; font-size: x-small;">cd /usr /ports<br />
make fetchindex<br />
portsdb -u<br />
&nbsp;</span></b><br />
<b><span style="color: blue; font-size: x-small;"># Beritahu software yang perlu upgrade</span></b><br />
<b><span style="color: blue; font-size: x-small;"><br />
echo "Ports berikut perlu di upgrade"<br />
portversion -l "&lt;"</span></b><br />
<br />
*Execute Script<br />
#chmod 700 .periksa_software<br />
#./.periksa_software<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhsbSROWp7fsFFMiyojbxjGaNCMp-UkTklyzvzqsQPWs0rr12m3hR9wI7LmDg36N8MjSD-f2ACBo35vAZJP6UdvRX0dkxDMC4d89bmW6VqRqYXysg7MvfACRdSZhcnHjIh_i4oBav3jsg/s1600/update.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhsbSROWp7fsFFMiyojbxjGaNCMp-UkTklyzvzqsQPWs0rr12m3hR9wI7LmDg36N8MjSD-f2ACBo35vAZJP6UdvRX0dkxDMC4d89bmW6VqRqYXysg7MvfACRdSZhcnHjIh_i4oBav3jsg/s400/update.png" width="400" /></a></div>
<br />
<br />
<b><u>Langkah 2</u></b><br />
Upgrade Software :<br />
<br />
a) Guna porteasy command untuk download port skeletons yang perlu<br />
b) Guna portupgrade command untuk bagitahu supaya upgrade mana-mana dependencies pada software.<br />
<br />
Cth nak upgrade software php5 :<br />
<br />
<b>lonurhazve#cd /usr</b><br />
<b>lonurhazve#porteasy -u lang/php5</b><br />
<b>lonurhazve#portupgrade -rR php5</b>
