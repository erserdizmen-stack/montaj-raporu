# 🔗 Webhook Konfigürasyon Bilgileri

## Make.com Şantiye Listesi Webhook

**Status:** ✅ Aktif ve Konfigüre Edilmiş

### Webhook Detayları

| Bilgi | Değer |
|-------|-------|
| **URL** | `https://hook.eu1.make.com/[SEN_WEBHOOK_IDSIN]` |
| **Method** | POST |
| **Adı** | Santiye Listesi |
| **Durum** | Aktif |
| **Source** | Excel Online - Proje Planlari Sheet |

### İşleyiş

1. **Form Yüklendiğinde:**
   - JavaScript webhook'u çağırır
   - Make.com scenario'su tetiklenir

2. **Make.com İçinde:**
   - Module 1: Webhook çağrısı alır
   - Module 2: Excel "Proje Planlari" sheet'ini okur (max 500 satır)
   - Module 3: Verileri JSON formatında döner

3. **Form Tarafında:**
   - JSON yanıtı işlenir
   - Dropdown liste doldurulur
   - Kullanıcı şantiye seçer

### Örnek Webhook Yanıtı

```json
{
  "sites": [
    "İstanbul - Ofis",
    "Ankara - Depo"
  ]
}
```

### Veri Akışı

```
[Form Sayfası]
    ↓
[POST İsteği]
    ↓
[Make.com Webhook]
    ↓
[Excel Online Bağlantısı]
    ↓
[Proje Planlari Sheet]
    ↓
[JSON Yanıtı]
    ↓
[Dropdown Doldurulur]
```

## Test Etme

### Browser Console'da Test

Tarayıcıyı aç (F12), Console sekmesine git ve şu kodu yapıştır:

```javascript
const WEBHOOK = 'https://hook.eu1.make.com/[WEBHOOK_ID_BURAYA]';
fetch(WEBHOOK, { method: 'POST', headers: { 'Content-Type': 'application/json' } })
  .then(r => r.json())
  .then(d => console.log('Webhook yanıtı:', d))
  .catch(e => console.error('Hata:', e));
```

Eğer veri görürsen, webhook çalışıyor demektir. ✅

### Postman'de Test

1. Postman aç
2. **POST** seç
3. URL'yi yapıştır: `https://hook.eu1.make.com/kk2l6u4ndu8u!fema0z701yc7alprbxc`
4. **Send** tıkla
5. Yanıtı kontrol et

## Webhook Verisi Nasıl Kullanılır?

### Form Kodunda (index.html içinde)

```javascript
// Webhook'tan veri alınması
const response = await fetch(SAHALAR_WEBHOOK_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' }
});

const data = await response.json();

// Veriler işlenir ve dropdown doldurulur
if (data && data.sites) {
    sahaList = Array.isArray(data.sites) 
        ? data.sites 
        : Object.values(data.sites);
}

updateSahaDropdown();
```

## Excel Verisi Nerede Saklanıyor?

📊 **Dosya:** Microsoft 365 Excel (Online)  
📑 **Sheet:** "Proje Planlari"  
📍 **Sütun:** Şantiye / Site adları  
🔄 **Senkronizasyon:** Otomatik (Real-time)

## Webhook URL'i Değiştirmek

Eğer şantiye listesi webhook'unu değiştirmek istersen:

1. `index.html` dosyasını düzenle
2. Satır ~216 bulundu:
   ```javascript
   const SAHALAR_WEBHOOK_URL = 'https://hook.eu1.make.com/[NEW-URL]';
   ```
3. Yeni webhook URL'sini yapıştır
4. Dosyayı kaydet
5. GitHub (veya hosting) güncelle

## Rapor Webhook'unu Entegre Etme (İleride)

Form şu anda sadece form verilerini gösteriyor. Raporu Make.com'a göndermek için:

1. Make.com'da yeni bir webhook oluştur (Rapor Yazma için)
2. URL'yi kopyala
3. `index.html`de satır ~220 güncellendir:
   ```javascript
   const REPORT_WEBHOOK_URL = 'https://hook.eu1.make.com/[REPORT-URL]';
   ```
4. `submitReport()` fonksiyonunu güncelle

## Hata Ayıklama

### CORS Hatası?
Make.com webhook'u CORS'u destekler, sorun olmamalı.

### Timeout?
- Make.com scenario'sunun aktif olduğundan emin ol
- Webhook "Santiye Listesi" adıyla aktif olmalı

### Boş Liste?
- Excel sheet'inde veri kontrol et
- Sütun adı "Saha" veya "saha" olmalı
- Sheet adı tamamen "Proje Planlari" olmalı

---

**Tarih:** 2026-09-22  
**Webhook Status:** ✅ Aktif  
**Test Edildi:** ✅ Başarılı
