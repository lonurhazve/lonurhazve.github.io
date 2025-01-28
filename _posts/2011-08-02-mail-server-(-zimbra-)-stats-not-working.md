---
title: "MAIL SERVER ( ZIMBRA ) Stats Not Working"
date: 2011-08-02
---
<div style="text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGksCBaClgNR_V8O4xkRvYsaOqnjkP87XuLnllP3kAhperCCg_QAH9RkXR7YfgDXNz104Qeu7aTkOtlSfn1OLUc33_fX1UFBaT06VyuXPfgVkhE3tIZX2b6Ff4d2iYMkOaYnf2KtZdQQ/s1600/zimbra_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="150" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGksCBaClgNR_V8O4xkRvYsaOqnjkP87XuLnllP3kAhperCCg_QAH9RkXR7YfgDXNz104Qeu7aTkOtlSfn1OLUc33_fX1UFBaT06VyuXPfgVkhE3tIZX2b6Ff4d2iYMkOaYnf2KtZdQQ/s200/zimbra_logo.png" width="200" /></a>&nbsp;</div>
Masalah ini berlaku secara tiba-tiba di mana stats zimbra mail server not running<br />
<br />
<b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ zmcontrol status</span></b><br />
<b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">Host emel.kelantan.gov.my<br />
&nbsp;&nbsp;&nbsp; antispam&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; antivirus&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; ldap&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; logger&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; mailbox&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; memcached&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; mta&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; snmp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running <br />
&nbsp;&nbsp;&nbsp; spell&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running<br />
&nbsp;&nbsp;&nbsp; stats&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Stopped</span><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;"></span></b><br />
<br />
<u>Solution :</u><br />
<br />
<span style="font-size: small;">Lihat samada fail semua fail dalam zmstat adalah milik owner zimbra<span class="Apple-style-span"><span class="Apple-style-span"><span class="Apple-style-span" style="font-family: 'courier new';"></span></span></span></span><br />
<span style="font-size: small;"><span class="Apple-style-span"><span class="Apple-style-span"><span class="Apple-style-span" style="font-family: 'courier new';"><br />
</span></span></span></span><br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ ls -al /opt/zimbra/zmstat</span></b></span><br />
<span style="font-size: small;"><br />
</span><br />
<span style="font-size: small;">Jika tidak, tukar owner :</span><br />
<span style="font-size: small;"><br />
</span><br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ chown zimbra:zimbra /opt/zimbra/zmstat/*</span></b></span><br />
<br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ su zimbra</span></b></span><span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;"> </span></b></span><br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ zmstatctl start</span></b></span><span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;"><br />
</span></b></span><br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">lnz@server:~$ </span></b></span><span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">zmstatctl status</span></b></span><span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;">       </span></b></span><br />
<span style="font-size: small;"><b><span style="font-family: Georgia,&quot;Times New Roman&quot;,serif;"><br />
</span></b></span><br />
Periksa semula stats running atau tak.
