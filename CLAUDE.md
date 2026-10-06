# Çalışma kuralları

Bu depo TUS Dinleyici sayfasını barındırır. Ana sayfa `index.html` dosyasıdır; kullanıcı onu her gün
tablette, Bluetooth kulaklıkla kullanır: https://mehmetsevketkaya2-ai.github.io/tus-dinleyici/

## Değişiklikler önce deneme sayfasına

6 Ekim 2026'da kullanıcıyla kararlaştırıldı:

1. Yeni bir özellik ya da düzeltme önce ayrı bir deneme sayfasına (`deneme.html`) konur.
   `index.html` olduğu gibi kalır.
2. Her seferinde tek değişiklik konur. Kullanıcı kendisi isterse birkaç değişiklik birlikte konabilir
   (6 Ekim: "Aynı anda hepsini yap, denemeye at; tek tek zaman alır denemesi"). Birlikte konanlar ayrı ayrı
   çıkarılabilir yazılır.
3. Kullanıcı deneme sayfasını tablette, kulaklıkla dener. Açıkça "tamam" demeden değişiklik
   `index.html` dosyasına geçmez.
4. Kullanıcı istemeden hiçbir dosya değiştirilmez. Yalnızca soru sorduysa cevap verilir, işlem
   yapılmaz.

## Neden

5 Ekim 2026'da yedi değişiklik bir günde, doğrudan `index.html` dosyasına kondu. Bunlar yalnızca
taklit bir sunucu ve kayıtlı seslerle denenebilmişti: gerçek tablet, Bluetooth kulaklık ve gerçek
Google servisi buradan denenemez. O gece oturumlarda ses gelmedi, nedeni bulunamadı ve hepsi geri
alındı; `index.html` 4 Ekim sürümüne döndü. Bir şeyin gerçekten çalıştığını yalnızca kullanıcı
kendi cihazında görebilir.

Geri alınan değişiklikler git geçmişinde duruyor (`803ebc1` … `fab7632`). Yeniden istenirse oradan,
tek tek ve deneme sayfası üzerinden alınır.

## Deneme sayfası nasıl kurulur

`deneme.html` = `index.html` + denenen tek değişiklik + şunlar: üstte sarı deneme şeridi, ayrı kayıt öneki
(`tusddeneme.`). Anahtar ve ayarları her açılışta asıl sayfanın kayıtlarından (`tusd.`) okur; notları her yeni
denemede bir kez kopyalar. Asıl sayfanın kayıtlarına hiçbir zaman yazmaz.

## Durum

- 6 Ekim 2026: **1-notlar** (Notlar bölümünde yalnızca en son not, tek satır; "Tümünü göster" ile açılır)
  deneme sayfasında denendi, kullanıcı "tamam" dedi ve `index.html` dosyasına geçti ("Sürüm: 6 Ekim 2026",
  `c1567ed`).
- 6 Ekim 2026: **2-sesyolu** (yalnızca kayıt: "Ses yolu · …" satırları ve "Ses gelmiyor" düğmesi) deneme
  sayfasında kullanıldı ve işi bitti; `index.html` dosyasına geçmedi. Gerekirse `0833bcd` sürümündeki
  `deneme.html` dosyasından geri alınır.
- 6 Ekim 2026: **4-toplu** (kullanıcının isteğiyle dört değişiklik birlikte; aşağıda) deneme sayfasında denendi,
  kullanıcı "4 Deneme tamam yayına geçebilir" dedi ve dördü birden `index.html` dosyasına geçti. `index.html`
  artık 4 Ekim sürümü + notlar + bu dört değişikliktir ("Sürüm: 6 Ekim 2026 (2)"). Geri dönmek gerekirse:
  yalnız notları içeren önceki ana sayfa `c1567ed` sürümündeki `index.html` dosyasıdır.

## Çözülen sorun: ses kulaklıkta kesiliyordu (sayfadan değildi)

5-6 Ekim'de dinleyicinin sesi kulaklıkta kesiliyordu: sayfa cevabı çalıyor ("Konuşuyor", sonra "Dinliyor"),
döküme yazıyor, ama duyulmuyordu. 5 Ekim gecesi Android "Arama sessize alındı, ses seviyesini artırın" uyarısı
göstermişti. 6 Ekim'deki kayıt, sayfanın sesi çıkardığını (çıkış düzeyi 0,19-0,28, bekletme yok, ses saati
yürüyor) ve sayfa tarafında hiçbir şeyin değişmediğini gösterdi.

Kullanıcı tabletin Bluetooth ayarlarında, Jabra Evolve2 55 için "Ses seviyesini telefonla senkronize et"
seçeneğini açınca ses geri geldi (kendi deyişiyle "düzeldi sanırım"). Mikrofon açıkken ses kulaklığa arama
kanalından gider; o kanalın ses düzeyi tabletle eşleşmediği için kısılı kalıyordu. Yeniden olursa önce bu ayara
ve oturum sürerken ses düzeyine bakılır.

Bu sorunda sayfa üç kez boşuna suçlandı ("Tamam" diyor; bekletme takılıyor; tabletin mikrofonuna geçiyor).
Ders: ses duyulmuyorsa önce sayfanın sesi çıkarıp çıkarmadığı ölçülür, tahminle değişiklik yapılmaz.

## Ana sayfadaki dört değişiklik (4-toplu, 6 Ekim)

Kullanıcı yalnızca 0,5 sn bekleme kullanıyor; bütün mantık yalnızca 0,5 sn'ye göre tasarlanır.
Dördü aşağıdaki sırayla üst üste uygulandı. Adımların ayrı hâlleri yalnızca git geçmişindeki deneme
sayfalarında durur (`de58890` sürümündeki `deneme.html`: yalnız 1; `e85ef1f` sürümündeki: dördü). Biri
çıkarılacaksa ilgili kod elle ayıklanır ve sonuç yine önce deneme sayfasına konur.

1. **0,5 sn sabit**: bekleme süresi hep 0,5 sn, "Sustuğunuzda kaç saniye beklesin?" ayarı yok. Kayıtlı eski
   değer okunmaz.
2. **Her soruya cevap**: talimata not eklenir (kısa sorular, "Şu peki?", "Doğru mu?" da sorudur; soruya
   "Tamam" denmez). Sayfa da güvence sağlar: söz soruyla bittiyse ve dinleyici yalnızca dolgu söz söylediyse
   ya da 4 sn hiç ses gelmediyse soru bir kez yazıyla yeniden sorulur; nedeni döküme yazılır
   ("… soru yeniden soruldu"). Ders anlatırken yalnızca açık sorular (soru işareti ya da soru eki), dinleyici
   az önce konuşmuşken soru sözcüğüyle ya da "… peki" ile biten sözler de sayılır.
3. **Kısa araya girme**: dinleyici konuşurken söylenen 1,5 sn'den kısa söz atılmaz; dinleyici cümlesini
   bitirir, söz o bitince iletilir (0,3 sn'den kısa sesler atılır). Uzun sözde eskisi gibi kalan cevap bırakılır.
4. **"Nerede kalmıştık?"**: talimata not eklenir (kalınan yeri tek cümleyle hatırlat, konu dışı sözleri sayma).
   "Kaldığın yerden devam et" ile başlayan ya da bağlamı kaybolan oturuma dökümün son ~1400 karakteri verilir;
   "Yeni ders"te verilmez.

Buradan gerçek Google ile denenemeyen, yalnızca kullanıcının görebileceği şeyler: dinleyici yeniden sorulana
da "Tamam" diyebilir (5 Ekim'de bir kez oldu); yeniden sorma gereksiz yerde devreye girebilir (ders sırasında
kendi kendine sorulan sorularda). Kullanıcı dördünü tablette deneyip onayladı; bunlarla ilgili bir şikâyet
bildirmedi. Bildirirse önce dökümdeki "… soru yeniden soruldu" satırlarına bakılır.
