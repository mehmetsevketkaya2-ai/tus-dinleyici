# Çalışma kuralları

Bu depo TUS Dinleyici sayfasını barındırır. Ana sayfa `index.html` dosyasıdır; kullanıcı onu her gün
tablette, Bluetooth kulaklıkla kullanır: https://mehmetsevketkaya2-ai.github.io/tus-dinleyici/

## Değişiklikler önce deneme sayfasına

6 Ekim 2026'da kullanıcıyla kararlaştırıldı:

1. Yeni bir özellik ya da düzeltme önce ayrı bir deneme sayfasına (`deneme.html`) konur.
   `index.html` olduğu gibi kalır.
2. Her seferinde tek değişiklik konur.
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
  deneme sayfasında denendi, kullanıcı "tamam" dedi ve `index.html` dosyasına geçti. `index.html` artık
  4 Ekim sürümü + bu değişikliktir ("Sürüm: 6 Ekim 2026"). `deneme.html` aynı değişiklikle duruyor; şu an
  denenen yeni bir şey yok.
- Kullanıcının isteğiyle **şimdilik bekliyor** (istemeden başlanmaz): kısa takip sorularına cevap
  ("Paratiroid peki?"); "Nerede kalmıştık?" sorusunda kalınan konuyu söylemesi ("Kaldığın yerden devam et"
  ile sürdürüldüğünde de; "Yeni ders"te unutur).
