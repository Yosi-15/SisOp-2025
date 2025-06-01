Nama  : Yosiyanti Cendekia Sari  
NRP   : 3124500059  
Kelas : 1 D3 IT B  
Dosen Pengampu : 

# Operating System Concepts, 10th Edition (Silberschatz, 2018)
---

## 1. Pendahuluan Sistem Operasi

* **Definisi & Tujuan**: Sistem operasi (OS) adalah lapisan perangkat lunak yang bertugas mengelola perangkat keras, menyediakan antarmuka bagi pengguna dan aplikasi, serta menjamin keamanan dan efisiensi eksekusi program.
* **Sejarah & Evolusi**: Berawal dari OS sederhana pada mesin batch di era 1950–1960, berkembang ke sistem time-sharing (multi‐user), real-time, terdistribusi, dan lalu ke virtualisasi/cloud di abad 21.

## 2. Struktur dan Mekanisme Dasar OS

* **Arsitektur Monolitik vs. Berlapis vs. Mikro-kernel**:

  * *Monolitik*: Semua layanan inti (penjadwalan, manajemen memori, I/O) terintegrasi dalam satu kernel besar.
  * *Berlapis*: OS dipecah ke dalam beberapa level—tingkat paling bawah berinteraksi langsung dengan hardware, tingkat tertinggi menyediakan layanan kepada aplikasi.
  * *Mikro-kernel*: Hanya fungsi minimal (seperti IPC dan penjadwalan) di kernel, sisanya (driver, sistem berkas) berjalan di user space.
* **Sistem Call & API**:
  Aplikasi berinteraksi dengan kernel lewat sistem call (misalnya `fork()`, `read()`, `write()`). Kernel memvalidasi argumen, memproses permintaan, lalu mengembalikan hasil/penyebab error.
* **Mode Eksekusi**:
  Proses dapat berjalan dalam *user mode* (akses terbatas) atau *kernel mode* (akses penuh). Berpindah terjadi saat terjadi interrupt, trap, atau sistem call.

## 3. Proses dan Thread

* **Proses (Process)**:
  Sebuah entitas yang mewakili program yang sedang dijalankan, terdiri dari: PID (Process ID), ruang alamat (code, data, stack), register CPU, dan status (ready, running, waiting, terminated).
* **Life‐Cycle Proses**:

  1. *New* (dibuat),
  2. *Ready* (siap dieksekusi),
  3. *Running* (sedang dieksekusi),
  4. *Waiting* (menunggu I/O atau peristiwa lain),
  5. *Terminated* (selesai/dihapus).
* **Thread**:
  Unit eksekusi ringan dalam proses, berbagi ruang alamat yang sama. Thread memungkinkan concurrency lebih efisien (lebih cepat beralih konteks daripada proses) dan pemanfaatan CPU yang lebih baik di sistem multiprosesor.
* **Model Thread**:

  * *User-level Threads*: Dikelola sepenuhnya di user-space (kernel tidak sadar adanya thread), switching cepat tapi sulit memanfaatkan multiprosesor.
  * *Kernel-level Threads*: Dikelola oleh kernel, dapat dipetakan ke beberapa CPU, switching lebih mahal (context switch kernel).
  * *Hybrid Model*: Kombinasi, beberapa user thread dipetakan ke beberapa kernel thread.

## 4. Penjadwalan CPU (CPU Scheduling)

* **Tujuan Penjadwalan**:
  Meningkatkan *throughput*, meminimalkan *turnaround time*, *waiting time*, dan meningkatkan *responsiveness* pada sistem interaktif.
* **Algoritma Dasar**:

  * *First-Come, First-Served (FCFS)*: Eksekusi sesuai urutan kedatangan proses di queue.
  * *Shortest Job First (SJF)*: Pilih proses dengan burst time terpendek—optimal untuk rata-rata waktu tunggu, tapi sulit memprediksi durasi.
  * *Priority Scheduling*: Setiap proses diberikan prioritas; bisa preemptive atau non-preemptive. Risiko *starvation* bagi proses prioritas rendah.
  * *Round Robin (RR)*: Setiap proses diberi *time quantum* (misalnya 10ms) secara bergiliran, cocok untuk sistem time-sharing.
  * *Multilevel Queue & Multilevel Feedback Queue*: Proses dibagi ke dalam beberapa level queue berdasarkan karakteristik (I/O-bound vs CPU-bound), dengan aturan promosi/demosi antar queue.
* **Evaluasi & Metode**:

  * *Turnaround Time*: Waktu total dari submit hingga lengkap.
  * *Waiting Time*: Waktu proses menunggu di ready queue.
  * *Response Time*: Waktu dari submit hingga output pertama (penting di sistem interaktif).
  * *Utilization*: Persentase waktu CPU bekerja (ideal mendekati 100%).

## 5. Sinkronisasi Proses (Process Synchronization)

* **Masalah Critical Section**:
  Saat beberapa proses/threads ingin mengakses sumber daya bersama (misalnya variabel global), perlu jaminan *mutual exclusion* (hanya satu pada satu waktu).
* **Kondisi untuk Solusi**:

  1. *Mutual Exclusion*: Hanya satu proses di critical section.
  2. *Progress*: Jika tidak ada proses di critical section, yang menunggu harus diperbolehkan masuk (tidak deadlock passive).
  3. *Bounded Waiting*: Batas wajar untuk menunggu (tidak starvation).
* **Mekanisme Sinkronisasi**:

  * *Peterson’s Algorithm*: Solusi software untuk dua proses.
  * *Lock & Unlock*: Instruksi hardware (Test-and-Set, Test-and-Test-and-Set, Compare-and-Swap).
  * *Semaphore*: Variabel integer yang atomik: `wait()` (P) dan `signal()` (V). Mendukung mutual exclusion (semaphore biner) dan sinkronisasi (semaphore penghitung).
  * *Monitors*: Abstraksi tingkat tinggi yang menggabungkan variabel bersama dan prosedur terproteksi; garansi mutual exclusion dan kondisi sinkronisasi lewat *condition variables* (wait/signal).

## 6. Deadlock

* **Definisi**:
  Situasi di mana dua atau lebih proses saling menunggu sumber daya yang dipegang satu sama lain, sehingga tidak ada yang dapat melanjutkan eksekusi.
* **Karakteristik (Coffman Conditions)**:

  1. *Mutual Exclusion*: Sumber daya tidak dapat dibagi (hanya satu proses akses).
  2. *Hold and Wait*: Proses memegang setidaknya satu sumber daya sambil menunggu sumber daya lain.
  3. *No Preemption*: Sumber daya tidak dapat diambil paksa dari proses.
  4. *Circular Wait*: Ada rantai proses $P_1$ menunggu milik $P_2$, $P_2$ menunggu milik $P_3$, … , hingga $P_n$ menunggu milik $P_1$.
* **Penanganan Deadlock**:

  * *Prevention*: Hancurkan salah satu kondisi Coffman—misalnya, tolak permintaan jika proses sudah memegang sumber daya lain, atau izinkan preemption.
  * *Avoidance*: Gunakan algoritma Bankir (Banker’s Algorithm) untuk memastikan bahwa alokasi sumber daya tidak memasuki keadaan yang tidak aman.
  * *Detection & Recovery*: OS secara berkala memeriksa grafik alokasi sumber daya—jika ada siklus, maka deadlock terdeteksi. Untuk recovery:

    * *Abort* proses tertentu (satu-per-satu, hingga bebas deadlock).
    * *Preempt* sumber daya dari proses (memungkinkan rollback dan restart proses).

## 7. Manajemen Memori

* **Konsep Dasar**:
  Manajemen memori bertujuan memanfaatkan RAM secara efisien, memisahkan ruang alamat proses, dan memberi kesan setiap proses memiliki memori sendiri (isolasi).
* **Alokasi Kontigu**:

  * *Fixed Partition*: Memori dibagi ke dalam partisi statis; proses ditempatkan ke partisi sesuai ukuran—sederhana tapi boros (internal fragmentation).
  * *Dynamic Partition*: Partisi dibentuk sesuai kebutuhan proses; mengurangi pemborosan tapi menimbulkan external fragmentation (lubang memori kecil yang tidak terpakai).
  * *First Fit, Best Fit, Worst Fit*: Algoritma untuk memilih lubang memori—masing-masing punya trade-off antara fragmentasi dan waktu pencarian.
* **Paging**:

  * Memori fisik dibagi menjadi *frame* (misal 4 KB), memori logis (virtual) dibagi ke *page* seukuran frame.
  * Tabel halaman (page table) menerjemahkan nomor page virtual ke frame fisik.
  * Menghilangkan external fragmentation, tapi dapat terjadi *internal fragmentation* (sisa ruang pada frame).
  * *TLB (Translation Lookaside Buffer)*: Cache terintegrasi di CPU untuk mempercepat translasi alamat; menurunkan overhead referensi page table.
* **Segmentasi**:

  * Alokasi berdasarkan segmen logis (code, data, stack) dengan ukuran bervariasi.
  * Tabel segmen (segment table) berisi (base, limit) tiap segmen—memberikan perlindungan dan fleksibilitas, namun memungkinkan external fragmentation.
* **Memori Virtual**:

  * “Hanya sebagian” program ditempatkan di RAM; sisanya di disk (swap).
  * *Demand Paging*: Page di-load ke memori hanya saat diakses (page fault).
  * *Page Replacement Algorithms*:

    * *FIFO*: Menyingkirkan page tertua—sederhana tapi kadang buruk.
    * *LRU (Least Recently Used)*: Menggantikan page yang paling lama tak diakses—optimal tapi sulit diimplementasi dengan tepat.
    * *Optimal*: Teoritis (menggantikan page yang akan paling lama tak diakses), tidak praktis karena memerlukan prediksi masa depan.
    * *Clock (Second Chance)*: Perbaikan LRU yang lebih murah—menggunakan bit referensi dan pointer melingkar.
  * *Thrashing*: Saat sistem terus-menerus melakukan page fault dan swapping, kinerja turun drastis; solusi lewat *working set model* dan pengaturan load multiprogramming.

## 8. Sistem Berkas (File System)

* **Konsep Dasar**:
  Sistem berkas mengatur cara data disimpan dan diorganisasi dalam disk/disk virtual.
* **Abstraksi File**:
  File diakses melalui *file descriptor* atau *file handle*, sistem menyediakan operasi seperti `open`, `read`, `write`, `close`, `seek`, dll.
* **Struktur Direktori**:

  * *Single-Level Directory*: Semua file dalam satu direktori—sederhana tapi tidak scalable.
  * *Two-Level Directory*: Setiap pengguna punya direktori sendiri—meminimalkan konflik nama.
  * *Hierarchical (Tree)*: Struktur pohon dengan sub-direktori (umum di UNIX, Windows).
* **Implementasi File**:

  * *Contiguous Allocation*: File ditempatkan dalam blok yang berurutan—kecepatan baca/tulis tinggi, tapi rentan external fragmentation.
  * *Linked Allocation*: Setiap blok file berisi pointer ke blok berikutnya—tanpa external fragmentation, tapi akses acak lambat.
  * *Indexed Allocation*: Menggunakan blok indeks yang menyimpan daftar semua blok file—menggabungkan kelebihan keduanya, tetapi perlu ruang indeks.
* **Manajemen Ruang Bebas**:

  * *Bit Vector*: Tabel bit menandai blok bebas/terpakai (1 bit per blok).
  * *Linked List*: Daftar blok bebas.
  * *Grouping / Counting*: Teknik optimasi linked list agar traversal lebih cepat.
* **Variasi Sistem Berkas Modern**:

  * *Journaling File System* (mis. ext4, NTFS): Menyimpan catatan transaksi (journal) untuk mempercepat pemulihan setelah crash.
  * *Log-Structured File System*: Tulis semua data dan metadata dalam urutan log, mempercepat penulisan kecil namun memerlukan pengumpulan sampah (garbage collection).

## 9. Manajemen Penyimpanan Sekunder

* **Disk Structure & Penjadwalan**:

  * Komponen disk: *platters*, *tracks*, *sectors*, *cylinder*.
  * *Disk Scheduling Algorithms*:

    * *FCFS*: Pelayanan sesuai urutan permintaan—sederhana tapi jarak head movement bisa bengkak.
    * *SSTF (Shortest Seek Time First)*: Pilih permintaan terdekat—mengurangi jarak, tapi risiko starvation permintaan jauh.
    * *SCAN / Elevator*: Head bergerak satu arah hingga ujung, lalu berbalik—memastikan permintaan terlalu jauh tetap terlayani.
    * *C-SCAN*: Hanya satu arah (setelah mencapai ujung, head lompat ke awal tanpa melayani request) untuk fairness.
* **RAID (Redundant Array of Independent Disks)**:

  * Tingkat-tingkat RAID:

    * *RAID 0*: Striping (tanpa redundansi)—performa tinggi, tapi risiko kehilangan data.
    * *RAID 1*: Mirroring (cermin)—keandalan tinggi, tapi biaya 2×.
    * *RAID 5*: Striping dengan parity tersebar—efisien di kapasitas & keandalan, membaca cepat, menulis lebih lambat karena perhitungan parity.
    * *RAID 6*: Mirip RAID 5, tapi dengan dua blok parity (toleransi dua disk mati).

## 10. Sistem I/O (Input/Output)

* **Hierarki I/O**:
  Perangkat keras (device controllers, bus), *device drivers*, OS (buffering, caching, spooling), user programs.
* **Teknik Dasar**:

  * *Programmed I/O*: CPU secara aktif menunggu (polling) hingga I/O selesai—sederhana, tapi memboroskan CPU.
  * *Interrupt-Driven I/O*: Perangkat akan memberikan interrupt setelah siap, CPU dapat menangani tugas lain selama menunggu.
  * *DMA (Direct Memory Access)*: Controller I/O mampu memindahkan data ke/ dari memori utama langsung tanpa intervensi CPU—efisien untuk transfer blok besar.
* **Driver & Abstraksi**:

  * Driver menampung kode spesifik perangkat, menerjemahkan permintaan OS ke operasi perangkat.
  * *Character Devices* (mis. keyboard, mouse) vs. *Block Devices* (mis. disk).
  * Buffering (penyangga data) dan caching (penyimpanan sementara) meningkatkan kinerja dan mengurangi akses fisik berulang.

## 11. Keamanan dan Proteksi

* **Proteksi (Protection)**:
  Menjamin setiap entitas (proses/user) hanya dapat mengakses data dan sumber daya yang diizinkan.

  * *Access Matrix*: Matriks baris = subjek (user/proses), kolom = objek (file/memory), nilai = hak akses (read, write, execute).
  * Transformasi: *Access List* (per objek, siapa yang punya izin) dan *Capability List* (per subjek, objek apa yang bisa diakses).
* **Keamanan (Security)**:
  – Melindungi sistem dari ancaman internal (mis. pengguna nakal) dan eksternal (virus, hacker).

  * *Keamanan Fisik*: Pengamanan server, media penyimpanan.
  * *Keamanan Jaringan*: Firewall, enkripsi komunikasi (TLS/SSL), IDS/IPS.
  * *Otentikasi & Otorisasi*:

    * Otentikasi: Verifikasi identitas pengguna (password, biometrik, token).
    * Otorisasi: Mengecek hak akses pengguna terhadap resource.
  * *Kriptografi*:

    * Simetris (AES, DES) untuk enkripsi cepat.
    * Asimetris (RSA, ECC) untuk pertukaran kunci dan sertifikat digital.
  * *Keamanan Kernel*:

    * *Trusted Computing Base (TCB)*: Bagian OS yang dipercayai penuh; bug di TCB bisa berdampak besar.
    * *Mode Audit & Logging*: Mencatat aktivitas penting untuk deteksi intrusi dan forensik.

## 12. Studi Kasus Sistem Operasi Nyata

* **UNIX/Linux**:

  * Filosofi: “Everything is a file,” dukungan multitasking, multi-user.
  * Struktur kernel monolitik (Linux) dengan modul yang bisa dimuat dinamis.
  * Komponen utama: *Process Management* (fork/exec, scheduler CFS), *Memory Management* (VM, slab allocator), *VFS* (Virtual File System) untuk mendukung banyak sistem berkas (ext4, XFS), *Device Drivers*, *Networking Stack*.
* **Windows (NT Family)**:

  * Kernel hybrid: gabungan mikro-kernel dan monolitik.
  * *Executive Layer* (menyediakan service API), *Kernel Mode* (penjadwalan, sinkronisasi), *Hardware Abstraction Layer (HAL)*.
  * Sistem Berkas: NTFS dengan journaling, keamanan built‐in (ACL, EFS).
* **Sistem Lain (Android, macOS)**:

  * *Android*: Berbasis Linux Kernel, ditambah layer runtime (ART/Dalvik), framework aplikasi Java/Kotlin, dan middleware untuk manajemen daya & sumber daya mobile.
  * *macOS*: Berbasis XNU (hybrid kernel bergabung FreeBSD dan Mach), menggunakan HFS+ atau APFS sebagai sistem berkas dan menyediakan API Cocoa untuk aplikasi.

## 13. Topik Lanjutan

* **Virtualisasi & Mesin Virtual**:

  * **Hypervisor Tipe 1 (Bare-metal)**: VMware ESXi, Xen—langsung dijalankan di hardware.
  * **Hypervisor Tipe 2 (Hosted)**: VirtualBox, VMware Workstation—dijalankan di atas OS host.
  * *Para‐virtualization* vs. *Full-virtualization* vs. *Containerization* (mis. Docker)—perbedaan dalam isolasi dan overhead.
* **Cloud Computing & OS di Data Center**:

  * OS di cloud harus mendukung skalabilitas horizontal, live migration VM, load balancing, dan high availability.
  * Konsep *Infrastructure as a Service* (IaaS), *Platform as a Service* (PaaS): Contoh implementasi AWS EC2, Google Compute Engine.
* **Sistem Operasi Real-Time**:

  * Real-Time OS (RTOS) menjamin batas waktu (deadlines) untuk tugas kritis (embedded, kontrol industri).
  * *Hard Real-Time* vs *Soft Real-Time*: Hard—gagal memenuhi deadline berarti kegagalan sistem; Soft—toleransi pelanggaran deadline terbatas.
  * Contoh: FreeRTOS, VxWorks. Algoritma penjadwalan khusus (Rate Monotonic, Earliest Deadline First).
* **Sistem Operasi pada Perangkat Mobile & IoT**:

  * Tantangan: Keterbatasan daya, CPU, memori, dan persistensi.
  * Android / iOS menggunakan kernel diadaptasi (Linux di Android, XNU di iOS) dengan optimasi manajemen daya (wakelocks, Doze Mode).
  * Custom RTOS untuk mikrokontroler (Contoh: Zephyr, ARM Mbed OS).
* **Keamanan Tingkat Lanjut & Isolasi**:

  * *Trusted Execution Environment (TEE)* seperti Intel SGX, ARM TrustZone.
  * *Sandboxing* (mis. browser, aplikasi mobile) untuk membatasi akses tanpa izin.

---

## Kesimpulan

*Operating System Concepts* edisi ke-10 membahas **semua aspek fundamental** mulai dari pengantar, struktur, proses & thread, penjadwalan, sinkronisasi, deadlock, manajemen memori, I/O, sistem berkas, keamanan, hingga topik modern seperti virtualisasi dan cloud. Buku ini dirancang untuk:

1. **Mahasiswa**: Memberikan dasar teoritis beserta ilustrasi studi kasus nyata (Linux, Windows).
2. **Insinyur & Profesional IT**: Menjadi referensi dalam merancang atau memahami perilaku OS yang menggerakkan server, desktop, maupun perangkat mobile.

Ringkasan di atas diharapkan memberikan gambaran yang mencakup **semua komponen penting** OS secara terstruktur dan mudah dipahami. Jika masih diperlukan detail lebih lanjut pada bagian tertentu (contoh algoritma spesifik, kode ilustrasi, atau studi kasus mendalam), silakan diinformasikan!
