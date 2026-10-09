# MX-3 Garage 2.0 — GitHub Pages

## Mevcut siteyi güvenli güncelleme
1. GitHub repository'nde **inventory.json dosyasına dokunma**. Mevcut satın alma işaretlerin burada kalıyor.
2. Eski `index.html` içindeki `GITHUB_TOKEN` değerini yalnızca kendi bilgisayarında not et. **Token'ı kimseyle paylaşma.**
3. ZIP'ten `index.html`, `style.css`, `app.js`, `legacy-data.js`, `config.js` dosyalarını repo köküne yükle. Mevcut `index.html` değişecek.
4. `config.js` içindeki `TOKEN_BURAYA` değerini **senin mevcut fine-grained GitHub token'ınla** değiştir. İstersen owner/repo bilgilerini açıkça ayarlayabilirsin. Token'ın yalnızca bu repoya `Contents: Read and write` izni olmalı.
5. GitHub Pages güncellenmesini bekle; sonra Ctrl+Shift+R ile aç. `data/` dosyalarını **elle oluşturma zorunluluğu yok**: ilk yeni kayıtta GitHub API bunları oluşturur.
6. Dashboard'dan güncel kilometreyi ilk kez gir; geçmiş kayıtları doğrulamadan doldurma.

## Veri koruma
- `inventory.json` **aynı dosya ve aynı eski ID'lerle** okunur/yazılır. Eski listedeki 5 öncelik grubu ve Gunpla/Multimetre bilgileri aynen korundu.
- `data/vehicle.json`, `maintenance.json`, `service-plans.json`, `issues.json`, `expenses.json`, `fuel.json`, `reminders.json` kullanıcı veri dosyalarıdır. İlk kez kaydederken oluşturulurlar, mevcutlarsa son sürümleri korunur.
- Her kayıt kendi `id` değeriyle güncellenir. Aynı dosyada yarışan commit'ler için SHA çakışması algılanıp tekrar denenir. Aynı kaydın iki cihazda eş zamanlı düzenlenmesinde son kaydeden kazanır; Git geçmişinden eski veriye geri dönülebilir.
- Takım envanterinde eski `inventory.json` içindeki bilinmeyen alanlar ve bilinmeyen ID'ler korunur.
- `JSON yedek` veri JSON'larını dışarı çıkarır, **yüklenen fiziksel fotoğraf/PDF dosyalarını içermez**; onlar repodadır.
- Public GitHub repository'sinde **token ve yüklenen belgeler herkese açıktır**. Belgelerdeki kişisel bilgileri temizle.

## Kullanım
- Dashboard: Kilometre, masraf özeti, yaklaşan bakım ve tarihler.
- Bakımlar: Yapılmış bakım + ayrı periyodik bakım planı. Bakım aralıkları senin girdiğin değerlere göre değerlendirilir.
- Arızalar: Durum, önem, belirtiler, teşhis notu, belge.
- Takım Çantası: Var olan alışveriş işaretleri otomatik okunur/yazılır.
- Masraflar: Ayrı harcamalar; bakım ve yakıt masrafları iki kez sayılmaz.
- Yakıt: Tam depo esaslı yakıt tüketimi hesabı; aradaki kısmi dolumlar dahil.
- Tarihler: Muayene/sigorta son günleri (sayfa içi hatırlatma).
- Belgeler: Bakım/arıza/masraf/yakıt/tarih kayıtlarına fotoğraf/PDF eklenebilir; dosya başına 5 MB. Silinen kayıtların belgeleri otomatik silinmez.

## Sınırlamalar
- Anlık push bildirim / arka planda senkronizasyon yok; sayfayı açınca GitHub'dan veri okunur.
- GitHub yazma işlemleri bağlantı gerektirir; çevrimdışı değişiklikler kayıt işlemine kabul edilmez.
- Yeni kayıtların PDF ve görsel dosyaları tek tek GitHub'a commit edilir. Dosya yüklenip JSON kaydı başarısız olursa yetim dosya kalabilir.
- GitHub API büyük kayıt ve istek limitlerine tabidir. Çok yüksek hacimlerde ayrı depolama gerekir.
- Güncel km ilk kurulumda kullanıcı tarafından girilir. Tahmini değerler otomatik gerçek veri olarak kaydedilmez.
