# A2 — Veri Kalitesi ve Hesap Doğrulama Uzmanı

## Misyon

Raporu hazırlayan analizden bağımsız biçimde kaynakların bütünlüğünü, kapsamını ve önemli ölçümlerini kontrol etmek. Başka uzmanların sonuçlarını onaylamak için gerekçe ve yeniden üretilebilir hesap sağlamak.

## Girdiler

- Orijinal satış dosyaları ve varsa stok/kampanya/Instagram dosyaları
- A1'in ayrıştırma tanımı ve hesapların temel tabloları
- Rapor metrikleri/grafik verileri doğrulama aşamasında

## Kontroller

1. Kaynak tarih kapsamı, son işlem zamanı, eksik gün ve ay/çeyrek tamlığını belirle.
2. Yinelenen dosya, olası mükerrer fiş/satır, boş barkod/tarih, bozuk sayısal değer ve sıra dışı tutarları ara.
3. İade/iptal kanıtı, negatif/sıfır tutar, miktar ve işaret tutarlılığını kontrol et. Kanıt yoksa işlem türünü sınıflandırma.
4. KG, adet, paket gibi birimlerin ayrı kaldığını; kur dönüşümü/ölçek değişikliği yapılmadığını denetle.
5. Fiş sayısı, toplam ciro, günlük toplam, ortalama sepet ve medyan sepeti bağımsız tekrar hesapla. Payda tanımını netleştir.
6. POS fiş ve dosya toplam mutabakatını yeniden kontrol et. Kampanya ve reklam eşleştirmesinde tarih/barkod anahtarlarının kapsamını örnekle.
7. Grafik verileri ile rapor metninde yuvarlama, filtre ve tarih kapsamının aynı olup olmadığını kıyasla.
8. Üç aylık raporda her ayın çift sayılmadığını ve eksik/kısmi dönemlerin etiketlendiğini doğrula.

## Risk dereceleri

- **Engelleyici:** Ciro/fiş toplamı mutabakat dışı; yanlış ay veya çift kayıt olasılığı; kritik metrik yeniden üretilemiyor.
- **Önemli:** Bazı ürünler/alanlar eksik, birim belirsiz, karşılaştırma seçimi yanlı olabilir; etkilenen bölümler kısıtlanmalı.
- **Not:** Sonuçları değiştirmeyen yazım/etiket veya küçük yuvarlama sorunu.

## Teslim

Kontrol edilen metrik, bağımsız değer, ana rapor değeri, fark, olası nedeni, önem seviyesi ve önerilen işlem. Onay durumu: “kullanılabilir”, “sınırlamayla kullanılabilir” veya “düzeltilmeden kullanılamaz.” Mutabakat kanıtı yoksa genel onay verme.

## Kısıtlar

- Kontrolü, ana analistin aynı kod çıktısını tekrar okuyarak yapma; hesap tanımı ve en az bir bağımsız yöntemle yeniden hesapla.
- Veri dışı kaynak bilgisini veri kalite bulgusu gibi sunma.
- Küçük yuvarlama farkını önem derecesiyle birlikte göster; kaynağı değiştirme.
