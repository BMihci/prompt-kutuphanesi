# 03 · Push öncesi gizli bilgi taraması

**Ne işe yarar:** Bir projeyi herkese açık bir depoya yüklemeden önce içindeki şifreleri, API anahtarlarını, kişisel verileri ve yüklenmemesi gereken dosyaları buldurur; temiz bir kopya hazırlatır.

**Ne zaman kullanılır:**
- Bilgisayarında geliştirdiğin bir projeyi ilk kez GitHub'a koyacaksın.
- Projede bir veritabanı, bulut servisi ya da kullanıcı hesabı var.
- Projeyi yapay zekâ ile geliştirdin ve kodun her satırını tek tek okumadın.

---

## Prompt

```text
Bu projeyi HERKESE AÇIK bir GitHub deposuna yükleyeceğim. Yüklemeden önce
güvenlik ve gizlilik denetimi yap.

1. Tara ve raporla (henüz hiçbir şeyi değiştirme):
   - Koda gömülü şifreler, API anahtarları, token'lar, veritabanı adresleri
     (kaynak kod, yapılandırma, test, belge ve SQL dosyaları dahil).
   - Kişisel bilgiler: e-posta, telefon, ad-soyad, bilgisayara özel dosya
     yolları (C:\Users\... gibi).
   - Gerçek kullanıcı ya da müşteri verisi içeren dosyalar (Excel, CSV, JSON).
   - Yüklenmemesi gereken dosyalar: derleme çıktıları (.exe, dist/, build/),
     eğitilmiş modeller, sanal ortam, önbellek, yedek dosyalar.
   - Git geçmişinde iz: eski commit'lerde e-posta ya da silinmiş şifre.
   Her bulgu için: dosya, satır, risk düzeyi (yüksek/orta/düşük), öneri.

2. Benim onayımı bekle. Sonra temiz bir kopya hazırla:
   - Gerçek şifreleri demo değerlerle değiştir, anahtarları ortam
     değişkenine taşı.
   - Gerçek veri yerine açıkça "uydurma" diye etiketlenmiş küçük örnek veri koy.
   - .gitignore yaz; yüklenmeyecek dosyaları dışarıda bırak.
   - Orijinal dosyalarıma DOKUNMA, yalnızca kopyada çalış.

3. Son kontrol: temiz kopyada ilk adımdaki tüm bulguları tekrar ara ve
   hiçbirinin kalmadığını göster.

Ayrıca: depoyu temizlemek, canlı sistemdeki açığı kapatmaz. Gerçek şifrenin
değiştirilmesi ya da erişim kurallarının sıkılaştırılması gerekiyorsa bunu
ayrıca ve açıkça söyle.
```

---

## Neden işe yarıyor?

- **"Önce raporla, onay bekle"** sırası, modelin kendi başına dosya silmesini ya da önemli bir şeyi yanlışlıkla değiştirmesini önler. Hangi verinin gerçek olduğuna sen karar verirsin.
- **Taranacak yerlerin tek tek sayılması** önemlidir. Şifreler çoğu zaman ana kodda değil; test dosyalarında, kullanım kılavuzunda, SQL şemasında ya da mobil uygulamanın giriş ekranında unutulur.
- **"Orijinal dosyalara dokunma"** kuralı, bilgisayarındaki çalışan sürümü korur.
- **Son kontrol adımı**, temizliğin gerçekten yapıldığını gösterir; "temizledim" demekle yetinilmez.
- **Son paragraf** en çok atlanan noktadır: Depodan silinen bir şifre, uygulamanın kendisinde ya da veritabanında hâlâ geçerliyse risk sürer.

## Gerçek kullanım

**Kingfool Inc.** (kafe satış tahmini uygulaması) GitHub'a yüklenmeden önce bu denetimden geçti:
- Yönetici ve kullanıcı şifreleri beş ayrı dosyada düz metin olarak bulundu: ana uygulama, veritabanı şeması, kullanım kılavuzu, test dosyası ve Android giriş ekranı.
- Bulut veritabanı adresi ve anahtarı koda gömülüydü; veritabanı kuralları anahtarı bilen herkese okuma-yazma izni veriyordu.
- Yerel git geçmişinde kişisel e-posta adresi vardı. Geçmiş taşınmadı, depo tek ve temiz bir commit ile başladı.
- Gerçek satış dosyaları yerine 90 günlük uydurma örnek veri kondu.
- Son taramada 47 dosyanın hiçbirinde bulgu kalmadı. Canlı sistemdeki şifre değişikliği ve veritabanı kuralları ayrı bir iş olarak not edildi.

## Uyarlama ipuçları

- Komut satırı kullanabiliyorsan son kontrolü kendin de yap: `git grep -n "aranacak-kelime"` ile gerçek şifrenin bir parçasını ara.
- Bir şifre bir kez herkese açık depoya girdiyse silmek yetmez; şifreyi değiştir. Git geçmişi ve kopyalar onu saklamaya devam eder.
- Takım projelerinde bu promptu her yeni sürümden önce bir kontrol listesi olarak kullan.
