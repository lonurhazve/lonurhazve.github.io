---
title: "TIPS : CBpolicyD Cannot Start & Error problem talking to server 127.0.0.1:10031: Connection refused"
date: 2012-03-11
---
<div style="text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s1600/policyd_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="138" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s320/policyd_logo.png" width="320" /></a></div>
<br />
<br />
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">
<span style="font-size: small;">Selepas buat konfigurasi pada cbpolicyd zimbra, semua running dengan baik tetapi selepas selepas 1 hari postfix/smtpd problem dan email tidak dapat dihantar dan terima. Error mesej seperti berikut :</span></div>
</div>
<span style="font-size: small;"><br /></span><br />
<span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;"><b>Mar 11 07:27:02 mail postfix/smtpd[2508]: warning: problem talking to server 127.0.0.1:10031: Connection refuse</b></span><span style="font-size: small;">d</span><br />
<span style="font-size: small;"><br /></span><br />
<div style="text-align: justify;">
<span style="font-size: small;"><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">Ini berlaku disebabkan cbpolicyd tidak running dan failed apabila manually start. Boleh dikatakan semua code fail cbpolicyd aku study tapi tak jumpa mana silapnya... Tiba-tiba terpikir mengenai log fail... kosong .... tak diduga rupanya perkara sekecil macm ini boleh melumpuhkan fungsi kesemua mail server... huh</span>uu</span></div>
<br />
<u><b>SOLUTION</b></u><br />
<div style="text-align: justify;">
<br /></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Tengok pada log fail cbpolicyd yang telah bertukar owner syslog adm selepas create yang baru.</span></div>
<br />
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<b><span style="font-size: small;">#ls /opt/zimbra/log/</span></b></div>
<br />
<span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;"><b>-rw-r--r--&nbsp; 1 syslog adm&nbsp; 0 2012-03-11 06:45 cbpolicyd.log</b></span><br />
<br />
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">
<span style="font-size: small;">Tukarkan kembali owner kepada zimbra dan semua sistem berjalan dengan baik.</span></div>
<br />
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<b><span style="font-size: small;">#chown zimbra.zimbra /opt/zimbra/log//cbpolicyd.log</span></b></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<b><span style="font-size: small;">#zmcontrol restart</span></b><br />
<span style="font-size: small;"><br /></span><br />
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">
<span style="font-size: small;"><b>MENGAPA LOG CBPOLICYD DITUKAR PERMISSIONNYA KEPADA SYSLOG ADM?</b></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Pada asasnya fail log yang ada dalam <b>/var/log/*</b> menggunakan permission fail syslog.adm dan log fail yang berada dalam <b>/opt/zimbra/log/*</b> menggunakan permission <b>zimbra.zimbra</b>.</span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Jika kita lihat, log fail cbpolicyd.log berada di <b>/opt/zimbra/log/*</b> tetapi menggunakan permission fail <b>syslog.adm</b>.</span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Hal ini perlu dilihat pada konfigurasi logrotate.</span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><b><u>Step :</u></b></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Buka fail <b>/etc/logrotate.d/</b>zimbra dan cari konfigurasi untuk cbpolicyd</span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;"><br /></span></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Paparan fail konfigurasi seperti ini :</span></div>
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjxpRXT6zFn591PT_2zL58jIEwEWzAUK8tB76OJJ9EKmrBVAlMJWgK1eMXC8kVlc4qXeMzB1uaarNswyL1Vfq5H9twmhqFtF1_1G4XQqSkMm7yeFH45I7cha76XxNMuxyf-y31tIdB8aQ/s1600/rotatezimbralog.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="260" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjxpRXT6zFn591PT_2zL58jIEwEWzAUK8tB76OJJ9EKmrBVAlMJWgK1eMXC8kVlc4qXeMzB1uaarNswyL1Vfq5H9twmhqFtF1_1G4XQqSkMm7yeFH45I7cha76XxNMuxyf-y31tIdB8aQ/s400/rotatezimbralog.png" width="400" /></a></div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<span style="font-size: small;"><br /></span><br />
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Terbukti bahawa konfigurasi telah memberi permission kepada cbpolicyd.log kepada syslog.adm selepas rotation fail log baru.</span></div>
<div style="font-family: Arial,Helvetica,sans-serif; text-align: justify;">
<br /></div>
<div style="font-family: Georgia,&quot;Times New Roman&quot;,serif; text-align: justify;">
<span style="font-size: small;">Tukar <b style="font-family: &quot;Courier New&quot;,Courier,monospace;">create 0644 syslog adm</b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;"> </span></span><span style="font-size: small;">kepada <b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">create 0644 zimbra zimbra</span> </b></span><span style="font-size: small;">dan masalah berhantu ini boleh diselesaikan.</span></div>
</div>
