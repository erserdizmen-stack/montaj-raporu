# 🚀 Hızlı Yayınlama Rehberi

## En Hızlı Yol (2 dakika) - GitHub Pages

### Adım 1: GitHub Repository Oluştur
1. [github.com](https://github.com) adresine git
2. Sağ üstte **+** → **New repository** tıkla
3. Repository adı: `montaj-raporu`
4. **Public** seç
5. **Create repository** tıkla

### Adım 2: Dosyaları Yükle
1. Repository içinde **Add file** → **Upload files** tıkla
2. `index.html` dosyasını sürükle-bırak
3. **Commit changes** tıkla

### Adım 3: GitHub Pages Aç
1. Repository **Settings** kısmına git
2. Sol menüden **Pages** seç
3. Source kısmında **Main** branch seç
4. **Save** tıkla

✅ **Tamamdır!** 2-3 dakika sonra form şu URL'de canlı olacak:
```
https://[github-kullanıcı-adın].github.io/montaj-raporu/
```

---

## Alternatif Yollar

### Netlify ile (1 dakika)
1. [netlify.com](https://netlify.com) adresine git
2. **GitHub ile bağlan** seç
3. Senin `montaj-raporu` repositoryni seç
4. **Deploy site** tıkla
5. Otomatik URL alırsın

### Vercel ile (1 dakika)
1. [vercel.com](https://vercel.com) adresine git
2. **GitHub ile bağlan** seç
3. Repositoryni seç
4. **Import** tıkla
5. Otomatik deploy olur

### Başka bir server'a yükle
`index.html` dosyasını şu şekilde yükle:
```bash
scp index.html kullaniciadi@server.com:/var/www/html/
```

---

## Webhook URL'i Değiştirme (İleride)

Eğer webhook URL'ini değiştirmek istersen, `index.html` dosyasını düzenle:

```javascript
// Satır ~213
const SAHALAR_WEBHOOK_URL = 'https://hook.eu1.make.com/[YENİ-WEBHOOK-URL]';
```

Dosyayı kaydet ve repositoryye push et. GitHub Pages otomatik olarak güncellenecek.

---

## Sorun Giderme

| Sorun | Çözüm |
|-------|-------|
| "Şantiye listesi yüklenemedi" | Make.com webhook'unun aktif olduğunu kontrol et |
| Form açılmıyor | Browser cache'i temizle (Ctrl+Shift+Del) |
| Düzenleme sonrası gösterilmiyor | 5 dakika bekle, GitHub Pages senkronizasyonundan sonra yeni yükleni |

---

## İletişim

Sorunlar için Make.com scenario'sunu kontrol et veya webhook URL'nin doğru olduğundan emin ol.
