---
title: "Error Pemindahan Website Joomla Ke Webserver Baru"
date: 2010-08-16
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhetk-8HAgGrWZX7MqFwH2GOd7XMOtbUs7MQtjZ2LIdH6HyA9z_6YN7E_ekFgz6oRhwqSDXe7DF7TxjyI2mL4LkpFI82w9wmhO9e5uGrRVKRhMWgKRyB8K2Y2bgn11juAAhJf4EWmVSjw/s1600/joomla-logo2.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="198" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhetk-8HAgGrWZX7MqFwH2GOd7XMOtbUs7MQtjZ2LIdH6HyA9z_6YN7E_ekFgz6oRhwqSDXe7DF7TxjyI2mL4LkpFI82w9wmhO9e5uGrRVKRhMWgKRyB8K2Y2bgn11juAAhJf4EWmVSjw/s200/joomla-logo2.png" width="200" /></a></div>
<br />
<b>1.</b><b> 2010/08/14 15:15:20 [error] 1556#0: *2 FastCGI sent in stderr: "PHP Fatal error:&nbsp; Call to undefined function xml_parse() in /home/lnz/www/lnz.n$</b><br />
<br />
xml_parse() : Error ini disebabkan oleh module xml ( php5-xml ) tidak install/enable semasa installation php.<br />
<br />
2. <b>Error: 'chat.js.tpl.php' could not be found, please check your themepath</b> <br />
<br />
Ini berlaku selepas pemindahan website ke webserver lain menggunakan path berlainan.<br />
<br />
<u>Penyelesaian </u><br />
<br />
Clear cache dalam folder components/com_jpfchat/pfc/data/private/cache<br />
( Delete semua data dalam folder cache )<br />
<br />
Tukar permission kepada 777 components/com_jpfchat/pfc/data dan 777 semua data dalam folder data.<br />
<br />
3. <b>PHP Warning:&nbsp; Parameter 1 to modMainMenuHelper::buildXML() expected to be a reference( Menu tidak dipaparkan )</b><br />
<b><br />
</b><br />
<u>Penyelesaian</u><b></b><br />
<b><br />
</b><br />
Buka fail /modules/mod_mainmenu/helper.php<b></b><br />
Tukar function buildXML(<b>&amp;$params</b>)<b> </b>kepada function buildXML(<b>$params</b>)<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDXfDEi-BbSd97GOUmw6WTXwhtSOoGwM1ZYFhfAQQWQdBX47DzvOuTsRMsgJ8pGIHQ0JXVglyDa0ZiOarVhY47sXmQz_LGMwI9NixCPvz2LI9dJmewt_LA7csxzg3s5z-f2KhnjukSlQ/s1600/helper" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDXfDEi-BbSd97GOUmw6WTXwhtSOoGwM1ZYFhfAQQWQdBX47DzvOuTsRMsgJ8pGIHQ0JXVglyDa0ZiOarVhY47sXmQz_LGMwI9NixCPvz2LI9dJmewt_LA7csxzg3s5z-f2KhnjukSlQ/s400/helper" width="400" /></a></div>
<div class="separator" style="clear: both; text-align: center;">
</div>
<b></b>
