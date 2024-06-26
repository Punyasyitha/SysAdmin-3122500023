<h1 align="center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>

<h3 align="center">Dosen Pembimbing: Dr. Ferry Astika Saputra ST, M.Sc</h3>

<p align="center"><img src="images/logo.png" alt="logo"></p>

<div align="center">
  <h3>Disusun Oleh:</h3>
  <p align="center">Masyitha Fahra Nabila 3122500023</p>
</div>

<div align="center">
  <h3>PROGRAM STUDI TEKNIK INFORMATIKA <br>
      POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br>
      TAHUN 2023/2024 <br>
  </h3>
</div>

---
Daftar Isi
- [1. Setup NTP Server](#1-setup-ntp--network-time-protocol)
- [2. Install WebServer Apache2](#2-install-web-server--apache2--php-fm)
- [3. Install Database Server MariaDb](#3-install-database-server--mariadb-server)
- [4. Install SMTP Sever Postfix](#4-install-postfix-mailserver-smtp-server)
- [5. Install IMAP POP3 Dovecot](#5-install-dovecot-imap-pop3)
- [6. Debian Evolution](#6-debian-evolution)
- [7. RoundCube Email Client](#7-roundcube-email-client)
- [8.  PERCOBAAN MAILSERVER JARINGAN JARKOM C307](#8-percobaan-mailserver-jaringan-jarkom-c307)


## 1. Setup NTP (Netwotk Time Protocol)
- Gunakan command ``sudo apt install systemd-timesyncd``
- Berikutnya, ubah TimeZone ke Asia/Jakarta
- Setelah mengubah TimeZone, maka ubahlah RTC menjadi sama dengan UTC
- Aktifkan NTP supaya waktu Sinkron.
![alt text](images/1.png)
- Ubahlah config file timesync.d dengan cara menavigasikan pool ke terdekat supaya delay jadi pendek. Ubahlah line 16 dengan,
``NTP=0.id.pool.ntp.org``
![alt text](images/2.png)
- Restart Service yang berjalan dan cek statusnya
![alt text](images/3.png)
- Cek Tanggal
![alt text](images/4.png)

## 2. Install WebServer Apache2 (APACHE2 & PHP-FM)
> APACHE2 <br>
- Install paket dengan command berikut ``sudo apt -y install apache2``
![alt text](images/5.png)
- Berikutnya, ubahlah ServerToken Menjadi Prod. Pada line 12 gantilah <br> ``ServerTokens Prod``
![alt text](images/6.png)
- Tambahkan Directory yang dapat diakses
![alt text](images/7.png)
- Tambahkan ServerName pada line 70 dengan menuliskan server lebih spesifik, ``wwww.(namakelompok).local``
![alt text](images/8.png)
- Webmaster email
![alt text](images/9.png)
- Lakukan reload pada service apache2
![alt text](images/10.png)
- Apakah webserver berjalan pada browser? Mari kita cek!
![alt text](images/11.png)
> PHP 8.2<br>
- Install dengan perintah berikut
![alt text](images/12.png)
- Lakukan pengecekan dan testing apakah sudah berhasil terinstall
![alt text](images/13.png)
> PHP-FM<br>
- Install dengan perintah berikut
![alt text](images/14.png)
- Mengkonfigurasi PHP-FM pada file konfigurasi Apache dengan menambahakan <br> ``<FilesMatch .php$> SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/"``
![alt text](images/15.png)
- Setenvif pada ae2enmod proxy_fcgi
- Load config
- Jalankan kembali servicenya
![alt text](images/16.png)
- Buatlah file info php untuk mengetes webserver
![alt text](images/17.png)
- Hasil webservernya
![alt text](images/18.png)

## 3. Install Database Server MariaDb
- Install paket dengan perintah berikut
![alt text](images/19.png)
- Cek file etc/mysql/mariadb.conf.d/50-server.cnf kemudian pastikan atau ubah charset ke utf8mb4.
![alt text](images/20.png)
- Lakukan installasi dengan perintah di bawah ini
![alt text](images/21.png)
    - Instalasi pattern untuk menggunakan MariaDB<br>
    - Enter current password for root (enter for none): Tekan Enter<br>
    - Switch to unix_socket authentication [Y/n] n<br>
    - Change the root password? [Y/n] n<br>
    - Remove anonymous users? [Y/n] y<br>
    - Disallow root login remotely? [Y/n] y<br>
    - Remove test database and access to it? [Y/n] y<br>
    - Reload privilege tables now? [Y/n] y
    - Masuk kedalam mysql perintah mysql
![alt text](images/22.png)
![alt text](images/23.png)
![alt text](images/24.png)

## 4. Install SMTP Sever Postfix
- Install dengan perintah<br>
``sudo nano apt -y install postfix sasl2-bin``<br>
- Pilih opsi No Configuration
![alt text](images/25.png)
- Ubah beberapa Konfigurasi pada file postfix main.cf<br>
    - uncomment mail_owner = postfix
    ![alt text](images/26.png)
    - uncomment and specify hostname myhostname = mail.kelompok10.local
    ![alt text](images/27.png)
    - uncomment and specify domainname mydomain = kelompok10.local
    ![alt text](images/28.png)
    - uncomment myorigin = $mydomain
    ![alt text](images/29.png)
    - uncomment inet_interfaces all
    ![alt text](images/30.png)
    - uncomment mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
    ![alt text](images/31.png)
    - uncomment local_recipient_maps = unix:passwd.byname $alias_maps
    ![alt text](images/32.png)
    - uncomment mynetworks_style = subnet
    - add your local network mynetworks = 127.0.0.0/8, 10.0.0.0/24, 192.168.0.0/16
    ![alt text](images/33.png)
    - uncomment alias_maps = hash:/etc/aliases
    - uncomment alias_database = hash:/etc/aliases
    ![alt text](images/34.png)
    - uncomment home_mailbox = Maildir/
   ![alt text](images/35.png)
    - comment out and add #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)<br>
    smtpd_banner = $myhostname ESMTP
    ![alt text](images/36.png)
        - add sendmail_path = /usr/sbin/postfix<br>
        - add newaliases_path = /usr/bin/newaliases<br>
        - add mailq_path = /usr/bin/mailq<br>
        - add setgid_group = postdrop<br>
        - comment out html_directory =<br>
        - comment out<br>
        #manpage_directory =
    ![alt text](images/37.png)
        - comment out<br>
        #sample_directory =<br>
        - comment out<br>
        #readme_directory =
        - if also listen IPv6, change to [all] inet_protocols = ipv4<br>
        - #add follows to the end<br>
        -  #disable SMTP VRFY command disable_vrfy_command = yes<br>
        - #require HELO command to sender hosts<br>
        - smtpd_helo_required = yes<br>
        - #limit an email size<br>
        - #example below means 10M bytes limit<br>
        - message_size_limit = 10240000<br>
        - #SMTP-Auth settings<br>
        - smtpd_sasl_type = dovecot<br>
        - smtpd_sasl_path = private/auth<br>
        - smtpd_sasl_auth_enable = yes<br>
        - smtpd_sasl_security_options = noanonymous<br>
        - smtpd_sasl_local_domain = $myhostname<br>
        - smtpd_recipient_restrictions = permit_mynetworks<br>
        - permit_auth_destination,<br>
        permit_sasl_authenticated, reject<br>
    ![alt text](images/38.png)
    ![alt text](images/39.png)
    ![alt text](images/40.png)
- Menambahkan konfigurasi anti spam<br>
    > nano /etc/postfix/main.cf<br>
    #add to the end<br>
    #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do not match<br>
    smtpd_client_restrictions = permit_mynetworks,
    reject_unknown_client_hostname, permit<br>
    #rejects senders that domain name set in FROM are not registered in DNS or not registered with FQDN<br>
    smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender<br>
    #reject hosts that domain name set in FROM are not registered in DNS or not registered with FQDN when your SMTP server receives HELO command<br>
    smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit<br>
    ![alt text](images/41.png)

## 5. Install DOVECOT (IMAP POP3)
- Gunakan Perintah berikut untuk installasi ``sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd``
![alt text](<images/42.png>)
- Ubah listen IP dengan beberapa command di bawah ini:
    - nano /etc/dovecot/dovecot.conf<br>
    #line 30 : uncomment <br>
    listen = *, ::
    ![alt text](<images/43.png>)
    - nano /etc/dovecot/conf.d/10-auth.conf<br>
    #line 10 : uncomment and change (allow plain text auth)<br>
    disable_plaintext_auth = no
    ![alt text](<images/44.png>)
    #line 100 : add<br>
    auth_mechanisms = plain login
    ![alt text](<images/45.png>)
    - nano /etc/dovecot/conf.d/10-mail.conf <br>
    #line 30 : change to Maildir<br>
    mail_location = maildir:~/Maildir
    ![alt text](<images/46.png>)
    - nano /etc/dovecot/conf.d/10-master.conf<br>
    #line 107-109 : uncomment and add<br>
    #Postfix smtp-auth<br>
    unix_listener /var/spool/postfix/private/auth { <br>
    mode = 0666 <br>
    user = postfix <br>
    group = postfix}
    ![alt text](images/47.png)
    - systemctl restart dovecot
- ``netstat -a| grep LISTEN``<br>
Akan terlihat hasilnya seperti di bawah, dengan status Server (LISTEN) : MariaDB(MySQL), IMAP,POP3, DNS(domain), IMAPS, POP3S, Postfix (SMTP)
![alt text](images/48.png)
- Lakukan test connection ke postfix dengan perintah ``telnet mail.kelompok2.local``
![alt text](images/57.png)
> Instal phpMyAdmin
![alt text](images/50.png)
> Lakukan konfigurasi PHP MyAdmin pada Apache2
![alt text](images/51.png)
> Create user dengan password (123)
![alt text](images/52.png)
> sudo systemctl restart mariadb <br>
> sudo systectl restart php8.2-fpm apache2
> Cek pada browser apakah login berhadil dilakukan?
![alt text](images/53.png)
![alt text](images/54.png)
![alt text](images/55.png)
## 6. Debian Evolution
- Buat User Terlebih  yaitu tharala
![alt text](images/66.png)
- Buat user lagi (dummy)  dengan langkah yang sama, ``adduser`` terlebih dahulu
![alt text](images/59.png)
- Mengirim pesan
![alt text](images/67.png)
- Terdapat email dari user dan budi yang kita lakukan maka berhasil
![alt text](images/68.png)
## 7. RoundCube Email Client
- Lakukan konfigurasi untuk user  roundcube, tambahkan pada tabel db user
![alt text](images/69.png)
![alt text](images/70.png)
![alt text](images/71.png)
- Install Roundcube paket dengan command <br> ``sudo apt-get install roundcube -y``
- Lakukan config
![alt text](images/61.png)
- Lakukan config file apache pada roundcube, uncomment line 3 dan hapus public_html path.
![alt text](images/62.png)
- Lakukan symlink pada folder roundcube ke folder dimana aplikasi ini dionline kan
- Tambahkan Servername dan DocumentRoot pada file:
![alt text](images/63.png)
- Lakukan rekonfigurasi
    - sudo dpkg-reconfigure roundcube-core
![alt text](images/73.png)
![alt text](images/74.png)
![alt text](images/75.png)
![alt text](images/76.png)
![alt text](images/77.png)
![alt text](images/78.png)
![alt text](images/79.png)
![alt text](images/80.png)
![alt text](images/81.png)
![alt text](images/82.png)
![alt text](images/83.png)
![alt text](images/84.png)
![alt text](images/85.png)
- Lakukan pengecekan roundcube 
![alt text](images/64.png)
- Lakukan percobaan untuk mengirim pesan ke user lain.
![alt text](images/86.png)
- Lakukan pengecekan pesan masuk pada user kedua 
![alt text](images/87.png)
- Pesan berhasil masuk dan diterima oleh user kedua. Roundcube berhasil berjalan dengan baik.

## 8.  PERCOBAAN MAILSERVER JARINGAN JARKOM C307
1. Pastikan sudah terkoneksi dengan ethernet LAB JARKOM
2. Lakukan Ping ke 1.1.1.1 pastikan sudah terhubung ke dns 1.1.1.1
3. Setting Virtual Box Ke Dalam Network Bridge dengan cara pergi ke setting/machine >> Network
   ![alt text](images/12.3.png)
   
4. Supaya DNS Kita dapat diresolve oleh kelompok lain lakukan Konfigurasi Berikut
5. Setting interfaces:
   ![alt text](images/12.5.png)

6. Setting named.conf.options:
   
   sudo nano /etc/bind/named.conf.options
   ![alt text](images/12.6.1.png)
   ![alt text](images/12.6.2.png)
   ![alt text](images/12.6.3.png)
7. Setting resolv.conf:
   
   sudo nano /etc/resolv.conf
   ![alt text](images/12.7.1.png)
   ![alt text](images/12.7.2.png)
8. Lakukan sudo restart systemctl networking Setelahnya
   
   sudo systemctl restart networking
   
9.  Lakukan Ping Detik.com atau IP Kelompok lain disini 192.168.10.10
    
    ping detik.com
    nslookup ns.kelompok2.local
    
10. Buat DHCP Server Bridge Pada Aplikasi WINBOX. Connect Ke Server/Router Klik DHCP SETUP, Pilih Bridge Interface
    ![alt text](images/12.10.jpg)

11. Masukkan dns
    ![alt text](images/12.11.jpg)

12. Cek Mail Server
    
    nslookup mail.kelompok10.local
    
13. nslookup -q=MX kelompok2.local
    <!-- <img src="../Tugas-UTS/img" width="90%" height="auto"><br> -->
14. Buka Mail Server Kelompok Kita
    <!-- <img src="../Tugas-UTS/img" width="90%" height="auto"><br> -->
15. Lakukan Pengiriman Ke Kelompok Lainnya
    ![alt text](images/12.15.jpg)

### 9. ANALISIS MIME(HEADER), POP3, DAN SMTP

Berikut adalah analisis singkat untuk MIME (Multipurpose Internet Mail Extensions), POP3 (Post Office Protocol version 3), dan SMTP (Simple Mail Transfer Protocol):

---

1. *Multipurpose Internet Mail Extensions (MIME):*
- Apa itu MIME: <br>
  MIME adalah standar yang memungkinkan berbagai jenis informasi, seperti teks, gambar, audio, dan video, untuk disampaikan melalui protokol email. Ini memungkinkan email untuk mengirim dan menerima konten multimedia.
- Header MIME: <br>
  Header MIME terdiri dari beberapa bagian yang mengontrol bagaimana konten email diinterpretasikan oleh klien email. Beberapa header MIME umum meliputi:
  - Content-Type: Menunjukkan tipe media konten (teks, gambar, dll.).
  - Content-Disposition: Mengontrol cara konten tersebut ditampilkan atau diproses.
  - Content-Transfer-Encoding: Mengonversi data biner ke format teks agar dapat ditransmisikan melalui protokol email.
- Penggunaan MIME:
  MIME digunakan untuk menyampaikan email yang mengandung lampiran, gambar, format teks kaya, dan konten multimedia lainnya. Ini memungkinkan pengguna untuk mengirim pesan email yang lebih kaya dan lebih bervariasi.

---

2. *Post Office Protocol version 3 (POP3):*
- Apa itu POP3: <br>
  POP3 adalah protokol yang digunakan untuk mengambil email dari server email ke klien email. Ini adalah salah satu protokol yang paling umum digunakan untuk mengakses email dari server.
- Cara Kerja POP3:
  1) Klien email terhubung ke server email melalui port 110.
  2) Setelah koneksi dibuat, klien mengirimkan kredensial pengguna untuk otentikasi.
  3) Server memvalidasi kredensial dan memberikan akses ke kotak surat pengguna.
  4) Klien mengunduh email dari server, dan email dihapus dari server (secara default) atau ditandai untuk penghapusan kemudian.
- Kelebihan dan Kekurangan POP3:
  1) Kelebihan:
  - Mudah diimplementasikan dan dipahami.
  - Cocok untuk penggunaan di lingkungan dengan koneksi internet yang tidak stabil.
  2) Kekurangan:
   - Email hanya dapat diakses dari satu perangkat pada satu waktu.
   - Standar POP3 tidak menyertakan fitur untuk menyinkronkan pesan di antara beberapa perangkat.
---

1. *Simple Mail Transfer Protocol (SMTP):*
- Apa itu SMTP:
- SMTP adalah protokol yang digunakan untuk mengirim email antara server email. Ini mengatur proses pengiriman email dari klien email pengirim ke server email penerima.
- Cara Kerja SMTP:
  1) Klien email mengirim pesan ke server email pengirim melalui port 25 (atau port 587 untuk pengiriman yang aman).
  2) Server email pengirim mengautentikasi klien dan menerima pesan email.
  3) Pesan email kemudian ditransfer ke server email penerima melalui jaringan internet menggunakan protokol SMTP.
  4) Server email penerima menyimpan pesan di kotak surat penerima atau meneruskannya ke klien email penerima.
- Kelebihan dan Kekurangan SMTP:<br>
  1) Kelebihan:
  - Cepat dan andal dalam pengiriman email.
  - Mendukung pengiriman email massal. 
  1) Kekurangan:
  - Rentan terhadap spam dan serangan phishing.
  - Tidak menyediakan enkripsi bawaan, sehingga pesan email dapat rentan terhadap penyadapan. 