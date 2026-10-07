# Üçyıldız Kitabevi Sipariş — Gizlilik Politikası

Bu depo, **Üçyıldız Kitabevi Sipariş** uygulamasının (`com.ucyildizkitabevi.siparis`; iOS, Android, Windows)
gizlilik politikası sayfasını içerir. Sayfa GitHub Pages ile yayımlanır ve adresi App Store Connect'teki
**Privacy Policy URL** alanına girilir. Uygulamanın kaynak kodu bu depoda değildir.

Yürürlük tarihi: **7 Ekim 2026**

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `index.html` | Politika sayfası. Tek dosyadır, dış CSS/JS/font kullanmaz, çevrimdışı da açılır. Türkçe metnin altında Apple incelemecisi için "Summary in English" bölümü vardır. |
| `.nojekyll` | GitHub Pages'in Jekyll işlemesini kapatır, böylece dosya olduğu gibi yayımlanır. |
| `.gitignore` | İşletim sistemi artık dosyalarını dışarıda tutar. |

## Yayımlama

GitHub → depo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / `(root)`.
Adres `https://<kullanıcı>.github.io/<depo>/` biçiminde olur.

## İletişim e-postası

Sayfadaki `[İLETİŞİM E-POSTASI]` yer tutucusu **`bilgi@ucyildizkitabevi.com`** ile dolduruldu. Adres 3 yerde
`mailto:` bağlantısı olarak geçer: sayfa başındaki kısa özet, 7. bölüm (Haklarınız ve iletişim) ve İngilizce özet.
Adres değişirse üçünü birlikte değiştirin:

```bash
grep -n "bilgi@ucyildizkitabevi.com" index.html
```

## Sayfanın dayandığı yedek ayarları

Sayfa, uygulama deposundaki `.github/workflows/gece_yedegi.yml` iş akışını anlatır: yedekler `age` ile şifrelenir,
oturum/token tabloları yedeğe alınmaz ve yedekler **30 gün** saklanır (`retention-days: 30`). Bu iş akışı değişirse
`index.html` içinde kısa özeti, 4. bölümü (Saklama), 5. bölümü (Paylaşım), 6. bölümü (Güvenlik) ve İngilizce özeti güncelleyin.

## App Privacy için özet

App Store Connect → App Privacy formu için. Kaynak: uygulama kodu (`supabase/migrations/`, `lib/`, `ios/Runner/Info.plist`).

| Veri türü (Apple kategorisi) | Uygulamadaki karşılığı | Kullanıcıya bağlı mı | Takip için mi | Amaç |
|---|---|---|---|---|
| Contact Info → **Name** | Çalışanın ad soyadı; öğretmenin (hoca) ad soyadı | Evet | Hayır | App Functionality |
| Contact Info → **Phone Number** | Öğretmenin telefon numarası (isteğe bağlı) | Evet | Hayır | App Functionality |
| User Content → **Other User Content** | Sipariş kalemleri, teslim şekli, durum, sipariş notu; okul ve öğretmen kayıtları | Evet | Hayır | App Functionality |
| Identifiers → **User ID** | Hesap kimliği (Supabase UUID) ve ad soyaddan türetilen iç giriş adı | Evet | Hayır | App Functionality |

Formdaki diğer yanıtlar:

- **Veri toplanıyor mu?** Evet (yukarıdaki dört tür).
- **Takip (tracking):** Hiçbir veri türü takip için kullanılmıyor. Uygulamada reklam ya da analitik SDK'sı yok, App Tracking Transparency izni gerekmez.
- **Toplanmayanlar:** konum, kişiler (rehber), fotoğraf/video, ses, sağlık, finans, tarama/arama geçmişi, satın almalar, tanılama (diagnostics), reklam kimliği.
- **Kamera:** Görüntü yalnızca cihazda işleniyor, sunucuya gönderilmiyor. Bu yüzden Apple'ın tanımına göre "toplanan veri" sayılmaz. iOS sürümü barkodu Apple Vision ile okur, Google ML Kit içermez.

## Emin olunmayanlar (karar sizde)

- **Supabase sunucu kayıtları (IP adresi):** Supabase, isteklere ait bağlantı kayıtlarını (IP dahil) tutabilir. Uygulama bunları kullanmıyor. Apple formunda ayrı bir veri türü olarak bildirilip bildirilmeyeceğini kesinleştirmedim.
- **Android'de Google ML Kit:** Android derlemesi gömülü `com.google.mlkit:barcode-scanning` kullanıyor. Google'ın belgelerine göre bu kütüphane teknik kullanım ölçümleri gönderebilir. App Store formunu etkilemez, ama uygulama ileride Google Play'e çıkarsa Data safety formunda dikkate alınmalı.
- **Uygulama içi bağlantı:** App Store İnceleme Yönergeleri 5.1.1(i), gizlilik politikası bağlantısının uygulamanın içinde de kolayca bulunmasını istiyor. Şu anda `lib/` altında böyle bir bağlantı yok.
