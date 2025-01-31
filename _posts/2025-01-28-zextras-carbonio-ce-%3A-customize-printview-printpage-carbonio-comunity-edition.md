---
title: "Zextras Carbonio CE: Customize Printview/printpage Carbonio Community Edition"
date: 2025-01-28
---

Find Files Containing the Title "Carbonio"

Run the following command to search for files containing "Carbonio":
   
   ```sh
   grep "<title>Carbonio</title>" /opt/zextras/web/iris/carbonio-mails-ui/* -rl
   ```

This command will display a list of files containing that text. An example output:
   
   ```log
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a43dc6b1.chunk.map
   ```

Backup Files

It is always recommended to create a backup before making any modifications.

Run the following command to create a backup of the file:
   
   ```sh
   cp /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js \
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js.bak
   ```

Changing the Title Using `sed`

1. Replace the title "Carbonio" with a new title using the `sed` command:
   
   ```sh
   sed -i s/"<title>Carbonio</title>"/"<title>NEW TITLE</title>"/g \
   /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   ```

   - Replace `NEW TITLE` with the desired text.

Editing Manually

If you prefer to edit the file manually, proceed with caution:

Open the file using a text editor like `nano`:
   
   ```sh
   nano /opt/zextras/web/iris/carbonio-mails-ui/30ed9d1491400e80f4ec5e16939456d00a4f3ce3/534.a41dc3b1.chunk.js
   ```

Look for the following line:
   
   ```html
   <title>Carbonio</title>
   ```

Change it to:
   
   ```html
   <title>NEW TITLE</title>
   ```

Save the file and exit the text editor. You can also modify the Header Content in the printview within this file.
