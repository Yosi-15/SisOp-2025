Nama  : Yosiyanti Cendekia Sari  
NRP   : 3124500059  
Kelas : D3 IT B  
Dosen Pengajar : Dr Ferry Astika Saputra ST, M.Sc

## Container Virtualization

### What is Container Virtualization?

**Container virtualization** is a method used to run multiple applications **separately (isolated)** on the same operating system (OS).
Each **container** includes the application and all the dependencies it needs (such as libraries, configurations, etc.), but **does not require its own operating system** like a virtual machine. Containers **share the host OS kernel**, making them lightweight and fast.

---

### How It Works

Containers use features provided by the host OS kernel (typically Linux), such as:

* **Namespaces** → Isolate processes, users, networks, and files between containers.
* **cgroups (control groups)** → Manage how much CPU, memory, and I/O each container can use.

Because containers don’t run a full OS, they start up in seconds and use minimal system resources.

---

### Advantages of Containers

* **Fast**: Startup time is only a few seconds
* **Lightweight**: Small in size, no full OS included
* **Isolated**: Applications in different containers do not interfere
* **Portable**: Can run anywhere (laptops, servers, cloud)

---

### Container vs Virtual Machine

| Aspect       | Container                    | Virtual Machine                  |
| ------------ | ---------------------------- | -------------------------------- |
| OS Kernel    | Shared with host OS          | Has its own OS                   |
| Boot Time    | Very fast (seconds)          | Slower (minutes)                 |
| Size         | Small (MBs)                  | Large (GBs)                      |
| Isolation    | Process-level                | Hardware-level                   |
| Common Usage | Microservices, cloud, DevOps | Running different OS, simulation |

---

### Common Tools

* **Docker**: The most popular tool for building and running containers
* **Podman**: Docker alternative that works without root
* **Kubernetes**: Manages large-scale container deployments
* **containerd** and **runc**: Core components used to run containers behind the scenes

---

### Example Use Cases

* Running separate web servers without port conflicts
* Testing new apps without affecting the main system
* Automated CI/CD in DevOps pipelines
* Deploying microservices-based applications in the cloud

---

### Conclusion

**Container virtualization** allows applications to run efficiently, in isolated environments, and with minimal overhead compared to traditional virtual machines.
It is a key technology in modern software development, especially in the era of **cloud computing** and **DevOps**.

<br/>
<br/>
<br/>
<br/>
<br/>

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
Ini merupakan teknologi kunci dalam pengembangan perangkat lunak modern, terutama di era **cloud computing** dan **DevOps**.
