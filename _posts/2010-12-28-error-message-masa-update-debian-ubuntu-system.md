---
title: "Error Message Masa Update Debian/Ubuntu System"
date: 2010-12-28
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiabjqSmsfHkPqGEmgXt4LxdlTe0vGIs_oX8ETehQF-C84RdezpUIT5AWi0zvqxw7UCPRzfkbtDekXclUQa0lKUYqltYGxdPgKGnGo-80sxwXRJkEtBTWrGrayYq3YrIqsdrCQ6DxF07g/s1600/ubuntu-logo-g.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="200" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiabjqSmsfHkPqGEmgXt4LxdlTe0vGIs_oX8ETehQF-C84RdezpUIT5AWi0zvqxw7UCPRzfkbtDekXclUQa0lKUYqltYGxdPgKGnGo-80sxwXRJkEtBTWrGrayYq3YrIqsdrCQ6DxF07g/s200/ubuntu-logo-g.png" width="200" /></a></div>
<br />
<b>W: GPG error: http://ftp.us.debian.org squeeze Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE312C</b><br />
<br />
Mesej ini dipaparkan semasa update debian/ubuntu system.<br />
<br />
Solution :<br />
<br />
<div style="color: blue;">
<b>lonurhazve~#</b>gpg --keyserver pgpkeys.mit.edu --recv-key<b> 9AA38DCD55BE312C</b><b>&nbsp;</b></div>
<div style="color: blue;">
<b>lonurhazve~#</b>gpg -a --export <b>9AA38DCD55BE312C</b> | sudo apt-key add - </div>
<br />
Gantikan no public key dengan no public key pada error message yang dipaparkan. NO_PUBKEY 9AA38DCD55BE312C
