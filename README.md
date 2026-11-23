# Sistem Monitoring & Kontrol IoT Berbasis REST API Node-RED

Proyek praktikum untuk membangun sistem monitoring suhu & kelembaban serta kontrol perangkat IoT menggunakan protokol **MQTT**, **Node-RED** sebagai backend REST API, dan **Custom Web Dashboard (HTML/CSS/JS)**.

## Identitas Mahasiswa
- **Nama:** [Isi Nama Anda]
- **NIM:** [Isi NIM Anda]
- **Mata Kuliah:** Pemrograman Internet of Things

---

## Arsitektur & Alur Sistem
1. **Publisher (`simulasi_esp32.py`)**: Mengirim data simulasi `suhu` dan `kelembaban` dalam format JSON ke topik MQTT `iot/sensor` setiap 3 detik.
2. **MQTT Broker (Mosquitto)**: Berjalan di `localhost:1883` sebagai perantara pesan antara simulator ESP32 dan Node-RED.
3. **Backend REST API (`flows.json` di Node-RED)**:
   - Melakukan subscribe ke `iot/sensor` dan menyimpan data terbaru serta riwayat data.
   - Menyediakan endpoint HTTP REST API untuk diakses oleh dashboard.
   - Meneruskan perintah kontrol dari API ke topik MQTT `iot/kontrol`.
4. **Web Dashboard (`dashboard.html`)**: Menampilkan nilai sensor secara berkala, tabel riwayat data, log aktivitas, dan tombol kontrol lampu.

---

## Struktur File
```text
├── simulasi_esp32.py   # Simulator ESP32 (MQTT Publisher)
├── flows.json          # Export flow Node-RED (Backend REST API)
├── dashboard.html      # Antarmuka Web Dashboard
└── README.md           # Dokumentasi proyek
