# SMART 5 Eksen CNC İşleme Merkezi
## LAB 1 · Safety Architecture — Safety Function Map
**Hazırlayan:** Ömer Bal – 230541108

> Not: Makinenin emniyet donanımı üretici tarafından yayımlanmamıştır. Aşağıdaki mimari **tipik bir ahşap CNC işleme merkezine dayanan varsayımdır**; sahada doğrulanmalıdır.

### 1. Bu makinede tehlike nedir? İnsan neyden zarar görür?
- **Dönen takım:** 7,5 kW şekillendirme kesicisi (Ø120 mm, yüksek devirli) ve elektrospindle; temas halinde uzuv kaybı/kesilme.
- **Hareketli eksenler:** 5 eksenli hareket, ±90° yatan freze kafası ve torna ekseni; sıkışma ve ezilme.
- **Fırlayan parça/talaş:** Dönen ahşap iş parçası (torna) kopması veya takım kırılması.
- **Takım değişimi:** 5 pozisyonlu magazin ve otomatik değişim sırasında mekanik hareket.
- **Ahşap tozu:** Yanıcı toz birikimi ve solunum riski (emiş sistemi gerekli).
- **Gürültü:** Yüksek devirli kesici ve emiş.

### 2. Safety function hangisidir?
Acil durdurma (E-stop) veya koruyucu kapak/ışık perdesi ihlalinde iş mili ve servo/tahrik torkunun kesilmesi (**STO – Safe Torque Off**) ve kapak kilitlemesi (kapak, takım durmadan açılmaz).

### 3. Safety-related control system nerede?
E-stop / kapak anahtarı / ışık perdesi → **emniyet rölesi veya Safety PLC** → **STO girişi (iş mili inverteri + servo sürücüler)** ve ana kontaktör. *(Varsayım; saha doğrulaması gerekli.)*

### 4. Normal PLC ile Safety PLC farkı nedir?
| | Normal kontrol (CNC/PLC) | Safety PLC / emniyet rölesi |
|---|---|---|
| Görev | NC programı, eksen hareketi, takım değişimi | İnsanı koruyan fonksiyonlar |
| Mimari | Tek kanal | Çift kanal, kendi kendini denetler |
| Sertifika | Gerekmez | PL d / SIL 2 seviyesinde olabilir |
| Yazılım ile değiştirme | Kolay | Kilitli, şifreli, doğrulamalı |

### 5. PLr / SIL neden var? Bu fonksiyon için neden önemli?
Bu fonksiyon başarısız olursa sonuç ağır ve geri dönüşsüz yaralanmadır (uzuv kaybı). Gerekli güvenilirlik riskle orantılıdır; **PL d (SIL 2)** seviyesi bu tür dönen takımlı makineler için yaygın hedeftir. Seviye **kesin olarak makine tarafından doğrulanmalıdır**. Bu güvenilirlik, safety konfigürasyonunun (parametreler, zamanlar) bütünlüğüne bağlıdır.

### 6. Safe state (güvenli durum) nedir?
Tahrik torku kesilir (STO), iş mili ve eksenler durur, kapak durma onayına kadar kilitli kalır. **Toz emişi çalışmaya devam eder** (yanıcı toz birikimini önlemek için); yani "her şeyi kapat" doğru güvenli durum değildir.

### 7. Safety function hangi dijital bağımlılıklara sahip?
Safety konfigürasyonu (zaman/eşik parametreleri), sürücü STO parametreleri, saha veri yolu (varsa) ve bakım/mühendislik yazılımına erişim.

### 8. Siber müdahale hangi noktadan bu fonksiyonu bozar?
- Kontrol bilgisayarı üzerinden **sürücü/safety parametrelerinin değiştirilmesi** (ör. durma süresi, STO bypass).
- Uzaktan bakım erişimiyle emniyet ayarlarının değişmesi.
- Zararlı bir NC programıyla aşırı hız/yanlış hareket (safety yolu bağımsızsa durdurur, değilse tehlike).

**Çıktı → Safety Function Map (EP 03 Safety Functions)**

```
NORMAL YOL:  Sensör → CNC/PLC → Servo + İş mili         (üretim)
SAFETY YOL:  E-stop/Kapak/Işık perdesi → Safety röle/PLC → STO + Kontaktör → Safe State
```
