# 🛡️ AdvancedGuard Bot - Kurulum ve Kullanım Kılavuzu

## 📋 İçindekiler
1. [Bot Hakkında](#bot-hakkında)
2. [Sistem Gereksinimleri](#sistem-gereksinimleri)
3. [Kurulum Adımları](#kurulum-adımları)
4. [İlk Yapılandırma](#ilk-yapılandırma)
5. [Komut Listesi](#komut-listesi)
6. [Guard Sistemleri](#guard-sistemleri)
7. [Log Sistemi](#log-sistemi)
8. [Özelleştirme](#özelleştirme)
9. [Sorun Giderme](#sorun-giderme)
10. [Destek](#destek)

---

## 🤖 Bot Hakkında

**AdvancedGuard**, Discord sunucunuzu en üst seviyede korumak için tasarlanmış profesyonel bir güvenlik botudur. 8 farklı guard sistemi, kategorize edilmiş log sistemi ve 15+ komut ile sunucunuzu tüm tehditlere karşı korur.

### ✨ Öne Çıkan Özellikler
- 🛡️ **8 Farklı Guard Sistemi** (Rol, Kanal, Emoji, Ban/Kick, Webhook, Bot, Sunucu, Anti-Nuke)
- 📊 **6 Kategoride Log Sistemi** (Guard, Anti-Nuke, Blacklist, Üye, Sunucu, Genel)
- ⚡ **15+ Slash Komutu** (Admin, Moderasyon, Bilgi, Genel)
- 🔄 **Otomatik Geri Yükleme** (Silinen rol/kanal/emoji)
- 🚫 **Blacklist/Whitelist Sistemi**
- 🎨 **Tamamen Özelleştirilebilir Mesajlar**
- 🇹🇷 **Türkçe Dil Desteği**

---

## 💻 Sistem Gereksinimleri

- **Node.js:** v16.9.0 veya üzeri
- **NPM:** v7.0.0 veya üzeri
- **İşletim Sistemi:** Windows, Linux, macOS
- **RAM:** Minimum 512MB (Önerilen: 1GB)
- **Disk Alanı:** 100MB

---

## 🚀 Kurulum Adımları

### 1️⃣ Node.js Kurulumu
1. [Node.js resmi sitesinden](https://nodejs.org/) LTS sürümünü indirin
2. İndirilen dosyayı çalıştırıp kurulumu tamamlayın
3. Terminal/CMD'de kontrol edin:
   ```bash
   node --version
   npm --version
   ```

### 2️⃣ Bot Oluşturma (Discord Developer Portal)
1. [Discord Developer Portal](https://discord.com/developers/applications)'a gidin
2. "New Application" butonuna tıklayın
3. Bot ismi girin ve "Create" butonuna tıklayın
4. Sol menüden "Bot" sekmesine gidin
5. "Add Bot" butonuna tıklayın
6. **Token'ı kopyalayın** (Bu çok önemli!)
7. "Privileged Gateway Intents" bölümünden şunları aktif edin:
   - ✅ Presence Intent
   - ✅ Server Members Intent
   - ✅ Message Content Intent

### 3️⃣ Bot Davet Etme
1. Sol menüden "OAuth2" > "URL Generator" sekmesine gidin
2. **Scopes** bölümünden:
   - ✅ `bot`
   - ✅ `applications.commands`
3. **Bot Permissions** bölümünden:
   - ✅ Administrator (Önerilen)
   - VEYA aşağıdaki yetkileri tek tek seçin:
     - Manage Roles, Manage Channels, Manage Guild
     - Ban Members, Kick Members, Moderate Members
     - Manage Messages, Send Messages, Embed Links
     - View Audit Log, Manage Webhooks
4. Oluşan linki kopyalayıp sunucunuza botu davet edin

### 4️⃣ Proje Kurulumu
1. İndirdiğiniz bot dosyalarını bir klasöre çıkarın
2. Terminal/CMD'yi o klasörde açın
3. Bağımlılıkları yükleyin:
   ```bash
   npm install
   ```

### 5️⃣ Yapılandırma
1. `config/config.json` dosyasını açın
2. Bot token'ınızı girin:
   ```json
   {
     "bot": {
       "token": "BOT_TOKEN_BURAYA_YAPIŞTIRIN",
       "clientId": "BOT_CLIENT_ID_BURAYA",
       "prefix": "!"
     }
   }
   ```
3. Client ID'yi almak için Discord Developer Portal > General Information > Application ID

### 6️⃣ Botu Başlatma
```bash
npm start
```

✅ **Başarılı!** Bot artık çalışıyor ve sunucunuzda aktif.

---

## ⚙️ İlk Yapılandırma

Bot başladıktan sonra aşağıdaki adımları takip edin:

### 1️⃣ Log Kanallarını Ayarlama
```
/log-kanal genel #genel-log
/log-kanal guard #guard-log
/log-kanal anti-nuke #anti-nuke-log
/log-kanal blacklist #blacklist-log
/log-kanal uye #uye-log
/log-kanal sunucu #sunucu-log
```

### 2️⃣ Guard Sistemlerini Aktifleştirme
```
/guard-ayarla anti-spam
/guard-ayarla anti-raid
/guard-ayarla auto-mod
```

### 3️⃣ Yetki Rollerini Belirleme
`config/settings.json` dosyasından:
```json
{
  "permissions": {
    "adminRoles": ["ADMIN_ROL_ID"],
    "moderatorRoles": ["MOD_ROL_ID"],
    "trustedRoles": ["GUVENILIR_ROL_ID"],
    "bypassRoles": ["BYPASS_ROL_ID"]
  }
}
```

---

## 📋 Komut Listesi

### 🛡️ Guard Komutları
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/guard-ayarla anti-spam` | Anti-spam ayarları | Yönetici |
| `/guard-ayarla anti-raid` | Anti-raid ayarları | Yönetici |
| `/guard-ayarla auto-mod` | Otomatik moderasyon | Yönetici |
| `/guard-ayarla durum` | Guard durumunu göster | Yönetici |

### ⚙️ Admin Komutları
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/log-kanal genel #kanal` | Genel log kanalı | Yönetici |
| `/log-kanal guard #kanal` | Guard log kanalı | Yönetici |
| `/log-kanal anti-nuke #kanal` | Anti-nuke log kanalı | Yönetici |
| `/log-kanal blacklist #kanal` | Blacklist log kanalı | Yönetici |
| `/log-kanal uye #kanal` | Üye log kanalı | Yönetici |
| `/log-kanal sunucu #kanal` | Sunucu log kanalı | Yönetici |
| `/log-kanal liste` | Mevcut log kanalları | Yönetici |
| `/log-kanal sifirla` | Tüm log kanallarını sıfırla | Yönetici |
| `/blacklist ekle @kullanici` | Blacklist'e ekle | Yönetici |
| `/blacklist kaldir @kullanici` | Blacklist'ten çıkar | Yönetici |
| `/blacklist liste` | Blacklist'i göster | Yönetici |
| `/whitelist ekle @kullanici` | Whitelist'e ekle | Yönetici |
| `/whitelist kaldir @kullanici` | Whitelist'ten çıkar | Yönetici |
| `/whitelist liste` | Whitelist'i göster | Yönetici |

### 🔨 Moderasyon Komutları
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/ban @kullanici [sebep]` | Kullanıcı yasakla | Ban Members |
| `/kick @kullanici [sebep]` | Kullanıcı at | Kick Members |
| `/timeout @kullanici süre [sebep]` | Kullanıcı sustur | Moderate Members |
| `/warn @kullanici sebep` | Kullanıcı uyar | Manage Messages |
| `/uyari-gecmisi @kullanici [işlem]` | Uyarı geçmişi görüntüle/yönet | Manage Messages |

### 📊 Bilgi Komutları
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/sunucu-bilgi` | Sunucu bilgileri | Herkes |
| `/kullanici-bilgi [@kullanici]` | Kullanıcı bilgileri | Herkes |
| `/bot-bilgi` | Bot bilgi ve istatistikler | Herkes |

### 🎯 Genel Komutlar
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/help [kategori]` | Yardım menüsü | Herkes |
| `/ping` | Bot gecikmesi | Herkes |

---

## 🛡️ Guard Sistemleri

### 1️⃣ Anti-Spam Koruması
- **Özellik:** Spam mesajları otomatik tespit
- **Ayarlar:** Mesaj limiti, zaman aralığı, ceza türü
- **Cezalar:** Susturma, atma, yasaklama

### 2️⃣ Anti-Raid Koruması
- **Özellik:** Raid saldırılarını tespit ve engelle
- **Ayarlar:** Katılım limiti, zaman aralığı, lockdown
- **Cezalar:** Otomatik sunucu kilidi

### 3️⃣ Rol Koruma Sistemi
- **Özellik:** Yetkisiz rol oluşturma/silme engelleme
- **Otomatik Geri Yükleme:** ✅ Aktif
- **Cezalar:** Susturma, atma, yasaklama

### 4️⃣ Kanal Koruma Sistemi
- **Özellik:** Yetkisiz kanal oluşturma/silme engelleme
- **Otomatik Geri Yükleme:** ✅ Aktif
- **Cezalar:** Susturma, atma, yasaklama

### 5️⃣ Emoji/Sticker Koruma
- **Özellik:** Emoji/sticker silme engelleme
- **Otomatik Geri Yükleme:** ✅ Aktif
- **Cezalar:** Susturma, atma, yasaklama

### 6️⃣ Ban/Kick Koruma
- **Özellik:** Yetkisiz ban/kick engelleme
- **Otomatik Geri Alma:** ✅ Aktif
- **Cezalar:** Susturma, atma, yasaklama

### 7️⃣ Webhook Koruma
- **Özellik:** Yetkisiz webhook oluşturma engelleme
- **Otomatik Silme:** ✅ Aktif
- **Cezalar:** Susturma, atma, yasaklama

### 8️⃣ Anti-Nuke Sistemi
- **Özellik:** Toplu saldırı tespit ve engelleme
- **Koruma Alanları:** Tüm sunucu işlemleri
- **Otomatik Müdahale:** ✅ Aktif

---

## 📊 Log Sistemi

### 📝 Log Kategorileri

#### 🛡️ Guard Log
- Rol koruma olayları
- Kanal koruma olayları
- Emoji/sticker koruma
- Webhook koruma
- Bot ekleme koruma

#### 🚨 Anti-Nuke Log
- Toplu saldırı tespitleri
- Otomatik müdahaleler
- Sistem kilitlemeleri

#### 🚫 Blacklist Log
- Blacklist kullanıcı aktiviteleri
- Otomatik cezalar
- Blacklist değişiklikleri

#### 👥 Üye Log
- Üye giriş/çıkış
- Üye bilgi değişiklikleri
- Rol değişiklikleri

#### 🏰 Sunucu Log
- Sunucu ayar değişiklikleri
- Kanal/rol oluşturma/silme
- Sunucu güncellemeleri

#### 📋 Genel Log
- Moderasyon işlemleri
- Komut kullanımları
- Diğer bot aktiviteleri

---

## 🎨 Özelleştirme

### 📝 Mesajları Değiştirme

#### Embed Mesajları (`messages/embeds.json`)
```json
{
  "guard": {
    "antiSpam": {
      "title": "🛡️ Kendi Başlığınız",
      "description": "Kendi açıklamanız: {user}",
      "color": "#ff6b6b"
    }
  }
}
```

#### Metin Mesajları (`messages/messages.json`)
```json
{
  "guard": {
    "antiSpam": {
      "detected": "{user}, kendi uyarı mesajınız!"
    }
  }
}
```

#### Hata Mesajları (`messages/errors.json`)
```json
{
  "permissions": {
    "missingUserPermissions": "Kendi yetki hata mesajınız!"
  }
}
```

### ⚙️ Guard Ayarları (`config/settings.json`)

#### Anti-Spam Ayarları
```json
{
  "antiSpam": {
    "enabled": true,
    "maxMessages": 5,        // Maksimum mesaj sayısı
    "timeWindow": 5000,      // Zaman aralığı (ms)
    "punishment": "timeout", // Ceza türü
    "timeoutDuration": 300000 // Susturma süresi (ms)
  }
}
```

#### Anti-Raid Ayarları
```json
{
  "antiRaid": {
    "enabled": true,
    "maxJoins": 10,          // Maksimum katılım
    "timeWindow": 60000,     // Zaman aralığı (ms)
    "punishment": "kick",    // Ceza türü
    "lockdown": true         // Otomatik kilitleme
  }
}
```

### 🎨 Renk Kodları
- **Başarı:** `#2ed573` (Yeşil)
- **Hata:** `#ff4757` (Kırmızı)
- **Uyarı:** `#ffa502` (Turuncu)
- **Bilgi:** `#3742fa` (Mavi)
- **Guard:** `#ff6b6b` (Açık Kırmızı)

---

## 🔧 Sorun Giderme

### ❌ Bot Başlamıyor
**Çözüm:**
1. Node.js versiyonunu kontrol edin (`node --version`)
2. Token'ın doğru girildiğini kontrol edin
3. Bot'un gerekli yetkilere sahip olduğunu kontrol edin

### ❌ Komutlar Çalışmıyor
**Çözüm:**
1. Bot'un "applications.commands" yetkisine sahip olduğunu kontrol edin
2. Slash komutlarının Discord'a kaydolması için 1-2 dakika bekleyin
3. Bot'u sunucudan çıkarıp tekrar davet edin

### ❌ Log Mesajları Gönderilmiyor
**Çözüm:**
1. Log kanallarının doğru ayarlandığını kontrol edin (`/log-kanal liste`)
2. Bot'un kanallara mesaj gönderme yetkisi olduğunu kontrol edin
3. Kanalların silinmediğini kontrol edin

### ❌ Guard Sistemleri Çalışmıyor
**Çözüm:**
1. `config/settings.json` dosyasında guard sistemlerinin aktif olduğunu kontrol edin
2. Bot'un gerekli yetkilere sahip olduğunu kontrol edin (Manage Roles, Manage Channels, etc.)
3. Bot'un rol hiyerarşisinin yeterli olduğunu kontrol edin

### 📊 Performans Sorunları
**Çözüm:**
1. Sunucu kaynaklarını kontrol edin (RAM, CPU)
2. Bot'u yeniden başlatın
3. Gereksiz guard sistemlerini devre dışı bırakın

---

## 📞 Destek

### 🆘 Acil Destek
- **Discord:** [Destek Sunucusu](https://discord.gg/support)
- **E-posta:** support@advancedguard.com
- **Telegram:** @AdvancedGuardSupport

### 📚 Dokümantasyon
- **GitHub:** [Repository](https://github.com/advancedguard)
- **Wiki:** [Detaylı Dokümantasyon](https://wiki.advancedguard.com)
- **Video Kılavuzlar:** [YouTube Kanalı](https://youtube.com/advancedguard)

### 🐛 Bug Raporu
Bir hata bulduysanız:
1. Hatanın detaylı açıklaması
2. Hata mesajının ekran görüntüsü
3. Hangi komut/özellik kullanılırken oluştuğu
4. Sunucu bilgileri (üye sayısı, bot yetkileri)

### 💡 Özellik İsteği
Yeni özellik önerilerinizi Discord sunucumuzda paylaşabilirsiniz.

---

## 💰 Fiyat Bilgisi

**AdvancedGuard Bot** profesyonel bir güvenlik çözümüdür ve aşağıdaki fiyat seçenekleri mevcuttur:

### 🏷️ Fiyat Paketleri

#### 💎 **Premium Paket - ₺299**
- ✅ Tam kaynak kodu
- ✅ Tüm özellikler aktif
- ✅ Özelleştirilebilir mesajlar
- ✅ 6 ay ücretsiz güncelleme
- ✅ Discord destek
- ✅ Kurulum yardımı

#### 🚀 **Enterprise Paket - ₺499**
- ✅ Premium paket özellikleri
- ✅ Özel özellik geliştirme
- ✅ 1 yıl ücretsiz güncelleme
- ✅ Öncelikli destek
- ✅ Uzaktan kurulum hizmeti
- ✅ Özel eğitim

#### 🏆 **Lifetime Paket - ₺799**
- ✅ Enterprise paket özellikleri
- ✅ Ömür boyu güncelleme
- ✅ Ömür boyu destek
- ✅ Gelecekteki tüm özellikler
- ✅ Özel Discord sunucusu
- ✅ Bot hosting desteği

### 💳 Ödeme Yöntemleri
- 💳 Kredi Kartı
- 🏦 Banka Havalesi
- 💰 Papara
- 🎮 Steam Cüzdan Kodu
- 🪙 Kripto Para (BTC, ETH, USDT)

### 📞 Satın Alma
Satın almak için Discord sunucumuzdan iletişime geçin: **[discord.gg/advancedguard]**

---

## 📄 Lisans

Bu yazılım **telif hakkı ile korunmakta olup tescilli (proprietary)** bir lisans altındadır.  
Satın aldıktan sonra Ürünü yalnızca kendi kullanımınız için etkinleştirebilir, üçüncü kişilere **devredemez, satamaz veya paylaşamazsınız**.  

🔒 Detaylı hüküm ve koşullar için tam lisans anlaşmasını inceleyiniz:  
👉 [EULA.md](./EULA.md)

---

## 🎉 Teşekkürler

**AdvancedGuard Bot**'u tercih ettiğiniz için teşekkür ederiz! Sunucunuzun güvenliği bizim önceliğimizdir.

**İyi kullanımlar! 🛡️**

---

*Son güncelleme: 2024*
*Versiyon: 1.0.0*
