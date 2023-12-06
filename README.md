# Jarkom-Modul-4-D21-2023

## Kelompok D21
Akbar Putra Asenti P. 5025211004

Farrela Ranku Mahhisa 5025211129

## Pembagian IP
Kami mengggunakan VLSM pada CPT dan CIDR pada GNS3


Berikut ini adalah pembagian subnet beserta totalnya

![image](https://github.com/barpeot/Jarkom-Modul-4-D21-2023/assets/114351382/54b6872a-8346-4f6f-b956-845649ec33f0)

| Nama Subnet | Network ID  |
|  :---:      |     :---:   |
| A1          | 10.32.24.112|
| A2          | 10.32.24.64 |
| A3          | 10.32.24.136|
| A4          | 10.32.24.140|
| A5          | 10.32.0.0   |
| A6          | 10.32.12.0  |
| A7          | 10.32.24.144|
| A8          | 10.32.24.96 |
| A9          | 10.32.24.148|
| A10         | 10.32.24.104|
| A11         | 10.32.24.116|
| A12         | 10.32.20.0  |
| A13         | 10.32.24.120|
| A14         | 10.32.24.0  |
| A15         | 10.32.16.0  |
| A16         | 10.32.24.124|
| A17         | 10.32.23.0  |
| A18         | 10.32.24.128|
| A19         | 10.32.24.132|
| A20         | 10.32.8.0   |
| A21         | 10.32.22.0  |

### VLSM

Untuk VLSM karena jumlah total IP yang dibutuhkan sebesar 4255, maka dibutuhkan network dengan netmask dengan length sebesar /19 yang memiliki ukuran maksimal usable IP 8190

Pembagian IP yang dilakukan menggunakan  VLSM dilakukan dengan cara berikut ini

![WhatsApp Image 2023-12-05 at 12 54 28](https://github.com/barpeot/Jarkom-Modul-4-D21-2023/assets/114351382/34210e4d-5482-42c2-8e5e-cb2a0510e4dd)


Selanjutnya, kita bagi IP per subnet, berikut adalah hasilnnya

![image](https://github.com/barpeot/Jarkom-Modul-4-D21-2023/assets/114351382/56bbe30d-2314-46ef-8719-15c0307bfc90)

Setelah membagikan sesuai dengan subnet, kita assign masing-masing IP ke masing-masing node, pembagiannya adalah sebagai berikut

![IP vlsm](./assets/ip_vlsm.png)

Dalam langkah selanjutnya, network VLSM ini akan dibuat di **Cisco Packet Tracer**.

### Cisco Packet Tracer (VLSM)

Berikut adalah hasil topologi network yang dibuat di Cisco Packet Tracer.

![network cpt](./assets/network_cpt.png)

Langkah selanjutnya adalah konfigurasi IP untuk setiap node di topologi, sesuai dengan pembagian IP yang telah dilakukan sebelumnya. Proses ini disebut dengan **Subnetting**

Konfigurasi IP dapat dilakukan dengan membuka salah satu node kemudian masuk ke dalam menu **INTERFACE**, kemudian melakukan memasukkan IP address, Subnet Mask, dan menyalakan port dengan mencentang tombol **Port Status**.

Konfigurasi IP setiap router perlu memperhatikan interface eth yang dipakai di subnet yang mana, sebagai contoh berikut adalah salah satu contoh konfigurasi IP di router Fern pada Fa (FastEthernet) 0/0.

![example cpt](./assets/example_cpt.png)

Fa 0/0 pada Fern perlu disetup sedemikian karena interface ini mengarah ke node Flamme, sehingga dapat membentuk salah satu subnet yang telah ditentukan sebelumnya, yaitu subnet A4.

Untuk node yang merupakan host atau server, perlu ditambahkan default gateway yang mengarah ke interface router yang mengarah ke arah host atau server tersebut. Default gateway dapat ditentukan pada menu **Setting** pada host atau server.

Sebagai contoh, di node LaubHills (397 Hosts), default gateway yang digunakan adalah interface pada Fern Fa 0/1 yang mengarah ke LaubHills. 

### Di LaubHills

![example gateway cpt](./assets/example_gateway_cpt.png)

### Di Fern

![example gateway cpt 2](./assets/example_gateway_cpt_2.png)

### Routing

Proses selanjutnya adalah routing, tujuan dari proses ini adalah untuk "mengenalkan" satu subnet dengan subnet-subnet lainnya. Routing dapat dilakukan dengan cara menambahkan network ID, netmask, dan next hop untuk suatu subnet di dalam menu **Routing > Static**.

Untuk sebuah router yang memiliki host atau server, perlu ditambahkan routing dengan network ID 0.0.0.0 netmask 0.0.0.0 dengan next hop mengarah ke router utama (Aura).

Sebagai contoh, berikut adalah routing yang dilakukan pada router Fern:

![routing fern vlsm](./assets/routing_fern.png)

Setelah setup router Fern, perlu dilakukan setup pada router selanjutnya yang berhubungan dengan Fern, yaitu Flamme. Pada Flamme, setup routing adalah sebagai berikut:

![routing flamme vlsm](./assets/routing_flamme.png)

Pada Flamme, terdapat tiga buah routing yang dilakukan, 0.0.0.0 karena Flamme memiliki host berupa RohrRoad, 10.32.0.0 yang merupakan subnet LaubHills-AppetitRegion-Fern, dan 10.32.24.96 yang merupakan subnet Himmel-SchwerMountains.

Proses routing ini perlu dilanjutkan hingga router utama (Aura) dan perlu dijalankan untuk setiap cabang pada network. Sehingga di Aura terdapat routing untuk setiap subnet kecuali subnet yang bersebelahan dengan Aura (1 Hop), total terdapat 18 subnet yang perlu disimpan di Aura.

![routing aura vlsm](./assets/routing_aura.png)

Untuk next hop perlu disesuaikan dengan topologi, dalam contoh diatas next hop 10.32.24.114 di Aura mengarah ke Frieren (arah kiri), next hop 10.32.24.126 di Aura mengarah ke Denken (arah kanan), dan next hop 10.32.24.150 di Aura mengarah ke Eisen (arah bawah).

### Testing

Setelah subnetting dan routing dijalankan, dapat dilakukan testing di Cisco Packet Tracer dengan menggunakan tool PDU (Keybind P) untuk mengirim pesan dari satu node ke node yang lain.

![testing vlsm](./assets/testingvlsm.png)

Pengetesan yang dilakukan:

-	Sein –> Richter
-	GranzChannel –> Turk Region
-	RiegelCanyon –> Aura
-	Fern –> Linie
-	RoyalCapital –> LaubHills
-	Heiter –> Denken
-	SchwerMountains –> Lugner

### CIDR

Dalam CIDR langkah yang pertama dilakukan adalah melakukan penggabungan subnet. Penggabungan subnet yang kami lakukan adalah sebagai berikut:

![gabung cidr](./assets/gabung_cidr.png)

Dengan rincian sebagai berikut:

### Penggabungan pertama: B

![gabung 1](./assets/gabung_1.png)

### Penggabungan kedua: C

![gabung 2](./assets/gabung_2.png)

### Penggabungan ketiga: D
![gabung 3](./assets/gabung_3.png)

### Penggabungan keempat: E

![gabung 4](./assets/gabung_4.png)

### Penggabungan kelima: F

![gabung 5](./assets/gabung_5.png)

### Penggabungan keenam: G

![gabung 6](./assets/gabung_6.png)

Maka akan dihasilkan subnet G1 yang berisi semua subnet A. Selanjutnya perlu dilakukan pembagian Network ID CIDR dengan menggambar tree berdasarkan penggabungan yang tadi dilakukan, sehingga dihasilkan hasil sebagai berikut:

![tree cidr](./assets/treecidr.png)

Kemudian didapatkan pembagian network ID sebagai berikut:

![netid cidr](./assets/netidcidr.png)

Dari network ID tersebut dapat dilakukan pembagian IP kepada setiap node pada subnet, sebagai berikut:

![ip cidr](./assets/ip_cidr.png)

| Nama Subnet | Network ID   |
|  :---:      |     :---:    |
| A1          | 10.32.144.32 |
| A2          | 10.32.144.0  |
| A3          | 10.32.164.0  |
| A4          | 10.32.136.0  |
| A5          | 10.32.128.0  |
| A6          | 10.32.160.0  |
| A7          | 10.32.168.8  |
| A8          | 10.32.168.0  |
| A9          | 10.32.32.0   |
| A10         | 10.32.84.0   |
| A11         | 10.32.82.0   |
| A12         | 10.32.80.0   |
| A13         | 10.32.72.0   |
| A14         | 10.32.68.0   |
| A15         | 10.32.64.0   |
| A16         | 10.32.193.0  |
| A17         | 10.32.192.0  |
| A18         | 10.32.16.0   |
| A19         | 10.32.8.0    |
| A20         | 10.32.0.0    |
| A21         | 10.32.4.0    |

Selanjutnya hal yang perlu dilakukan adalah membuat network ini ke dalam tool GNS3.

### GNS3 (CIDR)
