```copy code 
Nama             : Muhammad Arief Satria Wibawa
NRP              : 3122600015
Kelas            : D4 IT A
Dosen Pengampu   : Dr. Ferry Astika Saputra S.T., M.Sc
```

- # _CHAT ANTAR KELOMPOK_

## - MENGGUNAKAN TELNET

- Melakukan pengiriman pesan
  ketik `telnet mail.kelompok4.local 25` lalu masukkan sintaks berikut:
  - `HELO` untuk memulai sesi Telnet dengan server
  - `MAIL FROM:` untuk mendefinisikan alamat email pengirim
  - `RCPT TO:` untuk mendefinisikan alamat email penerima
  - `DATA` untuk memasukkan isi dari email yang dikirim
  
  ![kirim email](assets/kirim%20email.png)
  >Jika muncul output tersebut, maka email berhasil dikirim ke alamat tujuan

- Pengecekan pesan yang masuk
  ketik `telnet mail.kelompok4.local 110` lalu masukkan sintaks berikut:
  - `user` untuk memasukkan username dari user
  - `pass:` untuk memasukkan password dari user
  - `list:` untuk melihat list dari email yang diterima
  - `RETR {index}` untuk melihat isi pesan dari index tertentu
  
  ![terima email](assets/accept%20email.png)
  
## - MENGGUNAKAN DEBIAN EVOLUTION

- Melakukan pengiriman pesan
  - Masukkan email pengirim
  - Masukkan email pengirim
  - Masukkan pesan yang akan dikirim
  
  ![mail send](assets/evol%20send%20email.png)

  Jika berhasil, maka akan muncul seperti gambar berikut: 

  ![mail success](assets/evol%20success.png)
  
## - MENGGUNAKAN ROUNDCUBE

1. Lakukan instalasi roundcube dengan perintah
   ```bash
   sudo apt install roundcube
   ```
![](assets/rc1.png)

![](assets/rc2.png)

![](assets/rc3.png)

2. Lalu kita buat MariaDB database dan user untuk roundcubenya

![](assets/rc4.png)

3. Lalu konfigurasi config.inc.php di roundcube.

![](assets/rc5.png)

4. Konfigurasi apache.conf.

![](assets/rc6.png)

5. Konfigurasi 000-default.conf.

![](assets/rc7.png)

6. Lalu kita rekonfigurasi dengan perintah
   ```bash
   sudo dpkg-reconfigure roundcube-core
   ```
![](assets/rc8.png)

![](assets/rc9.png)

![](assets/rc10.png)

![](assets/rc11.png)

![](assets/rc12.png)

![](assets/rc13.png)

![](assets/rc14.png)

![](assets/rc15.png)

![](assets/rc16.png)

![](assets/rc17.png)

![](assets/rc18.png)

![](assets/rc19.png)

![](assets/rc20.png)
