# Cara Kerja Sistem

## Alur boot

```
Boot
 └─ Ada SSID tersimpan?
     ├─ Tidak ─► Mode Access Point + Captive Portal
     └─ Ya ───► Coba konek WiFi (maks 20 detik)
                 ├─ Berhasil ─► Mode Station + Dashboard + sensor aktif
                 └─ Gagal ────► Mode Access Point + Captive Portal
```

Sensor HC-SR04 hanya dibaca saat mode Station (WiFi terhubung).

## Pembacaan sensor

- Pulsa TRIG 10 µs, ECHO diukur dengan `pulseIn` (timeout 30 ms)
- Jarak = durasi × 0,0343 / 2 (cm)
- Nilai valid: 2-400 cm, selain itu dianggap tidak terdeteksi
- Filter median dari 5 sampel, interval pembacaan 500 ms

## Status

| Jarak | Status | Warna |
|---|---|---|
| tidak terdeteksi | Tidak Terdeteksi | gray |
| < 10 cm | BAHAYA | red |
| 10-30 cm | WASPADA | orange |
| > 30 cm | AMAN | green |

## Endpoint

| Mode | Method | Path | Fungsi |
|---|---|---|---|
| AP | GET | `/` | halaman setup WiFi |
| AP | POST | `/save` | simpan SSID & password |
| AP | GET | `/generate_204`, `/hotspot-detect.html`, `/connecttest.txt`, `/redirect` | deteksi captive portal OS |
| Station | GET | `/`, `/dashboard` | dashboard |
| Station | GET | `/data` | data sensor JSON |

Contoh respons `/data`:

```json
{"distance":23.4,"status":"WASPADA","color":"orange"}
```
