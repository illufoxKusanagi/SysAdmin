```copy code 
Nama             : Muhammad Arief Satria Wibawa
NRP              : 3122600015
Kelas            : D4 IT A
Dosen Pengampu   : Dr. Ferry Astika Saputra S.T., M.Sc
```


**<h1 style="font-family:bahnschrift;">- Perbedaan Debian 12 (Bookworm) dan Debian 11 (Bullseye)</h1>**

| Perbedaan         | Debian 12 (Bookworm)                                                          | Debian 11 (Bullseye)                                                              |
| ----------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Versi Kernel      | 6.1                                                                           | 5.10                                                                              |
| Kebutuhan Sistem  | Mungkin lebih tinggi                                                          | Moderat                                                                           |
| Penerapan systemd | Aktivasi jurnal persisten oleh default dengan fallback ke penyimpanan volatil | Tidak dijelaskan, tetapi mungkin ada perbedaan versi                              |
| Perbedaan Package | Lebih baru, 11.089 paket baru, non-free software disertakan dalam ISO primer  | Tidak dijelaskan jumlahnya, namun non-free packages disertakan dalam ISO terpisah |

**<h1 style="font-family:bahnschrift;">Fungsi dari sudo</h1>**
>"sudo" (superuser do) adalah perintah yang memungkinkan pengguna untuk menjalankan perintah sebagai pengguna lain, biasanya sebagai superuser (root). Ini memberikan hak akses terbatas dan terkontrol kepada pengguna, yang dicatat dan dilacak.


**<h3 style="font-family:bahnschrift;">Langkah-langkah penambahan user sebagai user sudo</h3>**
- Buka terminal dan ketik su untuk masuk ke user
  <br><img src="assets/terminal.png" width="500"><br>
- Ketikkan perintah su untuk masuk ke user root
  <br><img src="assets/su.png" width="500"><br>
- Ketikkan perintah sudo visudo untuk membuka konfigurasi sudoers
  <br><img src="assets/sudo visudo.png" width="500"><br>
  <br><img src="assets/visudo menu.png" width="500"><br>
- Pada bagian ```#User privilege spesification``` tambahkan user dibawah user root
  <br><img src="assets/user.png" width="500"><br>
- Kemudian, ketik ctrl+x untuk keluar, namum save terlebih dahulu
  <br><img src="assets/terminal end.png" width="500"><br>
- Kemudian exit dari user root
  <br><img src="assets/exit.png" width="500"><br>