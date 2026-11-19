# Troubleshooting

| Masalah | Penyebab umum | Solusi |
|---|---|---|
| Jarak selalu "Tidak Terdeteksi" | wiring TRIG/ECHO salah, VCC bukan 5 V | cek pin 5 & 6, pastikan VCC 5 V dan GND bersama |
| Pembacaan tidak stabil | sinyal ECHO tidak melalui pembagi tegangan, kabel longgar | pasang pembagi 1 kΩ/2 kΩ, rapikan kabel |
| Portal tidak terbuka otomatis | OS/browser tidak mendeteksi captive portal | buka manual `http://192.168.4.1` |
| Gagal konek WiFi | password salah / sinyal lemah / WiFi 5 GHz | ESP32-S3 hanya mendukung 2,4 GHz; simpan ulang |
| Ingin ganti WiFi | | tahan BOOT 5 detik |
| Dashboard tidak terbuka | beda jaringan | pastikan HP/laptop satu WiFi dengan ESP32-S3 |
| Upload gagal | mode boot / port salah | tahan BOOT sambil menekan RESET, pilih port yang benar |
