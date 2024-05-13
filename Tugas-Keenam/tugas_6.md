<h1 align="center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>

<h3 align="center">Dosen Pembimbing: Dr. Ferry Astika Saputra ST, M.Sc</h3>

<p align="center"><img src="images/logo.png" alt="logo"></p>

<div align="center">
  <h3>Disusun Oleh:</h3>
  <p align="center">Mayada Azizah 3122500015</p>
  <p align="center">Adinda Zahra Qariru 3122500020</p>
  <p align="center">Masyitha Fahra Nabila 3122500023</p>
</div>

<div align="center">
  <h3>PROGRAM STUDI TEKNIK INFORMATIKA <br>
      POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br>
      TAHUN 2023/2024 <br>
  </h3>
</div>

---


## Web Browser(Client)
<p align="center">
  <img src="./images/web_browser.png" width="80%" height="auto">
</p>

Gambar di atas menunjukkan arsitektur dari komponen utama sebuah web browser. Komponen-komponen ini bekerja bersama untuk memungkinkan pengguna mengakses dan berinteraksi dengan situs web.

- **User Interface** <br>
  User Interface (UI) adalah bagian dari browser yang langsung berinteraksi dengan pengguna. Ini mencakup elemen seperti bilah alamat, tombol, menu, dan tab. Antarmuka pengguna bertanggung jawab untuk mengambil masukan pengguna dan mengirimkannya ke mesin browser.
- **Browser Engine** <br>
  Browser Engine adalah "otak" dari browser. Ini bertanggung jawab untuk menginterpretasi masukan pengguna dan berkomunikasi dengan komponen browser lainnya. Mesin browser juga menangani tugas seperti mengelola riwayat dan bookmark, dan memproses cookie.
- **Rendering Engine** <br>
- Rendering Engine bertanggung jawab untuk mengambil kode HTML, CSS, dan JavaScript dari server web dan mengubahnya menjadi representasi visual yang dapat ditampilkan di layar pengguna. Mesin pemrosesan juga menangani tugas seperti tata letak dan lukisan.
- **Networking** <br>
  Komponen jaringan bertanggung jawab untuk mengirimkan dan menerima permintaan dari dan ke server web. Ini menggunakan protokol seperti HTTP dan HTTPS untuk mentransfer data
- **JavaScript Interpreter** <br>
  JavaScript Interpreter bertanggung jawab untuk mengeksekusi kode JavaScript yang tertanam dalam halaman web. JavaScript adalah bahasa skrip yang memungkinkan halaman web menjadi lebih interaktif dan dinamis.
- **UI Backend** <br>
  UI Backend bertanggung jawab untuk menggambar elemen antarmuka pengguna di layar. Ini menggunakan pustaka grafis sistem operasi untuk merender antarmuka pengguna.
- **Data Persistence** <br>
  Komponen Data Persistence bertanggung jawab untuk menyimpan data seperti cookie, riwayat, dan bookmark. Data ini disimpan di komputer pengguna sehingga dapat digunakan bahkan ketika browser tidak terbuka.

Selain komponen utama ini, web browser juga mencakup sejumlah komponen lain, seperti security module, plug-in manager, dan search engine. 

Berikut adalah gambaran singkat tentang bagaimana komponen-komponen browser bekerja bersama untuk menampilkan halaman web:
1. Pengguna memasukkan URL ke dalam bilah alamat.
2. Mesin browser mengirim permintaan ke server web untuk halaman web.
3. Server web mengirimkan kode HTML, CSS, dan JavaScript untuk halaman web ke browser.
4. Mesin browser meneruskan kode HTML, CSS, dan JavaScript ke mesin pemrosesan.
5. Mesin pemrosesan mengkonversi kode HTML, CSS, dan JavaScript menjadi representasi visual.
6. Backend antarmuka pengguna menggambar representasi visual di layar.

#

<h2 align="center">Web Server</h2>
<p align="center">
  <img src="./images/web_server.JPG" width="80%" height="auto">
</p>

Gambar di atas menunjukkan diagram siklus permintaan-respons web. Siklus ini adalah proses dasar di mana browser web dan server web berkomunikasi untuk mengirimkan halaman web kepada pengguna.

- **Client** <br>
  Klien adalah perangkat lunak yang memulai permintaan untuk halaman web. Ini biasanya merupakan browser web, tetapi juga bisa menjadi jenis perangkat lunak lain, seperti aplikasi seluler atau aplikasi desktop.
- **Request** <br>
  Permintaan adalah pesan yang dikirim oleh klien ke server. Ini berisi informasi tentang sumber daya yang diminta, seperti URL, metode HTTP (mis., GET, POST), dan header apa pun.
- **Server** <br>
  Server adalah perangkat lunak yang menerima dan merespons permintaan dari klien. Biasanya terletak di komputer jarak jauh yang terhubung ke internet.
- **Respons** <br>
  Respons adalah pesan yang dikirim kembali oleh server ke klien. Ini berisi sumber daya yang diminta, seperti halaman HTML, gambar, atau objek JSON. Ini juga berisi informasi tentang status permintaan, seperti kode sukses (200) atau kode kesalahan (404).

Langkah-langkah dalam Siklus Permintaan-Respons Web:
1. Pengguna memasukkan URL ke dalam bilah alamat browser web
2. Browser mengurai URL dan mengirim permintaan DNS ke server DNS untuk meresolusi URL ke alamat IP.
3. Server DNS merespons dengan alamat IP dari server web yang menyimpan sumber daya yang diminta.
4. Browser membuka koneksi TCP ke server web menggunakan alamat IP.
5. Browser mengirim permintaan HTTP ke server web melalui koneksi TCP.
6. Server web menerima permintaan HTTP dan memprosesnya.
7. Server web mengirim respons HTTP kembali ke browser melalui koneksi TCP.
8. Browser menerima respons HTTP dan menguraikannya.
9. Browser menampilkan sumber daya yang diminta kepada pengguna.

Tambahan:
- Siklus permintaan-respons web dapat diulang beberapa kali untuk memuat semua sumber daya yang membentuk halaman web.
- Siklus permintaan-respons web dapat digunakan untuk mengirimkan data ke server, seperti saat pengguna mengirimkan formulir.
- Siklus permintaan-respons web dapat digunakan untuk menerima data dari server, seperti saat pengguna memuat halaman web.
##
# Containerized Web Server Using Docker
- Apakah Anda mengetahui mengenai Virtual Machine? Dahulu, semua perusahaan ataupun orang yang sedang ingin menjalankan aplikasi itu menggunakan Virtual Machine. Namun, dengan teknologi Virtual Machine ini akan menghabiskan resource yang digunakan. Karena konsep dari Virtual Machine ini sendiri yaitu berjalan diatas OS dan membuat OS terbaru untuk Virtual Machine yang dimana ini akan membebankan kinerja dari perangkat komputer itu sendiri. Namun, dengan adanya teknologi baru yang bernama Container, penggunaan Virtual Machine akan tergantikan. Karena dengan adanya teknologi Container ini sendiri memungkinkan para Developer untuk membuat aplikasi dan mendeploynya menggunakan OS yang ada di komputer itu sendiri. Dengan hal itu, akan mengurangi resource yang besar dan juga dapat berjalan dengan ringan. Pada teknologi Container terdapat sebuah Container yang bernama Docker, Docker merupakan sebuah aplikasi open source yang memungkinkan Anda membuat, menguji dan menerapkan aplikasi dengan cepat. Dengan Anda menggunakan Docker, Anda dapat dengan cepat menerapkan dan menskalakan aplikasi ke lingkungan apapun. Docker merupakan salah satu solusi dari permasalahan yang sering dialami oleh para Developer untuk mengembangkan aplikasi agar dapat berjalan fleksibel di berbagai lingkungan. Kemampuan yang dimiliki oleh Docker yaitu mampu untuk menjalankan berbagai macam aplikasi dengan konfigurasi yang berbeda, walaupun dalam perangkat yang sama.

## A. Pemasang Docker di Debian vmBox

### 1. Terlebih dulu hapus Docker.io dan dependency bawaan dari DEBIAN.
``  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done``

### 2.  Update/Upgrade Repository dan tambahkan Docker Official GPG Keys 
<p align="center">
  <img src="./images/docker_1.png" width="80%" height="auto">
</p>

### 3. Kemudian, tambahkan Repository Apt Resources
<p align="center">
  <img src="./images/docker_2.png" width="80%" height="auto">
</p>

### 4. Install DOCKER OFFICIAL PACKAGE
<p align="center">
  <img src="./images/docker_3.png" width="80%" height="auto">
</p>

### 5. Apabila telah terinstaal docker, maka jalankan Hello World.
<p align="center">
  <img src="./images/docker_4.png" width="80%" height="auto">
  <img src="./images/docker_5.png" width="80%" height="auto">
</p>

## B. Membuat Docker Image

### 1.Taruh file untuk Docker file pada salah satu direktori
<p align="center">
  <img src="./images/docker_6.png" width="80%" height="auto">
</p>

### 2. Ikuti langkah-langkah dari docker-examples
`git clone https://github.com/alfiyansys/docker-examples.git
 docker build -t example .
 docker run -p 3000:80 example`
  <p align="center">
  <img src="./images/docker_7.png" width="80%" height="auto">
</p>

### 3. Open browser http://localhost:3000 dan lihat hasilnya
<p align="center">
  <img src="./images/docker_8.png" width="80%" height="auto">
</p>

## C. Apache2 + Dns Resolver + Docker Uptime Kuma Package

### 1. Git Clone Uptime Kuma dahulu
`git clone https://github.com/louislam/uptime-kuma.git
cd uptime-kuma`

### 2. Coba jalankan
` sudo docker compose up
 sudo docker ps -a`

### 3. Cek pada port berjalan yaitu 3001
<p align="center">
  <img src="./images/docker_9.png" width="80%" height="auto">
</p>

## Bagaimana jika menggunakan url monitoring.kelompok10.local saat mengaksesnya?

### 1. Konfigurasi file /var/lib/bind/db.kelompok10.local
<p align="center">
  <img src="./images/docker_10.png" width="80%" height="auto">
</p>

### 2. Install beberapa Package berikut
`sudo a2enmod`

### 3. Lakukan Konfigurasi pada Apache2
`sudo nano /etc/apache2/sites-enabled/000-default.conf`
<p align="center">
  <img src="./images/docker_11.png" width="80%" height="auto">
</p>

### 4. Lakukan pengecekan pada web browser
<p align="center">
  <img src="./images/docker_12.png" width="80%" height="auto">
</p>