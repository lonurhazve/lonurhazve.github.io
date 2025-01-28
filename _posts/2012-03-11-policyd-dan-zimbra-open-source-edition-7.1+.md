---
title: "Policyd dan Zimbra Open Source Edition 7.1+"
date: 2012-03-11
---
<div style="text-align: justify;">
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s1600/policyd_logo.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="138" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjscytqIR7IZaY3NFd9hiyYcJ0XgwSkhO0kAQyiz-QvfdsJFuk7j2AeFA9qXtSQRQm3L-qb2Dpqyxb920yZFOTGZhnq-N_6Gz9kmVzIcu9Gy5FNXaNVZn9kv2iATP7orfxUycf6CoRlw/s320/policyd_logo.png" width="320" /></a></div>
<br />
Policyd digunakan pada MTA mail server bagi mengawal spam dan menentukan polisi-polisi yang diperlukan. Ianya amat berguna bagi setup mail server yang mempunyai pengguna yang besar. Policyd adalah opensource dan boleh didapati di website <a href="http://www.policyd.org/">http://www.policyd.org/</a>. Ianya juga dikenali dengan CBpolicyd ( cluebringer ).</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Disini aku rekodkan bagaimana setup policyd/cbpolicyd pada mail server zimbra.</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Step 1:</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Gunakan user zimbra&nbsp;</div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<span style="font-size: small;"><b>#su zimbra</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Step 2 :</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Package policyd telah pun ada pada Zimbra Open Source Edition 7.1+, cuma perlu enable sahaja.</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<span style="font-size: small;"><b>#zmprov ms servername +zimbraServiceEnabled cbpolicyd</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
( '+' bermaksud Enable '-' bermaksud Disable )</div>
<div style="text-align: justify;">
* Dalam hal ini, jangan lupa dengan tanda '+', kerana jika ianya tiada semua service pada zimbra kemungkinan akan disable. Sila rujuk post saya sebelum ini sekiranya ianya berlaku.<a href="http://lonurhazve.blogspot.com/2012/03/only-few-service-zimbra-start.html">Only A Few Services Zimbra Start</a>.</div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Step 3:</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Maklumkan Postfix untuk menggunakan policyD</div>
<div style="text-align: justify;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: justify;">
<span style="font-size: small;"><b>#zmlocalconfig -e postfix_enable_smtpd_policyd=yes</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Step 4 :</b></u></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
Tambahkan polisi zimbraMtaRestriction untuk cbpolicyd</div>
<div style="text-align: left;">
<b><br />
</b></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmprov mcf zimbraMtaRestriction "check_policy_service inet:127.0.0.1:10031" zimbraMtaRestriction reject_non_fqdn_recipient zimbraMtaRestriction permit_sasl_authenticated zimbraMtaRestriction permit_mynetworks zimbraMtaRestriction reject_unauth_destination zimbraMtaRestriction reject_unlisted_recipient zimbraMtaRestriction reject_invalid_hostname zimbraMtaRestriction reject_non_fqdn_sender zimbraMtaRestriction "reject_rbl_client b.barracudacentral.org" zimbraMtaRestriction "reject_rbl_client zen.spamhaus.org"</b></span></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
<u><b>Step 5:</b></u></div>
<div style="text-align: justify;">
<br /></div>
<div style="text-align: justify;">
Konfigurasi CBpolicyd logging dan active module sebagaimana berikut :</div>
<div style="text-align: justify;">
<span style="font-size: x-small;"><br />
</span></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmlocalconfig -e cbpolicyd_log_level=4</b></span></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmlocalconfig -e cbpolicyd_log_detail=modules,tracking,policies</b></span></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmlocalconfig -e cbpolicyd_module_accesscontrol=1 cbpolicyd_module_checkhelo=1 cbpolicyd_module_checkspf=1 cbpolicyd_module_greylisting=1 cbpolicyd_module_quotas=1</b></span></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
<u><b>Step 6</b></u></div>
<div style="text-align: left;">
Restart mta service dan start cbpolicyd</div>
<div style="text-align: left;">
<br /></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmmtactl restart</b></span></div>
<div style="font-family: &quot;Courier New&quot;,Courier,monospace; text-align: left;">
<span style="font-size: small;"><b>#zmcbpolicyd start</b></span></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: justify;">
Langah diatas telah berjaya mengaktifkan cbpolicyd pada mail server. Konfigurasi polisi yang dikehendaki perlu dibuat sama ada melalui web access cbpolicy atau buat polisi melalui SQL statement.</div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
<br /></div>
<div style="text-align: left;">
<br /></div>
