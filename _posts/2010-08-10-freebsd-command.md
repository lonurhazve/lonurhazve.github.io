---
title: "FreeBSD Command"
date: 2010-08-10
---
1. Periksa spec processor pada sistem<br />
<br />
lnz# sysctl -a | egrep -i 'hw.machine|hw.model|hw.ncpu'<br />
hw.machine: i386<br />
hw.model: Intel(R) Pentium(R) 4 CPU 2.40GHz<br />
hw.ncpu: 1<br />
hw.machine_arch: i386<br />
<br />
@<br />
grep -i cpu /var/run/dmesg.boot
