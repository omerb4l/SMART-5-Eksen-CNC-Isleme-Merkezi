# SMART – 5 Eksen CNC İşleme Merkezi (Dinçmak Makina San. – AIMSAD)

## SWOT Analizi: Fonksiyonel Emniyet, Endüstriyel Siber Güvenlik ve Dijitalleşme

**Rapor tarihi:** 9 Kasım 2026
**Hazırlayan:** Ömer Bal – 230541108
**Dayanak:** Safety 4.0 Bootcamp laboratuvar föyleri (LAB 1–7, bu depoda), üreticinin kamuya açık makine bilgileri ve [Wood & Panel (2023)](https://www.woodandpanel.com/woodnews/article/5-axis-cnc-machining-center-tormat-smart-from-dincmak/) haberi.

> **Kapsam notu:** Bu çalışma resmî uygunluk değerlendirmesi, penetrasyon testi veya belgelendirme raporu değildir. Üretici; kontrol sistemi, emniyet donanımı, uzaktan erişim ve yazılım sürümlerini yayımlamamıştır. Bu yüzden bu konulardaki ifadeler **varsayım** olup "saha doğrulaması gerekli" olarak işaretlenmiştir.

---

## 1. Yönetici özeti

SMART (TORMAT.SMART), tek gövdede şekillendirme, tornalama, 5 eksenli detaylı frezeleme ve zımparalamayı birleştiren, mobilya ayaklarına yönelik bir işleme merkezidir. Model 2019'da geliştirilmiş ve DREMA fuarında yenilik altın madalyası almıştır. Çok fonksiyonlu yapısı bir **verimlilik avantajıdır**, aynı zamanda **risk yüzeyini büyütür**: dönen ahşap parça, 7,5 kW kesici, yatan freze kafası ve otomatik takım değişimi aynı anda tehlike kaynağıdır.

En kritik konu yalnızca bilgisayarı korumak değildir; **program, parametre ve bakım erişiminin insan güvenliğine dönüşen etkisini** yönetmektir. Emniyet fonksiyonu (E-stop → Safety → STO) normal kontrol yolundan bağımsız olmalı, siber güvenlik bunu tamamlamalıdır.

---

## 2. Makine özeti (kamuya açık bilgiler)

| Özellik | Bilgi | Kaynak |
|---|---|---|
| Tip | 5 eksen CNC işleme merkezi + ahşap torna | Wood & Panel |
| Şekillendirme ünitesi | 7,5 kW AC kesici motor, Ø120 mm × 180 mm | Wood & Panel |
| Detaylı frezeleme | Elektrospindle, iki yana 90° yatan kafa, otomatik takım değişimi, 5 pozisyonlu magazin | Wood & Panel |
| Diğer üniteler | Tornalama, zımparalama, kesme | Wood & Panel |
| Kullanım | Koltuk, sandalye, masa, dolap ayakları | Wood & Panel |
| Kontrol sistemi, emniyet donanımı, bağlantı | **Belirtilmemiş** | Saha doğrulaması gerekli |

---

## 3. SWOT

**Etiketler:** **[K]** = üretici/haber kaynağında yazıyor · **[Ç]** = kaynaktaki bir özellikten mantıksal çıkarım · **[V]** = varsayım, saha doğrulaması gerekli. Makine ve üretici hakkında kaynağı olmayan bir iddia yazılmamıştır.

### S — Güçlü yönler (Strengths)
1. **Çok fonksiyonlu tek gövde [K]:** Şekillendirme, tornalama, detaylı frezeleme ve zımparalama tek makinede.
2. **5 eksen ve ±90° yatan freze kafası [K]:** Detaylı frezeleme, delik, geçme yuvası ve oyma işleri yapılabilir.
3. **Otomatik takım değişimi, 5 pozisyonlu magazin [K]:** Takım değişimi için elle müdahale ihtiyacı azalır; bu, tehlike maruziyetini düşürebilir [Ç].
4. **Ödüllü tasarım [K]:** DREMA fuarında yenilik altın madalyası.
5. **CNC ile programlanabilir üretim [Ç]:** Tekrarlanabilir işleme; kontrol türü bilinmediği için ayrıntı [V].

### W — Zayıf yönler (Weaknesses)
1. **Teknik şeffaflık eksikliği [K]:** Kontrol sistemi, emniyet donanımı (Safety PLC, STO, ışık perdesi), yazılım ve SBOM bilgisi kaynaklarda yer almıyor; bu yüzden emniyet ve siber güvenlik durumu doğrulanamıyor.
2. **Yüksek tehlike yoğunluğu [Ç]:** Dönen iş parçası, 7,5 kW kesici (Ø120 mm) ve hareketli freze kafası bir arada; temas ve fırlayan parça riski.
3. **Karmaşık çalışma yapısı [Ç]:** Birden fazla ünite (şekillendirme, torna, frezeleme, zımpara) bakım ve emniyet doğrulamasını zorlaştırır.
4. **Program aktarımı ve uzaktan bakım süreci belirsiz [V]:** USB/ağ ile NC aktarımı ve uzak erişim olup olmadığı kaynaklarda yok.
5. **Toz yönetimi [V]:** Ahşap işlendiği için toz oluşur [Ç]; makinede emiş sisteminin nasıl kurulduğu bilinmiyor.

### O — Fırsatlar (Opportunities)
1. **AB Makine Tüzüğü 2023/1230 ve CRA [Ç]:** Dijital bileşen içeren makineler için emniyet ve siber güvenlik gereksinimlerini karşılamak ürün güvenini artırabilir; makinenin AB'ye satılıp satılmadığı bilinmiyor [V].
2. **Güvenli uzaktan servis [V]:** Uzak erişim varsa jump server + VPN + MFA ile güvenli hâle getirilebilir (LAB 2, LAB 4).
3. **SBOM yayımlama [Ç]:** Bileşen listesinin paylaşılması şeffaflığı artırır (LAB 5).
4. **Veri toplama ve izleme [V]:** Kontrol sistemi veri sağlıyorsa iş mili/takım aşınması izlenebilir.
5. **YZ destekli kalite kontrol [V]:** Makinede YZ olduğu belirtilmemiştir; eklenirse fail-safe mimarisi gerekir (LAB 7).
6. **Standartlara uyum [Ç]:** IEC 62443, ISO 13849 ve IEC 62061 temelli doğrulama yol haritası sunar.

### T — Tehditler (Threats)
*Aşağıdaki tehditler LAB 3 risk kaydındaki varsayımsal senaryolardır; gerçekleşmiş olay değildir.*
1. **Çalınmış servis hesabı / yetkisiz uzaktan erişim [V]:** Emniyet parametrelerinin değiştirilmesi, fiziksel yaralanma (LAB 3 – R1, Kritik).
2. **USB ve değiştirilmiş NC programı [V]:** Beklenmedik hareket, takım kırılması, parça fırlaması (R2).
3. **Fidye yazılımı [V]:** Program arşivinin şifrelenmesi, üretimin durması (R5).
4. **Toz yangını/patlaması [Ç]:** Ahşap tozu yanıcıdır; emiş arızasında birikim riski (R4; S=3, öne alınır).
5. **Yasal yükümlülükler [Ç]:** CRA bildirim süreleri (24 s / 72 s / 14 gün) ve makine tüzüğü uyumsuzluğu satış ve hukuki risk doğurabilir.
6. **Bilinen açıklar (CVE) [V]:** Üçüncü taraf bileşenlerde yamalanamayan açıklar (LAB 5).
7. **YZ girdi manipülasyonu [V]:** Yalnızca YZ eklenirse geçerli (LAB 7).

---

## 4. TOWS: stratejik çıkarımlar

| | **Fırsatlar (O)** | **Tehditler (T)** |
|---|---|---|
| **Güçlü (S)** | Çok fonksiyonlu yapıyı CRA/62443 uyumuyla birleştirip ürün güvenini artır | Otomatik takım değişimiyle maruziyeti azalt; emniyeti kontrol yolundan ayır |
| **Zayıf (W)** | Güvenli uzaktan servis ve SBOM yayımlayarak şeffaflık açığını kapat | Safety donanımını doğrula, USB/aktarım sürecini kontrol altına al, olay müdahale planı hazırla |

## 5. Öncelikli öneriler

1. **Sahada doğrula:** Kontrol sistemi, Safety PLC/STO, ışık perdesi, kapak kilidi, uzaktan erişim ve ağ yapısı belgelensin.
2. **Safety'yi kontrol yolundan bağımsız tut;** safety parametreleri uzaktan ve normal yazılımdan değiştirilemesin (LAB 1, LAB 4).
3. **Güvenli uzaktan erişim:** jump server, VPN, MFA, kişisel hesap, tam kayıt, varsayılan kapalı (LAB 2, LAB 4).
4. **NC program aktarımı:** imza/hash doğrulaması ve tarama istasyonu; serbest USB yok.
5. **SBOM + yama süreci:** önce test, sonra safety yeniden doğrulaması (LAB 5).
6. **Olay müdahale planı:** CRA süreleriyle uyumlu, "resetleme" yerine kanıt koruma (LAB 6).
7. **Toz emişi izlemesi:** bağımsız alarm, bakım planında ayrı kalem (LAB 3 – R4).
8. **YZ eklenirse:** fail-safe, güven eşiği, insan onayı (LAB 7).

---

## 6. Sınırlılıklar

- Makineye özgü zafiyet, emniyet seviyesi (PL/SIL) veya mevzuat uygunluğu kesin kabul edilmemelidir.
- Olasılık/şiddet puanları varsayıma dayanır ve gerçek doğrulamayla güncellenmelidir.
- Doğrulanmamış senaryolar gerçekleşmiş olay gibi sunulmamıştır.

## Kaynaklar

- [Wood & Panel – 5 Axis CNC Machining Center TORMAT.SMART from Dinçmak (2023)](https://www.woodandpanel.com/woodnews/article/5-axis-cnc-machining-center-tormat-smart-from-dincmak/)
- Safety 4.0 Bootcamp – Laboratuvar Föyleri, Genel Sürüm (ders materyali)
