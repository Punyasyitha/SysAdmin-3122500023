<h1 align="center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>

<h3 align="center">TUGAS 2</h3>

<h4 align="center">Dosen Pembimbing: Dr. Ferry Astika Saputra ST, M.Sc</h4>

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

<div align="justify">

<p> Linux merupakan sistem operasi yang basenya menyerupai unix. Keunikan dari sistem operasi linux sendiri adalah karena sourcenya dapat kita manipulasi sesuai keinginan kita sendiri dengan cara memanipulasi dan mengedit directory serta isinya yang ada pada sistem. </p>

- <b> /root </b> : Struktur direktori standar dari Debian mengawali dengan sistem file root "/" ( di baca root ) yang merupakan direktori utama untuk seluruh struktur dimana semua direktori berada. Partisi di mana / (direktori root) berada pada sistem UNIX.
- <b> /boot </b> : Direktori yang berfungsi untuk menyimpan konfigurasi dan file-file yang berhubungan dengan proses booting, memuat Linux Kernel dan file lain yang diperlukan LILO dan GRUB boot manager. 
- <b> /sys </b> : Direktori /sys ini berisi hal-hal special yang memuatkan informasi mengenai hard disk seperti Kernel, Firmware, dan berkas-berkas terkait sistem. 
- <b> /sbin </b> : Merupakan direktori yang berfungsi untuk menyimpan aplikasi dasar dari linux yang dijalankan oleh super user (root) misalnya mount, shutdown, umount.
- <b> /bin </b> : Direktori ini berisi program perintah esensial yang dibutuhkan oleh semua user. progam-progam disini dapat dijalankan, meskipun tidak ada sistem file lain yang di mount. directory ini tidak memiliki subdirectory.ini perintah-perintah yang harus ada di directory /bin cat, chgrp, chmod, chown, cp, date, dd, df, dmesg, echo, false, hostname, kill, ln, login, ls, mkdir, mknod, more, mount, mv, ps, pwd, rm, rmdir, sed, sh, stty, su, sync, true, unmount, uname.
- <b> /lib </b> : Berisi berkas-berkas pustaka atau library dasar untuk semua binari yang terdapat dalam direktori /sbin & /bin termasuk modul driver yang dapat diisi pada sistem boot.
- <b> /dev </b> : Direktori /dev berisi berkas-berkas sistem penting dan driver-driver. Direktori ini yang berfungsi untuk menyimpan konfigurasi device atau hardware dari sistem, seperti harddisk (hda, sda), terminal (tty) etc.
- <b> /etc </b> : Direktori /etc berisi berkas-berkas konfigurasi sistem penting termasuk /etc/hosts, /etc/resolv.conf, nsswitch.conf, berkas-berkas default, dan konfigurasi jaringan. Ini sebagian besar berkas-berkas konfigurasi sistem dan aplikasi yang spesifik untuk host.
- <b> /home </b> : Semua direktori home pengguna disimpan di bawah direktori ini dengan pengecualian direktori home root yang disimpan di bawah direktori /root. Direktori ini menyimpan berkas-berkas pengguna, pengaturan pribadi seperti .profile, dll.
- <b> /media </b> : Titik pemasangan generik untuk media yang dapat dilepas seperti CD-ROM, USB, Floppy disk, dll. Saat menghubungkan perangkat media ke komputer, isi dari perangkat tersebut akan tersedia di dalam folder /media.
- <b> /mnt </b> : Titik pemasangan generik untuk sistem file sementara. Ini berguna terutama saat memecahkan masalah dari CDROM dll di mana Anda mungkin harus memasang sistem file root dan mengedit konfigurasi.
- <b> /opt </b> : Merupakan direktori yang berfungsi untuk menyimpan aplikasi tambahan diluar aplikasi bawaan dari linux. Dan juga jarang digunakan dalam Linux untuk Paket Perangkat Lunak Opsional. Ini digunakan secara luas dalam sistem operasi UNIX seperti Sun Solaris di mana paket-paket perangkat lunak diinstal.
- <b> /usr </b> : Direktori untuk menyimpan aplikasi yang diinstall oleh user, misalkan OpenOffice, Kate , chrome dan sebagainya.
- <b> /usr/sbin </b> : Berisi binari sistem non-esisensial dan utilitas jaringan non-kritis. Berisi program-program penting untuk pengelolaan sistem, lebih banyak digunakan oleh administrator sistem.
- <b> /usr/bin </b> : Berisi binari perintah non-esisensial dan non-kritis untuk pengguna. Berisi program-program yang berguna untuk pengguna sehari-hari, seperti menjalankan perintah dasar, mengelola file, dan sebagainya.
- <b> /usr/lib </b> : Berkas-berkas perpustakaan untuk binari-binari dalam direktori /usr/bin & /usr/sbin.
- <b> /usr/share </b> : Direktori data bersama yang independen platform.
- <b> /usr/local </b> : Sub hirarki di bawah direktori /usr yang memiliki data sistem lokal termasuk binari pengguna dan sistem serta perpustakaan mereka.
- <b> /var </b> : Direktori /var sebagian besar dipasang sebagai sistem file terpisah di bawah root di mana semua konten variabel seperti log, berkas spool untuk printer, crontab, pekerjaan at, surat, proses yang berjalan, berkas kunci, dll. Perlu diambil perhatian dalam merencanakan sistem file ini dan pemeliharaannya karena ini dapat cepat penuh dan ketika sistem file penuh dapat menyebabkan masalah operasional sistem dan aplikasi.
- <b> /tmp </b> : Sebuah sistem file sementara yang menyimpan berkas-berkas sementara yang dibersihkan saat sistem di-reboot. Ada juga direktori /var/tmp yang menyimpan berkas-berkas sementara juga. Satu-satunya perbedaan antara keduanya adalah direktori /var/tmp menyimpan berkas-berkas yang dilindungi saat sistem di-reboot. Dengan kata lain, berkas-berkas /var/tmp tidak dibersihkan saat reboot.

Kemudian ada sistem file virtual (pseudo) /proc yang berada di dalam memori dan dipasang di bawah Root yang menyimpan statistik kernel dan proses dalam format berkas teks.

</div>

### Linux Directory Structure in Visual View:
![height:4in](img/struktur%20(1).jpg)
![height:4in](img/struktur%20(2).jpg)
![height:4in](img/struktur%20(3).jpg)
![height:4in](img/struktur%20(4).jpg)
![height:4in](img/struktur%20(5).jpg)
