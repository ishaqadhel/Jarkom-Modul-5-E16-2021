# 📖 Laporan Resmi Jaringan Komputer Modul 5 E16 2021 

**Anggota Kelompok:**
 - Ishaq Adheltyo (05111940000167)

## 📝 Soal
![image](https://user-images.githubusercontent.com/49280352/145668022-35e1d71f-8b7d-4e3c-8e3a-3e4dbf223360.png)
![image](https://user-images.githubusercontent.com/49280352/145668044-949ec6ad-9c71-4239-a636-32064134021a.png)

**REVISI: 1.0 -> 1.1: Revisi Soal No. 2 dari “yang memiliki ip DHCP” menjadi “yang merupakan DHCP Server”**

## 📡 Pembagian Region
![image](https://user-images.githubusercontent.com/49280352/145668533-be3146e7-cdfe-4eb7-9c66-7fef9a7cbec0.png)

## 📶 Table Subnet
![image](https://user-images.githubusercontent.com/49280352/145668585-0751aa01-5265-4674-8462-b4909d3aca75.png)

## 📡 VSLM

### 🗒️ Pengertian
Teknik VSLM untuk mengefisienkan pembagian IP di dalam jaringan. Besar netmask disesuaikan dengan banyaknya komputer/ host yang membutuhkan alamat IP.

### 📖 List IP Host
![image](https://user-images.githubusercontent.com/49280352/145668585-0751aa01-5265-4674-8462-b4909d3aca75.png)

Dapat dilihat di tabel diatas bahwa total jumlah ip yang dibutuhkan oleh seluruh pada host adalah 1314 yang dimana masuk kategori netmask 21. Oleh karena itu, untuk pembagian IP pada pohon dimulai dengan netmask 21.

### 🌳 Pohon Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/145668943-69799eb7-4896-42ee-ab5f-57cd162f98d7.png)

**Penjelasan Penambahan IP:**

Q: Mengapa 10.37.7.0/25 dilanjutkan dengan 10.37.7.128/25 ?

A: 
- IPv4 terdiri dari 32 bit dengan 8 bit di setiap titiknya {(x.x.x.x) x berisi 8bit}.
- Digunakan Rumus x = (32 - length netmask) MOD 8
- x = (32 - 25) MOD 8
- x = 7
- Kemudian hasil x gunakan dirumus 2^x untuk mencari network address berikutnya
- 2^7 = 128
- Berarti setelah 10.37.7.0/25 dilanjut dengan 10.37.7.128/25

Untuk lebih mudahnya bisa menggunakan calculator pada https://www.calculator.net/ip-subnet-calculator.html

### 📚 Hasil Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/145669142-00c49c6d-7682-4fe8-8a4a-6955df5da20c.png)

## 🔧 Config Node

### 🔧 Edit Network Configuration Ubuntu 1.2

```
auto eth0
iface eth0 inet static
address 192.168.122.250
netmask 255.255.255.0
gateway 192.168.122.146
```

### 🔧 Edit Network Configuration Foosha

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.37.7.146
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.37.7.149
netmask 255.255.255.252
```

### 🔧 Edit Network Configuration Water7

```
auto eth0
iface eth0 inet static
address 10.37.7.145
netmask 255.255.255.252
gateway 10.37.7.146

auto eth1
iface eth1 inet static
address 10.37.7.129
netmask 255.255.255.248

auto eth2
iface eth2 inet static
address 10.37.7.1
netmask 255.255.255.128

auto eth3
iface eth3 inet static
address 10.37.0.1
netmask 255.255.252.0
```

### 🔧 Edit Network Configuration Blueno

```
auto eth0
iface eth0 inet static
address 10.37.7.2
netmask 255.255.255.128
gateway 10.37.7.1
```

### 🔧 Edit Network Configuration Cipher

```
auto eth0
iface eth0 inet static
address 10.37.0.2
netmask 255.255.252.0
gateway 10.37.0.1
```

### 🔧 Edit Network Configuration Doriki

```
auto eth0
iface eth0 inet static
address 10.37.7.130
netmask 255.255.255.248
gateway 10.37.7.129
```

### 🔧 Edit Network Configuration Jipangu

```
auto eth0
iface eth0 inet static
address 10.37.7.131
netmask 255.255.255.248
gateway 10.37.7.129
```

### 🔧 Edit Network Configuration Guanhao

```
auto eth0
iface eth0 inet static
address 10.37.7.150
netmask 255.255.255.252
gateway 10.37.7.149

auto eth1
iface eth1 inet static
address 10.37.7.137
netmask 255.255.255.248

auto eth2
iface eth2 inet static
address 10.37.4.1
netmask 255.255.254.0

auto eth3
iface eth3 inet static
address 10.37.6.1
netmask 255.255.255.0
```

### 🔧 Edit Network Configuration Elena

```
auto eth0
iface eth0 inet static
address 10.37.4.2
netmask 255.255.254.0
gateway 10.37.4.1
```

### 🔧 Edit Network Configuration Fukurou

```
auto eth0
iface eth0 inet static
address 10.37.6.2
netmask 255.255.255.0
gateway 10.37.6.1
```

### 🔧 Edit Network Configuration Jorge

```
auto eth0
iface eth0 inet static
address 10.37.7.138
netmask 255.255.255.248
gateway 10.37.7.137
```

### 🔧 Edit Network Configuration Maingate

```
auto eth0
iface eth0 inet static
address 10.37.7.139
netmask 255.255.255.248
gateway 10.37.7.137
```

## ⚖️ Config Routing di GNS3

### 🔧 Foosha

```
# kiri ke water7
route add -net 10.37.7.128 netmask 255.255.255.248 gw 10.37.7.145
route add -net 10.37.7.0 netmask 255.255.255.128 gw 10.37.7.145
route add -net 10.37.0.0 netmask 255.255.252.0 gw 10.37.7.145

# kanan ke guanhao
route add -net 10.37.4.0 netmask 255.255.254.0 gw 10.37.7.150
route add -net 10.37.6.0 netmask 255.255.255.0 gw 10.37.7.150
route add -net 10.37.7.136  netmask 255.255.255.248 gw 10.37.7.150
```

### 🔧 Water7

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.37.7.146
```

### 🔧 Guanhao

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.37.7.149
```
