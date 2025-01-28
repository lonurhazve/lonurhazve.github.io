---
title: "Php Error Pada Server Apache dan PHP5"
date: 2010-08-27
---
<div class="separator" style="clear: both; text-align: center;">
<a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhk9NLI4iFwmdWx1D1vrX4BclxBMQ_sawbaAuD7DBzh1SuSoE8gPjGyd7qcLTYIBNZhhMpdR5dU6hNTsq1RT_7VFhFEqMTAIyY5_LvHMhXqNCnVxmQKyFszfw7c1yO4kBbWTdTMnTRvdw/s1600/php.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="105" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhk9NLI4iFwmdWx1D1vrX4BclxBMQ_sawbaAuD7DBzh1SuSoE8gPjGyd7qcLTYIBNZhhMpdR5dU6hNTsq1RT_7VFhFEqMTAIyY5_LvHMhXqNCnVxmQKyFszfw7c1yO4kBbWTdTMnTRvdw/s200/php.png" width="200" /></a></div>
<br />
<u><b>error 1</b></u><br />
<br />
<i style="color: blue;">Warning: putenv() [function.putenv]: Safe Mode warning: Cannot set environment variable 'TZ' - it's not in the allowed list in ...</i><br />
<br />
<u><b>Solution</b></u><br />
<br />
Buka fail php.ini dan tukar<br />
<br />
safe_mode = On kepada safe_mode = Off<br />
<br />
<b><u>error2</u></b><br />
<br />
<i style="color: blue;">Warning: Cannot modify header information - headers already sent by (output started at</i><br />
<br />
<u><b>Solution</b></u> <br />
<br />
Buka fail php.ini dan tukar<br />
<br />
output_buffering = Off kepada output_buffering = On
