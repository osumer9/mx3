# MX-3 Garaj Envanteri — GitHub senkronizasyonlu

## Kurulum
1. Bu klasördeki `index.html` ve `inventory.json` dosyalarını boş GitHub repository’nin **ana dizinine** yükle (Add file → Upload files → Commit changes).
2. Settings → Pages → Build and deployment: `Deploy from a branch`, branch `main`, folder `/(root)` seç.
3. Siteyi aç; kullanıcı adı/repo bilgileri GitHub Pages adresinden otomatik doldurulur.
4. GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token. Repository access olarak yalnızca kendi repository’ni seç. Repository permissions altında **Contents: Read and write** ver. Bir bitiş tarihi seç. Token’ı kopyala.
5. Sitede token’ı gir ve `GitHub'a bağlan ve listeyi çek` de. İşaretlediğin her değişiklik `inventory.json` dosyasına GitHub commit'i olarak kaydedilir. Diğer cihazlarda da aynı hesabın token’ıyla bağlan.

## Güvenlik ve sınırlamalar
- Token **koda, inventory.json'a veya localStorage'a yazılmaz**; sayfanın JS belleğinde kalır. Yenilemede tekrar girmen gerekir.
- Public GitHub Pages sitesi herkese açık olabilir; JSON da public repoda görülebilir. Bu listede özel bilgi tutma.
- İnternet yokken veya token girmeden yapılan işaretlemeler yerel tarayıcıda saklanır. **Sonradan bağlanınca GitHub'daki liste esas alınır**; bağlantı öncesi yerel değişiklikler otomatik yüklenmez. Önceden yaptığın işaretleri korumak için önce yedek al.
- Aynı anda iki cihazdan yapılan değişikliklerde API çakışması yeniden okunarak birleştirilmeye çalışılır; anlık iki yönlü canlı güncelleme yoktur, diğer cihaz `GitHub'dan yenile` yapmalı ya da sayfayı yeniden açıp bağlanmalıdır.
- GitHub API'nin `main` branch üzerinde yazma izni olmalı. Korunan branch ya da farklı varsayılan branch kullanıyorsan `index.html` içindeki `branch:'main'` değerini değiştir.
- Tarayıcıda çalışırken erişim token'ını asla URL'ye, GitHub commit'ine veya paylaşılan ekran görüntüsüne ekleme.
