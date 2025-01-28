---
title: "Reset Password Admin Joomla"
date: 2009-12-06
---
Gunakan MySQL Query untuk reset password admin joomla.<br />
<br />
UPDATE `<b>jos_users</b>` SET `password` = MD5( '<b>password_baru</b>' ) WHERE `<b>jos_users</b>`.`username` = "<b>admin</b>" ;<br />
<br />
"<b>jos_users</b>"= nama table<br />
<br />
"<b>password_baru"= </b>password yang baru<br />
<br />
"<b>admin"=</b>user admin yang digunakan ( periksa pada table user )
