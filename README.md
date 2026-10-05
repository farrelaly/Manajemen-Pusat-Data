# Tugas Manajemen Pusat Data: Enterprise Server Provisioning, Observability, & Remote Administration

**Nama:** Ahmad Farrel Aly  
**NIM:** 09011282328045  
**Kelas:** SK7  
**Mata Kuliah:** Manajemen Pusat Data  
**Dosen Pengampu:** Adi Hermansyah, M.T.

---

## Deskripsi Proyek
Proyek ini merupakan persiapan infrastruktur *Enterprise Data Center* berbasis virtualisasi. Fokus utama pada tahap ini adalah melakukan *provisioning* server mandiri (*Standalone Server*) menggunakan arsitektur *LXC Container*, pengaktifan layanan *Database* & *Web Server*, implementasi sistem pemantauan (*Observability*), serta akses administrasi jarak jauh (*Remote SSH*).

## Tech Stack & Topology
- **Hypervisor:** Proxmox VE 9.2.21 (Berjalan di atas VMware)
- **Container Environment:** LXC (Linux Container)
- **Base OS:** AlmaLinux 10 (Purple Lion) x86_64
- **Web & Database Tier:** Nginx, MariaDB
- **Observability Tier:** Node Exporter, Prometheus, Grafana
- **Remote Protocol:** OpenSSH
- **Network Topology:** Direct Bridged to Host LAN

## Langkah Implementasi

### 1. Local DNS Mapping & Web Server Deployment
Instalasi web server menggunakan **Nginx** dipadukan dengan **MariaDB** untuk persiapan *database*. Mensimulasikan akses nama domain layaknya *Data Center* komersial dengan melakukan pemetaan DNS lokal (*Local Host Mapping*) pada mesin klien (*Windows*) agar IP server merespons domain khusus: `farrel-datacenter.com`.

<img width="942" height="434" alt="image" src="https://github.com/user-attachments/assets/10923aa7-a423-452d-a450-8b4c64dac550" />


### 2. NOC Monitoring & Observability
Untuk memantau *Service Level Agreement* (SLA) dan kesehatan server, dipasang agen telemetri **Node Exporter** di dalam AlmaLinux. Data metrik ditarik menggunakan *Time-Series Database* **Prometheus**, lalu divisualisasikan secara *real-time* di **Grafana** layaknya layar pantau *Network Operation Center* (NOC).

<img width="950" height="437" alt="image" src="https://github.com/user-attachments/assets/8fdb1d9f-0c75-48c4-8a0e-831e48ad1ad2" />


### 3. Remote Administration (SSH)
Mengaktifkan dan mengamankan layanan `sshd` di AlmaLinux untuk memungkinkan administrasi server jarak jauh. Akses dienkripsi dan dilakukan menggunakan *native OpenSSH client* langsung dari mesin Windows.

<img width="1350" height="767" alt="image" src="https://github.com/user-attachments/assets/787a9cc5-01fe-4608-9866-c957ae9000fd" />

---
