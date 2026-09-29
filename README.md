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

Cloudflare hesabınızda bu depoyu Workers projesine bağlayıp derleme komutunu `npx wrangler deploy` olarak ayarlayın. Kaynak depodaki dağıtım bağlantısı fork'a otomatik taşınmaz. Alternatif olarak Cloudflare yetkili bir ortamda aynı komutu çalıştırın. `wrangler.jsonc` statik `site/` klasörünü yayınlar.

Yayın öncesi `impressum.html` ve `datenschutz.html` içindeki kimlik, iletişim ve gizlilik bilgilerini site sahibiyle doğrulayın. Brevo formunun double opt-in onay e-postası ve PDF teslim şablonunu Brevo hesabında test edin; bunlar depoda saklanmaz. Kayıt formu başarılı teslim iddiası göstermez; Brevo'nun yanıtına yönlendirir.
