# SMART 5 Eksen CNC İşleme Merkezi
## LAB 2 · IEC 62443 Mini Workshop — Zone / Conduit Diagram
**Hazırlayan:** Ömer Bal – 230541108

> Bölge modeli mantıksal bir başlangıçtır; gerçek bağlantılar sahada doğrulanmalıdır.

### Görev A — Varlıkları bölgelere ayırma

| Bölge | Varlıklar | Gerekçe |
|---|---|---|
| **Z1 – Ofis BT** | ERP, e-posta, ofis bilgisayarları | Düşük kritiklik, internete açık |
| **Z2 – Mühendislik / CAD-CAM** | Tasarım ve CAM istasyonu, NC program deposu, mühendislik istasyonu | Program üretimi ve onayı; USB/dosya kaynağı |
| **Z3 – CNC hücresi (kontrol)** | CNC kontrolcüsü / kontrol PC'si, HMI, PLC, servo ve iş mili sürücüleri | Üretimi yöneten, hareketi belirleyen varlıklar |
| **Z4 – Safety** | E-stop, kapak kilidi, ışık perdesi, Safety PLC/röle, STO hattı | İnsan güvenliği; en yüksek koruma |
| **Z5 – Uzak servis (DMZ)** | Jump server, VPN geçidi | Üretici/servis erişimi için ayrılmış ara bölge |

**2. Safety PLC hangi bölgede, neden?** Z4'te, ayrı bir bölgede. Normal kontrol bölgesi ele geçirilse bile emniyet fonksiyonu etkilenmemeli; bu yüzden Z3 ile arasında yalnızca zorunlu, tek yönlü ve filtrelenmiş bağlantı bulunur.

**3. Geçişler (conduit) ve kontroller**

| Conduit | Kontrol |
|---|---|
| Z1 ↔ Z2 | Güvenlik duvarı, yalnızca gerekli portlar, dosya taraması |
| Z2 → Z3 (NC program aktarımı) | Program onayı (imza/hash), kontrollü aktarım noktası, **serbest USB yok** (tarama istasyonu) |
| Z3 ↔ Z4 | Mümkünse hardwired; veri yolu varsa salt izleme, **safety parametre yazma yetkisi kapalı** |
| Uzak servis → Z3 | Yalnızca DMZ üzerinden, jump server, onaylı oturum |

### Görev B — Uzak erişim kararı

| Karar | Seçim | Neden |
|---|---|---|
| Aracı | **Jump server** | Tek kontrollü giriş noktası, doğrudan bağlantı yok |
| Tünel | **VPN** | Şifreli kanal, açık port yok |
| Kimlik | **MFA** | Çalınan parola tek başına yetmez |
| Hesap | **Kişisel** | Kim ne yaptı izlenir, sorumluluk net |
| Kayıt | **Tam oturum kaydı** | Olay sonrası kanıt |
| Zamanlama | **Varsayılan kapalı** | Yalnızca onaylı bakım penceresinde açılır |

**Çıktı → Zone / Conduit Diagram (EP 05)**

```
[Ofis BT] --FW--> [CAD-CAM] --kontrollü aktarım--> [CNC hücresi] --hardwired--> [Safety]
                                                         ^
                          [Uzak servis DMZ: jump+VPN+MFA, varsayılan kapalı]
```
