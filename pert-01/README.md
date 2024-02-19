```copy code 
Nama             : Muhammad Arief Satria Wibawa
NRP              : 3122600015
Kelas            : D4 IT A
```
**<h1 style="font-family:bahnschrift;">Instalasi Debian Linux menggunakan Virtual Box</h1>**


**<h2 style="font-family:bahnschrift;">Pra instalasi</h2>**
- Setelah men-download file iso dari debian 12(yang mahasiswa gunakan), buka vbox, lalu klik new

    <br><img src="assets/buka vbo.png" width="500"><br>

- Kemudian, user akan diarahkan ke pemilihan iso file. Ketikkan path dimana user ingin menyimpan OS ini pada bagian folder, serta file debian iso disimpan di bagian ISO image, serta check pada pilihan 'skip unattended installation'
  <br><img src="assets/pilih iso (2).png" width="500"><br>

- kemudian, pilih memory dan processor, disesuaikan dengan hardware milik user, lalu klik next.
  <br><img src="assets/setting hardware.png" width="500"><br>

- kemudian, pilih size virtual hard disk yang diinginkan. Namun, perlu disesuaikan dengan kemampuan hardware user. 
  <br><img src="assets/setting storage.png" width="500"><br>

**<h2 style="font-family:bahnschrift;">Instalasi</h2>**

- Lalu klik next, maka user akan masuk ke halaman pertama instalasi, lalu pilih graphical install
  <br><img src="assets/01 install gui.png" width="500"><br>

- Lalu, user akan dibawa ke tampilan berikut untuk setting bahasa, lokasi, serta keyboard
  <br><img src="assets/02 setting bahasa.png" width="500"><br>
  <br><img src="assets/03 pilih lokasi.png" width="500"><br>
  <br><img src="assets/04 pilih localization.png" width="500"><br>
  <br><img src="assets/05 pilih keyboard.png" width="500"><br>

- Setelah itu, user melakukan setting hostname, username, serta password
    <br><img src="assets/06 set hostname.png" width="500"><br>
    <img src="assets/07 domain name.png" width="500"><br>
    <img src="assets/08 set password.png" width="500"><br>
    <img src="assets/09 set nama.png" width="500"><br>
    <img src="assets/10 set uname.png" width="500"><br>
    <img src="assets/11 set password for user.png" width="500"><br>

- Kemudian, user dapat memilih zona waktu, sesuai dengan kebutuhan
    <br><img src="assets/12 setting jam.png" width="500"><br>

- Setelah itu, user bisa melakukan setting disk secara manual
    <br><img src="assets/13 set disk manual.png" width="500"><br>
- Setting storage sedemikian rupa menjadi berikut : 
  1. 20gb untuk keperluan OS
  2. 1.8gb untuk swap area
  3. 5gb untuk keperluan lain
   
    <br><img src="assets/16 setting storage.png" width="500"><br>
- kemudian tunggu proses instalasi base systemnya
    <br><img src="assets/17 tunggu instalasi.png" width="500"><br>

- Setelah itu, anda diminta untuk memilih debian archive mirror (disarankan menggunakan mirror pada region user)
    <br><img src="assets/pilih mirror.jpg" width="500"><br>
    
- Kemudian, tunggu proses instalasinya selesai. Proses ini bisa memakan waktu yang cukup lama, tergantung pada koneksi internet dari user
  <br><img src="assets/tunggu proses instalasi.jpg" width="500"><br>

- Setelah selesai, user diberi pilihan apakah ingin menginstall GRUB boot loader atau tidak. Lalu ketik yes untuk menginstallnya, kemudian klik device yang tersedia, lalu continue
  <br><img src="assets/install grub.jpg" width="500"><br>

- Setelah proses instalasi selesai, akan muncul notifikasi berikut 
  <br><img src="assets/17 setup complete.png" width="500"><br>


**<h2 style="font-family:bahnschrift;">Setup akhir</h2>**
- Setelah itu, anda bisa login ke OS debian dan siap digunakan
  <br><img src="assets/welcome.png" width="500"><br>

- User juga diminta untuk melakukan beberapa setup sebagai berikut
    <br><img src="assets/welcome 1.png" width="500"><br>
    <img src="assets/welcome 2.png" width="500"><br>
    <img src="assets/welcome 3.png" width="500"><br>