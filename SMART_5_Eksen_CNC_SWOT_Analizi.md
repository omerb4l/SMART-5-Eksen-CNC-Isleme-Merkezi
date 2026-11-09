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

### S — Güçlü yönler (Strengths)
1. **Çok fonksiyonlu tek gövde:** Tornalama, şekillendirme, frezeleme ve zımparalama tek makinede; parça aktarımı ve el işçiliği azalır.
2. **5 eksen ve yatan freze kafası:** Karmaşık mobilya ayak formları tek bağlamada işlenebilir.
3. **Otomatik takım değişimi:** Operatörün takıma elle müdahalesi azalır (tehlike maruziyeti düşer).
4. **Yerli üretim ve ödüllü tasarım:** DREMA altın madalyası; üreticiye erişim ve servis kolaylığı.
5. **CNC kontrolü:** Tekrarlanabilir kalite, programlanabilir üretim; dijital iz sürme olanağı.
6. **Eğitim çıktısının gücü:** Risk analizi, tehlikeyi insana verilen zarar üzerinden ele alıyor (föyler LAB 1–7).

### W — Zayıf yönler (Weaknesses)
1. **Şeffaflık eksikliği:** Kontrol sistemi, Safety PLC/STO, ışık perdesi, yazılım ve SBOM bilgisi yayımlanmamış; doğrulanamayan emniyet iddiaları var.
2. **Yüksek tehlike yoğunluğu:** Dönen iş parçası, 7,5 kW kesici ve hareketli kafa aynı hacimde; fırlayan parça ve temas riski.
3. **Uzaktan bakım ve program aktarımı için tanımlı güvenli süreç görünmüyor** (USB/ağ ile NC aktarımı varsayımı; saha doğrulaması gerekli).
4. **Küçük/orta ölçekli üretici:** Siber güvenlik (62443, CRA) ve güvenlik açığı yönetimi için ayrılmış kaynak sınırlı olabilir.
5. **Toz yönetimi:** Ahşap tozu birikimi yanıcı ortam oluşturabilir; emiş sistemi arızası kritik.
6. **Yazılım ömrü:** Kontrol PC'si işletim sistemi ve bileşen yamalarının uzun vadeli desteği belirsiz.

### O — Fırsatlar (Opportunities)
1. **AB Makine Tüzüğü 2023/1230 ve CRA:** Uygunluk, ihracatta rekabet avantajı sağlar; "güvenli by design" bir satış argümanıdır.
2. **Güvenli uzaktan servis:** Jump server + VPN + MFA ile uzaktan teşhis, servis maliyetini ve duruş süresini azaltır.
3. **SBOM ve yama yönetimi:** Müşteriye şeffaf bileşen listesi güven yaratır.
4. **Tahminsel bakım ve veri analitiği:** İş mili ve takım aşınması izlenerek plansız duruş azaltılabilir.
5. **YZ destekli kalite kontrol:** Kamera ile yüzey kusuru tespiti; doğru fail-safe mimarisiyle verim artar.
6. **Mobilya sektörünün otomasyon talebi:** Nitelikli usta eksikliği 5 eksen otomasyona talebi artırıyor.
7. **Eğitim ve belgelendirme:** IEC 62443 / 62061 / ISO 13849 uyumlu ürün sertifikasyonu.

### T — Tehditler (Threats)
1. **Çalınmış servis hesabı / yetkisiz uzaktan erişim:** Emniyet parametrelerinin değiştirilmesi, fiziksel yaralanma (LAB 3 – R1, Kritik).
2. **USB ve değiştirilmiş NC programı:** Beklenmedik hareket, takım kırılması, parça fırlaması (R2).
3. **Fidye yazılımı:** CAD-CAM ve program arşivi şifrelenir, üretim durur (R5).
4. **Toz patlaması/yangını:** Emiş arızası veya devre dışı bırakılması (R4; S=3, öne alınır).
5. **Yasal yükümlülükler:** CRA bildirim süreleri (24 s / 72 s / 14 gün), CE ve makine tüzüğü; uyumsuzlukta satış ve cezai risk.
6. **Bilinen açıklar (CVE):** Üçüncü taraf bileşenlerdeki kritik açıkların yamalanamaması (LAB 5).
7. **Rakip üreticiler ve ithal makineler:** Siber güvenlik ve emniyet belgelerini öne çıkaran rakipler.
8. **YZ girdi manipülasyonu:** Sahte/bozuk kamera verisiyle yanlış kabul (LAB 7).

---

## 4. TOWS: stratejik çıkarımlar

| | **Fırsatlar (O)** | **Tehditler (T)** |
|---|---|---|
| **Güçlü (S)** | Otomasyon ve ödüllü tasarımı CRA/62443 uyumuyla birleştirip ihracatta öne çık | Takım değişimi ve kapalı hücre ile maruziyeti azalt; emniyeti kontrol yolundan ayır |
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
