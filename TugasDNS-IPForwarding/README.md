**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---

# **DNS dan IP Forwarding**
## VM 1
### 1. Set Interface dan IP
- Adapter 1: Bridge Adapter
- Adapter 2: Internal Network

### 2. Instalasi Iptables dan BIND

Jalankan perintah berikut:
```code
sudo apt install bind9 bind9utils
```
![installbind](/TugasDNS-IPForwarding/img/installbind.png)


Kemudian jalankan perintah berikut:
```code
sudo apt install iptables iptables-persistent
```
![installiptables](/TugasDNS-IPForwarding/img/installiptables.png)

### 3. Konfigurasi DNS
Konfigurasikan file '/etc/bind/named.conf' dan tambahkan
```code
include "/etc/bind/named.conf.external-zones";
```
![namedconf1](/TugasDNS-IPForwarding/img/namedconf1.png)

Kemudian file `/etc/bind/named.conf.options` dan tambahkan line
```code
allow-query { any; };
allow-transfer { any; };
recursion yes;
```
![namedconfoptions](/TugasDNS-IPForwarding/img/namedconfoptions.png)

Lalu buat `/etc/bind/named.conf.external-zones` dan konfigurasi dengan kode sebagai berikut:
![externalzones](/TugasDNS-IPForwarding/img/externalzones.png)

Untuk konfigurasi zones, buat file `/etc/bind/kelompok05.com` dan isi dengan sebagai berikut:
![kelompok05](/TugasDNS-IPForwarding/img/kelompok05.png)

Kemudian pada `1.200.168.192.db`
![2001db](/TugasDNS-IPForwarding/img/2001db.png)

Cek syntax menggunakan perintah
```code
named-checkzone [nama_zone] [file_konfigurasi_zone]
```
![checkzone](/TugasDNS-IPForwarding/img/checkzone.png)

### 4. Konfigurasi IP Address
Pada file `/etc/network/interfaces` isi konfigurasi sebagai berikut:
![interfaces](/TugasDNS-IPForwarding/img/interfaces.png)

Kemudian restart jaringan menggunakan `sudo systemctl restart networking`

### 5. Aktifkan IP Forwarding

Edit file sysctl menggunakan `sudo nano /etc/sysctl.conf` dan
uncomment bagian 
```code
net.ipv4.ip_forward=1
```
![sysctl](/TugasDNS-IPForwarding/img/sysctl.png)

### 6. Atur NAT dengan iptables
Jalankan perintah sebagai berikut:
```code
sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
sudo iptables -A FORWARD -i enp0s3 -o enp0s8 -j ACCEPT
```
![iptables](/TugasDNS-IPForwarding/img/iptables.png)

## VM 2
### Set Interface dan IP:
Adapter 1: Internal Network
<br>
Konfigurasi IP Static:
<br>
![settingvm2](/TugasDNS-IPForwarding/img/settingvm2.png)

## Testing
### Ping VM 2 ke VM 1:
![pingvm1](/TugasDNS-IPForwarding/img/pingvm1.png)

### Ping VM 1 ke VM 2:
![pingvm2](/TugasDNS-IPForwarding/img/pingvm2.png)

### Ping VM 2 ke Google:
![pinggoogle2](/TugasDNS-IPForwarding/img/pinggoogle2.png)
