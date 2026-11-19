# Panduan Setup

## 1. Persiapan Arduino IDE

1. Instal Arduino IDE 2.x.
2. Tambahkan board **esp32 by Espressif Systems** lewat *Boards Manager*.
3. Pilih board: **ESP32S3 Dev Module**.
4. Library `WiFi`, `WebServer`, `Preferences`, `DNSServer` sudah termasuk dalam paket board ESP32, tidak perlu instal tambahan.

## 2. Upload

1. Buka `firmware/esp32s3_smart_iot/esp32s3_smart_iot.ino`.
2. Pilih port yang sesuai, lalu **Upload**.
3. Buka *Serial Monitor* dengan baud rate **115200**.

> Nama folder sketch harus sama dengan nama file `.ino` (sudah sesuai).

## 3. Konfigurasi WiFi

1. Sambungkan HP/laptop ke WiFi `ESP32-S3`, password `12345678`.
2. Portal terbuka otomatis; jika tidak, buka `http://192.168.4.1`.
3. Pilih jaringan, isi password, tekan **HUBUNGKAN WIFI**.
4. ESP32-S3 restart dan mencoba terhubung (batas 20 detik). Jika gagal, otomatis kembali ke mode portal.

## 4. Dashboard

Setelah terhubung, IP muncul di Serial Monitor. Buka `http://<IP-ESP32>/` di browser pada jaringan yang sama.

## 5. Reset WiFi

Tahan tombol **BOOT** selama 5 detik. Konfigurasi dihapus dan perangkat restart ke mode portal.

## Mengubah nama/password Access Point

Edit di bagian atas file `.ino`:

```cpp
const char* apSSID = "ESP32-S3";
const char* apPassword = "12345678";
```
