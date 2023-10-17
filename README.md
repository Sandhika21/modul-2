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
  Penjelasan jawaban:
`Eth0`: Mendapatkan alamat IP melalui `DHCP`.

Dalam topologi ini, Pandudewanata berperan sebagai node yang mungkin berfungsi sebagai router atau gateway untuk node lainnya. Yudhistira adalah DNS Master, Werkudara adalah DNS Slave, dan Arjuna adalah Load Balancer yang terdiri dari beberapa server web, yaitu Prabakusuma, Abimanyu, dan Wisanggeni.
### Soal 2
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
  ```
  nano /etc/bind/jarkom/arjuna.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/2/ar2.png)
- Restart bind9
  ```
  service bind9 restart
  ```

### Soal 3

- Membuka file named.conf.local untuk konfigurasi domain abimanyu.D25.com pada Yudhistira
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
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/abimanyu.D25.com
  ```
- Buka file abimanyu.D25.com 
  ```
  nano /etc/bind/jarkom/abimanyu.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/3/ab.png)
  
- Restart bind9
  ```
  service bind9 restart
  ```

### Soal 4
- Pada Yudhistira buka file abimanyu.D25.com
  ```
  nano /etc/bind/jarkom/abimanyu.D25.com
  ```
  Edit menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/4/par.png)
- Restart bind9
  ```
  service bind9 restart
  ```

### Soal 5
- Membuka file named.conf.local untuk konfigurasi reverse domain abimanyu.D25.com pada Yudhistira
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain
  
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
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/5/rv-ab2.png)
- Restart bind9
  ```
  service bind9 restart
  ```
### Soal 6
#### Pada Yudhistira sebagai DNS Master
- Membuka file named.conf.local untuk konfigurasi domain abimanyu.D25.com
  ```
  nano /etc/bind/named.conf.local
  ```

  Kemudian isikan konfigurasi domain abimanyu.D25.com menjadi
  
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
  ```
  nano /etc/bind/named.conf.local
  ```
  Kemudian isikan konfigurasi domain abimanyu.D25.com menjadi
  
  ![alt_text](https://github.com/Sandhika21/modul-2/blob/main/jarkom2/6/W-ab.png)
- Restart bind9
  ```
  service bind9 restart
  ```
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
