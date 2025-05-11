**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---
# Resume Mail Server dan Protokol Email

Sistem email merupakan bagian penting dalam komunikasi digital modern yang memungkinkan pengguna untuk saling berkirim pesan secara cepat dan efisien. Teknologi ini mengandalkan kombinasi dari berbagai protokol jaringan, sistem server, dan standar keamanan untuk menjamin pesan sampai ke tujuan dengan benar dan aman.

---

## 1. Protokol Mail (SMTP, POP3, IMAP, POP3S)

### Tabel Perbandingan Protokol Email

| Protokol | Fungsi Utama            | Port Standar | Port Aman (SSL/TLS) | Penyimpanan Email | Cocok untuk                                        |
| -------- | ----------------------- | ------------ | ------------------- | ----------------- | -------------------------------------------------- |
| SMTP     | Mengirim email          | 25           | 465 / 587           | Tidak             | Semua jenis pengiriman                             |
| POP3     | Mengambil & hapus email | 110          | -                   | Diunduh ke klien  | Akses dari satu perangkat                          |
| POP3S    | POP3 dengan keamanan    | -            | 995                 | Diunduh ke klien  | Akses dari satu perangkat dengan keamanan tambahan |
| IMAP     | Sinkronisasi email      | 143          | 993                 | Tetap di server   | Multi-perangkat & mobilitas tinggi                 |

Dalam arsitektur email, protokol memiliki peran utama dalam mengatur jalannya pesan dari pengirim ke penerima. Berikut penjelasan masing-masing protokol:

* **SMTP (Simple Mail Transfer Protocol)**: Merupakan protokol standar untuk mengirimkan email. Protokol ini digunakan oleh klien email saat mengirim pesan ke server serta antar server email. SMTP hanya digunakan untuk proses pengiriman, bukan penerimaan email. Ia berjalan pada port 25 untuk komunikasi standar dan port 587 atau 465 jika menggunakan koneksi terenkripsi (SSL/TLS). SMTP memastikan bahwa email dari pengirim sampai ke server tujuan dengan benar.

* **POP3 (Post Office Protocol version 3)**: POP3 digunakan untuk mengambil atau mendownload email dari server ke perangkat klien. Setelah email diambil, secara default pesan akan dihapus dari server. Ini membuat POP3 cocok untuk pengguna yang hanya mengakses email dari satu perangkat. Protokol ini menggunakan port 110 dalam koneksi standar.

* **IMAP (Internet Message Access Protocol)**: Berbeda dengan POP3, IMAP memungkinkan email tetap tersimpan di server dan dapat diakses dari berbagai perangkat secara sinkron. IMAP sangat cocok untuk pengguna yang sering berpindah perangkat atau memerlukan akses email dari lokasi berbeda. IMAP berjalan pada port 143, atau port 993 jika menggunakan SSL/TLS.

* **POP3S (POP3 Secure)**: Ini adalah versi aman dari POP3, menggunakan SSL/TLS untuk mengamankan data selama proses pengambilan email. POP3S umumnya menggunakan port 995.

Protokol-protokol ini bekerja sama untuk memastikan bahwa email dikirim dan diterima dengan aman dan efisien sesuai kebutuhan pengguna.

---

## 2. Informasi Mail Server dalam Sebuah Domain

Agar sebuah email dapat dikirim ke penerima yang tepat, sistem email perlu mengetahui ke mana pesan harus diarahkan. Proses ini melibatkan sistem **Domain Name System (DNS)** dan beberapa jenis DNS record, terutama **MX record (Mail Exchange Record)**.

* **MX Record**: Jenis record ini menentukan mail server mana yang bertanggung jawab untuk menerima email untuk domain tertentu. MX record memiliki prioritas (preference number) yang menunjukkan urutan mail server mana yang dicoba terlebih dahulu jika ada beberapa server.

* **A Record dan AAAA Record**: Digunakan untuk menerjemahkan nama domain ke alamat IP (IPv4 untuk A dan IPv6 untuk AAAA). Mail server biasanya juga membutuhkan informasi ini untuk menyambungkan ke host tujuan.

* **TXT Record (SPF, DKIM, DMARC)**:

  * **SPF (Sender Policy Framework)**: Menentukan server mana saja yang diizinkan mengirim email atas nama domain tersebut.
  * **DKIM (DomainKeys Identified Mail)**: Menyediakan tanda tangan digital untuk memverifikasi keaslian email dan memastikan tidak diubah selama pengiriman.
  * **DMARC (Domain-based Message Authentication, Reporting and Conformance)**: Menggabungkan SPF dan DKIM serta memberikan instruksi kepada mail server penerima tentang bagaimana menangani email yang gagal verifikasi.

Semua record ini sangat penting untuk memverifikasi dan mengamankan pengiriman email, serta mencegah praktik penipuan seperti spoofing dan phishing.

---

## 3. Pengantar Sistem Surat Elektronik (Email)

Email merupakan sistem komunikasi elektronik yang memungkinkan pengguna untuk bertukar pesan melalui jaringan komputer, khususnya internet.

### Komponen Utama:

* **User Agent (UA)**: Program untuk mengirim, menerima, dan mengelola email (misalnya Outlook, Gmail).
* **Message Transfer Agent (MTA)**: Bertanggung jawab untuk mengirim email antar server menggunakan **SMTP**.
* **Kotak Surat**: Tempat penyimpanan email pada server atau perangkat pengguna, yang hanya dapat diakses oleh pemiliknya.
* **File Spool**: Menyimpan email keluar yang belum terkirim. MTA mengambil email dari file spool untuk dikirimkan.

![email](/ResumeEmailServer/img/email.png)

### Fitur Umum:

* Pengiriman file atau **attachment** (lampiran)
* Pengelolaan kotak masuk seperti filter spam, folder, dan label
* Sinkronisasi multi-perangkat dengan IMAP

### Aspek Keamanan:

* Enkripsi (SSL/TLS) untuk melindungi transmisi data
* Mekanisme autentikasi seperti SPF, DKIM, dan DMARC untuk memverifikasi pengirim

### Proses Pengiriman Email:

* Tulis pesan baru di klien email Anda.
* Masukkan alamat email penerima di kolom “To”.
* Tambahkan baris subjek untuk meringkas konten pesan.
* Tulis isi pesannya.
* Lampirkan berkas relevan jika diperlukan.
* Klik “Kirim” untuk mengirimkan pesan ke server email penerima.
* Email juga dapat menyertakan fitur seperti cc (salinan karbon) dan bcc (salinan karbon buta) untuk mengirim salinan pesan ke beberapa penerima, dan opsi balas, balas semua, dan teruskan untuk mengelola percakapan.

### Layanan yang Disediakan oleh Sistem Email:

* **Komposisi –** Proses pembuatan pesan dan balasan. Editor teks apa pun dapat digunakan untuk komposisi.
* **Transfer –** Proses pengiriman email dari pengirim ke penerima.
* **Pelaporan –** Konfirmasi pengiriman email yang membantu pengguna memeriksa status pengiriman email apakah terkirim, hilang, atau ditolak.
* **Menampilkan –** Penyajian email dalam format yang dapat dimengerti oleh pengguna.
* **Disposisi –** Langkah yang berkaitan dengan tindakan yang diambil oleh penerima setelah menerima email, misalnya menyimpan email, menghapusnya sebelum membaca, atau menghapus setelah membaca.

Email tidak hanya digunakan untuk komunikasi personal tetapi juga sebagai alat penting dalam dunia bisnis, pendidikan, serta layanan pelanggan. Dengan evolusi teknologi, email terus ditingkatkan untuk memberikan pengalaman komunikasi yang lebih aman, cepat, dan fleksibel.

---
