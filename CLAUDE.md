# 5F1 Amfi Simülatörü — asistan yönergesi

Türkçe konuş. Kullanıcı elektrik-elektronik mühendisliği öğrencisi; devreyi
biliyor, kodu öğreniyor. Jargonu sadeleştirme, kodu açıkla.

## Proje

5F1 tabanlı modifiye tüplü gitar amfisinin (12AX7 + 6V6GT + 5Y3GT, single-ended)
**çevrimdışı simülatörü**. Saf HTML/CSS/JS — derleme adımı, paket yöneticisi ve
bağımlılık yok. `index.html` doğrudan tarayıcıda açılır.

Ayrıntı: `README.md` (kullanım ve sayfalar), `ARCHITECTURE.md` (modüller ve veri
akışı), `docs/MODEL_KARTLARI.md` (tüp modelleri ve sınırları),
`docs/KARAR_GUNLUGU.md` (hangi kararın neden verildiği).

Repo `5F1-Amfi` organizasyonuna ait; iki Owner var: `osmanevski` (Osman Çekilmez)
ve `gokturkbabaoglu` (Afşın Göktürk Babaoğlu).

## Değişmez kurallar

- **Bağımlılık ekleme.** npm paketi, CDN linki, build adımı yok. Fontlar
  `assets/fonts/` içinde gömülü ve öyle kalmalı; simülatör internetsiz çalışır.
- **Elektrik modeline dokunduysan doğrula.** `node tests/run-tests.js` çalıştır,
  sonra `dogrulama.html` sayfasını tarayıcıda aç. Sayılar tutmadan "çalışıyor"
  deme. Kabul testleri `docs/DOGRULAMA.md` içinde tanımlı.
- **Sayı uydurma.** Çalışma noktası, gerilim ve bileşen değerleri girdi
  belgelerinden geliyor; o belgeler repo'da değil. Bilmediğin bir değeri tahmin
  etmek yerine sor.
- **Kararların gerekçesi yazılı.** `docs/KARAR_GUNLUGU.md` içindeki bir kararı
  tersine çeviriyorsan önce oradaki gerekçeyi oku; değiştirdiysen günlüğe yeni
  satır ekle.
- **Geçmişi yeniden yazma.** `--force` push yok, `main` üstünde rebase yok —
  repo'da ikinci bir sahip var.

## Çalışma biçimi

```bash
node tests/run-tests.js          # kabul testleri
./start_server.command           # yerel sunucu, http://localhost:8090
```

`main`'e doğrudan basmak yerine branch açıp PR at; iki sahip aynı dal üstünde
çalışıyor. Merge'den sonra yeni sürümü `rev-a-YYYY-AA-GG` etiketiyle işaretle ve
`DEGISIKLIKLER.md`'ye o etiketin bölümünü ekle.

## Yayın

Her push **otomatik yayına girer**: https://5f1-amfi.github.io/Amplifier-Simulator/
`main`'e giren hata canlıya çıkar — bunu push etmeden önce söyle.
