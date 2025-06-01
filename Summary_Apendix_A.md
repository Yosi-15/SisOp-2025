Nama  : Yosiyanti Cendekia Sari  
NRP   : 3124500059  
Kelas : 1 D3 IT B  
Dosen Pengampu : 

# Summary of Operating System Concepts, 10th Edition (Silberschatz, 2018)
---

### 1. **Introduction to Operating Systems**

* **Definition & Purpose**: An operating system (OS) is a software layer responsible for managing hardware, providing an interface for users and applications, and ensuring secure and efficient program execution.
* **History & Evolution**: Originated from simple batch OS in the 1950s–60s, evolving into time-sharing (multi-user), real-time, distributed, and eventually cloud/virtualized systems in the 21st century.

---

### 2. **Basic OS Structures and Mechanisms**

* **Architectures**:

  * *Monolithic*: All core services (scheduling, memory, I/O) integrated into one large kernel.
  * *Layered*: OS divided into levels—from low-level hardware interaction to high-level application services.
  * *Microkernel*: Only essential functions (e.g., IPC, scheduling) in kernel; others (drivers, file system) in user space.

* **System Calls & APIs**: Applications communicate with the OS via system calls (e.g., `fork()`, `read()`, `write()`), which are processed by the kernel.

* **Execution Modes**: Processes can run in *user mode* (restricted access) or *kernel mode* (full access), switching through interrupts, traps, or system calls.

---

### 3. **Processes and Threads**

* **Process**: Represents a running program with its own PID, memory space (code, data, stack), CPU registers, and states.

* **Process Life-Cycle**:

  1. *New*
  2. *Ready*
  3. *Running*
  4. *Waiting*
  5. *Terminated*

* **Threads**: Lightweight units of execution within a process, sharing memory space. Threads improve concurrency and CPU efficiency, especially in multiprocessor systems.

* **Thread Models**:

  * *User-Level Threads*: Managed in user space; fast context switch but limited CPU utilization.
  * *Kernel-Level Threads*: Managed by kernel; supports multi-core execution but slower switching.
  * *Hybrid Model*: Maps multiple user threads to kernel threads for flexibility.

---

### 4. **CPU Scheduling**

* **Goals**: Maximize throughput, minimize turnaround/waiting time, improve responsiveness.

* **Core Algorithms**:

  * *FCFS*: First-Come, First-Served.
  * *SJF*: Shortest Job First.
  * *Priority Scheduling*: With preemption or not; risks starvation.
  * *Round Robin*: Equal time quantum per process (e.g., 10ms).
  * *Multilevel Queue & Feedback*: Separate queues for I/O-bound and CPU-bound processes.

* **Metrics**:

  * *Turnaround Time*
  * *Waiting Time*
  * *Response Time*
  * *CPU Utilization*

---

### 5. **Process Synchronization**

* **Critical Section Problem**: Multiple processes/threads accessing shared resources need *mutual exclusion*.

* **Solution Conditions**:

  1. *Mutual Exclusion*
  2. *Progress*
  3. *Bounded Waiting*

* **Mechanisms**:

  * *Peterson’s Algorithm*: For two processes.
  * *Hardware Locks*: Test-and-Set, Compare-and-Swap.
  * *Semaphores*: Integer-based, supporting `wait()` and `signal()` for mutual exclusion/synchronization.
  * *Monitors*: High-level abstraction with condition variables (`wait`/`signal`).

---

### 6. **Deadlock**

* **Definition**: A situation where two or more processes wait on each other indefinitely.

* **Coffman Conditions**:

  1. Mutual Exclusion
  2. Hold and Wait
  3. No Preemption
  4. Circular Wait

* **Handling**:

  * *Prevention*: Break one condition.
  * *Avoidance*: Use Banker’s Algorithm.
  * *Detection & Recovery*: Use resource allocation graph, abort or preempt processes.

---

### 7. **Memory Management**

* **Goal**: Efficient RAM use, process isolation, virtual memory support.

* **Contiguous Allocation**:

  * *Fixed Partitioning*
  * *Dynamic Partitioning*
  * Fit strategies: First Fit, Best Fit, Worst Fit

* **Paging**:

  * Divides memory into *frames* and virtual memory into *pages*.
  * Uses page tables and TLB for address translation.

* **Segmentation**: Logical segments (code, data, stack), each with base and limit.

* **Virtual Memory**:

  * Partial program loaded into RAM, rest on disk.
  * *Demand Paging*: Loads page on access.
  * *Page Replacement Algorithms*: FIFO, LRU, Optimal, Clock.
  * *Thrashing*: Excessive swapping reduces performance.

---

### 8. **File System**

* **Basic Concept**: Manages data storage and organization on disk.

* **File Abstraction**: Access via file descriptors; operations include `open`, `read`, `write`, `close`, `seek`.

* **Directory Structures**:

  * Single-Level, Two-Level, Hierarchical (tree)

* **File Allocation**:

  * *Contiguous*, *Linked*, *Indexed*

* **Free Space Management**:

  * Bit Vectors, Linked Lists, Grouping

* **Modern Filesystems**:

  * *Journaling*: (e.g., ext4, NTFS)
  * *Log-Structured*: Log-like writes, garbage collection needed

---

### 9. **Secondary Storage Management**

* **Disk Structure**: Platters, tracks, sectors, cylinders

* **Disk Scheduling Algorithms**:

  * FCFS, SSTF, SCAN, C-SCAN

* **RAID Levels**:

  * *RAID 0*: Striping (no redundancy)
  * *RAID 1*: Mirroring
  * *RAID 5/6*: Striping with parity (fault tolerance)

---

### 10. **I/O Systems**

* **I/O Stack**: Devices → Drivers → OS (buffering, spooling) → User programs

* **Techniques**:

  * *Programmed I/O*
  * *Interrupt-Driven I/O*
  * *DMA (Direct Memory Access)*

* **Device Types**: Character vs. Block devices

* **Optimizations**: Buffering, caching

---

### 11. **Security and Protection**

* **Protection**: Ensures processes/users only access permitted resources.

  * *Access Matrix*, *Access Lists*, *Capability Lists*

* **Security**: Protects system from internal and external threats.

  * *Physical Security*
  * *Network Security*: Firewalls, encryption, IDS/IPS
  * *Authentication & Authorization*: Passwords, biometrics, tokens
  * *Cryptography*: Symmetric (AES), Asymmetric (RSA, ECC)
  * *Kernel Security*: TCB (Trusted Computing Base), auditing/logging

---

### 12. **Case Studies of Real Operating Systems**

* **UNIX/Linux**:

  * Philosophy: "Everything is a file"
  * Monolithic kernel with dynamically loaded modules
  * Features: Process management, VFS, ext4/XFS, networking

* **Windows NT**:

  * Hybrid kernel
  * Components: Executive Layer, Kernel Mode, HAL
  * NTFS with journaling and security features (ACL, EFS)

* **Others (Android, macOS)**:

  * *Android*: Linux-based, ART runtime, Java/Kotlin framework
  * *macOS*: XNU kernel (FreeBSD + Mach), HFS+/APFS, Cocoa APIs

---

### 13. **Advanced Topics**

* **Virtualization**:

  * Type 1 (Bare-metal): VMware ESXi, Xen
  * Type 2 (Hosted): VirtualBox, VMware Workstation
  * Full, para-virtualization, containers (e.g., Docker)

* **Cloud OS**:

  * Must support scaling, VM migration, fault tolerance
  * Models: IaaS, PaaS (e.g., AWS EC2, GCP)

* **Real-Time OS**:

  * *Hard vs Soft Real-Time*
  * Examples: FreeRTOS, VxWorks
  * Scheduling: Rate Monotonic, Earliest Deadline First

* **Mobile & IoT OS**:

  * Constraints: power, CPU, memory
  * Android/iOS use adapted kernels with power management
  * Custom RTOS for microcontrollers: Zephyr, ARM Mbed OS

* **Advanced Security**:

  * *Trusted Execution Environment (TEE)*: Intel SGX, ARM TrustZone
  * *Sandboxing*: Browser, mobile apps

---

### **Conclusion**

*Operating System Concepts* (10th Edition) explores all essential areas of operating systems—from foundational theories to modern implementations.





# Operating System Concepts, 10th Edition (Silberschatz, 2018)
---

## 1. Pendahuluan Sistem Operasi

* **Definisi & Tujuan**: Sistem operasi (OS) adalah lapisan perangkat lunak yang bertugas mengelola perangkat keras, menyediakan antarmuka bagi pengguna dan aplikasi, serta menjamin keamanan dan efisiensi eksekusi program.
* **Sejarah & Evolusi**: Berawal dari OS sederhana pada mesin batch di era 1950–1960, berkembang ke sistem time-sharing (multi‐user), real-time, terdistribusi, dan lalu ke virtualisasi/cloud di abad 21.

---
## 2. Struktur dan Mekanisme Dasar OS

* **Arsitektur Monolitik vs. Berlapis vs. Mikro-kernel**:

  * *Monolitik*: Semua layanan inti (penjadwalan, manajemen memori, I/O) terintegrasi dalam satu kernel besar.
  * *Berlapis*: OS dipecah ke dalam beberapa level—tingkat paling bawah berinteraksi langsung dengan hardware, tingkat tertinggi menyediakan layanan kepada aplikasi.
  * *Mikro-kernel*: Hanya fungsi minimal (seperti IPC dan penjadwalan) di kernel, sisanya (driver, sistem berkas) berjalan di user space.
* **Sistem Call & API**:
  Aplikasi berinteraksi dengan kernel lewat sistem call (misalnya `fork()`, `read()`, `write()`). Kernel memvalidasi argumen, memproses permintaan, lalu mengembalikan hasil/penyebab error.
* **Mode Eksekusi**:
  Proses dapat berjalan dalam *user mode* (akses terbatas) atau *kernel mode* (akses penuh). Berpindah terjadi saat terjadi interrupt, trap, atau sistem call.

---
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

---
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

---
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

---
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

---
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

---
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

---
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

---
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

---
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

---
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

---
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

*Operating System Concepts* edisi ke-10 membahas **semua aspek fundamental** mulai dari pengantar, struktur, proses & thread, penjadwalan, sinkronisasi, deadlock, manajemen memori, I/O, sistem berkas, keamanan, hingga topik modern seperti virtualisasi dan cloud. 
