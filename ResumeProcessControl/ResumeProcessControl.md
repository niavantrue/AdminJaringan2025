**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---

# Resume Bab 4: Kontrol Proses

#### **Komponen Proses**
- **Proses** terdiri dari ruang alamat (memori) dan struktur data di kernel.
- **Ruang alamat** menyimpan kode, data, dan tumpukan proses.
- **Struktur data kernel** melacak status, prioritas, sumber daya, file terbuka, dan informasi lain tentang proses.
- **Thread** adalah konteks eksekusi dalam proses. Beberapa thread dapat berbagi ruang alamat dan sumber daya.
- **Contoh**: Server web menggunakan thread untuk menangani banyak permintaan secara bersamaan.

#### **Identifikasi Proses**
- **PID (Process ID)**: Nomor unik yang mengidentifikasi proses.
- **PPID (Parent Process ID)**: PID dari proses induk yang membuat proses tersebut.
- **UID & EUID**: ID pengguna yang memulai proses dan ID pengguna efektif yang menentukan akses sumber daya.

#### **Siklus Hidup Proses**
- Proses baru dibuat dengan `fork` (atau `clone` di Linux), yang menyalin proses induk.
- Proses pertama saat sistem boot adalah `init` atau `systemd` (PID 1).
- Semua proses lain adalah turunan dari proses ini.

#### **Sinyal**
- Sinyal digunakan untuk mengirim pemberitahuan ke proses (misalnya, menghentikan atau menjeda proses).
- Jenis sinyal umum:
  - **KILL**: Menghentikan proses secara paksa.
  - **TERM**: Permintaan untuk menghentikan proses.
  - **HUP**: Meminta proses untuk restart (biasanya digunakan pada daemon).
  - **INT**: Menghentikan operasi saat ini (dikirim saat pengguna menekan `Ctrl+C`).

#### **Perintah untuk Mengelola Proses**
- **`kill`**: Mengirim sinyal ke proses (default: TERM).
  - Contoh: `kill -9 PID` (menghentikan proses secara paksa).
- **`killall`**: Menghentikan proses berdasarkan nama.
- **`pkill`**: Menghentikan proses berdasarkan kriteria (misalnya, nama pengguna).

#### **Pemantauan Proses**
- **`ps`**: Menampilkan informasi tentang proses (PID, status, penggunaan CPU/memori).
  - Contoh: `ps aux` (menampilkan semua proses).
- **`top`**: Tampilan real-time proses dan penggunaan sumber daya sistem.
- **`htop`**: Versi interaktif dari `top` dengan antarmuka yang lebih baik.

#### **Prioritas Proses**
- **Nice Value**: Menentukan prioritas proses (nilai rendah = prioritas tinggi).
  - **`nice`**: Memulai proses dengan nilai nice tertentu.
  - **`renice`**: Mengubah nilai nice proses yang sedang berjalan.
- Rentang nice value di Linux: -20 (prioritas tertinggi) hingga +19 (prioritas terendah).

#### **Sistem Berkas `/proc`**
- Direktori `/proc` menyediakan informasi tentang proses dan status sistem.
- Setiap proses memiliki direktori dengan nama sesuai PID-nya, berisi informasi seperti baris perintah, variabel lingkungan, dan file yang dibuka.

#### **Debugging Proses**
- **`strace`**: Melacak panggilan sistem dan sinyal yang dilakukan oleh proses.
- **`lsof`**: Menampilkan file yang dibuka oleh proses.

#### **Proses yang Tidak Terkendali**
- Proses yang menggunakan 100% CPU dan mengabaikan prioritas.
- Dapat dihentikan dengan `kill -9 PID`.
- Penyebab dapat diselidiki dengan `strace` atau `lsof`.

#### **Proses Periodik**
- **`cron`**: Menjalankan perintah pada jadwal tertentu.
  - Format crontab: `* * * * * perintah` (menit, jam, hari, bulan, hari minggu).
  - Contoh: `30 2 * * * /path/to/script.sh` (menjalankan script setiap hari pukul 2:30 pagi).
- **Systemd Timer**: Alternatif modern untuk `cron`, lebih fleksibel dan canggih.

#### **Penggunaan Umum Tugas Terjadwal**
- **Mengirim email**: Mengirim laporan otomatis.
- **Membersihkan sistem berkas**: Menghapus file sampah secara berkala.
- **Rotasi log**: Membagi file log berdasarkan ukuran atau tanggal.
- **Pekerjaan batch**: Menjalankan tugas berat di latar belakang.
- **Backup dan mirroring**: Mencadangkan data secara otomatis ke sistem jarak jauh.

### **Kesimpulan**
Kontrol proses melibatkan manajemen sumber daya, prioritas, dan eksekusi tugas. Dengan alat seperti `ps`, `top`, `kill`, dan `cron`, administrator sistem dapat memantau, mengontrol, dan mengotomatiskan proses secara efektif.
