# modul-2

| **No** | **Nama** | **NRP** | 
| ------------- | ------------- | --------- |
| 1 | Andrian Tambunan  | 5025211018 | 
| 2 | Sandhika Surya Ardyanto | 5025211022 |

### Soal 1

Soal: 

"Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologi dengan pembagian sebagai berikut. Folder topologi dapat diakses pada drive berikut"


![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/1.png)

Penjelasan:

Membuat sebuah topologi jaringan dengan beberapa node yang memiliki konfigurasi jaringan tertentu. Node-node ini adalah Pandudewanata, Yudhistira, Nakula, Sadewa, Werkudara, Arjuna, Abimanyu, Prabakusuma, dan Wisanggeni.


Network Configuration untuk masing-masing node
- Pandudewanata
  ```
  auto eth0
  iface eth0 inet dhcp

  auto eth1
  iface eth1 inet static
	  address 10.34.1.1
	  netmask 255.255.255.0

  auto eth2
  iface eth2 inet static
	  address 10.34.2.1
	  netmask 255.255.255.0

  auto eth3
  iface eth3 inet static
	  address 10.34.3.1
	  netmask 255.255.255.0
  ```
- Yudhistira
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.2.2
	  netmask 255.255.255.0
	  gateway 10.34.2.1
  ```
- Nakula
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.1.2
	  netmask 255.255.255.0
	  gateway 10.34.1.1
  ```
- Sadewa
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.1.3
	  netmask 255.255.255.0
	  gateway 10.34.1.1
  ```
- Werkudara
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.3.2
	  netmask 255.255.255.0
	  gateway 10.34.3.1
  ```
- Arjuna
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.3.3
	  netmask 255.255.255.0
	  gateway 10.34.3.1
  ```
- Abimanyu
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.3.4
	  netmask 255.255.255.0
	  gateway 10.34.3.1
  ```
- Prabukusuma
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.3.5
	  netmask 255.255.255.0
	  gateway 10.34.3.1
  ```
- Wisanggeni
  ```
  auto eth0
  iface eth0 inet static
	  address 10.34.3.6
	  netmask 255.255.255.0
	  gateway 10.34.3.1
  ```
  Penjelasan Jawaban:
`Eth0`: Mendapatkan alamat IP melalui `DHCP`.

Dalam topologi ini, Pandudewanata berperan sebagai node yang mungkin berfungsi sebagai router atau gateway untuk node lainnya. Yudhistira adalah DNS Master, Werkudara adalah DNS Slave, dan Arjuna adalah Load Balancer yang terdiri dari beberapa server web, yaitu Prabakusuma, Abimanyu, dan Wisanggeni.
### Soal 2

Soal: 

"Buatlah website utama pada node arjuna dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok."

Penjelasan:

Membuat konfigurasi DNS pada sebuah server dengan menggunakan aplikasi BIND9 di sistem operasi berbasis Debian atau Ubuntu. Tujuan dari konfigurasi ini adalah untuk membuat domain arjuna.D25.com dengan subdomain www.arjuna.yyy.com (dengan yyy sebagai kode kelompok) sebagai aliasnya.

- Install aplikasi bind9 pada Yudhistira dengan
  ```
  apt-get update
  apt-get install bind9 -y
  ```
- Membuka file named.conf.local untuk konfigurasi domain arjuna.D25.com 
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain
![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/2/ar.png)
- Membuat folder jarkom jika belum ada 
  ```
  mkdir /etc/bind/jarkom
  ```
- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file arjuna.D25.com
  
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/arjuna.D25.com
  ```
- Buka file arjuna.D25.com
  
  Kita perlu mengedit berkas ini untuk menentukan rekaman DNS yang sesuai untuk domain, termasuk alamat IP yang akan dihubungkan dengan domain dan subdomain.
  ```
  nano /etc/bind/jarkom/arjuna.D25.com
  ```
  Edit menjadi
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/2/ar2.png)
- Restart bind9 untuk menerapkan perubahan konfigurasi DNS.
  ```
  service bind9 restart
  ```
  Penjelasan Jawaban:
  
  Dengan langkah langkah diatas, konfigurasi server DNS BIND9 untuk menghubungkan domain arjuna.D25.com dengan subdomain www.arjuna.yyy.com telah dilakukan. Pastikan bahwa konfigurasi file arjuna.D25.com telah disesuaikan dengan kebutuhan dan bahwa website utama di Node Arjuna telah siap untuk menerima permintaan DNS.
### Soal 3
Soal:

"Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com."

Penjelasan Soal:

Konfigurasi DNS di server menggunakan BIND9 pada sistem berbasis Debian atau Ubuntu. Tujuan dari konfigurasi ini adalah untuk membuat domain arjuna.D25.com dan abimanyu.D25.com, masing-masing dengan subdomain www.arjuna.yyy.com dan www.abimanyu.yyy.com, dengan yyy sebagai kode kelompok.

- Membuka file named.conf.local untuk konfigurasi domain abimanyu.D25.com pada Yudhistira
  
Edit file `named.conf.local` di server Yudhistira untuk menambahkan konfigurasi zona DNS baru. Ini adalah langkah penting dalam konfigurasi DNS. Anda mendefinisikan zona baru yang disebut `arjuna.D25.com` dan `abimanyu.D25.com`, serta mengacu pada file zona yang sesuai.
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain
  ```
  zone "abimanyu.D25.com" {
	type master;
  	file "/etc/bind/jarkom/abimanyu.D25.com";
  };
  ```

- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file abimanyu.D25.com
  
  File `db.local` adalah contoh berkas zona yang dapat digunakan sebagai template. Kita dapat menyalin file ini ke dalam folder jarkom dengan nama `arjuna.D25.com` dan `abimanyu.D25.com`.
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/abimanyu.D25.com
  ```
- Buka file abimanyu.D25.com
  
  Edit berkas `arjuna.D25.com` dan `abimanyu.D25.com` yang telah di salin ke dalam folder jarkom. Dalam berkas ini, Anda mendefinisikan rekaman DNS yang sesuai, termasuk alamat IP yang akan dihubungkan dengan domain dan subdomain.
  ```
  nano /etc/bind/jarkom/abimanyu.D25.com
  ```
  Edit menjadi
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/3/ab.png)
  
- Restart bind9
  Restart layanan BIND9 agar semua perubahan konfigurasi DNS yang telah di buat dapat diterapkan dan berfungsi.
  ```
  service bind9 restart
  ```
Penjelasan Jawaban:

langkah-langkah yang dibutuhkan untuk mengkonfigurasi DNS yang memungkinkan domain `arjuna.D25.com` dan `abimanyu.D25.com` dengan subdomain `www.arjuna.yyy.com` dan `www.abimanyu.yyy.com` (dengan yyy sebagai kode kelompok). Dengan mengikuti langkah-langkah ini, Anda akan memiliki server DNS yang dapat mengarahkan permintaan ke website utama yang sesuai pada Node Arjuna dan Abimanyu. Pastikan untuk melakukan konfigurasi berkas zona dengan benar untuk menghubungkan nama domain dan subdomain dengan alamat IP yang tepat sesuai dengan kebutuhan.
### Soal 4
Soal:

"Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu."

Penjelasan Soal:

Buat sebuah subdomain dengan nama `parikesit` di bawah domain `abimanyu.yyy.com` yang kemudian akan diarahkan ke server Abimanyu. Ini berguna jika ingin meng-host beberapa website dengan subdomain yang berbeda di server yang sama.
- Pada Yudhistira buka file abimanyu.D25.com
  ```
  nano /etc/bind/jarkom/abimanyu.D25.com
  ```
  Edit menjadi

Dalam berkas `abimanyu.D25.com`, perlu ditambahkan rekaman DNS yang akan mengarahkan subdomain `parikesit` ke server Abimanyu. Ini dilakukan dengan menambahkan rekaman A (Address) yang menentukan alamat IP tujuan subdomain tersebut.
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/4/par.png)
- Restart bind9
  ```
  service bind9 restart
  ```
  Penjelasan Jawaban:

Dengan melakukan ini, konfigurasi DNS yang telah di ubah akan mulai berlaku, dan subdomain `parikesit.abimanyu.yyy.com` akan diarahkan ke server Abimanyu sesuai dengan konfigurasi yang Anda tambahkan ke berkas `abimanyu.D25.com`.

Dengan Menambahkan subdomain `parikesit.abimanyu.yyy.com` ke dalam konfigurasi DNS yang dikelola di server Yudhistira, sehingga subdomain tersebut dapat diarahkan ke server Abimanyu. Pastikan konfigurasi berkas `abimanyu.D25.com` telah diperbarui dengan benar sesuai dengan rekaman DNS yang di tambahkan.
  
### Soal 5
soal: 

"Buat juga reverse domain untuk domain utama. (Abimanyu saja yang direverse)"

Penjelasan Soal:

Soal ini mencakup konfigurasi Reverse DNS untuk domain utama `abimanyu.D25.com`. Reverse DNS digunakan untuk menghubungkan alamat IP dengan nama domain yang sesuai. Pada kasus ini, Anda diminta untuk membuat konfigurasi Reverse DNS untuk server Abimanyu.
- Membuka file named.conf.local untuk konfigurasi reverse domain abimanyu.D25.com pada Yudhistira
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain
  
Setelah membuka file `named.conf.local`, perlu menambahkan konfigurasi zona Reverse DNS yang sesuai. Dalam kasus ini, Anda akan menambahkan zona `3.34.10.in-addr.arpa`. Ini adalah zona Reverse DNS untuk subnet IP server.
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/5/rv-ab.png)
- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file 3.34.10.in-addr.arpa.com
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/3.34.10.in-addr.arpa.com
  ```
- Buka file 3.34.10.in-addr.arpa.com 
  ```
  nano /etc/bind/jarkom/3.34.10.in-addr.arpa.com
  ```
  Edit menjadi

  Dalam file `3.34.10.in-addr.arpa.com`, perlu ditambahkan rekaman PTR (Pointer) yang menghubungkan alamat IP ke nama domain Abimanyu.
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/5/rv-ab2.png)
- Restart bind9
  ```
  service bind9 restart
  ```
  Penjelasan Jawaban:

Membuat konfigurasi Reverse DNS untuk domain utama Abimanyu. Konfigurasi ini akan memungkinkan untuk menghubungkan alamat IP dengan nama domain Abimanyu yang sesuai. Pastikan konfigurasi berkas `3.34.10.in-addr.arpa.com` telah diperbarui dengan benar sesuai dengan rekaman PTR yang Anda tambahkan.
### Soal 6
Soal:

"Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama."

Penjelasan Soal:

Konfigurasi DNS Master-Slave antara Yudhistira (DNS Master) dan Werkudara (DNS Slave) untuk domain utama `abimanyu.D25.com`. Ini memungkinkan Werkudara untuk memiliki salinan (zona sekunder) dari zona DNS yang dimiliki oleh Yudhistira, sehingga jika Yudhistira mengalami masalah, DNS dapat tetap beroperasi.
#### Pada Yudhistira sebagai DNS Master
- Membuka file named.conf.local untuk konfigurasi domain abimanyu.D25.com
  
Di Yudhistira (DNS Master), buka file `named.conf.local` untuk mengkonfigurasi `zona abimanyu.D25.com`.
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain abimanyu.D25.com menjadi
  
Di dalam `named.conf.local`, tambahkan konfigurasi untuk zona `abimanyu.D25.com`. Ini akan mendefinisikan Yudhistira sebagai DNS Master untuk zona ini.

  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/6/Y-ab.png)
- Restart bind9
  ```
  service bind9 restart
  ```
#### Pada Werkudara sebagai DNS Slave
- Install aplikasi bind9 dengan
  ```
  apt-get update
  apt-get install bind9 -y
  ```
- Membuka file named.conf.local untuk konfigurasi domain abimanyu.D25.com

  Di Werkudara, buka file `named.conf.local` untuk mengkonfigurasi zona `abimanyu.D25.com`
  
  ```
  nano /etc/bind/named.conf.local
  ```
  Kemudian isikan konfigurasi domain abimanyu.D25.com menjadi

Di dalam `named.conf.local` pada Werkudara, tambahkan konfigurasi untuk zona `abimanyu.D25.com`. Namun, berbeda dengan Yudhistira, Werkudara harus didefinisikan sebagai DNS Slave untuk zona ini.

  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/6/W-ab.png)
- Restart bind9
  ```
  service bind9 restart
  ```
Konfigurasi Yudhistira sebagai DNS Master dan Werkudara sebagai DNS Slave untuk `zona abimanyu.D25.com`. Werkudara akan secara teratur mengambil zona sekunder dari Yudhistira dan akan dapat melayani permintaan DNS jika Yudhistira mengalami masalah.
### Soal 7
#### Pada Yudhistira
- Buka file abimanyu.D25.com 
  ```
  nano /etc/bind/jarkom/abimanyu.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/7/Y-ab.png)
- Buka file named.conf.options
  ```
  nano /etc/bind/named.conf.options
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/7/op.png)
- Restart bind9
  ```
  service bind9 restart
  ```
#### Pada Werkudara
- Membuka file named.conf.local untuk konfigurasi domain baratayuda.abimanyu.D25.com 
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/7/W-ab.png)
- Membuat folder baratayuda
  ```
  mkdir /etc/bind/baratayuda
  ```

- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file baratayuda.abimanyu.D25.com
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/baratayuda.abimanyu.D25.com
  ```
- Buka file baratayuda.abimanyu.D25.com 
  ```
  nano /etc/bind/jarkom/baratayuda.abimanyu.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/7/W-ab2.png)
- Buka file named.conf.options
  ```
  nano /etc/bind/named.conf.options
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/7/op.png)
- Restart bind9
  ```
  service bind9 restart
  ```
### Soal 8
- Buka file baratayuda.abimanyu.D25.com 
  ```
  nano /etc/bind/jarkom/baratayuda.abimanyu.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/8/W-rjp.png)
### Testing
- Pada bagian client Nakula dan Sadewa buka file resolv.conf
  ```
  nano /etc/resolv.conf
  ```
  Isikan pada file
  ```
  nameserver 10.34.2.2 ;	IP Yudhistira
  nameserver 10.34.3.2 ;	IP Werkudara
  ```
- Hasil ping arjuna.D25.com
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/ar.png)
- Hasil ping abimanyu.D25.com
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/ab.png)
- Hasil ping 3.34.10.in-addr.arpa
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/rv-ab.png)
- Hasil ping parikesit.abimanyu.D25.com
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/par.png)
- Hasil ping baratayuda.abimanyu.D25.com
  
![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/bar.png)
- Hasil ping rjp.baratayuda.abimanyu.D25.com
  
![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/t/rjp.png)
