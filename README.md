# ESP32-S3 Smart IoT Monitor

Sistem monitoring jarak berbasis **ESP32-S3** dan sensor ultrasonik **HC-SR04**, dilengkapi **captive portal** untuk konfigurasi WiFi tanpa perlu mengubah kode.

## Fitur

- Captive portal (mode Access Point) untuk memilih dan menyimpan WiFi
- Kredensial WiFi disimpan permanen di flash (`Preferences` / NVS)
- Dashboard web real-time (update tiap 500 ms) dengan endpoint JSON `/data`
- Filter median 5 sampel agar pembacaan jarak stabil
- Status kondisi: **AMAN** (> 30 cm), **WASPADA** (10-30 cm), **BAHAYA** (< 10 cm)
- Tahan tombol **BOOT 5 detik** untuk reset konfigurasi WiFi
- LED indikator: menyala saat terhubung ke WiFi

## Struktur Repositori

```
esp32s3-smart-iot-monitor/
├── README.md
├── LICENSE
├── .gitignore
├── firmware/
│   └── esp32s3_smart_iot/
│       └── esp32s3_smart_iot.ino    # kode sumber utama
├── wiring/
│   ├── wiring.svg                   # diagram rangkaian
│   └── pin-mapping.md               # tabel pin + rangkaian pembagi tegangan
├── docs/
│   ├── setup-guide.md               # instalasi & upload
│   ├── cara-kerja.md                # alur sistem & API
│   └── troubleshooting.md
└── media/
    ├── photos/                      # foto perangkat/rangkaian
    ├── demo/                        # video/GIF demo
    └── screenshots/                 # tangkapan layar portal & dashboard
```

## Perangkat Keras

| Komponen | Jumlah |
|---|---|
| ESP32-S3 DevKit | 1 |
| Sensor HC-SR04 | 1 |
| Resistor 1 kΩ dan 2 kΩ (pembagi tegangan ECHO) | 1 + 1 |
| LED + resistor 220 Ω (opsional, jika LED onboard tidak dipakai) | 1 |
| Kabel jumper & breadboard | secukupnya |

## Pin

| Fungsi | GPIO |
|---|---|
| TRIG | 5 |
| ECHO | 6 (lewat pembagi tegangan) |
| LED | 2 |
| BOOT (reset WiFi) | 0 |

Detail: [wiring/pin-mapping.md](wiring/pin-mapping.md)

## Cara Pakai Singkat

1. Rangkai sesuai [wiring](wiring/pin-mapping.md), upload `firmware/esp32s3_smart_iot/esp32s3_smart_iot.ino`.
2. Sambungkan HP ke WiFi **ESP32-S3** (password `12345678`), portal terbuka otomatis (atau buka `192.168.4.1`).
3. Pilih WiFi rumah, isi password, tekan **Hubungkan**.
4. Buka IP yang tampil di Serial Monitor (115200 baud) untuk melihat dashboard.

Panduan lengkap: [docs/setup-guide.md](docs/setup-guide.md)

## Demo

Letakkan foto/video di folder `media/` lalu tampilkan di sini, contoh:

```markdown
![Dashboard](media/screenshots/dashboard.png)
```

## Lisensi

MIT, lihat [LICENSE](LICENSE).
