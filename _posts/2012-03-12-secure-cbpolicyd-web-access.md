---
title: "Secure Cbpolicyd Web Access"
date: 2012-03-12
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s1600/policyd_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="86" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s200/policyd_logo.png" width="200" /></a></div>
<div style="text-align: justify;">
Ini adalah sambungan dari artikel sebelum ini berkenaan kaedah Enable <a href="http://lonurhazve.blogspot.com/2012/03/enable-web-access-cbpolicyd-zimbra.html">Web Access Cbpolicyd Zimbra Opensource Edition</a>.&nbsp;</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Kita boleh buat konfigurasi policyd menggunakan web admin yang telah disediakan semasa installation policyd tetapi cara capaiannya adalah tidak selamat kerana ianya boleh dicapai terus dengan mengetahui url dan portnya sahaja. Oleh itu baik kita buat agar capaian hanya boleh dicapai menggunakan katalaluan.</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Kaeadah :</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
1. Pada directory webui cbpolicyd ( /opt/zimbra/cbpolicyd-2.0.10/share/webui/ ), buat satu fail yang dinamakan sebagai .htaccess</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">#touch .htaccess</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
2. Buka fail tersebut .htaccess&nbsp; tersebut dan masukkan statement berikut :</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
-----------------------<span style="font-size: x-small;"><b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">/opt/zimbra/cbpolicyd-2.0.10/share/webui/.htaccess</span></b></span>---------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b>AuthUserFile /opt/zimbra/cbpolicyd-2.0.10/share/webui/.htpasswd <br />
AuthGroupFile /dev/null<br />
AuthName "User and Password"<br />
AuthType Basic<br /><br />
<limit get=""></limit></b>
<b><br />
require valid-user<br />
&nbsp;</b></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b>----------------------------------------------------------------- </b></div>
<br />
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
3. Buat&nbsp; fail baru <span style="font-family: &quot;Courier New&quot;,Courier,monospace;">.htpasswd <br /><span style="font-size: small;">&nbsp;</span></span></div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;"><span style="font-size: small;">#touch .htpasswd</span></span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
&nbsp;4. Create username dan password untuk webacess menggunakan command htpasswd :</div>
<div style="text-align: justify;">
<br /></div>
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">#htpasswd -c .htpasswd cbpadmin
   
  </span></b><br />
<div class="bbcode_container">
<div class="bbcode_quote">
</div>
</div>
&nbsp; <br />
<div style="color: red;">
<b><i style="color: black;">Sekiranya command tersebut tiada, sila install module <span style="font-size: small;"><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">apache2-utils </span></span>kerana command tersebut ada dalam module tu.</i><span style="font-size: small;"><span style="font-family: &quot;Courier New&quot;,Courier,monospace;"></span></span></b></div>
<div style="text-align: justify;">
&nbsp; </div>
<div style="text-align: justify;">
5.&nbsp; Buat konfigurasi pada httpd, buka fail<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;"> /opt/zimbra/conf/httpd.conf</span></b> dan tambah statement berikut pada line bawah sekali.</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><br /></b></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
-------------------<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">/opt/zimbra/conf/httpd.conf----</span></b>---------------</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><br />Alias /webui /opt/zimbra/cbpolicyd-2.0.10/share/webui/<br />
<directory cbpolicyd-2.0.10="" opt="" share="" webui="" zimbra=""><br />
    # Comment out the following 3 lines to make web ui accessible from anywhere<br />
        AllowOverride AuthConfig<br />
        Order Deny,Allow<br />
        Allow from all<br />
</directory></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
------------------------------------------------------------------------------------------------------------</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<b>Sekiranya kita mengaktifkan web access guna kaedah kedua sila masuk statement ini dalam </b><b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;">/opt/zimbra/conf/httpd.conf</span></b></div>
<div style="text-align: justify;">
<b><span style="font-family: &quot;Courier New&quot;,Courier,monospace;"><br /></span></b></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><span style="font-size: small;">&nbsp;Include /opt/zimbra/conf/cluebringer-httpd.conf</span></b></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
6. Restart apache dan cbpolicyd</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<b><span style="font-size: small;">#su - zimbra -c "zmapachectl restart"</span></b></div>
<div class="bbcode_container">
<div class="bbcode_quote">
<div class="quote_container" style="font-family: &quot;Courier New&quot;,Courier,monospace;">
<b><span style="font-size: small;">
   
   
    #su - zimbra -c "cbpolicdctl restart"&nbsp;</span></b></div>
<div class="quote_container">
</div>
<div class="quote_container">
Apabila semuanya selesai, cuba pergi ke url webaccess cbpolicyd dan ianya akan meminta katalaluan yang dibuat pada step 4 tadi.</div>
</div>
</div>
