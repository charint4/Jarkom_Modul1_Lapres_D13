## Praktikum Modul 1
Kelompok D13
- 05111840000094 Rafi Nizar Abiyyi
- 05111740000192 Faishal Abiyyudzakir

#### Soal 1

> Sebutkan webserver yang digunakan pada
> [testing.mekanis.me](testing.mekanis.me)

Cari packet yang berasal dari [testing.mekanis.me](testing.mekanis.me) menggunakan display filter  `http.host == "testing.mekanis.me"`

![soal1-1](/img/soal1-1.png)

Selanjutnya follow tcp stream dari salah satu packet dengan http 1.1

![soal1-2](/img/soal1-2.png)

Web server tertulis pada conversation dari server dalam tcp stream, server berada dalam web server nginx.



