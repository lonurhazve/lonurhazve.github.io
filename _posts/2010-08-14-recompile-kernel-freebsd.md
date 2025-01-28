---
title: "Recompile Kernel FreeBSD"
date: 2010-08-14
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihRoY_IaTMo59E0JWYcA5YYQPWAFMHOJC1T3hi3e5neP1Cs5SigfUBDSw4mxJqDHSmvNXdPnpqJV48tm744fhrioFfw2jWX6UXClPBs7Q2O-EC6tKXUpMFDyrmYKrkyZbqe4awyHWCVg/s1600/beastie.png" /></a></div>
<br />
Untuk setup server production adalah lebih baik recompile semula Kernel. Ini adalah sebab-sebab <b>Security</b> dan <b>Performance</b>.<br />
<br />
<i>Security --&gt; Vulnerability tidak ada sekiranya sesuatu yang tidak digunakan kita&nbsp;</i><br />
<i>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; disable dalam kernel. </i><br />
<i>Performance --&gt; Buang fail sistem dan driver tidak digunakan dapat mengelakkan berlakunya penggunaan RAM yang tinggi. ( boot sistem pun cepat ).</i><br />
<br />
<u><b>Langkah 1: </b></u><br />
<br />
Lokasi kernel Asal:&nbsp; <b>/usr/src/sys/<i style="color: #999999;">i386</i>/conf/GENERIC</b><br />
<br />
#<b>cp /usr/src/sys/<i style="color: #999999;">i386</i>/conf/</b><b>GENERIC /usr/src/sys/<i style="color: #999999;">i386</i>/conf/</b><b>NAMAKERNEL</b><br />
<br />
<u><b>Langkah 2</b></u><br />
<br />
Buka fail <b>NAMAKERNEL</b> dan buat configurasi add/remove function yang tidak diperlukan berdasarkan perkakasan dan jenis server yang akan disediakan.<br />
<br />
Cth :&nbsp; IPV6, PCMCIA, SERIAL tidak digunakan comment pada<br />
<br />
<span style="font-size: x-small;"><span style="color: blue;">#options&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; INET6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # IPv6 communications protocols</span></span><b><span style="font-size: x-small;"><br />
</span></b><br />
<div style="color: blue;">
<br /></div>
<span style="color: blue; font-size: x-small;"># PCCARD (PCMCIA) support<br />
# PCMCIA and cardbus bridge support<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cbb&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # cardbus (yenta) bridge<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; pccard&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # PC Card (16-bit) bus<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cardbus&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # CardBus (32-bit) bus<br />
<br />
# Serial (COM) ports<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; uart&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Generic UART driver<br />
# Parallel port<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ppc<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ppbus&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Parallel port bus (required)<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; lpt&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Printer<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; plip&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # TCP/IP over parallel<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ppi&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Parallel port interface device<br />
#device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; vpo&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Requires scbus and da</span><br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjCE7WwkxiFkEnNaLG5LMRqyIw9zgcK5deuZTxgoqus9HnZyzKK5N-Grus8PSVgZIo6DVX1pplY-Kjk7I3Ki5kLq4_lfK3NYWmddtLSFWV_ID3tiaySI9kopKSIRZrX9heJSa0dcosngg/s1600/rekerne" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjCE7WwkxiFkEnNaLG5LMRqyIw9zgcK5deuZTxgoqus9HnZyzKK5N-Grus8PSVgZIo6DVX1pplY-Kjk7I3Ki5kLq4_lfK3NYWmddtLSFWV_ID3tiaySI9kopKSIRZrX9heJSa0dcosngg/s400/rekerne" width="400" /></a></div>
<br />
<br />
Boleh rujuk pada <b>/usr/src/sys/<i style="color: #999999;">i386</i>/conf/NOTES</b><br />
<br />
<u><b>Langkah 3</b></u><br />
<br />
Simpan fail<b> NAMAKERNEL </b>dan<b> </b>tukar ker dir /usr/src<br />
<br />
<b>#cd /usr/src</b><br />
<br />
Build Kernel<b> </b><br />
<b>#make buildkernel KERNCONF=NAMAKERNEL</b><br />
<br />
Install Kernel<br />
<b>#make installkernel KERNCONF=NAMAKERNEL</b><br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgpZ1JFWO37cQ1x8sUboqIasjripbVd7odQ42SCoKuoy5RysMcMcXFuK8fyQPHPoKCEXSReQ6BsgO_uz1gY1mOW9pJHmioXbYN32f-L3ot57nih3ngZcMEB_kNxYd5sZgOYZorpRCs_Rg/s1600/installkernelsiap" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgpZ1JFWO37cQ1x8sUboqIasjripbVd7odQ42SCoKuoy5RysMcMcXFuK8fyQPHPoKCEXSReQ6BsgO_uz1gY1mOW9pJHmioXbYN32f-L3ot57nih3ngZcMEB_kNxYd5sZgOYZorpRCs_Rg/s400/installkernelsiap" width="400" /></a></div>
<br />
Shutdown &amp; Restart System<b> </b><br />
<b>#shutdown -r now</b><br />
<b>---------------------------------------------------------------------------------------------- </b><br />
<br />
<u>Periksa Maklumat CPU&nbsp;</u><b> </b><br />
<b># grep -i cpu /var/run/dmesg.boot<br />
<span style="color: blue; font-size: x-small;">CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (2400.10-MHz 686-class CPU)<br />
cpu0: <acpi cpu=""> on acpi0<br />
p4tcc0: <cpu control="" frequency="" thermal=""> on cpu0<br />
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (2400.10-MHz 686-class CPU)<br />
cpu0: <acpi cpu=""> on acpi0<br />
p4tcc0: <cpu control="" frequency="" thermal=""> on cpu0</cpu></acpi></cpu></acpi></span>&nbsp;</b><br />
<u>Lepas Restart, sekiranya kernel panic</u> <br />
<br />
Reboot<b> </b>dan press " 6 " pada menu<b> ( </b><i>Escape to Loader Prompt</i><b> )&nbsp;</b><br />
Taip <b>boot /boot/kernel.old/kernel&nbsp;</b><br />
Sistem akan restart dengan kernel lama<b><br />
</b>
