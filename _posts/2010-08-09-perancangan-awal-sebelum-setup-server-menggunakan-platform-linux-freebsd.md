---
title: "Perancangan Awal Sebelum Setup Server Menggunakan Platform Linux/FreeBSD"
date: 2010-08-09
---
<div style="text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" /></a></div>
<br />
Installation platform linux / freeBSD amat mudah dan boleh dilakukan secara default sekiranya kita ingin menggunakannya untuk kegunaan desktop tetapi untuk dijadikan server beberapa perkara perlu diberi perhatian. Ini melibatkan keselamatan pada server tersebut, mudah untuk menyelenggara dan juga keperluan server. Antaranya :</div>
<div style="text-align: justify;">
</div>
<ul>
<li>Diagram kedudukan server dalam rangkaian </li>
</ul>
<ul>
<li>Jenis server yang&nbsp; yang hendak dibangunkan, samada webserver, mail server, ftp server, firewall, proxy, dns server atau file server</li>
</ul>
<br />
<ul>
<li>Tentukan aplikasi yang perlu dipasang pada sistem tersebut </li>
</ul>
<ul>
<li>Sekiranya server ini menggunakan RAID tentukan jenis RAID yang sesuai digunakan</li>
</ul>
<ul>
<li>&nbsp;Tentukan partition dan size hardisk&nbsp; yang perlu di allocate untuk setiap&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; path</li>
</ul>
<ul></ul>
<ul>
<li>Tentukan komponen linux/freeBSD yang perlu sahaja akan dipasang </li>
</ul>
<div style="text-align: justify;">
<br />
<u><b>Partition</b></u></div>
<div style="text-align: justify;">
<br />
Semasa install linux/freeBSD kita boleh buat partition dengan cara mudah iaitu menggunakan kaedah auto/default, kalau FreeBSD kita hanya tekan "a" untuk buat partition. Tapi partition yang dibuat secara auto biasanya hanya sesuai untuk persekitaran workstation/desktop. Biasanya kalau default/auto partition saiz yang diberikan kepada /var ( tempat simpannya log ) amat kecil. Server memerlukan tempat simpan log yang besar. Adalah lebih baik kita buat partition secara manual dan tentukan sendiri path yang hendak digunakan.<br />
<br />
<br />
<br />
<u><b>Apa yang perlu Install</b></u> </div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Pemasangan minima sistem linux/freeBSD adalah terbaik untuk internet-facing server. Semasa installation linux/FreeBSD, kita perlulah memilih pemasangan yang minima pada menu installation. Sebarang pertambahan keperluan akan dipasang selepas pemasangan sistem operasi. Sistem server tidak memerlukan overhead pada package yang tidak digunakan. Ini akan melumpuhkan tahap keselamatan server dan operasi server. Sebarang dokumen atau manual tidak diperlukan untuk server production anda. Sebarang aktiviti pada server haruslah dilakukan melalui shell command ( X tidak diperlukan ). Sekiranya perlukan juga cuba install webmin yang akan membantu anda buat konfigurasi melalui web base tapi limitkan capaiannya pada port dan client tertentu sahaja ( adalah lebih baik dilakukan secara manual ).</div>
<div style="text-align: justify;">
<br />
<br />
Sebagai contoh :Pemasangan FreeBSD, kita tidak memerlukan seluruh port untuk pastikan port sentiasa up-to-date. Tetapi kita perlukan <b>src</b> file agar kita boleh recompile kernel dan incorporate sebarang perubahan pada sistem operasi apabila adanya updating baru.<span class="long_text" id="result_box"><span title="If"> Install package&nbsp;</span></span><b>src</b><span class="long_text" id="result_box"><span title="If"> adalah lebih cepat berbading download semua senarai package src menggunakan <b>cvsup</b>. <b>cvsup </b>akan download semua package untuk update termasuk yang tidak diperlukan. </span></span></div>
