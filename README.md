# Öğrenci Koçu

8-18 yaş öğrencilere online koçluk veren bir koç için Türkçe web sitesi.

Bu `main` sürümünün hedefi: velilerin ücretsiz PDF rehbere Brevo double opt-in kaydıyla ulaşması. Tanışma görüşmesi akışı bu sayfada yer almıyor.

## Teknoloji

- Statik HTML/CSS site (`site/`), derleme adımı yok
- Yayın: Cloudflare Workers statik varlıklar (`wrangler.jsonc`, `site/` klasörünü yayınlar)
- E-posta + PDF: Brevo double opt-in formuna yerel doğrulamalı HTML POST; rehber PDF'i `site/ogrenci-koclugu-rehberi.pdf`
- Çerez ve takip yok

## Sayfalar

- `site/index.html`: ücretsiz rehber açılış sayfası ve Brevo formu
- `site/impressum.html`, `site/datenschutz.html`: yasal sayfalar

## Yayın

Kaynak depodaki Cloudflare bağlantısı fork'a otomatik taşınmaz. Bu fork'ta `.github/workflows/deploy.yml`, `main` dalına push yapıldığında veya elle tetiklendiğinde Workers'a yayın yapar. Fork'un GitHub Actions sırlarına Cloudflare Workers deploy yetkili `CLOUDFLARE_API_TOKEN` ve `CLOUDFLARE_ACCOUNT_ID` eklenmelidir; sırları depoya yazmayın. `wrangler.jsonc` statik `site/` klasörünü yayınlar. Canlı alan adı ve Workers projesi Cloudflare hesabında ayrıca doğrulanmalıdır.

Yayın öncesi `impressum.html` ve `datenschutz.html` içindeki kimlik, iletişim ve gizlilik bilgilerini site sahibiyle doğrulayın. Brevo formunun double opt-in onay e-postası ve PDF teslim şablonunu Brevo hesabında test edin; bunlar depoda saklanmaz. Kayıt formu başarılı teslim iddiası göstermez; Brevo'nun yanıtına yönlendirir.
