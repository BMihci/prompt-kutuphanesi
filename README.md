# 🧠 Prompt Kütüphanesi

Yapay zekâ ile oyun, uygulama ve küçük işletme yazılımı geliştirirken **gerçekten kullandığım** prompt kalıpları. Her biri kopyala-yapıştır hazır; yanında neden işe yaradığı ve hangi projede nasıl sonuç verdiği yazıyor.

Türkçe, Claude ve benzeri sohbet tabanlı modellerle denenmiştir.

---

## Promptlar

| # | Prompt | Ne işe yarar? |
|---|---|---|
| 01 | [Devir notu yazdırma](prompts/01-devir-notu.md) | Uzun bir sohbetteki proje bilgisini tek belgeye döker; yeni sohbet kaldığı yerden devam eder. |
| 02 | [README hazırlatma](prompts/02-readme-hazirlatma.md) | Projeyi GitHub vitrinine çıkaran, dürüst ve denemesi kolay bir README yazdırır. |
| 03 | [Push öncesi gizli bilgi taraması](prompts/03-gizli-bilgi-taramasi.md) | Herkese açık depoya yüklemeden önce şifre, anahtar ve kişisel veriyi buldurur; temiz kopya hazırlatır. |
| 04 | [Botla oyun ve uygulama denetimi](prompts/04-botla-oyun-denetimi.md) | Oyunu ya da uygulamayı otomatik test botuna oynatıp hataları ölçülmüş bir raporla çıkarır. |
| 05 | [Haftalık iş planı çıkarma](prompts/05-haftalik-plan.md) | Projeleri ve ayırabildiğin zamanı günlere bölünmüş, bitirilebilir bir plana çevirir. |

Yeni promptlar haftalık olarak eklenir.

---

## Nasıl kullanılır?

1. Prompt dosyasını aç, **Prompt** bölümündeki metni kopyala.
2. Köşeli parantezli yerleri (`[ör. ...]`) kendi projenle doldur.
3. Gerekli dosyaları (kod, devir notu, ekran görüntüsü) sohbete ekle ve gönder.
4. Sonucu "Uyarlama ipuçları" bölümüne göre ince ayarla.

---

## Bu promptların ortak ilkeleri

Kütüphanedeki her prompt aynı birkaç ilkeye dayanır:

- **Okuyucuyu ve amacı söyle.** "README yaz" yerine "projeyi ilk kez gören bir işveren için README yaz."
- **Uydurmayı yasakla, belirsizliği işaretlet.** "Emin olmadığın şeyi 'doğrulanmadı' diye işaretle." Model boşlukları doldurmaya yatkındır; bu tek kural birçok hatayı önler.
- **Çıktının biçimini önceden tanımla.** Sabit bölümler, tablolar ve sıralama, her seferinde karşılaştırılabilir sonuç verir.
- **Riskli işlerde önce rapor, sonra onay.** Model dosya silmeden ya da değiştirmeden önce ne bulduğunu göstersin.
- **Doğrulamayı işin parçası yap.** "Temizledim" değil, "temizledikten sonra tekrar taradım, sonuç şu."
- **Sınırları söylet.** "Neyi test etmediğini yaz." Yeşil bir rapor, neyi kapsamadığını da söylemelidir.

---

## Bu promptlarla yapılan projeler

- [Mesafeler Uçar Gider](https://github.com/BMihci/mesafeler-ucar-gider): uzak mesafe temalı merge oyunu
- [Recipes of Barista – 3D Deluxe](https://github.com/BMihci/recipes-of-barista): 3D slot ve hikâye oyunu
- [Kingfool Inc. — Kafe Satış Tahmini](https://github.com/BMihci/CafePredictionApp): makine öğrenmesiyle satış tahmini
- [Kafe Stok ve Kasa Defteri](https://github.com/BMihci/kafe-stok-kasa-defteri): küçük kafeler için kasa ve stok takibi
- [Pomodoro Görev Takipçisi](https://github.com/BMihci/pomodoro-gorev-takipcisi): odak sayacı ve görev listesi

---

Promptları kendi projelerinde serbestçe kullanabilirsin.

© 2026 Barış Mıhçı
