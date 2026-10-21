# Başla buradan — yapay zekâ asistanına yönerge

> Bu dosya Göktürk'ün asistanı (Claude) içindir. Göktürk yapay zekâ araçlarında
> yeni; aşağıdaki kurulum adımlarını **onun yerine sen yap**, sonra bu dosyayı sil.
> Dosyayı Osman'ın asistanı yazdı. Kalıcı belge değildir.

## Bağlam

Bu repo bir **5F1 modifiye tüplü gitar amfisi simülatörü**. Teknik ayrıntı
`README.md` ve `ARCHITECTURE.md` içinde; önce onları oku.

Sahiplik: repo `5F1-Amfi` organizasyonuna ait ve **iki Owner** var —
Osman Çekilmez (`osmanevski`) ve Afşın Göktürk Babaoğlu (`gokturkbabaoglu`).
İkisi de eşit yetkili; repo kimsenin kişisel hesabı altında değil.

## Yapılacaklar

Adımlara geçmeden **Göktürk'e ne yapacağını söyle ve onayını al** — bunlar onun
GitHub hesabı üstünde işlem yapar.

### 1. Kimliği doğrula

```bash
gh auth status
```

Çıktı `gokturkbabaoglu` demiyorsa dur. Göktürk'ün `gh auth login` ile kendi
hesabıyla girmesi gerekir; onun yerine giriş yapma, parola ve kod isteme.

### 2. Organizasyon davetini kabul et

Göktürk'e Owner rolüyle bekleyen bir davet var:

```bash
gh api --method PATCH user/memberships/orgs/5F1-Amfi -f state=active \
  --jq '{state, role}'
```

Beklenen çıktı: `{"state": "active", "role": "admin"}` — API'de `admin`,
arayüzde **Owner** demektir.

Yetki hatası alırsan: `gh auth refresh -h github.com -s write:org` (bunu
Göktürk'ün kendisi çalıştırmalı, tarayıcıda onay ister), sonra komutu tekrarla.

### 3. Üyeliği herkese açık yap

Varsayılan olarak üyelik gizlidir ve org Göktürk'ün profilinde **görünmez**.
Görünür olması bu işin asıl amacıydı:

```bash
gh api --method PUT orgs/5F1-Amfi/public_members/gokturkbabaoglu
gh api orgs/5F1-Amfi/public_members --jq '.[].login'
```

İkinci komut `gokturkbabaoglu` yazdırmalı.

### 4. Git kimliğini ayarla

Commit'lerin profiline doğru düşmesi için GitHub'ın noreply adresi kullanılır;
kişisel e-posta commit geçmişine düşmesin, `.local` adresi de gri avatar üretir.

```bash
ID=$(gh api user --jq '.id')
git config user.name "Afşın Göktürk Babaoğlu"
git config user.email "${ID}+gokturkbabaoglu@users.noreply.github.com"
git config --get-regexp '^user\.'
```

### 5. Bu dosyayı sil ve commit at

Bu adım aynı zamanda Göktürk'ün **repo'ya ilk katkısı** olur; 6. adım buna bağlı.

- `BASLA-BURADAN.md` dosyasını sil.
- `README.md`'nin en üstündeki `BASLA-BURADAN.md`'ye işaret eden alıntı satırını
  (ve altındaki boş satırı) kaldır. Başka hiçbir yerine dokunma.

```bash
git rm BASLA-BURADAN.md
git add README.md
git commit -m "Kurulum notu kaldırıldı"
git push origin main
```

Push reddedilirse `git pull --rebase origin main` yapıp tekrar dene.
**`--force` kullanma**, geçmişi yeniden yazma: repo'da ikinci bir sahip var.

### 6. Repo'yu profile sabitle — bunu Claude yapamaz

Pinleme için API yok, tarayıcıdan yapılır. 5. adımdaki commit atıldıktan sonra
(GitHub yalnız son bir yıl içinde katkı verilmiş repo'ların pinlenmesine izin
verir) Göktürk'e şunu söyle:

> `github.com/gokturkbabaoglu` → profil sayfasında **"Customize your pins"** →
> listeden **Amplifier-Simulator**'ı seç → Save.

### 7. Rapor ver

Göktürk'e Türkçe, kısa: hangi adım tamamlandı, hangisi tamamlanmadı ve neden.
Yapamadığın bir adımı yapılmış gibi yazma.

## Bundan sonrası için

- **Doğrulama bu projede ciddiye alınır.** `docs/DOGRULAMA.md` kabul testlerini,
  `docs/KARAR_GUNLUGU.md` verilmiş kararların gerekçesini tutar. Elektrik
  modelinde değişiklik yaptıysan `node tests/run-tests.js` çalıştır ve
  `dogrulama.html` sayfasını tarayıcıda aç; sayılar tutmadan "oldu" deme.
- **Simülatör çevrimdışıdır.** `index.html` doğrudan tarayıcıda açılır; derleme
  adımı, paket kurulumu ve internet gerekmez. Yeni bağımlılık ekleme.
- **`main`'e doğrudan basmak yerine branch açıp PR at.** Repo'da iki sahip var,
  ikisi de aynı dal üstünde çalışıyor; çakışmanın ucuz çözümü budur.
- Simülatörün girdi belgeleri (proje raporu, tüp veri sayfaları) repo'da
  **değil**, Osman'da. Şartnameye ihtiyaç duyarsan Göktürk'e Osman'dan istemesini
  söyle; uydurma.
