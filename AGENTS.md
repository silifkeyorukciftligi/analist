# Aylık satış raporu çalışma talimatı

Bu depo, Silifke mağazası için AktifPOS aylık satış analizlerinde kaynak talimatları içerir. Kullanıcı yeni ayın verilerini yüklediğinde bu talimatı uygula. Çalışma alanında alt ajanlar kullanılabiliyorsa aşağıdaki rolleri paralel yürüt; yoksa aynı kontrolleri sırayla yap ve raporda otomatik olarak ajan kullanıldığını iddia etme.

## Sabit bağlam

- Mağaza Silifke'de, şehir merkezinde ana cadde üzerindedir.
- Kullanıcının verdiği açılış tarihi 7 Ağustos 2026; 5–6 Ağustos deneme satışlarıdır.
- Kullanıcının verdiği okul açılış tarihi 14 Eylül 2026, ara tatil 16–20 Kasım 2026'dır. Bunları kullanıcı girdisi olarak etiketle; doğrulanmış resmi kaynak gibi sunma.
- Önceki aylara kıyaslama, ancak kullanıcı özellikle isterse yapılır. Aylık raporun kapsamını ay ve mevcut veri bitiş tarihiyle açıkça yaz.
- Türkçe yanıt ver. Grafik ve tabloları karar almaya yardımcı olacak ölçüde kullan.

## Roller ve iş tanımları

Rolleri birbirinden bağımsız çalıştır; her rolden bulgu, kullandığı kapsam, hesap tanımı, kaynak ve belirsizlikleri döndürmesini iste. Bir rol başka rolün sonucunu varsaymasın.

1. **POS veri ve fiş ayrıştırma:** AktifPOS Excel/CSV yapısını inceler; rapor başlıklarını, fiş bloklarını, satır kalemlerini, perakende/cari ayrımını, tarih-saat ve birimleri belirler. Fiş sayısını, satır sayısını ve dosya toplamlarıyla mutabakatı raporlar.
2. **Veri kalite ve bağımsız doğrulama:** Çift kayıt, eksik/bozuk tarih, miktar, tutar, negatif/iptal/iade, boş barkod, birim karışması ve kaynak kapsamını kontrol eder. Ana hesapları POS ayrıştırmasından bağımsız tekrarlar. Uyuşmazlık varsa çözülmeden rapor sonucunu onaylamaz.
3. **Satış zaman serisi ve takvim:** Gün/hafta günü/saat dilimi satışlarını çıkarır. Resmi tatil, okul takvimi, yerel sezon ve kullanıcı tarafından verilen etkinlikleri kaynak ve tarih etiketiyle iliştirir. Açık gün/eksik veri etkisini belirtir.
4. **Ürün ve sepet analizi:** Barkodu ana ürün anahtarı olarak kullanır; farklı barkodları ad benzerliğinden hareketle birleştirmez. Ciro, adet/kg, fiş penetrasyonu ve eşli ürün alımlarını hesaplar. Birlikte alım için destek sayısı ve payda verir; ürün stokta yokluğu veya yerleşim verisi olmadan neden ileri sürmez.
5. **Kampanya analizi:** Kampanya listesini başlangıç/bitiş, ürün, kampanya fiyatı ve koşula göre normalize eder; POS fiyatlarıyla ürün/tarih bazında karşılaştırır. Tarih belirsizliği, kısmi eşleşme ve referans dönem sınırlamalarını belirtir. Basit dönem farkını artımlı etki veya nedensellik olarak adlandırmaz.
6. **Instagram ve pazarlama:** Reklam raporunun tarih kapsamı, harcama, gösterim/tıklama ve yaratıcı içerik alanlarını inceler. Video konusu/tarihi biliniyorsa ürün veya kategori satışlarıyla zaman bazında eşleştirir. Günlük harcama veya reklam yayını verisi yoksa reklam ROAS'ı, reklamın satış etkisi veya nedensellik hesaplamaz; rapor eksiklerini listeler.
7. **Hava durumu ve dış etkenler:** Mağaza konumuna ve satış tarihine uygun günlük gözlemleri kullanır; istasyon, ölçüm türü ve kaynağı kaydeder. Tahmini/iklim normali/gözlem verisini birbirinden ayırır. Erişilebilir kaynak yoksa hava etkisi ölçülmüş gibi sunmaz.
8. **Rapor editörü ve denetçi:** Bulguları tek anlatıda birleştirir; her önemli sayı için kaynak ve payda izini kontrol eder. Grafik başlığı, birim, eksen, tarih aralığı, eksik günler ve küçük örneklem uyarılarını inceler. Kullanıcının o ay için koyduğu kıyaslama kısıtlarına uyar.

## Aylık çalışma sırası

1. Gelen dosyaların adını, sayfasını, kapsadığı tarihleri ve dosya kopyalarını envanterle. Kaynak dosyaları değiştirme; normalize edilmiş veriyi ayrı türet.
2. Şemayı örnekle; POS ayrıştırıcısını belirle. Fiş başlık/toplam sınırlarını doğrula. Kalemlerin fiş tutarlarına ve fişlerin kaynak genel toplamına mutabakatını yap. Hata veya belirsizlikleri kaydet.
3. Önce güvenilir temel metrikleri hesapla: perakende fiş, ciro, ortalama/medyan sepet, günlük satış ve kapsam. İade/iptal ayrıştırılamıyorsa açıkça belirt.
4. Saat, ürün, sepet, kampanya, Instagram, hava ve takvim modüllerini yalnızca gerekli kaynak ve yeterli kapsam varsa çalıştır. Ürün barkodu ve ölçü birimini koru.
5. Agent'ler bağımsız bulgularını teslim ettikten sonra editör ve doğrulama rolü toplamları, grafik girdilerini, metin iddialarını ve kullanıcının yönergelerini çapraz kontrol eder.
6. Raporu HTML veya kullanıcı isterse PDF/diğer formatta üret. Kaynak dosyaları, normalize tabloları, hesaplama kodunu ve raporu açıkça ayır; kaynak veride değişiklik yapma.
7. Sonuçta veri kapsamını, dahil/haricini, tanımları, mutabakatı, önemli sınırlamaları ve gözlem ile yorum ayrımını ver. Sonraki ay tekrarlanabilmesi için kullanılan dosya adlarını ve veri kesim tarihini yaz.

## Standart metrik kuralları

- Fiş adedi, kaynak raporun belge sınırlarından türetilir; fiş kimliği yoksa kaynak satır numarası yalnızca geçici anahtar olarak kullanılır.
- Perakende ve diğer cari satışları ayrı tut; yalnızca açıkça perakende olarak işaretlenmiş fişleri perakende metriğine dahil et.
- Fiş finansal toplamını korurken poşet, fiyat farkı ve genel indirim gibi satırları ürün sıralaması/sepet ürünü analizinden çıkar; çıkarılanları rapor yönteminde yaz.
- KG ve ADET gibi farklı birimleri tek toplam miktara toplama. Barkod yoksa ürün eşleşmesini belirsiz olarak işaretle.
- Ciro, fiş sayısı, ortalama sepet ve kategori paylarında payda ile dönemi belirt. Kısmi ayı tam ay gibi adlandırma.
- Birlikte alınan ürünler ilişkiyi gösterir; tek başına çapraz satış önerisinin etkisini kanıtlamaz.
- Reklam/kampanya öncesi-sonrası değişimini nedensel etki diye sunma; sezon, hava, hafta günü, stok, fiyat ve mağaza düzeni gibi karıştırıcıları hesaba kat veya sınır olarak açıkla.
- Hava durumu bağlantısına erişilemiyorsa gözlem uydurma; eksik veriyi ve etkilediği analizi açıkça belirt.

## Bu ay için görev kartı şablonu

Her raporda agent'lere şu isteği ver:

> Bu ayın satış raporuna katkı ver. Yalnızca sana atanan rolü incele. Kullanılan dosyaları ve tarih kapsamını belirt; bulguları tanım, hesap/payda ve kaynakla ver; veri kalite risklerini ve çıkarım sınırlarını yaz. Kaynakta olmayan veriyi tahmin etme. Başka aylara kıyaslamayı yalnızca kullanıcı açıkça isterse yap. Bulgu yoksa bunu açıkça söyle.
