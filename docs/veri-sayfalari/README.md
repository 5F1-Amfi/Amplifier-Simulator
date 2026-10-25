# Tüp veri sayfaları

Model kartlarındaki sınır değerlerinin kaynağı. Hepsi üreticinin özgün taraması;
Frank Philipse'nin arşivinden (https://frank.pocnet.net) 25.10.2026'da indirildi.

Eldeki tüplerin kendi veri sayfası değildir. Sınır değerleri tüp tipine aittir
(JEDEC / Pro Electron kaydı): aynı tip adını taşıyan her üretici aynı sınırları sağlar.
Eğriler ise "ortalama tüp"ü anlatır; eldeki tüp bundan sapabilir.

| Dosya | Tüp | Üretici, belge | Sınır sistemi | Özgün bağlantı |
|---|---|---|---|---|
| `6V6GT_GE_ET-T914_1955.pdf` | 6V6GT | General Electric ET-T914, 3-55 | design-center | https://frank.pocnet.net/sheets/093/6/6V6GT.pdf |
| `6V6GTA_RCA_1962.pdf` | 6V6GTA | RCA, 1-62 | design-maximum | https://frank.pocnet.net/sheets/049/6/6V6GTA.pdf |
| `6V6GT_RCA_1962.pdf` | 6V6 / 6V6GT | RCA, 1-62: "6V6GT, 6V6GTA ile aynıdır; yalnız ısınma süresi farklı" | — | https://frank.pocnet.net/sheets/049/6/6V6.pdf |
| `12AX7_GE_ET-T509B_1953.pdf` | 12AX7 (= ECC83) | General Electric ET-T509B, 6-53 | design-center | https://frank.pocnet.net/sheets/093/1/12AX7.pdf |
| `5Y3GT_RCA_1961.pdf` | 5Y3GT | RCA, 7-61 | design-center | https://frank.pocnet.net/sheets/049/5/5Y3GT.pdf |

## Alınan değerler

**6V6GT** (gerilimler katoda göre)

| | Design-center (GE) | Design-maximum (RCA) |
|---|---|---|
| Plaka gerilimi | 315 V | 350 V |
| Screen gerilimi | 285 V | 315 V |
| Plaka gücü | 12 W | 14 W |
| Screen gücü | 2,0 W | 2,2 W |
| Heater–katot (tepe) | 200 V | 200 V |
| Grid devresi direnci, katot bias | 0,5 MΩ | 0,5 MΩ |
| Heater | 6,3 V / 0,45 A | 6,3 V / 0,45 A ± %6 |

**12AX7 / ECC83** (GE, design-center, her bölüm): plaka 300 V, plaka gücü 1,0 W,
heater–katot 180 V, heater 6,3 V / 0,3 A (paralel). Soğuk plaka gerilimi sınırı verilmemiş.

**5Y3GT** (RCA, design-center): ters tepe gerilimi 1400 V; kararlı tepe plaka akımı
440 mA / plaka; geçici tepe 2,5 A / plaka; kapasitör girişli filtrede plaka başına en çok
350 VRMS ve 125 mA DC çıkış (tipik çalışma, 20 µF, 50 Ω); filaman 5 V / 2 A.
Grafikten okunan, yaklaşık: 320 VRMS'de izin verilen DC çıkış ≈ 128 mA (Rating Chart I),
en küçük kaynak direnci ≈ 34 Ω / plaka (Rating Chart III).

## Sınır sistemleri

- **Design-maximum:** mutlak üst sınır. Şebeke dalgalanması ve parça toleransı dahil aşılmamalı.
- **Design-center:** nominal şebekede tasarım değeri; ≈ %10 şebeke yükselmesi payını içinde taşır.

Simülatör bu ikisini güvenlik payı olarak kullanır (karar K-17): design-center üstü uyarı,
design-maximum üstü hata. Yalnız design-center bilinen tüplerde design-center üstü hatadır.
