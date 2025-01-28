---
title: "Enable Web Access Cbpolicyd Zimbra Opensource Edition"
date: 2012-03-11
---
<div style="text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s1600/policyd_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="138" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s320/policyd_logo.png" width="320" /></a></div>
<br />
Konfigurasi policyd pada Zimbra Opensource Edition boleh dibuat melalui webaccess yang boleh dicapai menggunakan port 7780. Ianya perlu dienable selepas enable/install cbpolicyd. Ada dua kaedah samaada capaian secara sementara ( perlu konfigurasi semula sekiranya terdapat updating zimbra ) atau secara kekal.</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Kaedah Pertama</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Guna user root :</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
1. Buat symlink cbpolicyd webui pada folder httpd zimbra</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<span style="font-size: x-small;">root root&nbsp;&nbsp; 27 2012-03-09 23:27 webui -&gt; ../../cbpolicyd/share/webui</span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;"><b>#cd /opt/zimbra/httpd/htdocs/ &amp;&amp; ln -s ../../cbpolicyd/share/webui</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
2. Konfigurasi fail config webui cbpolicyd&nbsp;</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-size: small;"><b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">#vi /opt/zimbra/cbpolicyd-2.0.10/share/webui/includes/config.php</span></b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
comment semua yang start dengan $DB_DSN dan tambah statement berikut :</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;"><b>$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
CTH :</div>
<div style="text-align: justify;">
---------------------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: x-small;"><br />
# mysql:host=xx;dbname=yyy<br />
#<br />
# pgsql:host=xx;dbname=yyy<br />
#<br />
# sqlite:////full/unix/path/to/file.db?mode=0666<br />
#<br />
#$DB_DSN="sqlite:////tmp/cluebringer.sqlite";<br />
$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";<br />
#$DB_DSN="mysql:host=localhost;dbname=cluebringer";<br />
#$DB_USER="root";<br />
#$DB_PASS="";<br />
<br />
<br />
#<br />
# THE BELOW SECTION IS UNSUPPORTED AND MEANT FOR THE ORIGINAL SPONSOR OF V2<br />
#<br />
<br />
#$DB_POSTFIX_DSN="mysql:host=localhost;dbname=postfix";<br />
#$DB_POSTFIX_USER="root";<br />
#$DB_POSTFIX_PASS="";<br />
<br />
?&gt;</span></b><br />
----------------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
3. Restart zimbra apache</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;">#su - zimbra -c "zmapachectl restart"</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
4. Capaian Webaccess cbpolicyd boleh dicapai pada default url berikut :</div>
<div style="text-align: justify;">
<b><br />
</b></div>
<div style="text-align: justify;">
<b>http://serverurl:7780/webui/index.php</b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
(*semua konfigurasi tadi akan hilang sekiranya terdapat updating zimbra )</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Kaedah Kedua</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
1. Copy dail cluebringer-httpd.conf dari cbpolicyd kepada folder config zimbra</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><span style="font-size: small;">#cp /opt/zimbra/cbpolicyd/share/contrib/httpd/cluebringer-httpd.conf /opt/zimbra/conf/</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
2. Buka fail config yang copy tadi pada folder config zimbra dan edit </div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><span style="font-size: small;"># vi /opt/zimbra/conf/cluebringer-httpd.conf</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
------------------------------------cluebringer-httpd.conf-----------------------------------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-size: x-small;"><b style="font-family: &quot;Courier New&quot;,Courier,monospace;">Alias /cluebringer /opt/zimbra/cbpolicyd/share/webui/&nbsp;&nbsp;&nbsp; # Comment out the following 3 lines to make web ui accessible from anywhere&nbsp;&nbsp;&nbsp; <br />
<br />
Order Deny,Allow&nbsp; <br />
Deny from all&nbsp;&nbsp;&nbsp; <br />
Allow from 10.2.0.1/255.255.255.0</b></span></div>
<div style="text-align: justify;">
<span style="font-size: x-small;"><b style="font-family: &quot;Courier New&quot;,Courier,monospace;">#(subnet untuk benarkan dicapaian webacess )</b></span></div>
<div style="text-align: justify;">
-----------------------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
3. Edit konfigurasi httpd /opt/zimbra/conf/httpd.conf dan tambah statement berikut pada hujung fail:</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<span style="font-size: small;"><b>&nbsp;Include /opt/zimbra/conf/cluebringer-httpd.conf</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
</div>
<div style="text-align: justify;">
4. Konfigurasi fail config webui cbpolicyd&nbsp;</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-size: small;"><b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">#vi /opt/zimbra/cbpolicyd-2.0.10/share/webui/includes/config.php</span></b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
comment semua yang start dengan $DB_DSN dan tambah statement berikut :</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;"><b>$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
CTH :</div>
<div style="text-align: justify;">
------------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: x-small;">     <br />
# mysql:host=xx;dbname=yyy<br />
#<br />
# pgsql:host=xx;dbname=yyy<br />
#<br />
# sqlite:////full/unix/path/to/file.db?mode=0666<br />
#<br />
#$DB_DSN="sqlite:////tmp/cluebringer.sqlite";<br />
$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";<br />
#$DB_DSN="mysql:host=localhost;dbname=cluebringer";<br />
#$DB_USER="root";<br />
#$DB_PASS="";<br />
<br />
<br />
#<br />
# THE BELOW SECTION IS UNSUPPORTED AND MEANT FOR THE ORIGINAL SPONSOR OF V2<br />
#<br />
<br />
#$DB_POSTFIX_DSN="mysql:host=localhost;dbname=postfix";<br />
#$DB_POSTFIX_USER="root";<br />
#$DB_POSTFIX_PASS="";<br />
<br />
?&gt;</span></b><br />
--------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
5. Restart zimbra apache</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace; font-size: small;">#su - zimbra -c "zmapachectl restart"</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
4. Capaian Webaccess cbpolicyd boleh dicapai pada default url berikut :</div>
<div style="text-align: justify;">
<b><br />
</b></div>
<div style="text-align: justify;">
<b>http://serverurl:7780/cluebringer/index.php</b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<br />
Perlu diingat bahawa capaian kepada webaccess tersebut adalah tidak menggunakan password dan terdedah kepada risiko. Walaubagaimanapun ada caranya untuk kita securekannya. Nanti cerita semula pada post akan datang.</div>
<div style="text-align: justify;">
<br /></div>
