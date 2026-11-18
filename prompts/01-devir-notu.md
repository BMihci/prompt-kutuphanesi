# 01 · Devir notu yazdırma

**Ne işe yarar:** Uzun bir yapay zekâ sohbetinde biriken proje bilgisini tek bir belgeye döker. Bu belgeyi yeni bir sohbete ya da başka bir geliştiriciye verdiğinde iş kaldığı yerden devam eder.

**Ne zaman kullanılır:**
- Sohbet çok uzadı, model eski ayrıntıları karıştırmaya başladı.
- Projeyi başka bir araca, modele ya da kişiye taşıyacaksın.
- Birkaç gün ara vereceksin ve döndüğünde nereden başlayacağını bilmek istiyorsun.

---

## Prompt

```text
Bu projeyi yeni bir konuşmaya (ya da başka bir geliştiriciye) devredeceğim.
Kaldığımız yerden hiç soru sormadan devam edebilmesi için bir DEVİR NOTU yaz.

Kurallar:
- Yalnızca bu konuşmada gerçekten yapılmış ve doğrulanmış şeyleri yaz.
  Emin olmadığın bir şeyi "doğrulanmadı" diye işaretle; tahmin yürütme.
- Kısa ve taranabilir olsun: başlıklar, maddeler, gerektiğinde tablo.
- Dosya adlarını, komutları, dal adlarını ve adresleri birebir yaz.
- Şifre, API anahtarı ya da kişisel bilgi YAZMA; gerekiyorsa "nerede durduğunu" belirt.

Şu bölümleri kullan:
1. Proje nedir: tek paragraf; amaç, hedef kitle, teknoloji.
2. Nerede duruyor: depo adresi, dallar, yayın/demo adresi.
3. Dosya yapısı: hangi dosya ne işe yarar (tablo).
4. Bilinmesi gereken iç yapı: kritik fonksiyonlar, veri modeli, tuzaklar.
5. Sürüm geçmişi: her sürümde ne değişti (kısa).
6. Açık işler ve bilinen sorunlar: numaralı liste, en önemlisi en üstte.
7. Yeni sürüm çıkarma adımları: kopyala-yapıştır uygulanabilir sırayla.
8. Çalışma tercihlerim: dil, yanıt biçimi, kaçınılacak şeyler.

En üste tarih ve güncel sürüm numarasını yaz. Notu Markdown olarak ver.
```

---

## Neden işe yarıyor?

- **"Hiç soru sormadan devam edebilmesi" hedefi**, modele notun kime ve neye hizmet ettiğini söyler. Gereksiz anlatıyı keser, eksik bilgiyi görünür kılar.
- **"Doğrulanmadı" işareti**, modelin boşlukları uydurarak doldurmasını engeller. Devir notundaki tek bir yanlış bilgi, yeni sohbette saatlerce yanlış yöne gidilmesine yol açabilir.
- **Sabit bölümler**, her projede aynı yapıda not üretir. Birkaç projeyi paralel yürütürken hangi bilginin nerede olduğunu hemen bulursun.
- **"Açık işler" en önemlisi en üstte** olduğu için yeni sohbet ilk mesajda doğru işe başlar.
- **Gizli bilgi yasağı**, not başka yerlere kopyalandığında şifrelerin sızmasını önler.

## Gerçek kullanım

- **Mesafeler Uçar Gider** (merge oyunu): v14 sürümünde yazılan not; 12 kaynak dosyanın birleştirme sırasını, sürüm geçmişini, yeni sürüm çıkarma adımlarını ve 7 açık işi içeriyordu. Not başka bir konuşmaya verildiğinde, orada oyunu görmeden hazırlanmış bir README taslağı vardı. Not, depodaki README'nin zaten daha kapsamlı olduğunu (ekran görüntüleri, demo bağlantısı, sürüm listesi) gösterdi ve taslağın onun üzerine yazılması önlendi.
- **Recipes of Barista – 3D Deluxe**: public ve private iki depo arasındaki "public her zaman bir önceki sürüm" kuralını ve hangi bilginin herkese açık depoda bulunmaması gerektiğini not üzerinden aktardı.

## Uyarlama ipuçları

- Kod dışı projelerde (yazı, araştırma) 3. ve 7. bölümleri "kaynaklar" ve "sonraki adımlar" ile değiştir.
- Not çok uzarsa ikiye böl: kısa bir "devir notu" ve ayrıntılı bir "teknik ek".
- Yeni sohbete verirken ilk mesaja şunu ekle: "Bu notu oku, anladıklarını üç maddede özetle, sonra 6. bölümdeki ilk işe başla."
