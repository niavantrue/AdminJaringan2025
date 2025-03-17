**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---

# **Konfigurasi DNS untuk Jaringan Internal**
## 1. Instalasi BIND
Menginstall BIND dengan perintah `sudo apt -y install bind9 bind9utils`
![bindstatus](/img/bindstatus.png)

## 2. Konfigurasi BIND
Pada file /etc/bind/named.conf tambahkan `include "/etc/bind/named.conf.internal-zones";`
![namedconf](/img/namedconf.png)

Kemudian pada file /etc/bind/named.conf.options tambahkan teks sebagai berikut
![internalacl](/img/internalacl.png)
![options](/img/options.png)

Lalu atur konfigurasi pada file /etc/bind/named.conf.internal-zones menjadi:
![internalzones](/img/internalzones.png)

## 3. Konfigurasi File Zona untuk Jaringan Internal
Pada file /etc/bind/xxx.home.lan tambahkan teks:
![xxxhomelan](/img/xxxhomelan.png)

Kemudian pada file /etc/bind/0.0.10.db
![010db](/img/010db.png)

## 4. Restart BIND Service
Menggunakan perintah `sudo systemctl restart bind9`

## 5. Testing
Menggunakan perintah `dig xxx.home 10.0.0.1`
![dighome](/img/dighome.png)
Output mengeluarkan `ANSWER SECTION`, maka DNS BIND untuk jaringan internal berhasil dikonfigurasikan


# **Konfigurasi DNS untuk Jaringan External**
## 1. Instalasi BIND
Menginstall BIND dengan perintah `sudo apt -y install bind9 bind9utils`
![bindstatus](/img/bindstatus.png)

## 2. Konfigurasi BIND
Pada file /etc/bind/named.conf tambahkan `include "/etc/bind/named.conf.external-zones";`
![namedconf](/img/namedconf.png)

Kemudian pada file /etc/bind/named.conf.options tambahkan teks sebagai berikut
![externalacl](/img/externalacl.png)
![options](/img/options.png)

Lalu atur konfigurasi pada file /etc/bind/named.conf.external-zones menjadi:
![externalzones](/img/externalzones.png)

## 3. Konfigurasi File Zona untuk Jaringan External
Pada file /etc/bind/xxx.home.lan tambahkan teks:
![examplezone](/img/examplezone.png)

Kemudian pada file /etc/bind/2.0.10.db
![210db](/img/210db.png)

## 4. Restart BIND Service
Menggunakan perintah `sudo systemctl restart bind9`

## 5. Testing
Menggunakan perintah `dig xxx.example.com 10.0.2.15`
![dighome](/img/dighome.png)
Output mengeluarkan `ANSWER SECTION`, maka DNS BIND untuk jaringan external berhasil dikonfigurasikan
