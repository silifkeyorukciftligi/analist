# Silifke mağaza satış analizi agent rolleri

Bu klasör, AktifPOS aylık ve üç aylık satış analizlerinde tekrar kullanılacak rol tanımlarını içerir. Dosyalar kalıcı talimatlardır; agent oturumlarını kendileri başlatmaz. Her yeni görevde ana koordinatör, kullanıcı isteğine ve mevcut verilere göre ilgili rolleri çağırır. Bir oturumda alt-agent özelliği yoksa görevler sırayla yürütülür ve rapor bunu dürüstçe belirtir.

## Roller

| Kod | Agent | Rol belgesi | Kullanım |
|---|---|---|---|
| A0 | Rapor Yöneticisi / Ana Koordinatör | [coordinator.md](coordinator.md) | Her görevde; kapsamı belirler, işleri böler, birleştirir |
| A1 | POS Veri Uzmanı | [pos-data.md](pos-data.md) | Her satış dosyasında; fiş ve ürün satırlarını ayrıştırır |
| A2 | Veri Kalitesi ve Hesap Doğrulama Uzmanı | [data-quality.md](data-quality.md) | Her analizde; bağımsız kontrol yapar |
| A3 | Satış Zamanı ve Takvim Uzmanı | [sales-time-calendar.md](sales-time-calendar.md) | Gün/saat ve takvim incelemesinde |
| A4 | Ürün ve Sepet Analizi Uzmanı | [product-basket.md](product-basket.md) | Ürün, kategori ve birlikte alım incelemesinde |
| A5 | Kampanya ve Fiyat Uzmanı | [campaign-pricing.md](campaign-pricing.md) | İndirim/kampanya dosyası varsa |
| A6 | Instagram Reklam ve Pazarlama Uzmanı | [instagram-marketing.md](instagram-marketing.md) | Video/reklam verisi varsa |
| A7 | Hava Durumu ve Dış Etken Uzmanı | [weather-external.md](weather-external.md) | Hava veya dış etken analizi istenmiş ve veri erişilebilir olduğunda |
| A8 | Rapor Editörü ve Görsel Denetçi | [report-editor.md](report-editor.md) | Her nihai/ara raporda; anlatı ve görselleri kontrol eder |

## Döneme göre kullanım

- **Ay tamamlanmadan:** `Geçici aylık rapor` üret; son veri tarihini başlıkta göster. Yeni fişler gelince aynı ayı güncelle.
- **Ay tamamlandıktan sonra:** `Nihai aylık rapor` üret; dosya kapsamının ayın tamamını içerdiğini doğrula.
- **Üç aylık rapor:** Üç ayın her birini aynı tanımlarla doğrula; sonra dönem toplamı, aylık eğilim, gün/ürün/kampanya/reklam bulgularını birleştir. Eksik veya kısmi ayları dönem toplamında açıkça işaretle.
- Başka aylarla kıyaslamayı veya önceki raporlara atıf yapmayı, kullanıcı kapsamı izin veriyorsa yap.

## Agent'lere ortak görev talimatı

Her uzman yalnızca atanmış rolü inceler ve şu şablonla döner:

1. İncelenen dosyalar ve tarih/kayıt kapsamı
2. Yöntem, tanımlar ve hesap/payda
3. Bulgu ve kaynağı
4. Veri kalite riski veya çözülemeyen soru
5. Sonucun güven sınırı; nedensel yorum yapılabiliyor mu?
6. Koordinatöre önerilen sonraki adım

Her uzman kaynağa dayalı bulgu vermeli; olmayan alanı tahmin etmemeli. Başka uzmanın çıktısını görmeden bağımsız hesap yapması istenen görevlerde, bulgularını önce bağımsız teslim etmelidir.
