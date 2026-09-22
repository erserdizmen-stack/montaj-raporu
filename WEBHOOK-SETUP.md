# 🔗 Webhook Konfigürasyonu

## ⚠️ ÖNEMLİ: Webhook URL'i Ayarla

Formu GitHub'a koymadan **MUTLAKA** webhook URL'ini güncellemen gerekiyor.

### Adım 1: Webhook URL'ini Bul

1. Make.com'da oturum aç
2. "Santiye Listesi" webhook'unu aç
3. URL'yi kopyala: `https://hook.eu1.make.com/[WEBHOOK_ID]`

### Adım 2: index.html Dosyasını Düzenle

`index.html` dosyasını aç ve şu satırı bul (satır ~213):

```javascript
const SAHALAR_WEBHOOK_URL = 'https://hook.eu1.make.com/[WEBHOOK_ID_BURAYA]';
```

`[WEBHOOK_ID_BURAYA]` yerine kendi webhook ID'ini yapıştır:

```javascript
const SAHALAR_WEBHOOK_URL = 'https://hook.eu1.make.com/[WEBHOOK_ID_BURAYA]';
```

### Adım 3: Kaydet ve Koy

Dosyayı kaydedip GitHub'a push et.

---

**NOT:** Webhook URL'i sırrı olarak kalmalı! GitHub'a koymadan önce URL'i private tutulması için kontrol et.

Eğer hata yaptıysan ve URL public oldu:
1. Make.com'da webhook'u regenerate et (yeni URL al)
2. index.html'i güncelleyip tekrar push et
