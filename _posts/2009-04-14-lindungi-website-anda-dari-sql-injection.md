---
title: "Lindungi Website Anda dari SQL Injection"
date: 2009-04-14
---
Kebanyakan website dan aplikasi online masakini menggunakan pengkalan data dan mempunyai interface yang membenarkan pengguna memasukkan input. Sememangnya ini mendatangkan risiko yang tinggi. Kebiasaannya input yang dibenarkan pada interface sesebuah website dan aplikasi adalah untuk:<br />
<ul><li>Melihat data-data yang bersesuaian di dalam pengkalan data</li>
</ul><br />
<ul><li> Menyimpan data yang diisi oleh pengguna</li>
</ul><br />
Oleh kerana itu, kebanyakan pengguna menggunakan framing SQL statements untuk menjalankan aplikasi pada pangkalan data ( MySQL ). Sememangnya boleh berlaku sekiranya web atau aplikasi tidak ditentukan input sepatutnya dibenarkan secara sempurna.<br />
Dengan ini, pengguna boleh mencapai pengkalan data dan seterusnya menjalankan arahan yang ada pada pangkalan data.<br />
<br />
<a name='more'></a><br />
<br />
Apakah risiko sekiranya SQL Injection berjaya dilaksanakan pada aplikasi dan portal kita :<br />
<ul><li>Pengguna mendapatkan user administrator untuk aplikasi dan web kita.</li>
</ul><br />
<ul><li>Pengguna boleh mendapatkan maklumat yang tak sepatutnya seperti transaksi kewangan,</li>
</ul><br />
maklumat peribadi, dan sebagainya<br />
<ul><li>Pengguna boleh menukar konfigurasi dan data</li>
<li>Pengguna akan buat modifikasi struktur database ( delete data )</li>
<li>Pengguna boleh mengambil alih database server dengan menjalankan arahan SQL</li>
</ul>
