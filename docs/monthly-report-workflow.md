# Aylık raporlarda agent rolleri

Bu belge, `AGENTS.md` içindeki çalışma talimatının pratik özetidir. Agent'ler her yeni görev oturumunda yeniden çağrılabilir; depo dosyaları role yönelik kalıcı talimatları saklar, agent örneklerinin veya görev hafızasının kendisini saklamaz.

## İş bölümü

| Rol | Girdi | Teslim |
|---|---|---|
| POS ayrıştırma | AktifPOS aylık satış dosyaları | Şema, fiş tanımı, perakende/cari ayrımı, toplam mutabakatı |
| Veri kalite/doğrulama | Kaynak dosyalar ve türetilmiş tablolar | Kapsam, tutarsızlıklar, bağımsız metrik kontrolü |
| Zaman/takvim | Günlük fişler ve tarih bağlamı | Gün-saat desenleri, takvim olayları ve tarih kaynağı |
| Ürün/sepet | Barkodlu kalemler ve varsa stok listesi | Ürün sıralaması, miktar/birim, eşli ürün sepetleri |
| Kampanya | Kampanya takvimi ve POS kalemleri | Eşleşme, fiyat kontrolü, karşılaştırma sınırları |
| Instagram | Reklam ve video yayın bilgisi | Zamanı ve içeriği eşleşen tanımlayıcılar, eksik alanlar |
| Hava durumu | Konum ve satış tarihleri | İstasyon/kaynak bilgili gözlemler veya veri erişim engeli |
| Editör/denetçi | Tüm rol çıktıları ve kullanıcı isteği | Tutarlı anlatı, grafik denetimi, iddia ve sınır kontrolü |

## Aylık kullanıcıdan beklenen girdiler

- AktifPOS fiş detayları (Excel tercih edilir; CSV de olabilir) ve rapor tarih aralığı.
- Varsa güncel stok/katalog dosyası (barkod, ürün adı, kategori, birim, stok).
- Kampanya başlangıç/bitiş tarihleri, indirim fiyatları ve hangi ürünlere uygulandığı.
- Instagram video yayın günü/saati/konusu ile reklamın başlama-bitiş günü, hedefi ve harcaması.
- Varsa mağaza düzeni değişikliklerinin tarihi, ürün sergileme yeri ve stokta yok kalınan dönem.
- Kullanıcının istediği kıyaslama kapsamı ve önemli yerel/takvim bilgileri.

Eksik alanlar raporu durdurmaz; ilgili analiz daraltılır ve ölçülemeyen sonuç açıkça belirtilir.

## Devamlı kullanım

Her yeni ayda bu depodaki `AGENTS.md` talimatlarını uygula ve yeni dosyalarla yalnızca ilgili rolleri görevlendir. Herhangi bir rol/başlık değişikliği gerekiyorsa `AGENTS.md` güncellenir; rapor çıktıları kendi ay klasöründe tutulur. Bu rol seti kalıcı, bağımsız arka plan agent'leri oluşturmaz; agent'lerin her oturumda kullanılabilirliği çalışma ortamındaki multi-agent özelliğine bağlıdır.
