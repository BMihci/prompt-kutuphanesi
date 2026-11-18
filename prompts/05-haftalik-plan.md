# 05 · Haftalık iş planı çıkarma

**Ne işe yarar:** Elindeki projeleri ve gerçekten ayırabildiğin zamanı alıp günlere bölünmüş, uygulanabilir bir haftalık plan çıkarır. Büyük hedefi (örneğin "GitHub profilimi geliştirmek") her gün atılabilecek küçük adımlara çevirir.

**Ne zaman kullanılır:**
- Aklında çok proje var ama hangisinden başlayacağını bilmiyorsun.
- Düzenli üretmek istiyorsun ama vaktin sınırlı ve değişken.
- Geçen hafta planladığının yarısını yapabildin ve planı yeniden kurman gerekiyor.

---

## Prompt

```text
Bana gerçekçi bir HAFTALIK PLAN çıkar.

Hedefim: [ör. GitHub profilimi düzenli projelerle doldurmak]
Öne çıkarmak istediğim alanlar: [ör. oyun geliştirme, küçük işletmeler için yazılım]
Ayırabildiğim zaman: [ör. haftada 2-3 gün 1-2 saat, diğer günler 15 dakika]
Elimdeki projeler ve durumları: [liste]
Geçen haftadan kalanlar: [liste ya da "yok"]

Kurallar:
- Planı tabloyla ver: gün, süre, iş. Uzun günler ile kısa günleri dengele.
- Her iş o gün BİTİRİLEBİLİR olsun; bitmeyecek bir işi ikiye böl.
- Her günün sonunda elle tutulur bir çıktı olsun (bir dosya, bir commit,
  yayınlanmış bir sayfa).
- Benim yapmam gerekenleri (hesap açmak, ayar yapmak, onay vermek) senin
  yapabileceklerinden ayır ve açıkça yaz.
- Geçen haftadan kalan iş varsa önce onu yerleştir.
- Plan bozulursa ne yapacağımı tek cümleyle söyle.
- Her gün için bana gelirken ne getirmem gerektiğini yaz.
```

---

## Neden işe yarıyor?

- **Ayırabildiğin zamanı açıkça vermek**, modelin hayali bir planla değil senin gerçek takviminle çalışmasını sağlar. "Haftada 2-3 gün" ile "her gün 8 saat" çok farklı planlar üretir.
- **"O gün bitirilebilir" kuralı**, yarım kalan işlerin birikmesini önler. Her gün bir şeyi tamamlamak motivasyonu korur.
- **"Elle tutulur çıktı"** şartı, planı ölçülebilir kılar: commit atıldı mı, sayfa yayında mı?
- **Senin işlerin ile modelin işlerini ayırmak**, en sık yaşanan aksamayı önler: Model bir şeyi hazırlar ama yayınlamak için senin açman gereken bir hesap ya da depo yoktur.
- **"Bana gelirken ne getir"** satırı, her oturumun ilk dakikalarını hazırlıkla değil işle geçirmeni sağlar.
- **"Plan bozulursa"** cümlesi, bir günü kaçırınca bütün planın çöpe gitmesini engeller.

## Gerçek kullanım

Bu kütüphane, bu promptla çıkarılan planın bir parçası olarak yazıldı. İki hafta boyunca:
- 1. hafta: profil README'si, iki oyunun vitrin sayfaları, sıfırdan bir Pomodoro uygulaması ve Kingfool'un güvenli biçimde yayınlanması.
- 2. hafta: Kafe Stok ve Kasa Defteri ile bu prompt kütüphanesi.

Planın kaçırılan bir günü olduğunda (salı) iş ertesi güne kaydırıldı ve iki günün işi tek oturumda bitti; planın "bozulursa kaydır" kuralı tam olarak bu durum için.

## Uyarlama ipuçları

- Pazar günü kısa bir kapanış oturumu ekle: ne bitti, ne kaldı, yeni hafta ne olacak.
- Planı profil README'sinde ya da bir notta "Bu hafta" listesi olarak tut; işaretlemek ilerlemeyi görünür kılar.
- Haftada bir gün "boş gün" bırak; plan her zaman biraz kayar.
