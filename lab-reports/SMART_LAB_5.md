# SMART 5 Eksen CNC İşleme Merkezi
## LAB 5 · SBOM / CVE / Patch — Vulnerability Decision
**Hazırlayan:** Ömer Bal – 230541108

**Verilen kayıt:** Component X (kontrol/PLC firmware kütüphanesi) · Sürüm 2.4 · CVE-XXXX-XXXX · Critical (CVSS 9.8) · Yama mevcut.

> SMART makinesinin gerçek SBOM'u (yazılım malzeme listesi) yayımlanmamıştır; bu nedenle aşağıdaki karar akışı üretici SBOM'unun talep edilmesini de içerir.

### 1. Bu CVE bizi gerçekten etkiliyor mu? (üç şart)
| Şart | Kontrol |
|---|---|
| Bileşen var mı? | Makinenin SBOM'unda Component X aranır. SBOM yoksa üreticiden talep edilir. |
| Sürüm etkileniyor mu? | Kurulu sürüm 2.4 ise evet; diğer sürümlerde hayır. |
| Açık ulaşılabilir mi? | Bileşen yalnızca kapalı CNC hücresinde ve dış ağa/uzak erişime kapalıysa risk düşer; erişilebilirse risk yüksek. |

Üç şart da sağlanıyorsa makine etkilenir. Biri sağlanmıyorsa "etkilenmiyor" kararı gerekçeyle kayda geçirilir.

### 2. Üretimi hemen durdurur musunuz?
**Hayır, otomatik olarak durdurmam.** Önce erişilebilirlik değerlendirilir. Açık ağdan ulaşılabiliyor ve istismar bilgisi varsa geçici olarak ağdan izole edilir ve kontrollü durdurulur. Kapalı ve izole ise üretim sürer, yama planlı bir bakım penceresine alınır. CVSS tek başına karar verdirmez; bağlam belirleyicidir.

### 3. Yamayı doğrudan mı uygularsınız, önce test mi? Nerede?
**Önce test.** Üretici onayıyla, mümkünse aynı yapıdaki bir test makinesinde veya simülasyonda denenir. Yedek (konfigürasyon, NC program, sürücü parametreleri) alınır, geri dönüş planı hazırlanır. Doğrudan üretim makinesinde uygulamam; 5 eksen hareketi ve takım değişimi bozulabilir.

### 4. Yama bir safety validation'ı etkiliyor mu? Nasıl anlarsınız?
- Üretici sürüm notlarında safety fonksiyonu, sürücü veya zamanlama değişikliği olup olmadığına bakılır.
- Yama sonrası **E-stop, kapak kilidi, ışık perdesi ve STO yanıt süresi** yeniden test edilir.
- Safety parametrelerinin değişmediği (hash/karşılaştırma) doğrulanır. Değişiklik varsa safety yeniden doğrulaması (validation) gerekir.

### 5. Yama mümkün değilse compensating control
- Makineyi ağdan izole etmek, uzak erişimi kapatmak.
- Güvenlik duvarı ile yalnızca gerekli portlara izin vermek.
- USB ve dosya aktarımı için tarama istasyonu kullanmak.
- Ağ ve kontrol PC'sinde izleme/günlük kaydı; bakım penceresinde yama için üreticiyle plan.

**Çıktı → Vulnerability Decision (EP 09 · 10 · 11)**
