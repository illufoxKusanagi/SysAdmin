```copy code
Nama             : Muhammad Arief Satria Wibawa
NRP              : 3122600015
Kelas            : D4 IT A
Mata Kuliah      : Sistem Administrasi Jaringan
Dosen Pengampu : Dr. Ferry Astika Saputra S.T., M.Sc
```
    

# _PROSES IMPLEMENTASI PROJECT MONITORING DOCKER CONTAINER_

## INSTALASI DOCKER

### Menghapus Versi Lama (Jika sebelumnya pernah memasang)

- Ketik `for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done`:
  
  ![](assets/docker1.png)

### Install Dengan Repositori APT

- Masukkan command berikut ini:
  ```
  - sudo apt-get update
  - sudo apt-get install ca-certificates curl
  - sudo install -m 0755 -d /etc/apt/keyrings
  - sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
  - sudo chmod a+r /etc/apt/keyrings/docker.asc
  - echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \ $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```
    ![](assets/docker2.png)
  
  - `sudo apt-get update`:
    
      ![](assets/dockera.png)
  
### Install Paket Docker

- Untuk memasang paket versi terbaru gunakan perintah ini:
  - `sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`:
    
      ![](assets/docker3.png)
    
- Cek versi Docker:
  - `docker --version`:
    
      ![](assets/dockerb.png)

### Verifikasi

- Untuk memverifikasi bahwa penginstalan berhasil gunakan perintah:
  - `sudo docker run hello-world`:
    
      ![](assets/dockerc.png)

## INSTALASI PROMETHEUS, GRAFANA, CADVISOR

### Membuat Direktori Baru Untuk Monitoring

- Untuk membuat direktori baru gunakan perintah:
  - `mkdir Monitoring`:

      ![](assets/03.%20buat%20direktori%20Monitoring.png)

### Membuat File docker-compose.yml dan prometheus.yml

- Edit isi dengan vi:
  - `vi docker-compose.yml`
  - `vi prometheus.yml`
      ![](assets/02.%20buat%20direktori%20untuk%20file%20monitoring.png)

- Isi dari docker-compose.yml untuk instalasi Prometheus, Grafana, cAdvisor pada docker:

  ![alt text](assets/04.%20isi%20docker-compose%20.%20yml.png)
  - Prometheus
    - image: Menggunakan image prom/prometheus:latest, yang merupakan versi terbaru dari Prometheus.
    - container_name: Menetapkan nama container sebagai prometheus.
    - ports: Memetakan port 9090 di host ke port 9090 di container, yang merupakan port default Prometheus untuk akses web.
    - command: Menjalankan Prometheus dengan file konfigurasi yang ditentukan (--config.file=/etc/prometheus/prometheus.yml).
    - volumes: Mengikat file konfigurasi prometheus.yml dari direktori lokal ke dalam container di jalur /etc/prometheus/prometheus.yml dengan akses read-only (:ro).
    - depends_on: Menentukan bahwa layanan prometheus bergantung pada layanan cadvisor, sehingga cadvisor harus dijalankan terlebih dahulu.
  
  - Grafana
    - image: Menggunakan image grafana/grafana:latest, yang merupakan versi terbaru dari Grafana.
    - container_name: Menetapkan nama container sebagai grafana.
    - ports: Memetakan port 3000 di host ke port 3000 di container, yang merupakan port default Grafana untuk akses web.
    - volumes: Menyimpan data Grafana di volume Docker bernama grafana-storage, yang di-mount ke dalam container di jalur /var/lib/grafana.

  - cAdvisor
    - image: Menggunakan image gcr.io/cadvisor/cadvisor:latest, yang merupakan versi terbaru dari cAdvisor.
    - container_name: Menetapkan nama container sebagai cadvisor.
    - ports: Memetakan port 8080 di host ke port 8080 di container, yang merupakan port default cAdvisor untuk akses web.
    - volumes:
      - (/:/rootfs:ro) Mounting root filesystem dari host ke dalam container pada direktori /rootfs dengan akses read-only. Ini bertujuan supaya cAdvisor melihat keseluruhan filesystem host.
      - (/var/run:/var/run:rw) Mounting direktori /var/run di host ke dalam container dengan akses read-write. Bertujuan supaya cAdvisor dapat mengakses informasi runtime dari Docker.
      - (/sys:/sys:ro) Mounting direktori /sys di host ke dalam container dengan akses read-only. Bertujuan untuk memberikan cAdvisor akses ke filesystem sys untuk melihat statistik kernel.
      - (/var/lib/docker/:/var/lib/docker:ro) Mounting direktori /var/lib/docker di host ke dalam container dengan akses read-only. Bertujuan memberikan akses cAdvisor ke data Docker yang penting, seperti metadata container.


- Isi dari prometheus.yml untuk mengumpulkan metrik:

  ![alt text](assets/05.%20isi%20prometheus%20.%20yml.png)
  - Global Configuration: Menetapkan interval scraping default untuk semua target.
  - Job 'prometheus': Konfigurasi untuk melakukan scraping data dari instance Prometheus itu sendiri.
  - Job 'cadvisor': Konfigurasi untuk melakukan scraping data dari instance cAdvisor.

- Cek kontainer yang berjalan:
  - `docker ps -a`

      ![](assets/06.%20cek%20kontainer%20berjalan.png)

## KONFIGURASI GRAFANA DASHBOARD

- Buka web grafana dengan port 3000:
  - `localhost:3000`

      ![](assets/g1.png)

- Tambahkan dashboard untuk monitoring baru:
      ![](assets/g2.png)

- Import template dashboard:
      ![](assets/g3.png)

- Tambahkan ID dari template dashboard lalu tekan load:
      ![](assets/g4.png)

- Sesuaikan konfigurasi dashboard dan ambil dari prometheus:
      ![](assets/g5.png)

- Tampilan dashboard dari template seperti berikut:
      ![](assets/g6.png)

- Sesuaikan panel dan konfigurasi lain sehingga dapat menampilkan metrik yang diinginkan atau yang ingin dimonitoring:
  - Tampilan dashboard setelah dikonfigurasi ulang adalah seperti berikut.
      ![](assets/g13.png)
      - (CPU Usage on Node) Memantau penggunaan CPU pada host machine.
      - (Network Traffic on Node) Melacak traffic jaringan pada host machine.
      - (Running container) Menampilkan jumlah kontainer yang sedang berjalan.
      - (Sent Network Traffic per Container) Melacak traffic jaringan terkirim per kontainer.
      - (Received Network Traffic per Container) Melacak traffic jaringan yang diterima oleh kontainer tertentu. Ini melengkapi panel "Sent Network" untuk analisis traffic keseluruhan.
      - (CPU Usage per Container) Memantau penggunaan CPU per kontainer.
      - (Cached Memory per Container) Menampilkan memori cache per kontainer.
      - (Memory Usage per Container) Memantau penggunaan memori per kontainer.

## KONFIGURASI ALERT

### Membuat Bot Telegram

- Buka telegram dan search BotFather dan Get ID bot:
      ![](assets/g7.png)

- Buat bot alert pada BotFather:
      ![](assets/g10.png)

- Berikut tampilan bot yang telah dibuat:
      ![](assets/g12.png)

- Ikuti alurnya sehingga kita mendapatkan token API untuk mengirim data ke bot:
      ![](assets/g9.png)

- Dapatkan ID dari telegram kita menggunakan bot Get ID bot:
      ![](assets/g8.png)


### Menambahkan Contact Points untuk telegram
- Tambahkan token dan chat ID yang telah kita dapatkan sebelumnya:
      ![](assets/image-1.png)

### Konfigurasi Notification Policy untuk alert:
![alt text](assets/image-2.png)

### Konfigurasi Alert Rules ketika ada container yang mati:
![alt text](assets/image-3.png)

### Konfigurasi Alert Rules ketika ada memory container yang melebihi batas:
![alt text](assets/image-4.png)

### Konfigurasi template message untuk susunan teks telegram:
![alt text](assets/image-5.png)

### Percobaan ketika ada container yang mati:
![alt text](assets/g11.png)
