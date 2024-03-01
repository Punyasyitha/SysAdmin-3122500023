<h2>3. SETTING NETWORK</h2>
<h5>Ada 2 cara kita dapat melakukan setting network di debian yaitu dengan GUI ( NETWORK MANAGER ) dan CLI ( Menggunakan file /etc/network/interfaces)</h5>
<h5>Default Gateway:</h5>
<img src="img/Default Gateway.png">  

- <h4>NETWORK MANAGER</h4>

    - Buka Network Manage 
    - Buka setting pada interface terhubung terlebih dahulu <br> <img src="img/Wired SS.png"> 
    - Pilih Menu IPV4 lalu klik manual, isi kolom sesuai perintah di abwah ini <br> <img src="img/Menu IPV4.png">
    - Buka terminal dan tuliskan perintah ip addr, maka akan muncul hasil di bawah ini <br> <img src="img/Hasil Manual IPV4.png">

- INTERFACES FILES
    - Jalankan perintah pada terminal Debian <br> <img src="img/Jalankan perintah.png">
    - Setting format address dan gateway <br> <img src="img/Setting perintah.png">
    - Lakukan ifdown ifup interface menggunakan enp03s (nama interface) <br> <img src="img/Ifdown Ifup interface.png">
    - Makan akan muncul hasil seperti di bawah ini <br> <img src="img/Hasil ifdown ifup.png">
</body>
</html>
