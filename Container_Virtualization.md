## Virtualisasi Container

### Apa itu Virtualisasi Container?

**Virtualisasi container** adalah metode untuk menjalankan beberapa aplikasi secara **terpisah (terisolasi)** dalam satu sistem operasi (OS) yang sama.
Setiap **container** membawa aplikasi dan semua hal yang dibutuhkannya (seperti library, konfigurasi, dll), tetapi **tidak perlu OS sendiri** seperti virtual machine. Container **berbagi kernel OS host**, sehingga lebih ringan dan cepat.

---

### Cara Kerja

Container menggunakan fitur dari kernel sistem operasi (biasanya Linux), seperti:

* **Namespaces** → Mengisolasi proses, pengguna, jaringan, dan file antar container.
* **cgroups (control groups)** → Mengatur berapa banyak sumber daya (CPU, memori) yang boleh digunakan oleh container.

Karena tidak memerlukan OS sendiri, container bisa dijalankan dalam hitungan detik dan menggunakan sumber daya yang minimal.

---

### Keunggulan Container

* **Cepat**: Waktu startup hanya dalam beberapa detik
* **Ringan**: Ukurannya kecil, tanpa OS tambahan
* **Isolasi**: Aplikasi di dalam container tidak saling mempengaruhi
* **Portabel**: Bisa dijalankan di mana saja (laptop, server, cloud)

---

### Container Vs Virtual Machine

| Aspek           | Container                    | Virtual Machine                  |
| --------------- | ---------------------------- | -------------------------------- |
| Kernel OS       | Berbagi dengan OS host       | Memiliki OS sendiri              |
| Waktu Booting   | Sangat cepat (detik)         | Lebih lama (menit)               |
| Ukuran          | Kecil (MB)                   | Besar (GB)                       |
| Isolasi         | Proses-level                 | Level perangkat keras            |
| Penggunaan Umum | Microservices, cloud, DevOps | Menjalankan OS berbeda, simulasi |

---

### Alat yang Sering Digunakan

* **Docker**: Paling populer untuk membuat dan menjalankan container
* **Podman**: Alternatif Docker tanpa perlu root
* **Kubernetes**: Untuk mengatur banyak container dalam skala besar
* **containerd** dan **runc**: Komponen inti untuk menjalankan container

---

### Contoh Penggunaan

* Menjalankan web server secara terpisah tanpa bentrok port
* Menguji aplikasi baru tanpa mengganggu sistem utama
* CI/CD otomatis dalam DevOps
* Deploy aplikasi berbasis microservices di cloud

---

### Kesimpulan

**Virtualisasi container** memungkinkan aplikasi berjalan secara efisien, terisolasi, dan portabel tanpa overhead besar seperti virtual machine.
Ini adalah teknologi kunci dalam pengembangan perangkat lunak modern, terutama di era **cloud computing** dan **DevOps**.
