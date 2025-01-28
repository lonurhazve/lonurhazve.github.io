---
title: "FreeBSD : Update Software &amp; Security Patches"
date: 2009-10-19
---
Tool yang diperlukan : <b>portmanager, portsnap, pkg_version</b><br />
<br />
<b>INSTALL portmanager</b> :<br />
#cd /usr/ports/ports-mgmt/portmanager<br />
#make install clean<br />
<br />
<b><span style="text-decoration: underline;">Upgrade Port Collection</span></b><span style="text-decoration: underline;"> :<br />
</span>#portsnap fetch extract<br />
<br />
<b><span style="text-decoration: underline;">List Senarai Software Tidak Update :</span></b><br />
<br />
#pkg_version -L =<br />
<br />
<b><span style="text-decoration: underline;">List Semua Senarai Software Install :</span></b><br />
<br />
#pkg_info <br />
<br />
<b><span style="text-decoration: underline;">Update FreeBSD Sofware :</span></b><br />
<br />
# portmanager -u<br />
<br />
<b><span style="text-decoration: underline;">Fetch FreeBSD Update :</span></b><br />
<br />
#freebsd-update fetch<br />
<br />
<b><span style="text-decoration: underline;">Install Fetch Update </span></b><span style="text-decoration: underline;">:</span><br />
<br />
# freebsd-update install
