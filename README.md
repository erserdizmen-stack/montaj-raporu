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

                  ## Webhook Konfigürasyonu

                  Form şu anda Make.com'dan şantiye listesini alıyor. Webhook URL'sini `index.html`'de konfigure etmelisin.

                  ## Kullanım

                  1. Formu tarayıcıda aç
                  2. Şantiye, İş, Kişi Sayısı ve Tarih bilgilerini doldur
                  3. **"Kaydet"** tuşuna tıkla
                  4. Başarı mesajı görüntülenir

                  ---

                  **Tarih:** 2026-09-22  
                  **Teknoloji:** HTML5, JavaScript, Make.com, SheetJS
