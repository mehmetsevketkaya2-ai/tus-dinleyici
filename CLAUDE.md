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
- 6 Ekim 2026: `deneme.html` üzerinde **2-sesyolu** deneniyor. Yalnızca kayıt tutar, davranışı değiştirmez:
  döküme "Ses yolu · …" satırları yazar, "Ses gelmiyor" düğmesi o anki durumu bir kutuda gösterir ve kopyalar.
  Kullanıcının bir sonraki ses kaybında kutunun görüntüsünü ya da metnini göndermesi bekleniyor.
  Bu kayıt `index.html` dosyasına geçmeyecek; işi bitince kaldırılır.

## Açık sorun: ses kulaklıkta kesiliyor

Kullanıcının gözlemi (6 Ekim): oturum sürerken, ona göre uzun bir araya girmeden sonra, dinleyicinin sesi
kulaklıkta kesiliyor ve oturum yeniden başlatılana kadar gelmiyor. O sırada sayfa olağan çalışıyor: cevap
dökümde yazıyor, durum "Konuşuyor" olup "Dinliyor"a dönüyor, kullanıcının sözleri de yazıya dökülüyor.
5 Ekim gecesi aynı belirti vardı ve Android "Arama sessize alındı, ses seviyesini artırın" uyarısı göstermişti.

- Sayfanın bekletme mantığı değil: öyle olsaydı durum "Konuşuyor"da kalırdı. Taklit ortamda 178 cevap ve
  36 araya girmeyle sayfa sesi hiç kaybetmedi.
- Şüphe (doğrulanmadı): mikrofon açıkken Android sesi kulaklığa arama kanalından verir; bu kanal oturum
  ortasında düşüyor, Android tabletin kendi mikrofonuna ve hoparlörüne geçiyor, tabletin arama sesi de sıfırda.
- Doğrulanırsa sonraki adım: sayfa mikrofonu yeniden açıp kulaklık kanalını kendiliğinden geri getirsin.
- Bu sorunda iki kez yanlış tahmin yürütüldü ("Tamam" diyor; bekletme takılıyor). Kayıt görülmeden yeni
  tahminle değişiklik yapılmaz.

## Sırada (tek tek, her biri deneme sayfasında)

1. Kullanıcı istedi (6 Ekim): bekleme süresi 0,5 sn sabit olsun, "Sustuğunuzda kaç saniye beklesin?" ayarı
   kalksın. Kullanıcı yalnızca 0,5 sn kullanıyor; bundan sonraki bütün mantık yalnızca 0,5 sn'ye göre tasarlanır.
2. Kullanıcının araya girme kuralları (6 Ekim):
   - Kısa söz (soru olsun olmasın): dinleyici cümlesini bitirir; sayfa sözü saklar, o bitince iletir. Soruysa
     cevaplar, yorumsa tepki verir. Şu an kısa söz atılıyor.
   - Uzun söz: kalan cevap bırakılır; o an söylenen değerlendirilir. Yanlışsa düzeltir, soruysa cevaplar,
     doğru anlatımsa susar.
3. Şimdilik bekliyor (istemeden başlanmaz): "Nerede kalmıştık?" sorusunda kalınan konuyu söylemesi
   ("Kaldığın yerden devam et" ile sürdürüldüğünde de; "Yeni ders"te unutur).
