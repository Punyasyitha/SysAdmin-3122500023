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
- [1. Setup NTP Server](#2-setup-ntp--network-time-protocol)
- [2. Install WebServer Apache2](#3-install-web-server--apache2--php-fm)
- [3. Install Database Server MariaDb](#4-install-database-server--mariadb-server)
- [4. Install SMTP Sever Postfix](#5-install-postfix-mailserver-smtp-server)
- [5. Install IMAP POP3 Dovecot](#6-install-dovecot-imap-pop3)
- [6. Testing Dengan Debian Evolution](#7-debian-evolution)
- [7. RoundCube Email Client](#8-roundcube)

## 1. Setup NTP (Netwotk Time Protocol)
- Gunakan command ``sudo apt install systemd-timesyncd``
- Berikutnya, ubah TimeZone ke Asia/Jakarta
- Setelah mengubah TimeZone, maka ubahlah RTC menjadi sama dengan UTC
- Aktifkan NTP supaya waktu Sinkron.
<br>
    ![alt text](<images/1.png>)
- Ubahlah config file timesync.d dengan cara menavigasikan pool ke terdekat supaya delay jadi pendek. Ubahlah line 16 dengan,
``NTP=0.id.pool.ntp.org``
<br>
    ![alt text](<images/2.png>)
- Restart Service yang berjalan dan cek statusnya
<br>
    ![alt text](<images/3.png>)
- Cek Tanggal
<br>
    ![alt text](<images/4.png>)

## 2. Install WebServer Apache2 (APACHE2 & PHP-FM)
    > APACHE2
- Install paket dengan command berikut ``sudo apt -y install apache2``
<br>
    ![alt text](<images/5.png>)
- Berikutnya, ubahlah ServerToken Menjadi Prod. Pada line 12 gantilah ``ServerTokens Prod``
<br>
    ![alt text](<images/6.png>)
- Tambahkan Directory yang dapat diakses
<br>
    ![alt text](<images/7.png>)
- Tambahkan ServerName pada line 70 dengan menuliskan server lebih spesifik, ``wwww.(namakelompok).local``
<br>
    ![alt text](<images/8.png>)
- Webmaster email
<br>
    ![alt text](<images/9.png>)
- Lakukan reload pada service apache2
<br>
    ![alt text](<images/10.png>)
- Apakah webserver berjalan pada browser? Mari kita cek!
<br>
    ![alt text](<images/11.png>)
    > PHP 8.2
- Install dengan perintah berikut
<br>
    ![alt text](<images/12.png>)
- Lakukan pengecekan dan testing apakah sudah berhasil terinstall
<br>
    ![alt text](<images/13.png>)
    > PHP-FM
- Install dengan perintah berikut
<br>
    ![alt text](<images/14.png>)
- Mengkonfigurasi PHP-FM pada file konfigurasi Apache dengan menambahakan ``<FilesMatch .php$>
SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/"``
<br>
    ![alt text](<images/15.png>)
- Setenvif pada ae2enmod proxy_fcgi
- Load config
- Jalankan kembali servicenya
<br>
    ![alt text](<images/16.png>)
- Buatlah file info php untuk mengetes webserver
<br>
    ![alt text](<images/17.png>)
- Hasil webservernya
<br>
    ![alt text](<images/18.png>)

## 3. Install Database Server MariaDb
- Install paket dengan perintah berikut
<br>
    ![alt text](<images/19.png>)
- Cek file etc/mysql/mariadb.conf.d/50-server.cnf kemudian pastikan atau ubah charset ke utf8mb4.
<br>
    ![alt text](<images/20.png>)
Lakukan installasi dengan perintah di bawah ini
<br>
    ![alt text](<images/21.png>)
    > Instalasi pattern untuk menggunakan MariaDB<br>
    Enter current password for root (enter for none): Tekan Enter<br>
    Switch to unix_socket authentication [Y/n] n<br>
    Change the root password? [Y/n] n<br>
    Remove anonymous users? [Y/n] y<br>
    Disallow root login remotely? [Y/n] y<br>
    Remove test database and access to it? [Y/n] y<br>
    Reload privilege tables now? [Y/n] y
- Masuk kedalam mysql perintah mysql
<br>
    ![alt text](<images/22.png>)
<br>
    ![alt text](<images/23.png>)
<br>
    ![alt text](<images/24.png>)

## 5. Install POSTFIX mailserver (SMTP Server)
- Install dengan perintah<br>
``sudo nano apt -y install postfix sasl2-bin``
- Pilih opsi No Configuration
<br>
    ![alt text](<images/25.png>)
- Ubah beberapa Konfigurasi pada file postfix main.cf
    > ``sudo nano /etc/posfix/main.cf``
    - uncomment mail_owner = postfix
    <br>
    ![alt text](<images/26.png>)
    - uncomment and specify hostname myhostname = mail.kelompok10.local
    <br>
    ![alt text](<images/27.png>)
    - uncomment and specify domainname mydomain = kelompok10.local
    <br>
    ![alt text](<images/28.png>)
    - uncomment myorigin = $mydomain
    <br>
    ![alt text](<images/29.png>)
    - uncomment inet_interfaces all
    <br>
    ![alt text](<images/30.png>)
    - uncomment mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
    <br>
    ![alt text](<images/31.png>)
    - uncomment local_recipient_maps = unix:passwd.byname $alias_maps
    <br>
    ![alt text](<images/32.png>)
    - uncomment mynetworks_style = subnet
    - add your local network mynetworks = 127.0.0.0/8, 10.0.0.0/24, 192.168.0.0/16
    <br>
    ![alt text](<images/33.png>)
    - uncomment alias_maps = hash:/etc/aliases
    - uncomment alias_database = hash:/etc/aliases
    <br>
    ![alt text](<images/34.png>)
    - uncomment home_mailbox = Maildir/
    <br>
    ![alt text](<images/35.png>)
    - comment out and add #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
    smtpd_banner = $myhostname ESMTP
    <br>
    ![alt text](<images/36.png>)
    - add sendmail_path = /usr/sbin/postfix
    - add newaliases_path = /usr/bin/newaliases
    - add mailq_path = /usr/bin/mailq
    - add setgid_group = postdrop
    - comment out html_directory =
    - comment out
    #manpage_directory =
    <br>
    ![alt text](<images/37.png>)
    - comment out
    #sample_directory =
    - comment out
    #readme_directory =
    - if also listen IPv6, change to [all] inet_protocols = ipv4
    - #add follows to the end
    - #disable SMTP VRFY command disable_vrfy_command = yes
    - #require HELO command to sender hosts
    - smtpd_helo_required = yes
    - #limit an email size
    - #example below means 10M bytes limit
    - message_size_limit = 10240000
    - #SMTP-Auth settings
    - smtpd_sasl_type = dovecot
    - smtpd_sasl_path = private/auth
    - smtpd_sasl_auth_enable = yes
    -  smtpd_sasl_security_options = noanonymous
    - smtpd_sasl_local_domain = $myhostname
    - smtpd_recipient_restrictions = - permit_mynetworks
    - permit_auth_destination,
    - permit_sasl_authenticated, reject
    <br>
    ![alt text](<images/38.png>)
    <br>
    ![alt text](<images/39.png>)
    <br>
    ![alt text](<images/40.png>)
- Menambahkan konfigurasi anti spam
    > nano /etc/postfix/main.cf 
    #add to the end
    #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do not match
    smtpd_client_restrictions = permit_mynetworks, reject_unknown_client_hostname, permit
    #rejects senders that domain name set in FROM are not registered in DNS or not registered with FQDN
    smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender
    #reject hosts that domain name set in FROM are not registered in DNS or not registered with FQDN when your SMTP server receives HELO command
    smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit
    <br>
    ![alt text](<images/41.png>)
    <br>

## 6. Install DOVECOT (IMAP POP3)
- Gunakan Perintah berikut untuk installasi sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd
