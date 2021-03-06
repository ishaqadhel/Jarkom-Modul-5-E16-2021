# ๐ Laporan Resmi Jaringan Komputer Modul 5 E16 2021 

**Anggota Kelompok:**
 - Ishaq Adheltyo (05111940000167)

## ๐ Soal
![image](https://user-images.githubusercontent.com/49280352/145668022-35e1d71f-8b7d-4e3c-8e3a-3e4dbf223360.png)
![image](https://user-images.githubusercontent.com/49280352/145668044-949ec6ad-9c71-4239-a636-32064134021a.png)

**REVISI: 1.0 -> 1.1: Revisi Soal No. 2 dari โyang memiliki ip DHCPโ menjadi โyang merupakan DHCP Serverโ**

## ๐ก Pembagian Region
![image](https://user-images.githubusercontent.com/49280352/145668533-be3146e7-cdfe-4eb7-9c66-7fef9a7cbec0.png)

## ๐ถ Table Subnet
![image](https://user-images.githubusercontent.com/49280352/145668585-0751aa01-5265-4674-8462-b4909d3aca75.png)

## ๐ก VSLM

### ๐๏ธ Pengertian
Teknik VSLM untuk mengefisienkan pembagian IP di dalam jaringan. Besar netmask disesuaikan dengan banyaknya komputer/ host yang membutuhkan alamat IP.

### ๐ List IP Host
![image](https://user-images.githubusercontent.com/49280352/145668585-0751aa01-5265-4674-8462-b4909d3aca75.png)

Dapat dilihat di tabel diatas bahwa total jumlah ip yang dibutuhkan oleh seluruh pada host adalah 1314 yang dimana masuk kategori netmask 21. Oleh karena itu, untuk pembagian IP pada pohon dimulai dengan netmask 21.

### ๐ณ Pohon Pembagian IP
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

### ๐ Hasil Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/145669142-00c49c6d-7682-4fe8-8a4a-6955df5da20c.png)

## ๐ง Config Node

### ๐ง Edit Network Configuration Ubuntu 1.2

```
auto eth0
iface eth0 inet static
address 192.168.122.250
netmask 255.255.255.0
gateway 192.168.122.146
```

### ๐ง Edit Network Configuration Foosha

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

### ๐ง Edit Network Configuration Water7

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

### ๐ง Edit Network Configuration Blueno

```
auto eth0
iface eth0 inet static
address 10.37.7.2
netmask 255.255.255.128
gateway 10.37.7.1
```

### ๐ง Edit Network Configuration Cipher

```
auto eth0
iface eth0 inet static
address 10.37.0.2
netmask 255.255.252.0
gateway 10.37.0.1
```

### ๐ง Edit Network Configuration Doriki

```
auto eth0
iface eth0 inet static
address 10.37.7.130
netmask 255.255.255.248
gateway 10.37.7.129
```

### ๐ง Edit Network Configuration Jipangu

```
auto eth0
iface eth0 inet static
address 10.37.7.131
netmask 255.255.255.248
gateway 10.37.7.129
```

### ๐ง Edit Network Configuration Guanhao

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

### ๐ง Edit Network Configuration Elena

```
auto eth0
iface eth0 inet static
address 10.37.4.2
netmask 255.255.254.0
gateway 10.37.4.1
```

### ๐ง Edit Network Configuration Fukurou

```
auto eth0
iface eth0 inet static
address 10.37.6.2
netmask 255.255.255.0
gateway 10.37.6.1
```

### ๐ง Edit Network Configuration Jorge

```
auto eth0
iface eth0 inet static
address 10.37.7.138
netmask 255.255.255.248
gateway 10.37.7.137
```

### ๐ง Edit Network Configuration Maingate

```
auto eth0
iface eth0 inet static
address 10.37.7.139
netmask 255.255.255.248
gateway 10.37.7.137
```

## โ๏ธ Config Routing di GNS3

### ๐ง Foosha

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

### ๐ง Water7

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.37.7.146
```

### ๐ง Guanhao

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.37.7.149
```

### ๐ง Konfigurasi tambahan pada Foosha

- Tambahkan perintah dibawah pada .bashrc
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s [Prefix IP].0.0/21
```
Keterangan:
- **iptables** merupakan suatu tools dalam sistem operasi Linux yang berfungsi sebagai filter terhadap lalu lintas data.
- **Nat** adalah metode penafsiran alamat jaringan yang digunakan untuk menghubungkan lebih dari satu komputer ke jaringan internet dengan satu IP.
- **Masquerade** berfungsi untuk menyamarkan paket, misal mengganti alamat pengirim dengan alamat router.

- Buka /etc/resolv.conf

```
cat /etc/resolv.conf
```
Hasil dari file diatas, salin pada node **Lainnya** agar node dapat tersambung dengan internet.

## ๐ท๏ธ Prepare Tools: Sebelum lanjut ke soal shift pastikan meginstall semua tools dibawah

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Foosha

```
apt-get update
apt-get install nano
```

#### ๐ฅ๏ธ Node Water7 dan Guanhao

```
apt-get update
apt-get install nano
apt-get install isc-dhcp-relay -y
```

#### ๐ฅ๏ธ Node Jipangu

```
apt-get update
apt-get install nano
apt-get install isc-dhcp-server -y
```

#### ๐ฅ๏ธ Node Doriki

```
apt-get update
apt-get install nano
apt-get install bind9 -y
```

#### ๐ฅ๏ธ Node Jorge dan Maingate

```
apt-get update
apt-get install nano
apt-get install apache2 -y
```

#### ๐ฅ๏ธ Node Client

```
apt-get update
apt-get install nano
```

## ๐ท๏ธ Soal D: Tugas berikutnya adalah memberikan ip pada subnet Blueno, Cipher, Fukurou, dan Elena secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Water7 dan Guanhao

- Edit isc-dhcp-relay berisi ip node dimana DHCP Relay mengetahui siapa DHCP Server (Jipangu), Isi INTERFACES dengan 'eth0, eth1, eth2, eth3' untuk kemana saja DHCP relay bisa mendistribusikan IP dari DHCP Server (lihat topologi)

```
nano /etc/default/isc-dhcp-relay 
```

```
# Defaults for isc-dhcp-relay initscript
# sourced by /etc/init.d/isc-dhcp-relay
# installed at /etc/default/isc-dhcp-relay by the maintainer scripts

#
# This is a POSIX shell fragment
#

# What servers should the DHCP relay forward requests to?
SERVERS="10.37.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth0 eth1 eth2 eth3"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```

```
service isc-dhcp-relay start
```

#### ๐ฅ๏ธ Node Jipangu

- Edit Config dhcp server dengan menaruh interfaces 'eth0' karena interface eth0 adalah interface yang dipakai untuk dhcp request (lihat topologi)

```
nano /etc/default/isc-dhcp-server
```

```
# Defaults for isc-dhcp-server initscript
# sourced by /etc/init.d/isc-dhcp-server
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPD_CONF=/etc/dhcp/dhcpd.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPD_PID=/var/run/dhcpd.pid

# Additional options to start dhcpd with.
#       Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```

- Edit dhcpd.conf dan tambahkan beberapa config subnet untuk membantu DHCP Server mengenali topologi

```
nano /etc/dhcp/dhcpd.conf
```

```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option subnet-mask 255.255.255.224;
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

# Blueno
subnet 10.37.7.0 netmask 255.255.255.128 {
	range 10.37.7.2 10.37.7.126;
	option routers 10.37.7.1;
	option broadcast-address 10.37.7.127;
	option domain-name-servers 10.37.7.130;
	default-lease-time 600;
	max-lease-time 7200;
}

# Cipher
subnet 10.37.0.0 netmask 255.255.252.0 {
	range 10.37.0.2 10.37.3.254;
	option routers 10.37.0.1;
	option broadcast-address 10.37.3.255;
	option domain-name-servers 10.37.7.130;
	default-lease-time 600;
	max-lease-time 7200;
}


# Elena
subnet 10.37.4.0 netmask 255.255.254.0 {
	range 10.37.4.2 10.37.5.254;
	option routers 10.37.4.1;
	option broadcast-address 10.37.5.255;
	option domain-name-servers 10.37.7.130;
	default-lease-time 600;
	max-lease-time 7200;
}


# Fukurou
subnet 10.37.6.0 netmask 255.255.255.0 {
	range 10.37.6.2 10.37.6.254;
	option routers 10.37.6.1;
	option broadcast-address 10.37.6.255;
	option domain-name-servers 10.37.7.130;
	default-lease-time 600;
	max-lease-time 7200;
}

# Routing dari Jipangu ke Router Water7
subnet 10.37.7.128 netmask 255.255.255.248 {
        option routers 10.37.7.129;
}
```

```
service isc-dhcp-server stop
service isc-dhcp-server start
```

#### ๐ฅ๏ธ Node Jipangu

- Edit named.conf.options untuk menambahkan forwarder agar client yg menggunakan dhcp dan nameserver dns bisa menggunakan internet

```
nano /etc/bind/named.conf.options
```

```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
              192.168.122.1;
        };
        //=====================================================================$
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //=====================================================================$
        //dnssec-validation auto;
        allow-query { any; };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```

```
service bind9 restart
```

## ๐ท๏ธ Soal 1: Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Foosha

- Tambah Aturan IPTABLES dengan syarat ip eth0 sudah dibuat static tidak menggunakan DHCP (lihat config)

```
iptables -t nat -A POSTROUTING -s 10.37.0.0/21 -o eth0 -j SNAT --to-source 192.168.122.146
```

Keterangan:
- **NAT Table** adalah translasi jaringan lokal yg lewat firewall ke jaringan luar
- **POSTROUTING** adalah dijalankan SNAT mengubah almt asal paket
- **-t** adalah config untuk definisi table
- **-A** adalah command untuk menambah aturan iptable
- **-s** adalah source  
- **-o** adalah out interface
- **-j SNAT** adalah spesifikasi source  
- **--to-source** adalah spesifikasi alamat ip

## ๐ท๏ธ Soal 2: Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang merupakan DHCP Server dan DNS Server demi menjaga keamanan.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Foosha

- Tambah Aturan IPTABLES

```
iptables -A FORWARD -d 10.37.7.128/29 -i eth0 -p tcp --dport 80 -j DROP
```

Keterangan:
- **-A** adalah command untuk menambah aturan iptable
- **FORWARD** adalah filter paket yg akan diteruskan
- **-d** adalah destination
- **-i** adalah interface  
- **-p** adalah protocol yang ingin dimasukkan ke aturan iptable
- **--dport** adalah pilihan port untuk aturan IPTABLE
- **-j** adalah definisi rule  
- **DROP** adalah aturan untuk menolak paket

## ๐ท๏ธ Soal 3: Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Jipangu dan Doriki

- Tambah Aturan IPTABLES

```
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

Keterangan:
- **-A** adalah command untuk menambah aturan iptable
- **INPUT** adalah melakukan filter paket yang masuk firewall
- **-p** adalah protocol yang ingin dimasukkan ke aturan iptable
- **-m** adalah definisiin kesesuaian rule untuk tujuan
- **connlimit** adalah aturan untuk limit connection
- **connlimit mask** adalah definisi netmask yang akan masuk pada aturan kalau 0 berarti semua netmask
- **-j** adalah definisi rule  
- **DROP** adalah aturan untuk menolak paket

## ๐ท๏ธ Soal 4: Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut: (1) Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis. Selain itu direject.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Doriki

- Tambah Aturan IPTABLES

```
iptables -A INPUT -s 10.37.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 10.37.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 10.37.7.0/25 -j REJECT
iptables -A INPUT -s 10.37.0.0/22 -j REJECT
```

Keterangan:
- **-A** adalah command untuk menambah aturan iptable
- **INPUT** adalah melakukan filter paket yang masuk firewall
- **-s** adalah source  
- **-m** adalah definisiin kesesuaian rule untuk tujuan
- **-timestart** adalah deklarasi untuk range waktu mulai aturan
- **-timestop** adalah deklarasi untuk range waktu berenti aturan
- **โdays** adalah deklarasi untuk range hari aturan 
- **-j** adalah definisi rule  
- **ACCEPT** adalah aturan untuk menerima paket
- **REJECT** adalah aturan untuk menolak paket dengan memberi error message

## ๐ท๏ธ Soal 5: Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut: (2) Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Doriki

- Tambah Aturan IPTABLES

```
iptables -A INPUT -s 10.37.4.0/23 -m time --timestart 07:00 --timestop 15:00 -j REJECT
iptables -A INPUT -s 10.37.6.0/24 -m time --timestart 07:00 --timestop 15:00 -j REJECT
```

Keterangan:
- **-A** adalah command untuk menambah aturan iptable
- **INPUT** adalah melakukan filter paket yang masuk firewall
- **-s** adalah source  
- **-m** adalah definisiin kesesuaian rule untuk tujuan
- **-timestart** adalah deklarasi untuk range waktu mulai aturan
- **-timestop** adalah deklarasi untuk range waktu berenti aturan
- **โdays** adalah deklarasi untuk range hari aturan 
- **-j** adalah definisi rule  
- **ACCEPT** adalah aturan untuk menerima paket
- **REJECT** adalah aturan untuk menolak paket dengan memberi error message

## ๐ท๏ธ Soal 6: Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate.

### โ๏ธ Langkah-Langkah Pengerjaan:

#### ๐ฅ๏ธ Node Guanhao

- Tambah Aturan IPTABLES

```
iptables -A PREROUTING -t nat -p tcp -d 10.37.7.130 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.37.7.138:80
iptables -A PREROUTING -t nat -p tcp -d 10.37.7.130 --dport 80 -j DNAT --to-destination 10.37.7.139:80
iptables -t nat -A POSTROUTING -p tcp -d 10.37.7.138 --dport 80 -j SNAT --to-source 10.37.7.130
iptables -t nat -A POSTROUTING -p tcp -d 10.37.7.139 --dport 80 -j SNAT --to-source 10.37.7.130
```

#### ๐ฅ๏ธ Node Jorge dan Maingate

- Restart Apache2 dan Enable 000-default.conf untuk jaga2

```
cd /etc/apache2/sites-available
a2ensite 000-default.conf
service apache2 restart
```

- Ubah Index HTML untuk menandakan Jorge atau Maingate

```
nano /var/www/html/index.html
```

```
<h1>ini [namaserver]</h1>
```

Keterangan:
- **-A** adalah command untuk menambah aturan iptable
- **PREROUTING** adalah manipulasi paket sebelum masuk routing
- **-t** adalah config untuk definisi table
- **-p** adalah protocol yang ingin dimasukkan ke aturan iptable
- **-d** adalah destination
- **--dport** adalah pilihan port untuk aturan IPTABLE
- **statistic** adalah untuk skip or accept a rule based on some statistic conditions
- **mode** adalah deklarasi aturan loadbalancing ada 2 random ama nth (roundrobin)
- **every packet** adalah rule buat jalanin loadbalancing round robin  
- **-j** adalah definisi rule  
- **POSTROUTING** adalah mengubah alamat asal dari paket
