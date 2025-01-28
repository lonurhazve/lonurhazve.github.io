---
title: "Perkara yang perlu dilaksanakan pada Mail Server"
date: 2010-08-02
---
<div style="text-align: justify;"><div style="text-align: justify;"></div><div style="text-align: justify;">Memastikan kedudukan mail server pada rangkaian&nbsp; </div><div style="text-align: justify;">&nbsp;</div><div style="text-align: justify;">1. Memastikan Topologi Jaringan dan Konfigurasi Network.Konfigurasi yang tidak diset dengan baik akan membuat Zimbra menjadi<br />
open relay dan secara otomatis menjadi target serangan spam (sekaligus<br />
menjadi lokasi gateway bagi para spammer). Konfigurasi NAT pada<br />
mikrotik yang kurang tepat misalnya, bisa memicu masalah karena proses<br />
blacklist IP &amp; hostname sender tidak berjalan akibat IP sender yang<br />
direwrite menjadi IP lokal gateway. Link artikel : Tips Zimbra :<br />
Topologi Jaringan, Trusted Network &amp; Open Relay [2]<br />
<br />
2. Memastikan Semua Service Berjalan dengan Baik. Zimbra mail<br />
server versi 5.x sebagian besar masih menggunakan anti virus ClamAV<br />
yang out of date. Jika ClamAV kurang dari versi 0.95, Zimbra bisa<br />
mogok berjalan. Sebaiknya lakukan update hingga ke versi yang terbaru.<br />
Link artikel : End of Life untuk ClamAV 0.94 pada Zimbra 5.0.16 atau<br />
Versi Sebelumnya [3] dan Tips : Cara Mudah Update ClamAV untuk Zimbra<br />
[4]<br />
<br />
3. Block Email yang Dikirim ke Alamat Email yang Tidak Ada.<br />
Fasilitas ini dikenal dengan nama Reject Unlisted Recipient,<br />
aktivasinya sangat mudah karena hanya mengganti 3 huruf pada 1 baris<br />
file konfigurasi. Link artikel : Improvement Anti Spam Zimbra : Reject<br />
Unlisted Recipient [5]<br />
<br />
4. Aktivasi Blacklist Spammer Melalui Fasilitas Online Blacklist<br />
(Barracuda, Spamhaus dll). Link artikel : Tips Anti Spam Zimbra :<br />
Aktivasi Fasilitas Blacklist Spammer [6]<br />
<br />
5. Aktivasi Plugin SPF, Pyzor, Razor, DCC dll untuk Meningkatkan<br />
Kemampuan Deteksi Spam.<br />
<br />
6. Aktivasi Domain Blocking, misalnya blacklist email dari milis,<br />
email konfirmasi Facebook, email spam dari Indonesia dll (tergantung<br />
kebutuhan user)<br />
<br />
7. Perbaikan untuk Bug-Bug pada Zimbra, misalnya bug FH_DATE_PAST<br />
pada SpamAssasin dan bug Add X_Originating_IP yang membuat email<br />
normal salah tag menjadi email junk. Bug diatas sudah solved pada<br />
Zimbra versi terbaru.<br />
<br />
8. Menambahkan Fasilitas SPF pada Sisi DNS (hanya mail server<br />
tertentu yang berhak mengirimkan email atas nama domain<br />
perusahaan.co.id)<br />
<br />
9. Menambahkan Reverse DNS Records untuk meningkatkan<br />
akseptabilitas email server dan menghindari email yang terkirim ditag<br />
sebagai junk/bulk email pada email server tujuan<br />
<br />
10. Menambahkan DKIM/DomainKeys untuk meningkatkan akseptabilitas email server<br />
<br />
11. Memastikan Fasilitas Backup &amp; Recovery, termasuk maksimum down<br />
time yang masih bisa diterima oleh pihak klien<br />
<br />
12. Memastikan adanya Fasilitas Backup MX yang akan menghandle email<br />
masuk jika terjadi gangguan pada mail server utama<br />
<br />
13. Memastikan Kecukupan Kapasitas Harddisk. Jika harddisk sudah<br />
mendekati kapasitas 70-80%, rekomendasi untuk meningkatkan free space,<br />
baik dengan menghapus file/folder tertentu atau menambah harddisk lain<br />
<br />
14. Meningkatkan Aspek Keamanan Server, misalnya membatasi dan<br />
memodifikasi akses SSH ke server, membuka port hanya pada port<br />
tertentu, memasang Firewall dan IDS dll<br />
<br />
15. Melakukan Testing Pengiriman dan Penerimaan Email dari Berbagai<br />
Domain. Hal ini dilakukan untuk memastikan bahwa header email yang<br />
diterima atau dikirim sudah memuat hasil tweak yang dilakukan,<br />
misalnya score spam/non spam sudah sesuai dengan keinginan, plugin<br />
sudah diaktivasi, setting tanggal dan jam sudah benar dan lain-lain<br />
<br />
15 point diatas mestinya bisa menjadi catatan untuk menjadikan email<br />
server Zimbra yang handal dan mampu berjalan sesuai keinginan.<br />
<br />
URL to article:<br />
<a href="http://vavai.com/2010/06/08/tips-audit-sistem-zimbra-mail-server/" rel="nofollow">http://vavai.com/2010/06/08/tips-audit-sistem-zimbra-mail-server/</a><br />
<br />
URLs in this post:<br />
<br />
[2] Tips Zimbra : Topologi Jaringan, Trusted Network &amp; Open Relay :<br />
<a href="http://vavai.com../2010/06/03/tips-zimbra-topologi-jaringan-trusted-network-open-relay/" rel="nofollow">http://vavai.com../2010/06/03/tips-zimbra-topologi-jaringan-trusted-network-open-relay/</a><br />
<br />
[3] End of Life untuk ClamAV 0.94 pada Zimbra 5.0.16 atau Versi<br />
Sebelumnya: <br />
<a href="http://vavai.com/2010/02/05/end-of-life-untuk-clamav-0-94-pada-zimbra-5-0-16-atau-versi-sebelumnya/" rel="nofollow">http://vavai.com/2010/02/05/end-of-life-untuk-clamav-0-94-pada-zimbra-5-0-16-atau-versi-sebelumnya/</a><br />
<br />
[4] Tips : Cara Mudah Update ClamAV untuk Zimbra:<br />
<a href="http://vavai.com/2010/04/18/tips-cara-mudah-update-clamav-untuk-zimbra/" rel="nofollow">http://vavai.com/2010/04/18/tips-cara-mudah-update-clamav-untuk-zimbra/</a><br />
<br />
[5] Improvement Anti Spam Zimbra : Reject Unlisted Recipient:<br />
<a href="http://vavai.com/2010/05/03/improvement-anti-spam-zimbra-reject-unlisted-recipient/" rel="nofollow">http://vavai.com/2010/05/03/improvement-anti-spam-zimbra-reject-unlisted-recipient/</a><br />
<br />
[6] Tips Anti Spam Zimbra : Aktivasi Fasilitas Blacklist Spammer :<br />
<a href="http://vavai.com../2010/06/04/tips-anti-spam-zimbra-aktivasi-fasilitas-blacklist-spammer/" rel="nofollow">http://vavai.com../2010/06/04/tips-anti-spam-zimbra-aktivasi-fasilitas-blacklist-spammer/</a><br />
<br />
-- <br />
Best Regards,<br />
<br />
Masim "Vavai" Sugianto<br />
/************************************************************/<br />
Blog (ID)                                  : <a href="http://www.vavai.com/" rel="nofollow">http://www.vavai.com</a><br />
Excellent Infotama Kreasindo    : <a href="http://www.vavai.biz/" rel="nofollow">http://www.vavai.biz</a><br />
/************************************************************/<br />
<br />
-- <br />
FAQ milis di <a href="http://wiki.linux.or.id/FAQ_milis_tanya-jawab" rel="nofollow">http://wiki.linux.or.id/FAQ_milis_tanya-jawab</a><br />
Unsubscribe: kirim email ke tanya-jawab-unsubscr...@linux.or.id<br />
Arsip dan info milis selengkapnya di <a href="http://linux.or.id/milis" rel="nofollow">http://linux.or.id/milis</a></div><pre></pre></div>
