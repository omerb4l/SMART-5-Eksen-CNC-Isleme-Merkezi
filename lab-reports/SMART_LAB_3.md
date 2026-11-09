# SMART 5 Eksen CNC İşleme Merkezi
## LAB 3 · Threat & Risk + Risk Matrix — Risk Register
**Hazırlayan:** Ömer Bal – 230541108

**Skor = L × S × E** (her biri 1–3; L: olasılık, S: şiddet, E: maruziyet).
Öncelik: Kritik 18–27 · Yüksek 9–17 · Orta 4–8 · Düşük 1–3. **Kural:** S=3 ise skor düşük olsa bile senaryo öne alınır.

### Risk Register

| # | Senaryo (kim → kapı → ne yapar → zincir → fiziksel sonuç) | L | S | E | Skor | Öncelik |
|---|---|---|---|---|---|---|
| R1 | Yetkisiz kişi, çalınmış bakım/servis hesabıyla uzak erişime girer → sürücü/safety parametrelerini değiştirir (ör. durma süresi, STO bypass) → kapak açıkken takım tam durmaz → **operatör dönen kesiciye temas eder, uzuv kaybı** | 2 | 3 | 3 | 18 | **Kritik** |
| R2 | Kötü niyetli ya da hatalı kişi USB ile değiştirilmiş NC programı yükler → takım yolu/hız bozulur, ±90° kafa iş parçasına ya da tezgâha çarpar → **takım kırılır, parça fırlar, yakındaki operatör yaralanır** | 2 | 3 | 2 | 12 | Yüksek |
| R3 | Kontrol PC'sine zararlı yazılım bulaşır (USB/ağ) → HMI yanıt vermez veya eksen komutları bozulur → **beklenmedik hareket sırasında müdahale eden operatör ezilir** | 2 | 3 | 2 | 12 | Yüksek |
| R4 | Emiş sistemi arızalanır/devre dışı bırakılır (siber veya mekanik) → ahşap tozu birikir → statik kıvılcım → **toz yangını/patlaması** | 1 | 3 | 2 | 6 | Orta (**S=3 → öne alındı**) |
| R5 | Fidye yazılımı CAD-CAM ve NC program arşivini şifreler → üretim durur, teslimat aksar | 2 | 1 | 3 | 6 | Orta |

**1. En yüksek öncelikli senaryo:** **R1**. Siber erişimin doğrudan emniyet parametresine ulaşıp insana fiziksel zarar vermesi; hem şiddet hem maruziyet en yüksek.

**2. S=3 olup skoru düşük kalan senaryo:** **R4 (toz patlaması)**. Skoru 6 ("Orta"), ama sonuç ölümcül olabilir. Görünür kılmak için: risk kaydında "S=3 öncelikli" etiketi, emiş sisteminin durum izlemesi ve bağımsız bir alarm, bakım planında ayrı kalem.

**Altın kural kontrolü:** Hiçbir zincir "veri çalındı" ile bitmiyor; her biri hattaki insana ya da tesise bir sonuç bağlıyor.

> Olasılık değerleri varsayımdır; makinenin gerçek ağ ve emniyet yapısı doğrulanınca güncellenmelidir.

**Çıktı → Risk Register (EP 04 Risk Assessment)**
