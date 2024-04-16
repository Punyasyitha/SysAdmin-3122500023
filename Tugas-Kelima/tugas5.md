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
- [6. Test Email Menggunakan Thunderbird](#6-debian-evolution)
- [7. RoundCube Email Client](78-roundcube)

## 1. Setup NTP (Netwotk Time Protocol)
- Gunakan command ``sudo apt install systemd-timesyncd``
- Berikutnya, ubah TimeZone ke Asia/Jakarta
- Setelah mengubah TimeZone, maka ubahlah RTC menjadi sama dengan UTC
- Aktifkan NTP supaya waktu Sinkron.
<div align="center">
    <img src="images/1.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Ubahlah config file timesync.d dengan cara menavigasikan pool ke terdekat supaya delay jadi pendek. Ubahlah line 16 dengan,
``NTP=0.id.pool.ntp.org``
<div align="center">
    <img src="images/2.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Restart Service yang berjalan dan cek statusnya
<div align="center">
    <img src="images/3.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Cek Tanggal
<div align="center">
    <img src="images/4.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>

## 2. Install WebServer Apache2 (APACHE2 & PHP-FM)
    > APACHE2
- Install paket dengan command berikut ``sudo apt -y install apache2``
<div align="center">
    <img src="images/5.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Berikutnya, ubahlah ServerToken Menjadi Prod. Pada line 12 gantilah ``ServerTokens Prod``
<div align="center">
    <img src="images/6.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Tambahkan Directory yang dapat diakses
<div align="center">
    <img src="images/7.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Tambahkan ServerName pada line 70 dengan menuliskan server lebih spesifik, ``wwww.(namakelompok).local``
<div align="center">
    <img src="images/8.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Webmaster email
<div align="center">
    <img src="images/9.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Lakukan reload pada service apache2
<div align="center">
    <img src="images/10.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Apakah webserver berjalan pada browser? Mari kita cek!
<div align="center">
    <img src="images/11.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    > PHP 8.2
- Install dengan perintah berikut
<div align="center">
    <img src="images/12.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Lakukan pengecekan dan testing apakah sudah berhasil terinstall
<div align="center">
    <img src="images/13.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    > PHP-FM
- Install dengan perintah berikut
<div align="center">
    <img src="images/14.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Mengkonfigurasi PHP-FM pada file konfigurasi Apache dengan menambahakan ``<FilesMatch .php$>
SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/"``
<div align="center">
    <img src="images/15.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Setenvif pada ae2enmod proxy_fcgi
- Load config
- Jalankan kembali servicenya
<div align="center">
    <img src="images/16.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Buatlah file info php untuk mengetes webserver
<div align="center">
    <img src="images/17.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Hasil webservernya
<div align="center">
    <img src="images/18.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>

## 3. Install Database Server MariaDb
- Install paket dengan perintah berikut
<div align="center">
    <img src="images/19.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Cek file etc/mysql/mariadb.conf.d/50-server.cnf kemudian pastikan atau ubah charset ke utf8mb4.
<div align="center">
    <img src="images/20.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
Lakukan installasi dengan perintah di bawah ini
<div align="center">
    <img src="images/21.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    > Instalasi pattern untuk menggunakan MariaDB<br>
    Enter current password for root (enter for none): Tekan Enter<br>
    Switch to unix_socket authentication [Y/n] n<br>
    Change the root password? [Y/n] n<br>
    Remove anonymous users? [Y/n] y<br>
    Disallow root login remotely? [Y/n] y<br>
    Remove test database and access to it? [Y/n] y<br>
    Reload privilege tables now? [Y/n] y
- Masuk kedalam mysql perintah mysql
<div align="center">
    <img src="images/22.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
<div align="center">
    <img src="images/23.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
<div align="center">
    <img src="images/24.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>

## 4. Install SMTP Sever Postfix
- Install dengan perintah<br>
``sudo nano apt -y install postfix sasl2-bin``
- Pilih opsi No Configuration
<div align="center">
    <img src="images/25.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
- Ubah beberapa Konfigurasi pada file postfix main.cf
    > ``sudo nano /etc/posfix/main.cf``
    - uncomment mail_owner = postfix
<div align="center">
    <img src="images/26.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment and specify hostname myhostname = mail.kelompok10.local
<div align="center">
    <img src="images/27.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment and specify domainname mydomain = kelompok10.local
<div align="center">
    <img src="images/28.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment myorigin = $mydomain
<div align="center">
    <img src="images/29.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment inet_interfaces all
<div align="center">
    <img src="images/30.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
<div align="center">
    <img src="images/31.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment local_recipient_maps = unix:passwd.byname $alias_maps
<div align="center">
    <img src="images/32.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment mynetworks_style = subnet
    - add your local network mynetworks = 127.0.0.0/8, 10.0.0.0/24, 192.168.0.0/16
<div align="center">
    <img src="images/33.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment alias_maps = hash:/etc/aliases
    - uncomment alias_database = hash:/etc/aliases
<div align="center">
    <img src="images/34.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - uncomment home_mailbox = Maildir/
   <div align="center">
    <img src="images/35.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - comment out and add #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
    smtpd_banner = $myhostname ESMTP
<div align="center">
    <img src="images/36.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
    - add sendmail_path = /usr/sbin/postfix
    - add newaliases_path = /usr/bin/newaliases
    - add mailq_path = /usr/bin/mailq
    - add setgid_group = postdrop
    - comment out html_directory =
    - comment out
    #manpage_directory =
<div align="center">
    <img src="images/37.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
</div>
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
    <div align="center">
    <img src="images/38.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
    </div>
    <div align="center">
    <img src="images/39.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
    </div>
    <div align="center">
    <img src="images/40.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
    </div>
- Menambahkan konfigurasi anti spam
    > nano /etc/postfix/main.cf 
    #add to the end
    #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do not match
    smtpd_client_restrictions = permit_mynetworks, reject_unknown_client_hostname, permit
    #rejects senders that domain name set in FROM are not registered in DNS or not registered with FQDN
    smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender
    #reject hosts that domain name set in FROM are not registered in DNS or not registered with FQDN when your SMTP server receives HELO command
    smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit
    <div align="center">
    <img src="images/41.png" width="70%" height="auto"><br>
    <em style="font-size:10px"></em>
    </div>

## 5. Install DOVECOT (IMAP POP3)
- Gunakan Perintah berikut untuk installasi sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd
