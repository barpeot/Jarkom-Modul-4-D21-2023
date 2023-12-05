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

![IP vlsm](./assets/IP_vlsm.png)

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

Maka akan dihasilkan subnet G1 yang berisi semua subnet A. Selanjutnya perlu dilakukan pembagian Network ID![Alt text](image.png) CIDR dengan menggambar tree berdasarkan penggabungan yang tadi dilakukan, sehingga dihasilkan hasil sebagai berikut:

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

### Cisco Packet Tracer

### GNS3
