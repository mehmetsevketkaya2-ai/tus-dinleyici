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
  4 Ekim sürümü + bu değişikliktir ("Sürüm: 6 Ekim 2026").
- 6 Ekim 2026: **2-sesyolu** (yalnızca kayıt: "Ses yolu · …" satırları ve "Ses gelmiyor" düğmesi) deneme
  sayfasında kullanıldı ve işi bitti; `index.html` dosyasına geçmedi. Gerekirse `0833bcd` sürümündeki
  `deneme.html` dosyasından geri alınır.
- 6 Ekim 2026: `deneme.html` üzerinde **3-yarimsaniye** deneniyor: bekleme süresi 0,5 sn sabit,
  "Sustuğunuzda kaç saniye beklesin?" ayarı kalktı. Kullanıcının "tamam" demesi bekleniyor.

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

## Sırada (tek tek, her biri deneme sayfasında)

Kullanıcı yalnızca 0,5 sn bekleme kullanıyor; bütün mantık yalnızca 0,5 sn'ye göre tasarlanır.

1. **Her soruya cevap** (6 Ekim): dinleyici bir soruya "Tamam" deyip geçmesin, her soru duyulur bir cevap alsın.
2. **Araya girme kuralları** (6 Ekim):
   - Kısa söz (soru olsun olmasın): dinleyici cümlesini bitirir; sayfa sözü saklar, o bitince iletir. Soruysa
     cevaplar, yorumsa tepki verir. Şu an kısa söz atılıyor.
   - Uzun söz: kalan cevap bırakılır; o an söylenen değerlendirilir. Yanlışsa düzeltir, soruysa cevaplar,
     doğru anlatımsa susar.
3. **"Nerede kalmıştık?"** (6 Ekim): kalınan yeri tek cümleyle hatırlatsın ("Kaldığın yerden devam et" ile
   sürdürüldüğünde de; "Yeni ders"te unutur).
