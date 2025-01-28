---
title: "Webserver With FreeBSD + Nginx ( Engine X ) +  MYSQL + PHP"
date: 2010-08-03
---
<div style="text-align: justify;">Sebelum ini kebanyakan webserver saya gunakan apache, lighttpd sebagai enjin dan&nbsp; kebelakangan ini&nbsp; saya telah buat research tentang Nginx ( Engine X )&nbsp; yang merupakan&nbsp; salah satu alternatif kepada apache atau lighttpd. Nginx ini&nbsp; saya telah install pada FreeBSD 7.2-RELEASE untuk dijadikan webserver&nbsp; yang telah berjalan atas talian streamyx combo 384k dan menggunakan pc lama saya yang tidak&nbsp; digunakan. Webserver tersebut telah lama running iaitu pada bulan Ogos 2009 ( lebih kurang setahun ) dan so far tak ada masalah. Webserver ini juga telah digunakan sebagai hosting laman web pelancongan tempatan dan juga laman web persatuan alumni sekolah.&nbsp;</div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;">Nginx&nbsp; boleh dikonfigurasi sebagai high performance http dan reverse proxy server. Kelebihanya berbanding apache dan lighttpd ialah daemon yang baik, cara setup yang mudah dan jumlah option konfigurasi.<span class="long_text" id="result_box"><span title=""> Nginx  ditulis oleh Igor Sysoev untuk rambler.ru, halaman Russia kedua yang  paling banyak dikunjungi. Untuk permulaan, di sini saya tuliskan tips untuk dikongsi bersama setup webserver menggunakan Nginx running atas platform FreeBSD 7.2-RELEASE.</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><br />
</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><u><b>Langkah 1</b></u> ( Install FreeBSD 7.2-RELEASE )</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><br />
</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title="">Install FreeBSD dengan package yang diperlukan sahaja. Langkah ini telah ditunjukkan dalam post saya yang lepas <a href="http://lonurhazve.blogspot.com/2009/10/minimal-installation-configuration.html">( Minimal Installation &amp; Configuration FreeBSD 7.2 )</a>.&nbsp;&nbsp;</span></span></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><u><b>Langkah 2</b></u> ( Install NginX )</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><br />
</span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title="">Kaedahnya adalah seperti berikut :</span></span></div><div style="text-align: justify;"><b><span class="long_text" id="result_box"><span title=""><br />
</span></span></b></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve# cd /usr/ports/www/nginx</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve# ls<br />
<span style="color: red; font-size: xx-small;">Makefile&nbsp;&nbsp;&nbsp; distinfo&nbsp;&nbsp;&nbsp; files&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; pkg-descr&nbsp;&nbsp;&nbsp; pkg-plist</span></b></span></span><span class="long_text" id="result_box" style="color: red; font-size: xx-small;"><span title=""><b>lonurhazve</b></span></span><br />
<div style="color: red;"><br />
</div><span class="long_text" id="result_box"><span title=""><b># make config</b></span></span></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>---------- pastikan pilih module dibawah ------------<span style="color: red; font-size: xx-small;">&nbsp;</span></b></span></span><span class="long_text" id="result_box" style="color: red; font-size: xx-small;"><span title=""><b> </b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b><span style="color: red; font-size: xx-small;">HTTP_MODULE<br />
HTTP_REWRITE_MODULE<br />
HTTP_SSL_MODULE<br />
HTTP_STATUS_MODULE</span></b></span></span><br />
<span class="long_text" id="result_box"><span title=""><b><span style="color: red; font-size: xx-small;">&nbsp;</span> </b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve# make install</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>----------------- mesej akhir seperti berikut ----------------------------- </b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b><span style="color: red; font-family: &quot;Courier New&quot;,Courier,monospace; font-size: xx-small;">===&gt; Installing rc.d startup script(s)<br />
===&gt;&nbsp;&nbsp; Registering installation for nginx-0.7.67<br />
===&gt; SECURITY REPORT: <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This port has installed the following files which may act as network<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; servers and may therefore pose a remote security risk to the system.<br />
/usr/local/sbin/nginx<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This port has installed the following startup scripts which may cause<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; these network services to be started at boot time.<br />
/usr/local/etc/rc.d/nginx<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If there are vulnerabilities in these programs there may be a security<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; risk to the system. FreeBSD makes no guarantee about the security of<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ports included in the Ports Collection. Please type 'make deinstall'<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to deinstall the port if this is a concern.<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; For more information, and contact details about the security<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; status of this software, see the following webpage: <br />
http://sysoev.ru/nginx/</span>&nbsp;</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve# make clean</b></span></span></div><div style="text-align: justify;"><br />
Configure Nginx ( buka file /usr/local/etc/nginx/ngin.conf )<br />
<br />
Cth konfiurasi nginx.conf :<br />
<br />
<br />
<br />
<br />
<br />
<b>lonurhazve#pico /usr/local/etc/nginx/nginx.conf</b><br />
<br />
<br />
<br />
<br />
<br />
</div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title="">Enable nginx at start<b><br />
</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b><br />
</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve#echo 'nginx_enable="YES"' &gt;&gt; /etc/rc.conf</b></span></span></div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""><b>lonurhazve#nginx -c /usr/local/etc/nginx/nginx.conf -t</b></span></span></div><div style="text-align: justify;"><br />
<span class="long_text" id="result_box"><span title=""><u><b>Langkah 3</b></u> ( Install PHP5 )</span></span></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><b><span class="long_text" id="result_box"><span title="">lonurhazve#cd /usr/ports/lang/php5</span></span></b></div><div style="text-align: justify;"><b><span class="long_text" id="result_box"><span title="">lonurhazve#make config</span></span></b></div><div style="text-align: justify;"><br />
</div><div style="text-align: justify;"><span class="long_text" id="result_box"><span title="">Pilih : </span></span></div><blockquote><span style="font-size: xx-small;"><span style="color: red;">[X]CLI</span><br style="color: red;" /><span style="color: red;"> [X]CGI</span><br style="color: red;" /><span style="color: red;"> [X]SUHOSIN</span><br style="color: red;" /><span style="color: red;"> [X]IPV6</span><br style="color: red;" /><span style="color: red;"> [X]FASTCGI&nbsp; ( Sekiranya guna php5 5.3.3 pilih&nbsp; [X] FPM Build FPM version (experimental)</span><br style="color: red;" /><span style="color: red;"> [X]PATHINFO</span></span> </blockquote><div style="text-align: justify;"><b><span class="long_text" id="result_box"><span title="">lonurhazve#make install</span></span></b></div><div style="text-align: justify;"><br />
</div><br />
<span id="more-1507"></span><br />
<b></b><br />
<div style="text-align: justify;"><span class="long_text" id="result_box"><span title=""></span></span></div>
