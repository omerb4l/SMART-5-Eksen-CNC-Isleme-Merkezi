# SMART 5 Eksen CNC İşleme Merkezi
## LAB 7 · AI Safety Challenge — AI Fail-Safe Decision
**Hazırlayan:** Ömer Bal – 230541108

> Üretici, SMART'ta yapay zekâ kullanıldığını belirtmemiştir. Bu föy, makineye **eklenebilecek** bir YZ uygulamasını varsayar: kamera ile ahşap yüzey/ayak parçası kalite kontrolü ya da otomatik takım yolu/parametre önerisi.

**Akış:** Kamera → YZ modeli → OK / RED → Parametre/karar → Makine

**Kavram — Prediction ≠ Safety:** YZ karar üretir; güvenliği garanti eden mimari YZ'nin **dışında** tanımlanır (fail-safe, human override, monitoring, confidence threshold, fallback).

### 1. Model yanlış sınıflandırdı (kusurlu parçaya OK verdi)
Sistem tek başına karar vermemeli. **İkinci kontrol** (ölçüm/örnekleme) ve kritik parçalarda **insan onayı** olmalı. YZ'nin kararı hiçbir zaman emniyet fonksiyonunu devre dışı bırakmamalı; hatalı parça en fazla kalite sorunudur, ama YZ'nin ürettiği parametre insana zarar verebiliyorsa sınır kontrolü gerekir.

### 2. Girdi manipüle edildi (bozuk/sahte kamera verisi)
**Fark etme:** Görüntü kalitesi/histogram sapması, beklenmeyen aydınlatma, tekrar eden/dondurulmuş kare, referans parçayla tutarsızlık, sensör sağlık kontrolü. **Şüpheli girdide:** karar reddedilir, hat güvenli duruma alınır veya insan incelemesine yönlendirilir, olay kaydedilir.

### 3. Confidence düştü
**Eşik:** Örneğin %90 altı "emin değil" kabul edilir (eşik pilot veriyle kalibre edilir, burada örnek değerdir). **Altında:** otomatik kabul **yok**; parça ayrılır ve **insana sorulur**; tekrarlarsa **fallback** (manuel kontrol / sabit güvenli parametre).

### Karar tablosu — AI Fail-Safe Decision

| Başarısızlık | Güvenli davranış (kavram) |
|---|---|
| Model yanlış sınıflandırdı | İkinci kontrol + insan onayı (**human override**), sonuç izleme (**monitoring**) |
| Girdi manipüle edildi | Girdi doğrulama, şüphede durdur / reddet (**fail-safe**), olay kaydı |
| Confidence düştü | Eşik altında otomatik kabul yok (**confidence threshold**), insana sor, manuel kontrol (**fallback**) |

**Çıktı → AI Fail-Safe Decision (EP 03 + EP 15)**
