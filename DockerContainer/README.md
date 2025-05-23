**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---
# Membuat Container System Sederhana

## 1. Instalasi

### Docker
![docker](/DockerContainer/img/docker.png)

Pada project ini, Docker digunakan untuk menjalankan MySQL secara terisolasi tanpa perlu instalasi langsung ke OS. Docker diinstal dari situs resminya (https://www.docker.com), atau melalui Microsoft Store.

### Power BI
![powerbi](/DockerContainer/img/powerbi.png)

Power BI digunakan sebagai software untuk visualisasi dan analisis data. Power BI Desktop diinstal dari Microsoft Store atau situs resmi Power BI (https://powerbi.microsoft.com) 

### MySQL ODBC Driver
![odbc](/DockerContainer/img/odbc.png)

Dengan ODBC, Power BI dapat terhubung langsung ke database MySQL untuk membaca data. MySQL ODBC Driver versi 64-bit diunduh dari situs resmi MySQL.

---

## 2. Menjalankan MySQL di Docker

Menjalankan perinta:
```bash
docker run --name mysql-bi -e MYSQL_ROOT_PASSWORD=admin123 -e MYSQL_DATABASE=classicmodels -p 3306:3306 -d mysql:8
````
![dockerrun](/DockerContainer/img/dockerrun.png)
Perintah ini akan membuat container bernama `mysql-bi` yang menjalankan MySQL versi 8 dengan konfigurasi password dan nama database. Docker memberikan keunggulan dalam hal isolasi dan kemudahan manajemen.

Untuk mengecek apakah container berhasil dijalankan:

```bash
docker ps
```

![dockerps](/DockerContainer/img/dockerps.png)

---

## 3. Import Database SQL ke MySQL Docker

Menggunakan **DBeaver** untuk mengakses server MySQL dan mengimpor file SQL:

* File: `Axon sales - Mysql Database.sql`
* Tools: `Execute Script`

File ini berisi data lengkap penjualan mobil, seperti tabel `customers`, `orders`, `products`, `employees`, dan lainnya.

![importsql](/DockerContainer/img/importsql.png)

---

## 4. Setup ODBC Data Source

Menggunakan aplikasi **ODBC Data Sources (64-bit)** untuk menyiapkan koneksi:

* Server: `127.0.0.1`
* User: `root`
* Password: `admin123`
* Database: `classicmodels`

Jika koneksi berhasil diuji, Power BI dapat menarik data secara langsung dari MySQL.

![setupodbc](/DockerContainer/img/setupodbc.png)

---

## 5. Hubungkan Power BI ke ODBC

Buka Power BI dan pilih:

* `Get Data > ODBC`
* DSN: `MySQL_Classic`

Setelah koneksi berhasil, Power BI akan menampilkan seluruh tabel dari database `classicmodels`.

## 6. Load Tabel ke Power BI

Memilih tabel-tabel  dari database `classicmodels`, seperti `orders`, `customers`, `orderdetails`, `products`, dan lain-lain. Klik **Load** untuk mulai mengimpor ke Power BI.

![tables](/DockerContainer/img/tables.png)

Gunakan **Model View** untuk menampilkan/membuat relasi antar tabel.

![relation](/DockerContainer/img/relation.png)

---

## 7. Desain Dashboard Power BI

![axonsales](/DockerContainer/img/axonsales.png)
Gambar tersebut adalah contoh visualisasi dari database classicmodels, yang menampilkan jumlah customer berdasarkan benua, 5 negara dengan penjualan tertinggi, dan statistik lainnya.

---

## 8. Kesimpulan

Melalui project ini, kita dapat menjalankan MySQL server secara lokal menggunakan Docker tanpa perlu instalasi permanen. Tanpa Docker, kita harus menginstal MySQL Server dan setup database secara manual. Dengan Docker, semua dapat dilakukan dengan satu baris perintah.

Selain itu, integrasi antara DBeaver, ODBC, dan Power BI membuat sistem Business Intelligence ini efisien dan terstruktur.
