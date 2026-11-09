# dotlas

![dotlas](readme/cover.jpg)

Gezdiğin ülkeleri ve şehirleri kaydeden, hepsini bir dünya haritasında gösteren iOS uygulaması. Tasarımını ve kodunu tek başıma yaptım; 29 Ekim 2026'dan beri App Store'da.

**[App Store'da dotlas](https://apps.apple.com/app/dotlas/id6816267686)** · [site](https://yavuzhan642.github.io/dotlas/) · ücretsiz, iOS 18 ve üstü

## Ekranlar

| | | |
| :---: | :---: | :---: |
| <img src="readme/01-acilis.jpg" width="240" alt="harita"> | <img src="readme/02-geziler.jpg" width="240" alt="geziler"> | <img src="readme/03-istatistik.jpg" width="240" alt="istatistikler"> |
| <img src="readme/04-buzdolabi.jpg" width="240" alt="magnet buzdolabı"> | <img src="readme/05-karsilastirma.jpg" width="240" alt="arkadaşla karşılaştırma"> | <img src="readme/06-widgetlar.jpg" width="240" alt="widget'lar"> |

<img src="readme/demo.gif" width="240" alt="dotlas tanıtım videosundan kısa bir bölüm">

## Ne yapıyor

- **Harita:** her gezinin yerleri haritada kendi renginde nokta olarak görünür; bir noktaya dokununca o gezi açılır.
- **Gezi sayfası:** yerler, rota, tarihler, o gezide çekilen fotoğraflar ve getirilen magnetler bir arada.
- **Gezi fotoğrafları:** fotoğraf kütüphanesindeki fotoğraflar gezinin tarihine ve konumuna göre bulunur; kapak fotoğrafı cihazda seçilir.
- **Magnet buzdolabı:** buzdolabı magnetinin fotoğrafından magnet kesilip uygulamadaki buzdolabına yapıştırılır; üstündeki yazı okunup hangi yerden olduğu önerilir.
- **İstatistikler ve rozetler:** kaç ülke, kıta, yer ve kilometre; dünyanın ne kadarının görüldüğü.
- **Paylaşım:** yıl kartı, rota posteri ve rotanın çizildiği dikey video.
- **Arkadaşla karşılaştırma:** iki kişi birbirinin kodunu kamerayla tarar, internete hiçbir şey gönderilmez.
- **Widget'lar, Spotlight ve Siri:** ana ekranda harita ve bayraklar; geziler Spotlight'ta aranır, Siri'yle açılır.

Hesap yok, sunucu yok, reklam yok. Veriler telefonda kalır.

## Teknik

Swift ve SwiftUI · üçüncü parti kütüphane yok · iOS 26'da Liquid Glass, iOS 18'de de çalışır

| Özellik | Nasıl |
| --- | --- |
| Veri | Tüm atlas tek bir JSON dosyası; her değişiklik anında kaydedilir. Dosya okunamazsa bir kopyası saklanır ve kullanıcı karar verene kadar üzerine yazılmaz. |
| Harita ve rota | MapKit. Duraklar arasındaki yol `MKDirections` ile gerçek karayolundan çizilir; yol bulunamayan bacaklar düz çizgi olarak kalır. |
| Dünya haritası | Places sekmesindeki harita, [svg-maps](https://github.com/VictorCazanave/svg-maps) verisinden bir Node betiğiyle üretilen küçük bir JSON'dan uygulamada çizilir. |
| Gezi fotoğrafları | PhotoKit ile tarih ve konuma göre eşleştirme; Vision'ın sınıflandırma ve estetik puanlarıyla manzara ve yapılar öne, bulanık, karanlık ve belge fotoğrafları arkaya alınır. |
| Magnet kesme | Vision'ın ön plan maskesiyle magnet fotoğraftan ayrılır, tutan el insan maskesiyle çıkarılır; metin tanıma magnetteki yer adlarını okur. |
| Rota videosu | Her kare çizilip AVFoundation (`AVAssetWriter`) ile 1080×1920 videoya yazılır. |
| Karşılaştırma | Kod yalnızca isim, sayılar ve ülke kodlarını taşır; VisionKit'in `DataScannerViewController`'ı ile okunur. |
| İstatistikler | Swift Charts. |
| Widget'lar | WidgetKit; uygulama, widget'ların göstereceği her şeyi App Group klasörüne hazırlar. |
| Spotlight ve Siri | Core Spotlight ile her gezi aranabilir; App Intents ile "open … in dotlas". |
| Simge yapı fotoğrafları | Kendi fotoğrafı olmayan gezilerde yakındaki ünlü yapının fotoğrafı Wikipedia'dan, fotoğrafçı ve lisansıyla gösterilir. |

## Sayılarla

- Yaklaşık 18.400 satır Swift, 57 dosya
- İlk commit 23 Eylül 2026, App Store'da 29 Ekim 2026 (1.0), 1 Kasım 2026 (1.1)

## Kaynak kodu

Uygulamanın kaynak kodu private bir repoda. Görmek isteyenlere erişim verebilirim: [dotlasapp@gmail.com](mailto:dotlasapp@gmail.com)

Bu repo, uygulamanın GitHub Pages'taki destek ve gizlilik sayfalarını tutuyor (`index.html`, `privacy.html`).
