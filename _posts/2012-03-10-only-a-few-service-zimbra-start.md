---
title: "Only a few service zimbra start"
date: 2012-03-10
---
<div style="text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGksCBaClgNR_V8O4xkRvYsaOqnjkP87XuLnllP3kAhperCCg_QAH9RkXR7YfgDXNz104Qeu7aTkOtlSfn1OLUc33_fX1UFBaT06VyuXPfgVkhE3tIZX2b6Ff4d2iYMkOaYnf2KtZdQQ/s1600/zimbra_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="150" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgGksCBaClgNR_V8O4xkRvYsaOqnjkP87XuLnllP3kAhperCCg_QAH9RkXR7YfgDXNz104Qeu7aTkOtlSfn1OLUc33_fX1UFBaT06VyuXPfgVkhE3tIZX2b6Ff4d2iYMkOaYnf2KtZdQQ/s200/zimbra_logo.png" width="200" /></a>&nbsp;</div>
Bila start zimbra services dengan command zmcontrol start hanya satu service saja yang running.<br />
<br />
<b>Host mail.xxx.xxx</b><br />
<b><br />
</b><br />
<b>&nbsp;&nbsp;&nbsp; zmconfigd&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Running</b><br />
<br />
Mana perginya service yang lain.<br />
<br />
<u>Sebab berlaku :</u><br />
<br />
Command ini digunakan untuk disable cbpolicyd, semua services telah disable..<br />
<br />
<br />
<b>zimbra@mail:~$zmprov ms `zmhostname` zimbraServiceEnabled cbpolicyd<br />
</b><br />
<br />
Cuba enable kembali dengan command biasa<br />
<br />
<b>zimbra@mail:~$zmprov ms `zmhostname` +zimbraServiceEnabled cbpolicyd</b><br />
<b><br />
</b><br />
Keluar Error berikut :<b><br />
</b><br />
<br />
<b>[] INFO: I/O exception (java.net.ConnectException) caught when processing request: Connection refused<br />
[] INFO: Retrying request<br />
ERROR: zclient.IO_ERROR (invoke Connection refused, server: localhost) (cause: java.net.ConnectException Connection refused)</b><br />
<br />
Ini disebabkan ldap tidak running... cuba start manual ldap dengan command ldap start... tak nampak macam ldap running... so...<br />
<br />
<u>Penyelesaiannya aku guna command berikut :</u><br />
<br />
<b>zimbra@mail:~$zmprov -l ms `zmhostname` -- +zimbraServiceEnabled cbpolicyd</b><br />
<b>zimbra@mail:~$zmprov -l ms `zmhostname` -- +zimbraServiceEnabled ldap</b><br />
<b> zimbra@mail:~$zmprov -l ms `zmhostname` -- +zimbraServiceEnabled mailbox<br />
..<br />
..<br />
..</b><br />
<br />
Semua running macam biasa.
