# SMART 5 Eksen CNC İşleme Merkezi
## LAB 4 · Secure Remote Access — Secure Architecture
**Hazırlayan:** Ömer Bal – 230541108

### Görev A — Mevcut → Hedef

**Mevcut (varsayım):** Üretici/servis, kontrol PC'sine uzak masaüstü veya ortak bir bakım yazılımıyla doğrudan bağlanır; paylaşılan hesap kullanılır, erişim sürekli açıktır, kayıt tutulmaz.

```
Servis teknisyeni --(internet, doğrudan)--> Kontrol PC'si --> Sürücüler / Safety
```

**Hedef (beş ilke):**

```
Servis --VPN+MFA--> [Jump server (DMZ)] --onaylı oturum--> Kontrol PC'si (Z3)
                         |-- kişisel hesap
                         |-- tam oturum kaydı
                         |-- varsayılan kapalı (bakım penceresinde açılır)
Safety (Z4): ayrı yol, uzaktan yazma yok
```

| İlke | Uygulama |
|---|---|
| Ara nokta | Jump server |
| VPN | Şifreli tünel, dışarıya açık port yok |
| MFA | Parola + ikinci faktör |
| Kişisel hesap | Paylaşılan servis hesabı kaldırılır |
| Kayıt | Oturum ve değişiklik kaydı saklanır |
| Varsayılan kapalı | Erişim, onaylı bakım talebiyle belirli süre açılır |

### Görev B — Functional safety köprüsü

**1. Saldırgan tüm önlemlere rağmen içeri girerse emniyet fonksiyonu etkilenir mi?**
Mimari doğru kurulduysa **hayır**. E-stop, kapak kilidi ve STO hattı normal kontrol PC'sine bağlı olmayan, ayrı bir yoldur; saldırgan programı bozsa bile tork kesme çalışır. Ancak safety parametreleri aynı bilgisayardan değiştirilebiliyorsa **etkilenir**; bu yüzden aşağıdaki gereksinim şarttır. *(Makinedeki durum saha doğrulaması gerektirir.)*

**2. Bağımsızlık için GEREKSİNİM (çözüm değil):**
- Emniyet fonksiyonu, normal kontrol sisteminin çalışma durumundan **bağımsız** olarak güvenli duruma geçebilmelidir.
- Safety parametreleri, **uzaktan ve normal kontrol yazılımından değiştirilememelidir**; değişiklik yerinde, yetkili kişiyle ve şifreli/kilitli olmalıdır.
- Safety konfigürasyonunda yapılan her değişiklik kayıt altına alınmalı ve yeniden doğrulama gerektirmelidir.

*Tarafsızlık notu: Bu föy gereksinimi tanımlar; tasarım kararı üretici/işletmeye aittir.*

**Çıktı → Secure Architecture (EP 02 + EP 06)**
