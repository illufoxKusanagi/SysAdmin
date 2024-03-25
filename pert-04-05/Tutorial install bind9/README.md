```copy code 
Nama             : Muhammad Arief Satria Wibawa
NRP              : 3122600015
Kelas            : D4 IT A
Dosen Pengampu   : Dr. Ferry Astika Saputra S.T., M.Sc
```
**<h1 style="font-family:bahnschrift;">Intalasi bind9 dan konfigurasi di linux</h1>**

## Install bind9, bind9-doc dan bind9-dnsutils 

  - Memasukkan perintah `sudo apt install bind9` dan  `sudo apt install bind9-doc` 
    >Perintah ini digunakan untuk melakukan instalasi bind9

    <img width="100%" src="assets/step1, install bind9.png">
  
  - Memasukkan perintah `sudo apt install bind9-dnsutils`
    >Perintah ini digunakan untuk tools konfigurasi
  
    <img width="100%" src="assets/step2, install bind9-doc, dnsutils.png">
    
  - Masukkan perintah `cd /etc/bind` untuk masuk ke direktori ini, lalu ketik perintah  `sudo nano named.conf`
    >Perintah ini digunakan untuk mengedit isi dari `named.conf`. Lalu, edit isinya seperti berikut : 
  
    <img width="100%" src="assets/named conf.png">

## Konfigurasi

  - Masukkan perintah `sudo nano named.conf.options`
    > Perintah ini digunakan untuk mengedit isi dari `named.conf.options`, dan edit isinya menjadi seperti berikut : 

    <img width="100%" src="assets/step4, edit named.conf.options.png">

  - Masukkan perintah `sudo nano named.conf.local`
    >Perintah ini digunakan untuk mengedit isi dari `named.conf.local`, dan edit isinya menjadi seperti berikut :

    <img src="assets/step xx. locale.png">

  - Masukkan perintah `cd /var/lib/bind` untuk masuk ke direktori ini, lalu ketik perintah `sudo touch db.kelompok7.local` untuk membuat file kosong yang bernama `db.kelompok7.local`.

  - Masukkan  perintah `sudo nano db.kelompok7.local` 
    >Perintah ini digunakan untuk mengedit isi dari `db.kelompok7.local`, dan edit sehingga menjadi seperti berikut :
    
    <img width="100%" src="assets/step5, edit db.kel7.local.png">

  - Masukkan perintah `sudo touch db.kelompok7.local.inv` yang digunakan untuk membuat file kosong yang bernama `db.kelompok7.local.inv`.
  
  - Masukkan perintah `sudo nano db.kelompok7.local.inv`
    >Perintah ini digunakan untuk mengedit isi dari file `db.kelompok7.local.inv` dan edit isinya menjadi seperti berikut : 

    <img width="100%" src="assets/step6, edit db.kel7.local.env.png">

  - Masukkan perintah `cd` untuk keluar dari direktori `/var/lib/bind` dan masukkan perintah `sudo nano /etc/resolv.conf` untuk mengedit isinya, hingga seperti berikut
    
    <img width="100%" src="assets/step7, edit reolv.conf.png">

  - Masukkan perintah `named-checkzone kelompok7.local db.kelompok7.local` untuk mengecek domainnya, dan masukkan perintah`named-checkzone 136.168.192.inaddr-arpa` untuk mengecek domain inversnya.
  
    <img width="100%" src="assets/step8 9, pengecekan domain.png">

  - Masukkan perintah `sudo systemctl restart named` untuk melakukan restart pada domain named, kemudian lakukan tes dengan mengetikkan perintah `sudo systemctl status named`
    <img width="100%" src="assets/step9, pengecekan status.png">

  - Masukkan perintah `sudo dig kelompok7.local` untuk domain yang dibuat per-kelompok dan `sudo dig 192.168.137.18`
    >Perintah ini digunakan untuk melakukan pengecekan informasi lebih lanjut pada domain

    <img width="100%" src="assets/step10, pengecekan dig.png">

  - Masukkan perintah `nslookup ns` untuk melakukan query DNS dan melihat detail dari ns dan `nslookup -q=MX` yang digunakan untuk melihat detail domain mailnya
    
    <img width="100%" src="assets/step11, pengecekan nslookup MX.png">