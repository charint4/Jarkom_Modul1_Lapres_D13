## Praktikum Modul 1
Kelompok D13
- 05111840000094 Rafi Nizar Abiyyi
- 05111740000192 Faishal Abiyyudzakir

#### Soal 1
> Sebutkan webserver yang digunakan pada [testing.mekanis.me](testing.mekanis.me)

Cari packet yang berasal dari [testing.mekanis.me](testing.mekanis.me) menggunakan display filter  `http.host == "testing.mekanis.me"`

![soal1-1](/img/soal1-1.png)

Selanjutnya follow tcp stream dari salah satu packet dengan http 1.1

![soal1-2](/img/soal1-2.png)

Web server tertulis pada conversation dari server dalam tcp stream, server berada dalam web server nginx.
```
Server: nginx/1.14.0 (Ubuntu)
```

### Soal 2
> Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"

Gambar di dapat dari export object http

![soal2-1](/img/soal2-1.png)

Gambar yang diperoleh:

![soal2-2](/img/soal2-2.png)

### Soal 3
> Cari username dan password ketika login di [ppid.dpr.go.id](ppid.dpr.go.id)

Mencari packet yang berasal dari [ppid.dpr.go.id](ppid.dpr.go.id) dengan metode request POST

![soal3-1](/img/soal3-1.png)

Kredensial login berada pada header `HTML Form URL Encoded`

![soal3-2](/img/soal3-2.png)

Didapat kredensial:
```
Form item: "username" = "10pemuda"
Form item: "password" = "guncangdunia"
```

### Soal 4
> Temukan web-web yang menggunakan basic authentication method

Website dengan basic authentication method dapat dicari menggunakan display filter `http.authbasic`

![soal4-1](/img/soal4-1.png)

### Soal 5
> Ikuti perintah di [aku.pengen.pw](aku.pengen.pw),
> username dan password bisa didapatkan dari file `.pcapng`

Kredensial login didapat dari packet yang menuju host [aku.pengen.pw](aku.pengen.pw) dan menggunakan basic authentication method. Menggunakan display filter `http.host == "aku.pengen.pw" && http.authbasic`

![soal5-2](/img/soal5-2.png)

Kredensial yang didapat berada pada header `HTTP`
```
Authorization: Basic a2FrYWtnYW10ZW5rOmhhcnRhdGFodGFiZXJtdWRh\r\n
	Credentials: kakakgamtenk:hartatahtabermuda
```

![soal5-3](/img/soal5-3.png)

Perintah pada [aku.pengen.pw](aku.pengen.pw) adalah
> Sebutkan urutan konfigurasi pengkabelan T568B

Putih orange, orange, putih hijau, biru, putih biru, hijau, putih coklat, coklat

### Soal 6

> Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut)

Mencari packet yang membawa `Answer.zip` dalam ftp menggunakan display filter `ftp-data.command contains "Answer.zip"`

![soal6-1](/img/soal6-1.png)

`Answer.zip` di download dengan cara mengikuti stream tcp packet tersebut lalu menyimpan stream sebagai raw data dengan nama Answer.zip

![soal6-2](/img/soal6-2.png)

Mencari `Zipkey.txt` sama seperti sebelumnya, menggunakan display filter `ftp-data.command contains "Zipkey.txt"`. Lalu mengikuti stream tcp file tersebut.

![soal6-3](/img/soal6-3.png)

Password untuk file zip didapat adalah `hey997400323051`, yang kemudian digunakan untuk membuka zip dan mendapatkan:

![soal6-4](/img/soal6-4.png)

### Soal 7

> Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut.   Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"

File zip yang menyimpan `Yes.pdf` dicari menggunakan display filter `ftp-data contains "Yes.pdf"`

![soal7-1](/img/soal7-1.png)

Puisi berada dalam `473.zip`

![soal7-2](/img/soal7-2.png)

### Soal 8

> Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service

Mencari ip untuk Microsoft FTP Service menggunaka display filter `ftp contains "Microsoft"`

![soal8-1](/img/soal8-1.png)

Mencari packet RETR pada ip address `198.246.117.106` menggunakan display filter `ftp contains RETR && ip.addr == 198.246.117.106`

![soal8-2](/img/soal8-2.png)

### Soal 9
> Cari username dan password ketika login FTP pada localhost

Kredensial FTP didapat menggunakan display filter `ftp contains USER or ftp contains PASS`

![soal9-1](/img/soal9-1.png)

### Soal 10

> Cari file .pdf di wireshark lalu download dan buka file tersebut,
> clue: `25 50 44 46`

Packet yang menyimpan file pdf dicari menggunakan display filter `frame contains "application/pdf"`

![soal10-1](/img/soal10-1.png)

Klu yang diberikan merupakan hex dump dari file zip `25 50 44 46`, dapat ditemukan dalam stream tcp packet

![soal10-2](/img/soal10-2.png)

File pdf yang didapat:

![soal10-3](/img/soal10-3.png)

### Soal 11
> Filter sehingga wireshark hanya mengambil paket yang mengandung port 21

Capture filter untuk packet yang mengandung port 21: `port 21`

![soal11-1](/img/soal11-1.png)

### Soal 12
> Filter sehingga wireshark hanya mengambil paket yang berasal port 80

Capture filter untuk packet yang berasal dari port 80: `src port 80`

![soal12-1](/img/soal12-1.png)

### Soal 13
> Filter sehingga wireshark hanya mengambil paket yang menuju port 443

Capture filter untuk packet yang menuju port 443: `dst port 443`

![soal13-1](/img/soal13-1.png)

### Soal 14
> Filter sehingga wireshark hanya mengambil paket yang berasal dari ipkalian

Mencari ip klien dalam jaringan menggunakan `ipconfig` dalam cmd.
Capture filter untuk packet yang berasal dari ip klien: `src host 192.168.1.68`

![soal14-1](/img/soal14-1.png)

### Soal 15
> Filter sehingga wireshark hanya mengambil paket yang tujuannya ke [monta.if.its.ac.id](monta.if.its.ac.id)

Mencari ip hostname `monta.if.its.ac.id` menggunakan `ping monta.if.its.ac.id` dalam cmd.
Capture filter untuk packet yang berasal dari [monta.if.its.ac.id](monta.if.its.ac.id):
`dst host 103.94.190.11`

![soal15-1](/img/soal15-1.png)
