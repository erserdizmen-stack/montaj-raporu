# 📋 Montaj Raporu - Web Formu

## Özellikler

✅ **Dinamik Şantiye Listesi** - Make.com webhook'tan otomatik yüklenir  
✅ **Basit Form Arayüzü** - Mobil uyumlu, Türkçe arayüz  
✅ **Gerçek Zamanlı Doğrulama** - Gerekli alanlar otomatik kontrol edilir  
✅ **Excel Şablonu İndirme** - Standart rapor şablonunu indir  

## Kurulum & Yayınlama

### Seçenek 1: GitHub Pages ile Yayınla (Önerilen)

1. GitHub'da yeni bir public repository oluştur: `montaj-raporu`
2. `index.html` dosyasını repositoryye yükle
3. Repo ayarlarında **Settings → Pages** kısmından:
   - Source: Main branch seç
   - Root folder: `/` seç
   - **Save** tuşuna tıkla

4. Birkaç dakika sonra şu URL'de formu kullanabilirsin:
   ```
   https://[senin-github-username].github.io/montaj-raporu/
   ```

### Seçenek 2: Netlify ile Yayınla

1. [netlify.com](https://netlify.com) adresine git
2. GitHub hesabınla oturum aç
3. "New site from Git" → Repositoryni seç
4. Deploy tuşuna tıkla
5. Otomatik olarak bir URL alacaksın

### Seçenek 3: Başka bir web host'ta

Herhangi bir web sunucusuna `index.html` dosyasını yükle.

## Webhook Konfigürasyonu

Form şu anda Make.com'dan şantiye listesini alıyor:

```javascript
const SAHALAR_WEBHOOK_URL = 'https://hook.eu1.make.com/[WEBHOOK_ID_BURAYA]';
```

Bu webhook:
- Excel'deki **"Proje Planlari"** sheet'ini okur
- Şantiye listesini JSON olarak döner
- Form yüklendiğinde otomatik olarak dropdown'u doldurur

## Kullanım

1. Formu tarayıcıda aç
2. Şantiye, İş, Kişi Sayısı ve Tarih bilgilerini doldur
3. **"Kaydet ve Excel'e Ekle"** tuşuna tıkla
4. Başarı mesajı görüntülenir

## Hata Giderme

### "Webhook hatası" mesajı alıyorsan:
- Make.com scenario'sunun aktif olduğundan emin ol
- Webhook URL'nin doğru olduğundan emin ol
- Browser console'dan (F12) hata detaylarını kontrol et

### Şantiye listesi boş gösteriliyor:
- Excel dosyasının **"Proje Planlari"** sheet'inde data olduğundan emin ol
- Make.com Excel modulünün doğru sheet'i okuduğundan emin ol

## Gelecek Geliştirmeler

- [ ] Rapor gönderme webhook'unu entegre et (Make.com)
- [ ] Excel dosyasına otomatik yazma
- [ ] Raporları listeleme sayfası
- [ ] Kullanıcı doğrulama

---

**Oluşturan:** Claude Haiku 4.5  
**Tarih:** 2026-09-22  
**Teknoloji:** HTML5, JavaScript, Make.com, SheetJS
