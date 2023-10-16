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


