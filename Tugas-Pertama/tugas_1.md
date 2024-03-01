<h1 align="center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>

<h3 align="center">Dosen Pembimbing: Dr. Ferry Astika Saputra ST, M.Sc</h3>

<p align="center"><img src="img/logo.png" alt="logo"></p>

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

##
<h3>Soal</h3>

1. Buatlah tulisan tentang langkah-langkah instalasi sistem operasi Debian. Anda bisa menggunakan aplikasi virtualisasi seperti VirtualBox, VMWare Player, Vmware Fusion (MAC), dls. Kebutuhan sistem adalah sebagai berikut :
   - CPU : 2 core
   - RAM : 4096 (min)
   - HDD : 25 GB dengan partisi : <br>
     - / : 20 GB
     - /storage : 5 GB
     - swap : 1,5 GB
   - Hostname : SysAdmin-NRP <br>

2. Buat ringkasan tentang perbedaan dari Debian 12 (bookworm) dengan Debian 11 (bullseye) : versi kernel, kebutuhan sistem, penerapan systemd dan perbedaan packagenya (dalam bentuk tabel) !
3. Jelaskan fungsi dari file "/etc/groups" beserta formatnya!
4. Jelaskan perbedaan penggunaan perintah "su" dengan "su -"!
5. Jelaskan fungsi dari "sudo" !
6. Jelaskan langkah-langkah penambahan user anda sebagai user sudo ! Gunakan perintah "su -" lalu setelah masuk sebagai root, jalankan perintah "visudo". Tambahkan user anda di bawah user root pada bagian " # User privilege specification"

##

<h3>Jawaban dan Penjelasan</h3>

1. Langkah - langkah instalasi
   - <b>Langkah 1:</b> Sebelum memulai instalasi, pastikan Anda telah men-download file ISO Debian dari situs resminya (https://www.debian.org) dan memiliki aplikasi VirtualBox terpasang di sistem Anda. <br>
   <img src="img/1.png"> &nbsp; <img src="img/2.png">
   - <b>Langkah 2:</b> Buat Mesin Virtual di VirtualBox <br>
     - Buka VirtualBox dan klik tombol "New" untuk membuat mesin virtual baru.
       <img src="img/new.png">
     - Beri nama mesin virtual Anda, misalnya "debian12", dan pilih tipe "Linux". Pilih versi Debian yang sesuai dengan ISO yang Anda unduh (misalnya Debian 11 64-bit).
       <img src="img/new1.png">
     - Atur RAM sesuai kebutuhan (minimal 4096 MB) dan di sini kami setting CPU nya sesuai kebutuhan (minimal 2 core)
       <img src="img/new2.png">
     - Pilih "Create a virtual hard disk now" dan klik "Next".
       <img src="img/new3.png">
     - Kemudian akan muncul summary (kesimpulan).
       <img src="img/new4.png">
   - <b>Langkah 3:</b> Proses Instalasi <br>
     - Klik "Start" untuk memulai mesin virtual Debian.
       <img src="img/start.png">
     - Pilih opsi "Graphical Install" dari menu boot yang muncul.
       <img src="img/install.png">
     - Pilih bahasa yang diinginkan untuk instalasi dan tekan "Enter".
       <img src="img/install1.png">
     - Pilih lokasi Anda dan lanjutkan.
       <img src="img/install2.png"> <br>
       <img src="img/install3.png"> 
     - Pilih Konfigurasi keyboard yang diinginkan dan tekan "Enter" untuk melanjutkan instalasi
       <img src="img/install6.png"> <br>
       <img src="img/install7.png">
     - Selanjutnya konfigurasikan jaringan, membuat hostname, disini kami menggunakan "SysAdmin-NRP" kemudian untuk domain name nya di skip dan selanjutnya set up password. 
       <img src="img/install8.png"> <br>
       <img src="img/install9.png"> <br>
       <img src="img/install10.png"> <br>
       <img src="img/install11.png"> <br>
       <img src="img/install12.png"> <br>
       <img src="img/install13.png">
     - Konfigurasi waktu daerah (terserah pilih yang mana).
       <img src="img/install14.png">
     - Pilih opsi "Manual" untuk konfigurasi manual.
       <img src="img/manual.png"> <br>
       <img src="img/manual1.png"> <br>
       <img src="img/manual2.png">
     - Buat partisi sesuai dengan spesifikasi yang diberikan, yaitu: <br>
       Atur semua nya jadi "Primary", "Begining", dan jangan lupa save dengan tekan "Done setting up the partition" kemudian "Enter"
       - / (root): 20 GB
         <img src="img/partisi (19).png"> <br>
         <img src="img/partisi (18).png"> <br>
         <img src="img/partisi (17).png"> <br>
         <img src="img/partisi (16).png"> <br>
         <img src="img/partisi (15).png"> <br>
         <img src="img/partisi (14).png"> <br>
         <img src="img/partisi (13).png"> 
       - /storage: 5 GB
         <img src="img/partisi (12).png"> <br>
         <img src="img/partisi (11).png"> <br>
         <img src="img/partisi (10).png"> <br>
         <img src="img/partisi (15).png"> <br>
         <img src="img/partisi (9).png"> <br>
         <img src="img/partisi (8).png"> <br>
         <img src="img/partisi (7).png"> 
       - swap: 1.5 GB
         <img src="img/partisi (6).png"> <br>
         <img src="img/partisi (5).png"> <br>
         <img src="img/partisi (16).png"> <br>
         <img src="img/partisi (15).png"> <br>
         <img src="img/partisi (23).png"> <br>
         <img src="img/partisi (22).png"> <br>
         <img src="img/partisi (21).png"> <br>
         <img src="img/partisi (20).png"> 
     - Penginstalan Dasar
       <img src="img/base.png">
     - Konfigurasi package manager
       <img src="img/package (1).png"> <br>
       <img src="img/package (2).png"> <br>
       <img src="img/package (3).png"> <br>
       <img src="img/package (4).png"> <br>
       <img src="img/package (5).png">
     - Configuration popularity-contest ini di skip saja
       <img src="img/popularity.png">
     - Pilih perangkat lunak apa yang ingin Anda instal selama proses instalasi dasar. Tunggu hingga instalasi selesai.
       <img src="img/software (1).png"> <br>
       <img src="img/software (2).png"> <br>
       <img src="img/complete (1).png"> <br>
       <img src="img/complete (3).png"> <br>
       <img src="img/complete (2).png"> 
     - Setelah proses instalasi selesai, pilih opsi "Continue" dan reboot mesin virtual.
       <img src="img/complete (4).png"> 
    - <b>Langkah 4:</b> Cek partisi disk di debian
      - Buka activities kemudian search "Disk"
        <img src="img/disk.png">
      - Pilih yang Hard Disk kemudian disini akan tersedia informasi tentang partisi yang telah kita buat sebelumnnya
        <img src="img/disk1.png"> <br>
        <img src="img/disk2.png">

##

2. Perbedaan Debian 12 (bookworm) dan Debian 11 (bullseye)
   <table>
      <tr>
        <th></th>
        <th>Debian 12 (bookworm)</th>
        <th>Debian 11 (bullseye)</th>
      </tr>
      <tr>
        <td>Versi Kernel</td>
        <td>Debian 12 didukung oleh versi terbaru dari kernel Linux 6.1, yang menyediakan dukungan perangkat keras yang lebih baik, update untuk CPU (Central processing unit)  maupun GPU (graphics processing unit) keluaran terbaru dari Intel dan AMD. Linux Kernel 6.1 adalah rilis dukungan jangka panjang yang dipelihara hingga tahun 2027.</td>
        <td>Debian 11 (Bullseye) menggunakan kernel Linux versi 5.10. Kernel 5.10 merupakan versi kernel yang mendukung berbagai perangkat keras modern dan menyertakan berbagai perbaikan, peningkatan kinerja, serta fitur-fitur baru. Debian 11 (Bullseye) dirilis pada Agustus 2021 dan kernel 5.10 dipilih sebagai kernel default untuk distribusi tersebut</td>
      </tr>
      <tr>
        <td>Kebutuhan Sistem</td>
        <td>Memerlukan peningkatan ruang penyimpanan dan sumber daya yang mungkin disebabkan oleh tambahan fitur dan perubahan dalam paket perangkat lunak. Berikut ini adalah arsitektur yang didukung secara resmi untuk Debian 12:
            <ul>
                <li>PC 32-bit (i386) dan PC 64-bit (amd64)</li>
                <li>LENGAN 64-bit (lengan64)</li>
                <li>LENGAN EABI (armel)</li>
                <li>ARMv7 (EABI hard-float ABI, armhf)</li>
                <li>MIPS little-endian (mipsel)</li>
                <li>MIPS little-endian 64-bit (mips64el)</li>
                <li>PowerPC little-endian 64-bit (ppc64el)</li>
                <li>IBM Sistem z (s390x)</li>
            </ul>
        </td>
        <td>Kebutuhan sistem biasa, tidak signifikan perubahan dari rilis sebelumnya. Berikut ini adalah arsitektur yang didukung secara resmi untuk Debian 11:
            <ul>
                <li>PC 32-bit (i386) dan PC 64-bit (amd64)</li>
                <li>ARM 64-bit (arm64)</li>
                <li>LENGAN EABI (armel)</li>
                <li>ARMv7 (EABI hard-float ABI, armhf)</li>
                <li>MIPS little-endian (mipsel)</li>
                <li>MIPS little-endian 64-bit (mips64el)</li>
                <li>PowerPC little-endian 64-bit (ppc64el)</li>
                <li>IBM Sistem z (s390x)</li>
            </ul>
        </td>
      </tr>
      <tr>
        <td>Penerapan Systemd</td>
        <td>Pada versi 12 ada beberapa paket lain yang menyediakan layanan serupa. Standar debian sekarang systemd -timesyncd, yang mungkin cukup untuk pengguna yang hanya membutuhkan klien ntp untuk mengaturnya jam. Pada versi ini juga menyertakan chrony dan openntpd yang mendukung fitur-fitur lebih canggih, seperti mengoperasikan server NTP Anda sendiri</td>
        <td>Pada versi 11, systemd menggunakan grup kontrol v2 (cgroupv2), yang menyediakan hierarki kontrol sumber daya terpadu. Parameter baris perintah kernel tersedia untuk mengaktifkan kembali cgroup lama jika diperlukan. Systemd di bullseye mengaktifkan fungsionalitas jurnal persistennya secara default. Jika boot gagal pada systemd, dimungkinkan untuk mendapatkan shell root debug dengan mengubah kernel garis komando.</td>
      </tr>
  <tr>
    <td align="center"><b>Package</b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Apache</td>
    <td>2.4.54</td>
    <td>2.4.57</td>
  </tr>
  <tr>
    <td>Bash</td>
    <td>5.1</td>
    <td>5.2.15</td>
  </tr>
  <tr>
    <td>BIND DNS Serve</td>
    <td>9.16</td>
    <td>9.18</td>
  </tr>
  <tr>
    <td>Cryptsetup</td>
    <td>2.3</td>
    <td>2.6</td>
  </tr>
    <tr>
    <td>Emacs</td>
    <td>27.1</td>
    <td>28.2</td>
  </tr>
  <tr>
    <td>Exim default e-mail server</td>
    <td>4.94</td>
    <td>4.96</td>
  </tr>
    <tr>
    <td>GNU Compiler Collection as default compiler</td>
    <td>10.2</td>
    <td>12.2</td>
  </tr>
  <tr>
    <td>GIMP</td>
    <td>2.10.22</td>
    <td>2.10.34</td>
  </tr>
  <tr>
    <td>GnuPG</td>
    <td>2.2.27</td>
    <td>2.2.40</td>
  </tr>
  <tr>
    <td>Inkscape</td>
    <td>1.0.2</td>
    <td>1.2.2</td>
  </tr>
  <tr>
    <td>the GNU C library</td>
    <td>2.31</td>
    <td>1.2.2</td>
  </tr>
  <tr>
    <td>Linux kernel image</td>
    <td>5.10 series</td>
    <td>6.1 series</td>
  </tr>
  <tr>
    <td>LLVM/Clang toolchain</td>
    <td>9.0.1 and 11.0.1 (default) and 13.0.1</td>
    <td>13.0.1 and 14.0 (default) and 15.0.6</td>
  </tr>
  <tr>
    <td>MariaDB</td>
    <td>10.5</td>
    <td>10.11</td>
  </tr>
  <tr>
    <td>Nginx</td>
    <td>1.18</td>
    <td>1.22</td>
  </tr>
  <tr>
    <td>OpenJDK</td>
    <td>11</td>
    <td>17</td>
  </tr>
  <tr>
    <td>OpenLDAP</td>
    <td>2.4.57</td>
    <td>2.5.13</td>
  </tr>
  <tr>
    <td>OpenSSH</td>
    <td>8.4p1</td>
    <td>9.2p1</td>
  </tr>
  <tr>
    <td>OpenSSL</td>
    <td>1.1.1n</td>
    <td>3.0.8</td>
  </tr>
  <tr>
    <td>Perl</td>
    <td>5.32</td>
    <td>5.36</td>
  </tr>
    <tr>
    <td>PHP</td>
    <td>7.4</td>
    <td>8.2</td>
  </tr>
  </tr>
    <tr>
    <td>Postfix MTA</td>
    <td>3.5</td>
    <td>3.7</td>
  </tr>
    <tr>
    <td>PostgreSQL</td>
    <td>13</td>
    <td>15</td>
  </tr>
   <tr>
    <td>Python 3</td>
    <td>3.9.2</td>
    <td>3.11.2</td>
  </tr>
    <tr>
    <td>Rustc</td>
    <td>1.48</td>
    <td>1.63</td>
  </tr>
    <tr>
    <td>Samba</td>
    <td>4.13</td>
    <td>4.17</td>
  </tr>
   <tr>
    <td>Systemd</td>
    <td>247</td>
    <td>252</td>
  </tr>
   <tr>
    <td>Vim</td>
    <td>8.2</td>
    <td>9.0</td>
  </tr>
</table>

##

3. File /etc/group adalah file yang berisi daftar group yang dipisahkan per baris. Setiap baris terdiri dari 4 kolom, yang berisi informasi mengenai :
    - Group name: nama group
    - Group password: apabila di-set, mengijinkan user yang bukan bagian dari group bergabung ke dalam group dengan menggunakan perintah newgrp dan mengetikkan password. Jika lebih kecil dari x, maka shadow group password digunakan.
    - Group ID (GID): bilangan numerik yang ekuivalen dengan group name.
    - Member list: daftar user yang menjadi milik group.

    Format umum dari file "/etc/group" adalah sebagai berikut:<br>
    <b> nama_grup:sandi:ID_grup:daftar_anggota </b><br>
    Contoh baris pada file /etc/group :<br>
    <b> general:x:502:maya,dinda,syitha </b>

##

4. Perintah "su" dan "su -" pada sistem Linux umumnya digunakan untuk beralih identitas pengguna atau "superuser" (root). Meskipun keduanya memiliki tujuan yang sama, yaitu untuk masuk ke dalam sesi shell dengan hak akses superuser, ada perbedaan antara keduanya:
    - <b>"su"</b> : Perintah "su" (singkat dari "switch user") digunakan untuk beralih ke akun pengguna lain atau akun root tanpa mengubah lingkungan atau environment variables (variabel lingkungan). Ini berarti bahwa saat menggunakan perintah "su", akan memasuki shell baru sebagai pengguna yang dituju.
    - <b>"su -"</b> : Perintah "su -" (dengan opsi dash) atau sering disebut "su dengan dash", juga digunakan untuk beralih ke akun pengguna lain atau akun root, tetapi dengan perbedaan utama yaitu memuat lingkungan pengguna target sepenuhnya, termasuk direktori kerja, variabel lingkungan, dan file konfigurasi lainnya yang terkait dengan shell yang digunakan pengguna target. <br>
    <img src="img/no4-1.png">

##

5. Perintah sudo adalah singkatan dari "superuser do" dan digunakan dalam sistem operasi Linux dan untuk memberikan izin atau hak akses superuser (biasanya diwakili oleh akun "root") kepada pengguna biasa. Hal ini memungkinkan pengguna biasa untuk menjalankan perintah dengan hak akses administratif yang diperlukan untuk melakukan tugas tertentu yang membutuhkan izin superuser. <br>
Fungsi utama dari perintah sudo adalah:
    - <b>Eksekusi Perintah Sebagai Superuser</b>: Dengan menggunakan sudo, pengguna biasa dapat menjalankan perintah dengan hak akses superuser, yang memungkinkan mereka untuk melakukan tugas seperti menginstal perangkat lunak, mengelola layanan sistem, atau melakukan perubahan konfigurasi yang memerlukan izin tinggi.
    - <b>Pengendalian Akses</b>: sudo memungkinkan administrator untuk mengontrol akses pengguna ke perintah-perintah tertentu dengan memberikan atau mencabut hak akses sudo kepada pengguna atau kelompok pengguna tertentu. Hal ini membantu dalam menjaga keamanan sistem dengan membatasi akses ke operasi yang berpotensi berbahaya.
    - <b>Perekaman Aktivitas</b>: Banyak implementasi sudo memungkinkan administrator untuk memantau dan merekam aktivitas pengguna yang menggunakan sudo, sehingga memudahkan audit dan penelusuran jika terjadi masalah atau pelanggaran keamanan. <br><br>
    Contoh penerapan perintah "sudo" :
    <img src="img/no5.png">
6. Langkah - langkah penambahan user sebagai user sudo
   - Jalankan perintah "su -" untuk masuk sebagai root, setelah menjalankan perintah tersebut akan diminta ketikkan kata sandi root.<br>
    <img src="img/no6-1.png">
    - Setelah berhasil masuk sebagai root, jalankan perintah "visudo" untuk mengedit file konfigurasi sudoers dalam editor teks yaitu nano :<br>
    <img src="img/no6-2.png">
    - Cari bagian yang bertuliskan "# User privilege specification". Di bagian ini, tambahkan pengguna (username) sebagai pengguna sudo yang menyatakan hak akses root.<br>
    Contoh : <b>mayada ALL=(ALL:ALL) ALL </b><br>
    <b>Root ALL=(ALL:ALL) ALL </b> – baris ini berarti user root mempunyai hak-hak istimewa yang tidak terbatas dan dapat menjalankan semua command pada sistem. <br>
    <img src="img/no6-3.png">
    - Setelah menambahkan baris tersebut, simpan perubahan pada file konfigurasi sudoers. Untuk menggunakan editor nano, tekan Ctrl + O untuk menyimpan, diikuti dengan Enter, dan kemudian tekan Ctrl + X untuk keluar dari editor.
    - Sekarang pengguna telah ditambahkan sebagai pengguna sudo dengan hak akses yang sesuai. Pengecekan : 
    <img src="img/no6-4.png">