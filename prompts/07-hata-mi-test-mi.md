# 07 · Hata mı, test mi? Hata ayıklatma

**Ne işe yarar:** Bir test başarısız olduğunda ya da program beklenmedik davrandığında modelin rastgele düzeltme denemesi yerine sorunu önce yeniden üretmesini, nedenini sınıflandırmasını ve en küçük doğru düzeltmeyi yapmasını sağlar.

**Ne zaman kullanılır:**
- Otomatik testlerden biri ya da birkaçı kırmızı döndü.
- "Bende çalışıyordu" dediğin bir şey başka bir ortamda bozuldu.
- Model bir hatayı düzelttiğini söylüyor ama aynı hata başka bir yerde geri geliyor.

---

## Prompt

```text
Şu sorun var: [başarısız testin adı / hata mesajı / beklenmeyen davranış]

Düzeltmeye geçmeden önce şu sırayı izle:

1. Yeniden üret: Sorunu en kısa adımlarla tekrar oluştur ve gerçek çıktıyı
   göster. Üretemiyorsan bunu söyle; tahminle düzeltme yapma.

2. Sınıflandır: Sorun hangisi?
   a) Uygulamada gerçek bir hata
   b) Testin kendisinde hata (yanlış beklenti, yanlış seçici, eksik adım)
   c) Ortam farkı (sürüm, saat dilimi, ekran boyutu, ağ, izinler)
   Kararının kanıtını göster: hangi satır, hangi değer, neden.

3. Testi uygulamaya uydurma: Testi değiştireceksen, eski beklentinin neden
   yanlış olduğunu açıkla. "Test geçsin diye" bir beklentiyi gevşetmek yok.

4. En küçük düzeltme: Yalnızca nedeni ortadan kaldıran değişikliği yap;
   ilgisiz yerleri "fırsat bu fırsat" diye yeniden yazma.

5. Doğrula: Önce başarısız olan testi, sonra TÜM testleri yeniden çalıştır
   ve sonucu göster. Düzeltme başka bir şeyi bozdu mu?

6. Raporla: Neden, sınıf (a/b/c), değişiklik ve hâlâ belirsiz kalan ne varsa.
```

---

## Neden işe yarıyor?

- **Önce yeniden üretmek**, "galiba şundandır" diye yapılan ve sorunu çözmeyen değişiklikleri engeller. Üretilemeyen bir hata, doğrulanamayan bir düzeltme demektir.
- **Üç sınıf (uygulama / test / ortam)** en sık yapılan iki hatayı önler: doğru çalışan uygulamayı "düzeltip" bozmak ve hatalı uygulamayı testi gevşeterek gizlemek.
- **"Kanıtını göster" şartı**, modelin sınıflandırmayı tahminle değil, gerçek değerlere bakarak yapmasını sağlar.
- **En küçük düzeltme**, gözden geçirmeyi kolaylaştırır ve yeni hata riskini azaltır.
- **Tüm testleri yeniden çalıştırmak**, bir yeri onarırken başka bir yeri bozmayı yakalar.

## Gerçek kullanım

- **[Kafe Stok ve Kasa Defteri](https://github.com/BMihci/kafe-stok-kasa-defteri)**: İlk test koşusunda kırmızı dönen kontrollerin hiçbiri uygulama hatası değildi.
  - Bir test, gün sonu kasa farkının 0 olmasını bekliyordu ama sayımdan sonra 380 TL'lik nakit stok alımı eklenmişti. Uygulama 380 TL'yi doğru gösteriyordu; yanlış olan testin beklentisiydi (sınıf b).
  - İki test, sınıfı olmayan satırlarda `null` dönen bir değeri ve HTML özelliği olarak hiç yazılmamış bir `value`'yu arıyordu (sınıf b). Testler düzeltildi, uygulamaya dokunulmadı.
- **[Pomodoro Görev Takipçisi](https://github.com/BMihci/pomodoro-gorev-takipcisi)**: Sürükleyerek sıralama testi başarısız oldu. Olay kaydı tutularak yeniden üretildiğinde sorunun sayfanın kaydırılmamış olması olduğu görüldü (sınıf c); testte listeyi ekrana getirmek yetti.
- **[Kingfool Inc.](https://github.com/BMihci/CafePredictionApp)**: Örnek veriyle çalıştırma, `ml_ops.py` dosyasının eksik iki `import` yüzünden bazı Python sürümlerinde hiç açılmadığını gösterdi (sınıf a). Düzeltme iki satırdı.

## Uyarlama ipuçları

- Testin yoksa önce sorunu yakalayan küçük bir test yazdır, sonra düzelt; aynı hata geri gelirse test haber verir.
- Ekranla ilgili sorunlarda "yeniden üret" adımına ekran görüntüsü ekletmek çok işe yarar.
- Saatle ilgili hatalarda (gün değişimi, saat dilimi) testi farklı saatlerde çalıştırmak için saati taklit eden araçları (ör. Playwright `clock`) iste.
