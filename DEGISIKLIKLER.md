# Değişiklik dökümü

Her bölüm bir sürüm etiketine (git tag) karşılık gelir; en yenisi en üstte. Bir sürüme dönmek ya da
indirmek için: GitHub → Tags. Kararların gerekçesi `docs/KARAR_GUNLUGU.md`, test sonuçları
`docs/DOGRULAMA.md` içindedir. "Devre kimliği" devre tanımı değişince değişir; aynı kimlik aynı
simülasyon sonucunu verir.

## `rev-a-2026-10-25b` · 25.10.2026 · devre kimliği `2c2e1b56`

PR #3.

- **K-18 · Bright / Dark tek anahtar.** İki ayrı SPST anahtar (S3 Bright, S4 Dark) yerine tek
  SPDT ON-OFF-ON: BRIGHT / NORMAL / DARK. Ortak uç volume potunun wiper'ı; C11 wiper ile VR1 giriş
  ucu arasında, C12 wiper ile toprak arasında. S4 referansı kaldırıldı, BOM'da bir anahtar azaldı.
- Ses aynı: 5 kHz, volume %30'da Bright +5,25 dB, Dark −16,75 dB (önceki düzenle birebir).
  "İkisi birden" konumu kalktı.
- Arayüz: ön panelde üç konumlu düğme; şemada tek anahtarın iki kontağı ve mekanik bağlantı çizgisi.
- Eski ayar dosyaları içe aktarılırken dönüştürülür; Bright ve Dark birlikte açıksa reddedilir.
- Testler: EL-06 üç konuma, UI-01 24 anahtar kombinasyonuna güncellendi. 24 geçti · 0 kaldı.

## `rev-a-2026-10-25` · 25.10.2026 · devre kimliği `6a14dc7a`

PR #2.

- **K-02 · Tüp kimlikleri (KISMEN).** Baskılardan kaydedildi: V1 "ECC83" (markasız, emisyon %100),
  V2 Hitachi 6V6-GT (Japan), V3 "Ultaon" 5Y3GT (silik "11gr", emisyon %95). Bileşenlere üretici
  alanı eklendi; BOM ve bileşen paneli gösteriyor. Açık kalan: eldeki tüplerin çalışma noktası ölçümü.
- **Tüp veri sayfaları.** `docs/veri-sayfalari/` eklendi: GE 6V6-GT, RCA 6V6GTA / 6V6GT, GE 12AX7,
  RCA 5Y3GT özgün taramaları ve kaynak özeti. JJ referansları kaldırıldı; 6V6 heater 0,5 → 0,45 A.
- **K-17 · Güvenlik payı (yeni karar).** Tüp sınırlarında design-center üstü uyarı, design-maximum
  üstü hata; gerilimler katoda göre. 12AX7 ve 5Y3 denetimleri eklendi.
  Bulgu: 6V6 design-center'ın üstünde, design-max'ın altında (Pa ≈ 12,2 W; 12 · 14 W).
- **K-12 · Bleeder takılı.** R16 = 220 kΩ / 2 W, B+1 → toprak. Kapatıldıktan 40 s sonra B+1
  ≈ 444 V yerine ≈ 3 V. "Bleeder kopuk" arıza senaryosu oldu. Devre kimliği bu değişiklikle değişti.
- **K-14 · Volume potu.** Eldeki işaretsiz 1 MΩ pot kullanılır; taper ölçülmedi, simülatör lineer varsayar.
- **K-01 · B+ filtre zinciri.** Seri zincir kararlaştırıldı (P1 s.11, özgün 5F1 düzeni).
- Şemada kapanan kararlar artık "açık karar" üçgeniyle işaretlenmiyor.

## `rev-a-2026-10-01` · ilk sürüm · devre kimliği `4bdeedb1`

- 01.10.2026: 5F1 Amp Lab Simulator ilk sürüm (Rev A, profil DENEYSEL-01).
- 22.10.2026: depo düzenlemeleri (asistan yönergesi `CLAUDE.md`, README düzeltmesi, PR #1); devre değişmedi.
