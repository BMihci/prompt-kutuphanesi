# 02 · Proje için README hazırlatma

**Ne işe yarar:** Bir projeyi GitHub'da vitrine çıkaracak README'yi yazdırır: ne yaptığını birkaç saniyede anlatan, denemeyi kolaylaştıran ve projenin sınırlarını dürüstçe söyleyen bir sayfa.

**Ne zaman kullanılır:**
- Bitmiş ya da çalışan bir prototipi herkese açık depoya koyacaksın.
- Mevcut README sadece başlıktan ibaret ya da teknik notlarla dolu.
- Profilinde sabitleyeceğin bir depoyu ziyaretçiye hazır hale getirmek istiyorsun.

---

## Prompt

```text
Bu proje için GitHub README'si yaz. Okuyucu, projeyi ilk kez gören biri:
bir işveren, bir müşteri ya da projeyi denemek isteyen bir geliştirici.

Önce projeyi incele (dosyalar / devir notu ekte). Sonra README'yi şu sırayla kur:
1. Başlık ve tek cümlelik açıklama: ne yapar, kimin işine yarar.
2. Varsa "Hemen dene / Oyna" bağlantısı, en üstte.
3. Ekran görüntüleri için yer (ben ekleyeceğim; dosya adlarını öner).
4. Neler yapar: en fazla 8 madde; her madde "özellik: faydası" biçiminde.
5. Hızlı başlangıç: kopyala-yapıştır çalışan en kısa komutlar.
6. Proje yapısı: önemli dosyalar ve ne işe yaradıkları.
7. Bilinen sınırlar / yol haritası: dürüst bir liste.
8. Kısa İngilizce özet (3-4 cümle).

Kurallar:
- Projede GERÇEKTEN olan özellikleri yaz. Göremediğin ya da emin olmadığın bir
  özelliği listeye koyma; bana ayrıca "kontrol et" diye sor.
- Örnek çıktı koyacaksan uydurma; çalıştırıp gerçek çıktıyı kullan ya da
  "örnek" olduğunu açıkça yaz.
- Pazarlama dili kullanma ("devrim niteliğinde", "en iyi" vb.).
- Şifre, API anahtarı, kişisel dosya yolu ya da e-posta adresi geçmesin.
- Türkçe yaz; teknik terimleri gerekiyorsa parantez içinde İngilizce ver.
```

---

## Neden işe yarıyor?

- **Okuyucuyu tanımlamak** ("ilk kez gören biri"), modelin geliştirici notları yerine ziyaretçiye hitap eden bir metin yazmasını sağlar.
- **Sabit sıra**, en önemli şeyleri (ne yapar, nasıl denenir) en üste koyar. Ziyaretçilerin çoğu ilk ekranın altına inmez.
- **"Gerçekten olan özellikler" kuralı** en kritik satırdır. Model, konuşmada geçen istekleri yapılmış özellik gibi listelemeye çok yatkındır. Bu kural olmadan README, projede olmayan şeyleri vaat edebilir.
- **"Bilinen sınırlar" bölümü** güven verir. Prototip olduğunu açıkça söyleyen bir proje, her şeyi mükemmel gösteren bir projeden daha inandırıcıdır.
- **Gizli bilgi kuralı**, README'nin kendisinden bilgi sızmasını önler (kod taraması için bkz. [03 · Gizli bilgi taraması](03-gizli-bilgi-taramasi.md)).

## Gerçek kullanım

- **Kingfool Inc. — Kafe Satış Tahmini**: README'ye bir kafe sahibinin anlayacağı bir "Neler yapar?" tablosu, gerçek çalıştırma çıktısıyla bir "Hızlı deneme" bölümü, uydurma olduğu açıkça yazılan örnek veri ve dürüst bir "Bilinen sınırlar" listesi girdi.
- **Kafe Stok ve Kasa Defteri** ve **Mesafeler Uçar Gider**: en üste canlı demo bağlantısı ve üç ekran görüntüsü yan yana kondu.

Bu promptun ilk sürümü "gerçekten olan özellikler" kuralını içermiyordu. Oyunu görmeden, yalnızca konuşmada istenenlere bakarak yazılan bir README, yapılıp yapılmadığı bilinmeyen özellikleri de listeledi; kural o deneyimden sonra eklendi.

## Uyarlama ipuçları

- Oyunlarda 5. bölümü "Nasıl oynanır?" ile değiştir.
- Ticari bir projede lisans satırını açıkça iste ("Tüm hakları saklıdır" ya da açık kaynak lisansı).
- Ekran görüntülerini README'den önce hazırla; görselli bir README, görselsiz olandan çok daha fazla ilgi görür.
