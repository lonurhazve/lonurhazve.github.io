---
title: "Zextras Carbonio CE : Customize Printview/printpage Carbonio Community Edition"
date: 2025-01-28
---

## Cari Fail yang Mengandungi Title "Carbonio"

1. Jalankan arahan berikut untuk mencari fail yang mengandungi "Carbonio":
   
   ```sh
   grep "<title>Carbonio</title>" /opt/zextras/web/iris/carbonio-mails-ui/* -rl
   ```

2. Arahan ini akan memaparkan senarai fail yang mengandungi teks tersebut. Contoh yang saya dapat:
   
   ```log
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a43dc6b1.chunk.map
   ```

## Backup Fail

Dinasihatkan sentiasa buat salinan fail sebelum melakukan sebarang perubahan.

1. Jalankan arahan berikut untuk membuat salinan fail:
   
   ```sh
   cp /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js \
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js.bak
   ```

## Menukar Title Menggunakan `sed`

1. Gantikan title "Carbonio" dengan tajuk baru menggunakan arahan `sed`:
   
   ```sh
   sed -i s/"<title>Carbonio</title>"/"<title>TAJUK BARU</title>"/g \
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   ```

   - Gantikan `TAJUK BARU` dengan teks yang anda mahu.

## Mengedit Secara Manual

Sekiranya anda ingin mengedit fail secara manual, kena berhati-hati:

1. Buka fail menggunakan editor teks seperti `nano`:
   
   ```sh
   nano /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   ```

2. Cari baris yang mengandungi:
   
   ```html
   <title>Carbonio</title>
   ```

3. Tukar kepada:
   
   ```html
   <title>TAJUK BARU</title>
   ```

4. Simpan fail dan keluar dari editor teks. Kita juga boleh menukar Header Content dalam printview pada fail ini.
