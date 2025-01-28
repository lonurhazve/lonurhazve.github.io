---
title: "Minimal Installation &amp; Configuration FreeBSD 7.2"
date: 2009-10-16
---
Adalah lebih baik install FreeBSD dengan package yang diperlukan sahaja.<br />
<br />
Boot FreeBSD 7.2 dengan CD dan dengan Package minimal. ( Buat Partition dan Perhatikan pada Drive Geometry )<br />
<br />
__________________________________________________________________________________________<br />
<br />
1. Pertama sekali aku akan jadikan user aku (user1) menjadi user root ( Tambahkan user1 kedalam wheel group. ----&gt; Dengan cara ini aku boleh buat dengan gunakan personal akaun (use1).<br />
<br />
#vi /etc/group<br />
<br />
<img alt="Edit /etc/group" class="size-full wp-image-42" height="534" src="http://lonurhazve.files.wordpress.com/2009/10/gambar1.jpg" title="gambar1" width="572" /><br />
<br />
2. Install FreeBSD Ports Collection ( terdapat lebih 9000 package ---&gt; akan memudahkan kita install dan manage<br />
<br />
* Masukkan CD / pilih ftp server sebagai installation media then<br />
#sysinstall<br />
<br />
<img alt="sysinstall" class="size-full wp-image-56" height="395" src="http://lonurhazve.files.wordpress.com/2009/10/gambar23.gif" title="gambar2" width="628" /><br />
<br />
*Pilih Configure|Distributions|Ports then pilih ok|source<br />
*EXIT to #<br />
#cd /usr/ports/<br />
#ls -l ---&gt; periksa ports yang ada<br />
<br />
<img alt="List Ports" class="size-full wp-image-47" height="611" src="http://lonurhazve.files.wordpress.com/2009/10/gambar31.gif" title="gambar3" width="522" /><br />
<br />
3. Periksa jika source code install atau tidak<br />
#cd /usr/src/<br />
#ls<br />
* JIKA TIADA kena install source code tu melalui CD<br />
#mount -t cd9660 /dev/acd0 /cdrom<br />
#cd /cdrom<br />
#cd 7.2-RELEASE/src<br />
#./install.sh all<br />
*Tunggu sampai abis<br />
#umount /cdrom<br />
#ls /usr/src ---&gt; tengok ada ke tak<br />
4. Update ports collection kepada packages terbaru<br />
# cp /usr/share/examples/cvsup/ports-supfile /usr/src/port-supfile<br />
#vi port-supfile<br />
<br />
*EDIT pada default host=CHANGE_THIS.FreeBSD.org ---&gt; tukarkan dengan mirror terdekat<br />
<br />
<img alt="mirror" class="size-full wp-image-50" height="615" src="http://lonurhazve.files.wordpress.com/2009/10/gambar52.gif" title="gambar5" width="635" /><br />
<br />
#cd /usr/src --&gt; gi source code dir<br />
UPDATE<br />
#cvsup port-supfile ---&gt; ports akan diupdatekan<br />
<img alt="Finish Update" class="size-full wp-image-52" height="629" src="http://lonurhazve.files.wordpress.com/2009/10/gambar61.gif" title="gambar6" width="534" /><br />
<br />
5. Go to /usr/ports/<br />
&nbsp;&nbsp;&nbsp;&nbsp; Find package nak install<br />
&nbsp;&nbsp;&nbsp;&nbsp; #whereis &lt;package&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp; * Tukar ke directory package yang hendak install<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;INSTALL<br />
&nbsp;&nbsp;&nbsp;&nbsp; #make install clean<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;* Beberapa option untuk package yang hendak install akan dipaparkan dan pilih yang diperlukan ( default dah ok )<br />
&nbsp;&nbsp;&nbsp; * Dependent Package juga akan dipaparkan untuk option<br />
&nbsp;&nbsp;&nbsp; * Compiling akan dilaksanakan
