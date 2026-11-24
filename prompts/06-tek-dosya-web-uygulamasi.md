# 06 · Tek dosya web uygulaması yazdırma

**Ne işe yarar:** Kurulum, sunucu ya da hesap gerektirmeyen, telefonda uygulama gibi çalışan küçük bir web aracı yazdırır: tek bir `index.html`, internetsiz çalışma ve ana ekrana ekleme desteği. GitHub Pages'te ücretsiz yayınlanır.

**Ne zaman kullanılır:**
- Küçük bir işletme ya da kendin için basit bir araç gerekiyor (sayaç, takip listesi, hesaplayıcı, kasa defteri).
- Sunucu kiralamak, veritabanı kurmak ya da kullanıcı hesabı yönetmek istemiyorsun.
- Fikri hızlıca denenebilir bir hale getirip bir bağlantıyla paylaşmak istiyorsun.

---

## Prompt

```text
Bana tek dosyalık bir web uygulaması yaz: [uygulamanın adı].

Kimin için: [ör. küçük bir kafenin sahibi, telefonundan kullanacak]
Ne yapmalı:
- [özellik 1]
- [özellik 2]
- [özellik 3]

Teknik kurallar:
- Tek bir index.html: HTML, CSS ve JavaScript aynı dosyada; dış kütüphane,
  yazı tipi ya da CDN yok.
- Veriler localStorage'da; her okuma/yazma try/catch içinde, depolama
  kapalıysa uygulama yine açılsın ve kullanıcıya söylesin.
- Telefon öncelikli: 320 px genişlikte yatay kaydırma olmasın,
  dokunma hedefleri en az 34 px.
- Açık ve koyu tema (prefers-color-scheme).
- PWA: manifest.webmanifest, sw.js (önce ağ, çevrimdışıyken önbellek) ve
  192/512 px ikon; ana ekrana eklenebilsin, internetsiz çalışsın.
- İlk açılışta boş ekran yerine "örnek verilerle dene" seçeneği olsun.
- Silme işlemleri "Geri al" ile telafi edilebilsin; tarayıcının
  confirm() penceresini yalnızca geri alınamaz işlerde kullan.
- Kullanıcı girdisini innerHTML ile basma (textContent kullan).
- Türkçe arayüz; tutarlar Türk lirası biçiminde (Intl.NumberFormat),
  ondalık girişte virgül de kabul edilsin.

Teslimden önce:
- Playwright ile uygulamayı aç, her özelliği gerçek tıklamalarla dene,
  hesapları kontrol et, sayfayı yenileyip verilerin durduğunu doğrula,
  çevrimdışı açılışı ve 320 px ekranı test et.
- Ekran görüntüsü al ve kendin bakarak kontrol et.
- Neyi test edemediğini (ör. gerçek telefonda dokunmatik) açıkça yaz.
```

---

## Neden işe yarıyor?

- **"Kimin için" satırı** tasarımı yönlendirir: "telefondan kullanan kafe sahibi" büyük düğmeler, hızlı giriş ve az metin demektir.
- **Tek dosya ve bağımlılıksızlık**, uygulamayı yıllarca çalışır tutar: kapanan bir CDN ya da güncellenen bir kütüphane onu bozamaz. GitHub Pages'e tek dosya yüklemek yeter.
- **try/catch kuralı**, gizli sekmede ya da depolaması kapalı tarayıcılarda uygulamanın beyaz ekranla açılmasını önler.
- **"Örnek verilerle dene"**, profiline gelen birinin uygulamayı bir dokunuşla dolu haliyle görmesini sağlar; boş bir ekran hiçbir şey anlatmaz.
- **"Geri al"**, yanlışlıkla silinen bir satışı kurtarır; her silmede çıkan onay penceresinden çok daha az yorucudur.
- **Teslim öncesi test**, "yazdım" ile "çalışıyor" arasındaki farkı kapatır (ayrıntı için bkz. [04 · Botla oyun ve uygulama denetimi](04-botla-oyun-denetimi.md)).

## Gerçek kullanım

- **[Pomodoro Görev Takipçisi](https://github.com/BMihci/pomodoro-gorev-takipcisi)**: sayaç, görev listesi, sürükleyerek sıralama ve haftalık odak grafiği. 20 otomatik kontrolle teslim edildi. İkinci sürümü geliştirirken günlük sayacın gece 03:00'te sıfırlandığı fark edildi (tarih UTC'ye göre hesaplanıyordu) ve yerel saate çevrildi.
- **[Kafe Stok ve Kasa Defteri](https://github.com/BMihci/kafe-stok-kasa-defteri)**: hızlı satış, gider, gün sonu kasa sayımı, stok uyarısı, Excel'e aktarma ve yedek. 55 kontrolün hepsi geçti; ekran görüntüsünde uzun bir gider açıklamasının tutarı alt satıra ittiği görülüp düzeltildi. Excel'e aktarılan dosyada `=` ile başlayan metinlerin formül olarak çalışmaması için önlem alındı.

## Uyarlama ipuçları

- Birden fazla kişinin aynı verilere erişmesi gerekiyorsa bu kalıp yetmez; o zaman bir veritabanı (ör. Supabase) ve kullanıcı girişi gerekir.
- Verilerin tek cihazda durduğunu kullanıcıya açıkça söyle ve "Yedeği indir" düğmesi koy.
- Service worker'daki önbellek adını her sürümde artır (`uygulama-v1` → `v2`), yoksa kullanıcılar eski sürümde kalır.
