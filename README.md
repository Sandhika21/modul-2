# modul-2

| **No** | **Nama** | **NRP** | 
| ------------- | ------------- | --------- |
| 1 | Andrian Tambunan  | 5025211018 | 
| 2 | Sandhika Surya Ardyanto | 5025211022 |

### Soal 1
![alt_text]()

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

- Membuat folder jarkom jika belum ada 
  ```
  mkdir /etc/bind/jarkom
  ```
- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file arjuna.D25.com
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/arjuna.D25.com
  ```
- Buka file abimanyu.D25.com 
  ```
  nano /etc/bind/jarkom/arjuna.D25.com
  ```
  Edit menjadi
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
- Copy file db.local pada path /etc/bind ke dalam folder jarkom dengan nama file 3.34.10.in-addr.arpa.com
  ```
  cp /etc/bind/db.local /etc/bind/jarkom/3.34.10.in-addr.arpa.com
  ```
- Buka file 3.34.10.in-addr.arpa.com 
  ```
  nano /etc/bind/jarkom/3.34.10.in-addr.arpa.com
  ```
  Edit menjadi
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
- Buka file named.conf.options
  ```
  nano /etc/bind/named.conf.options
  ```
  Edit menjadi
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
- Buka file named.conf.options
  ```
  nano /etc/bind/named.conf.options
  ```
  Edit menjadi
- Restart bind9
  ```
  service bind9 restart
  ```

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
- Hasil ping abimanyu.D25.com
- Hasil ping 3.34.10.in-addr.arpa
- Hasil ping parikesit.abimanyu.D25.com
- Hasil ping baratayuda.abimanyu.D25.com
