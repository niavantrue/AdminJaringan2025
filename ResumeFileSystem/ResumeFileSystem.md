**Nama dosen pengampu:**

Dr Ferry Astika Saputra ST, M.Sc

**Dikerjakan oleh**

Nama	: Eugenia Valiant Van True  
NRP		: 3123600018  
Kelas	: 2 D4 IT A  

---

# **Resume Bab 5: Sistem Berkas**

#### **Tujuan Sistem Berkas**
- Sistem berkas bertujuan untuk mengatur dan mewakili sumber daya penyimpanan sistem.
- Terdiri dari empat komponen utama:
  1. **Ruang nama**: Cara memberi nama dan mengatur berkas dalam hierarki.
  2. **API**: Panggilan sistem untuk navigasi dan manipulasi objek.
  3. **Model keamanan**: Skema untuk melindungi dan berbagi sumber daya.
  4. **Implementasi**: Perangkat lunak yang menghubungkan model logis ke perangkat keras.

#### **Jenis Sistem Berkas**
- **Sistem berkas disk**: ext4, XFS, UFS, ZFS, Btrfs.
- **Sistem berkas asing**: FAT, NTFS (Windows), ISO 9660 (CD/DVD).
- Sistem berkas modern menawarkan kecepatan, keandalan, dan fitur tambahan.

#### **Nama Jalur (Pathname)**
- **Pathname**: String yang menunjukkan lokasi berkas dalam hierarki.
  - **Absolut**: Mulai dari root (`/home/username/file.txt`).
  - **Relatif**: Relatif terhadap direktori saat ini (`./file.txt`).

#### **Pemasangan dan Pelepasan Sistem Berkas**
- **Mount**: Menghubungkan sistem berkas ke pohon direktori.
  - Contoh: `mount /dev/sda4 /users`.
- **Unmount**: Melepaskan sistem berkas.
  - `umount -l`: Unmount malas (tidak langsung melepaskan).
  - `umount -f`: Unmount paksa.
- **Lsof/fuser**: Melihat proses yang menggunakan sistem berkas.

#### **Organisasi Pohon Berkas**
- **Direktori penting**:
  - `/boot`: Kernel OS.
  - `/etc`: Konfigurasi sistem.
  - `/bin`, `/sbin`: Utilitas penting.
  - `/tmp`: Berkas sementara.
  - `/usr`: Program dan pustaka.
  - `/var`: Log, spool, dan data yang berubah.

#### **Jenis Berkas**
1. **File biasa**: Data teks, biner, dll.
2. **Direktori**: Mengorganisir berkas.
3. **File perangkat karakter/blok**: Komunikasi dengan perangkat keras.
4. **Soket domain lokal**: Komunikasi antar proses.
5. **Pipa bernama (FIFO)**: Komunikasi antar proses.
6. **Tautan simbolis**: Tautan lunak ke berkas/direktori.
7. **Tautan keras**: Beberapa nama untuk satu berkas.

#### **Atribut Berkas**
- **Izin akses**: 9 bit izin (baca, tulis, eksekusi) untuk pemilik, grup, dan lainnya.
- **Bit khusus**:
  - **Setuid/Setgid**: Menjalankan berkas dengan hak pemilik/grup.
  - **Sticky bit**: Mencegah penghapusan berkas oleh pengguna lain di direktori bersama.
- **Perintah**:
  - `chmod`: Mengubah izin.
  - `chown`: Mengubah pemilik.
  - `chgrp`: Mengubah grup.
  - `umask`: Menetapkan izin default.

#### **Daftar Kontrol Akses (ACL)**
- **ACL**: Memperluas model izin tradisional.
  - **POSIX ACL**: Didukung oleh Linux, FreeBSD, Solaris.
  - **NFSv4 ACL**: Lebih canggih, dengan fitur seperti ACL default.
- **Perintah**:
  - `getfacl`: Menampilkan ACL.
  - `setfacl`: Menetapkan ACL.

#### **Perintah Penting**
- **`ls`**: Menampilkan informasi berkas/direktori.
  - Contoh: `ls -l` (format panjang).
- **`file`**: Menentukan jenis berkas.
- **`ln`**: Membuat tautan keras/simbolik.
- **`strace`/`lsof`**: Debugging proses dan berkas.

#### **Kesimpulan**
Sistem berkas mengatur penyimpanan data dengan hierarki direktori dan berkas. Dengan memahami struktur, jenis berkas, izin, dan alat seperti `mount`, `chmod`, dan ACL, administrator dapat mengelola sistem berkas secara efektif.
