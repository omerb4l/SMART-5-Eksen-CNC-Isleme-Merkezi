# SMART 5 Eksen CNC İşleme Merkezi
## LAB 6 · CRA Incident Simulation — Incident Workflow
**Hazırlayan:** Ömer Bal – 230541108

**Senaryo:** 10:15. Servis hesabında yetkisiz erişim tespit edildi. Kontrol PC'sindeki CNC/PLC konfigürasyonu değişmiş olabilir. Makine hâlâ çalışıyor. Vardiya sorumlususunuz.

### 1. 10:15 — İlk 15 dakika
- **Kimi ararsınız?** Üretim/fabrika müdürü, BT/OT güvenlik sorumlusu, makine üreticisi (Dinçmak) servisi.
- **İlk üç eylem:**
  1. Makineyi **kontrollü ve güvenli biçimde durdur** (tutulan parça bırakılır, iş mili durur); E-stop gerekiyorsa kullan.
  2. Uzak erişimi kes (VPN/jump server kapat) ve şüpheli hesabı devre dışı bırak.
  3. Zamanı, gördüklerini ve ekran görüntülerini not et. **Resetleme, yeniden başlatma veya format yok.**

### 2. İlk 2 saat
- **Emniyet güvende mi?** E-stop, kapak kilidi ve STO test edilerek doğrulanır; doğrulanana kadar makine çalıştırılmaz ve operatör tehlikeli alana sokulmaz.
- **Kanıt:** Kontrol PC'sinin diski/imajı, oturum ve VPN günlükleri, jump server kayıtları, NC programı ile sürücü/safety parametrelerinin mevcut kopyaları, USB/ağ günlükleri. Kanıt değiştirilmeden saklanır.
- **Hesap:** İlgili servis hesabı ve ortak kullanılan tüm kimlik bilgileri kapatılır, parolalar/anahtarlar yenilenir.

### 3. 24 saat — CRA erken uyarı
Hazır olması gereken bilgi: olayın ne zaman fark edildiği, etkilenen ürün (SMART, sürüm/seri no), şüpheli saldırı türü, **istismar edilen açık olduğu şüphesi**, ilk alınan önlemler, olayın birden fazla kullanıcıyı etkileyip etkilemediği.
*(CRA bildirim yükümlülüğü, ürün üreticisi için istismar edilen açık veya ciddi olay hâlinde doğar; ilgili durumun bu olayda geçerli olup olmadığı hukuki olarak kontrol edilmelidir.)*

### 4. 72 saat — CRA bildirim
| Konu | Sorumlu |
|---|---|
| Kök neden (hesap nasıl ele geçti?) | BT/OT güvenlik + üretici |
| Etki (hangi parametre/program değişti, emniyet etkilendi mi?) | Üretici mühendislik + bakım |
| Önlem (hesap, erişim, yama) | BT/OT güvenlik |
| Bildirim metni ve gönderimi | Uyum/hukuk sorumlusu |

### 5. 14 gün — son rapor
Korunması gereken kayıtlar: VPN/jump server ve oturum kayıtları, kontrol PC'si olay günlükleri, değişiklik öncesi/sonrası program ve parametre karşılaştırmaları, emniyet testi sonuçları, alınan önlemler ve zaman çizelgesi.

> **En sık hata:** "Resetleyip devam edelim." Bu, kanıtı siler. Önce emniyet, hemen sonra kanıt.

**Çıktı → Incident Workflow (EP 13 Incident Response)**
