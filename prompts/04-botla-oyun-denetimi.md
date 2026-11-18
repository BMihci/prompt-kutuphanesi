# 04 · Botla oyun ve uygulama denetimi

**Ne işe yarar:** Bir web oyununu ya da uygulamasını otomatik bir test botuna (Playwright) baştan sona oynatır; hataları, takılan seviyeleri, bozuk ekranları ve konsol hatalarını buldurur. "Bende çalışıyor" yerine ölçülmüş bir sonuç verir.

**Ne zaman kullanılır:**
- Oyuna yeni bir mekanik, tema ya da sürüm ekledin ve eski şeylerin bozulmadığından emin olmak istiyorsun.
- Seviye sayısı elle oynanamayacak kadar arttı.
- Görsel bir değişiklikten sonra oyun mantığının aynı kaldığını doğrulamak istiyorsun.

---

## Prompt

```text
Bu web oyunu için Playwright ile çalışan bir DENETİM BOTU yaz ve çalıştır.

Bot şunları yapsın:
1. Oyunu telefon boyutunda aç (390×844) ve giriş ekranından oyuna gir.
2. Gerçek oyuncu gibi tıklayarak oyna: her seviyede hedefe ulaşmaya çalış.
   Kısayol olarak oyunun iç durumunu değiştirme; yalnızca okuyabilirsin.
3. Her seviye için kaydet: geçildi mi, kaç hamle sürdü, takıldıysa neden.
4. Şunları ayrıca kontrol et:
   - Tarayıcı konsolunda hata var mı?
   - Menüler, ayarlar, mağaza gibi pencereler açılıp kapanıyor mu?
   - Kayıt: sayfa yenilenince ilerleme korunuyor mu?
   - Ekran taşması: 320 px genişlikte yatay kaydırma çıkıyor mu?
5. Önemli ekranların görüntüsünü al ve kendin bakarak kontrol et.

Sonunda bana rapor ver:
- Özet tablo: seviye, sonuç, hamle sayısı.
- Bulunan hatalar: yeniden üretme adımlarıyla.
- Botun YAPAMADIĞI şeyler: bir seviyeyi bot geçemiyorsa bunun oyunun
  hatası mı yoksa botun stratejisinin sınırı mı olduğunu ayırt et;
  emin değilsen "elle oynanmalı" diye işaretle.
- Neyi test etmediğini açıkça yaz.
```

---

## Neden işe yarıyor?

- **"Gerçek oyuncu gibi tıkla"** kuralı, botun oyunun iç değişkenlerini değiştirip seviyeyi "hile ile" geçmesini engeller. Aksi halde bot her şeyi geçer ama hiçbir şey test edilmemiş olur.
- **Telefon boyutu ve 320 px kontrolü**, mobil oyunlarda en sık görülen sorunu (taşan butonlar, kaybolan menüler) yakalar.
- **"Botun yapamadığı şeyler" bölümü** raporun en değerli kısmıdır. Botun takıldığı yer bazen gerçek bir denge sorununa, bazen sadece botun saflığına işaret eder; ikisini karıştırmak yanlış düzeltmelere yol açar.
- **"Neyi test etmediğini yaz"** kuralı, yeşil bir raporun her şeyi kapsadığı yanılgısını önler.
- **Ekran görüntüsüne bakma** adımı, kodda doğru görünen ama ekranda bozuk olan şeyleri yakalar.

## Gerçek kullanım

- **Mesafeler Uçar Gider** (80 seviyelik merge oyunu): Denetim botu oyunu seviye seviye oynadı. Kedili bölümün başladığı 28-41. seviyeleri geçemedi; bu, botun sınırı olarak işaretlendi ve "arkasında gerçek bir denge sorunu olabilir, elle oynanmalı" diye açık işler listesine girdi. Görsel tema değişikliğinden sonra botun harita kontrolü renge baktığı için yanlış uyarı verdi; ders: kontrolleri renge değil, öğenin durumunu gösteren sınıfa bağla.
- **Kafe Stok ve Kasa Defteri** ve **Pomodoro Görev Takipçisi**: 55 ve 20 kontrollük testler; hesapların tutarlılığı, Excel dosyasının içeriği, yedekten geri yükleme, çevrimdışı açılış ve dar ekranda taşma. Uzun açıklamalı bir giderde tutarın alt satıra kaydığı ekran görüntüsünden fark edilip düzeltildi.
- **Recipes of Barista – 3D Deluxe**: Aynı yaklaşımla 60 sanal oyunculu bir simülasyon, oyun ekonomisini dengelemek için kullanıldı.

## Uyarlama ipuçları

- Rastgelelik içeren oyunlarda botu sabit bir tohumla (seed) çalıştır ki aynı hata tekrar üretilebilsin.
- Her yeni sürümden önce aynı botu yeniden çalıştır; testleri depoda `tools/` ya da `tests/` klasöründe sakla.
- Bot raporunu bir sonraki sohbete devir notunun ekiyle birlikte ver (bkz. [01 · Devir notu](01-devir-notu.md)).
