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
- 6 Ekim 2026: `deneme.html` üzerinde **5-emir-uslup** deneniyor: üç değişiklik birlikte (aşağıda): emirler,
  sıcak üslup ve bağlantı. Kullanıcının "tamam" demesi bekleniyor; denince üçü birden `index.html` dosyasına
  geçer. Biri sorun çıkarırsa yalnızca o çıkarılıp deneme sayfası yeniden kurulur (üçü birbirinden bağımsız
  yazıldı). Emirlerle üslubu birlikte koymayı kullanıcı ayrıca istemedi; "tek tek zaman alır denemesi" sözüne
  dayanılarak konuldu ve kendisine bildirildi. Bağlantı düzeltmesi sorulunca "Ekle" dedi. Üçüncü değişiklik
  eklenirken deneme kimliği bilerek aynı bırakıldı: kimlik değişseydi deneme sayfasındaki notların yerine asıl
  sayfanınkiler kopyalanırdı.

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

## Deneme sayfasındaki üç değişiklik (5-emir-uslup)

Üçü birbirinden bağımsızdır; biri çıkarılırsa öbürleri kalır.

### 1. Emirler

Kullanıcı (6 Ekim): "Bir emir verirsem veya direktif onu kesin yapsin". Gösterdiği sorun: dinleyici bir cevap
verdi, kullanıcı "Devam et", "Son söylediğine devam etsene" dedi; dinleyici sustu. Üsteleyince "Rolüm gereği …
sadece yanlış bilgi olduğunda veya soru sorduğunuzda müdahale ediyorum", "anlatımı tekrar etmiyorum" dedi.

Neden: hazır talimat konuşulacak durumları tek tek sayıyor, bunların dışında "Tamam" dedirtiyor ve "tekrar etme"
diyordu; emir bu durumların arasında yoktu. Sayfa da "Tamam"ı duyurmuyor. 4 Ekim sürümünde de böyleydi; bugünkü
değişikliklerden değildir. Kullanıcı daha önce "gerekirse son dediğini tekrarla derim" demişti; dinleyicinin
emre uyup uymayacağı denenmeden varsayılmıştı.

Yapılan:
- Hazır talimatta emir beşinci durumdur ("Bu beş durumun dışında … Tamam"; "aday istemedikçe … tekrar etme").
- Her talimata (düzenlenmiş olana da) bir not eklenir: her emir yerine getirilir, "Tamam" denmez, rol anlatılmaz.
  "Devam et / son söylediğine devam et / tekrar et": dinleyici konuyla ilgili son sözünü sürdürür ya da baştan
  söyler ("sesiniz geliyor" gibi konu dışı cevabını değil). "Dur / sus / bekle"de yalnızca "Tamam" der.
- Sayfa güvencesi: söz bir emirle bittiyse ve dinleyici yalnızca dolgu ya da onay sözü söylediyse ("Tamam",
  "Tabii") ya da 4 sn hiç ses gelmediyse istek bir kez yazıyla iletilir; "devam et / tekrar et" türünde konuyla
  ilgili son söz de eklenir. Nedeni döküme yazılır ("… istek yeniden iletildi").
- Sayfa neyi emir sayar: son cümle en çok 80 karakterdir ve emir kipiyle biter ("devam et(sene)", "tekrar et",
  "tekrarla", "bir daha söyle", "açıkla", "özetle", "anlat", "say", "sırala", "örnek ver", "soru sor", "hatırlat" …;
  "tekrar eder misin?" ve tek başına "tekrar" da). Dinleyici az önce konuşmuşken "duymadım", "anlamadım" da
  "yeniden söyle" isteği sayılır. "Kontrol et", "değerlendir" gibi emirlerde kısa onay ("Evet, doğru.") cevaptır.
  "Dur / sus / bekle", olumsuzlar ("devam etme") ve anlatım cümleleri ("devam edilir", "tekrarlar") sayılmaz.
- İstek üzerine yinelenen söz notlara ikinci kez yazılmaz; yarıda kalmış not ("… …") tamamlanır.

Bilinen sınır: dinleyici konuşurken söylenen 1,5 sn'den kısa söz, kullanıcının kendi kuralıyla, dinleyici cümlesini
bitirince iletilir. Yani kısa bir "dur" onu anında susturmaz; anında susturmak için daha uzun konuşmak gerekir.

### 2. Sıcak üslup

Kullanıcı (6 Ekim): dinleyici "daha samimi … ciddi ama … meslektaşmış gibi daha sıcakkanlı, daha doğal, beraber
çalıştığımız bir arkadaş gibi" olsun.

- Her talimata bir üslup notu eklenir: "sen" diye hitap, sıcak ve doğal ses tonu, gündelik Türkçe; ciddiyet korunur,
  övgü ve resmî kalıp yok. Yalnızca nasıl konuştuğunu değiştirir; ne zaman ve ne kadar konuşacağı değişmez.
- "Benzer ses" notundaki örnek "… mi dedin?" oldu.
- Sayfanın üç ayıklayıcısı "sen" diline göre genişletildi: nota alınmayan "… mi dedin / demiştin?" sorusu; "nerede
  kalmıştık" için verilen son bölüme alınmayan "sesin geliyor" cevabı; ders sırasında susturulan "haklısın",
  "doğru söylüyorsun" gibi onaylar (soruya cevapken çalınır).
- Soru çöz bölümünün talimatı değişmedi (oradaki kalıp sözleri sayfa tanıyor).

### 3. Bağlantı

Kullanıcı 6 Ekim 16:58'de deneme sayfasından şu ekranı gönderdi: "Durdu · Google bağlantıyı kapattı · Google'ın
yanıtı: Internal error encountered." Bu yanıtı Google'ın sunucusu verir. Canlı modellerde son haftalarda sık
bildiriliyor; kullanıcının modeli için de var (gemini-3.8-live, 3 Ekim 2026:
https://github.com/google-gemini/gemini-live-api-examples/issues/60). Bildirimlere göre bu hatadan sonra eski
oturumun geri yüklenmesi reddedilebiliyor ya da geri yüklenen oturum yeniden kapanıyor; yeni oturum açılabiliyor.

Bilinmeyenler: hata başlatırken mi çıktı, oturum sürerken mi (kullanıcı yazmadı); deneme sayfasının daha uzun
talimatının payı var mı (bir bildirim uzun talimatta sıklaştığını söylüyor). Deneme sayfasında sık, ana sayfada hiç
olmuyorsa pay var demektir; o zaman talimat kısaltılır.

Sayfadaki eksik (4 Ekim sürümünde de vardı): oturum sürerken böyle kapanınca sayfa 16 sn içinde 6 kez, hep eski
oturumu geri yükleyerek deniyor, olmazsa duruyordu; başlatırken hiç yeniden denemiyordu.

Yapılan:
- "Google'ın kendi hatası" yalnızca yanıt metninden tanınır ("internal error"). Kod yetmez: Google kota, anahtar ve
  ayar hatalarını da 1011 ile bildirebiliyor; onlar eskisi gibi ele alınır.
- Oturum sürerken: önce eski oturum geri yüklenmeye çalışılır (bağlam kaybolmasın). Google bunu da kendi hatasıyla
  reddederse, ya da geri yüklenen oturum dinleyici tek bir cevabı bile bitiremeden yine aynı hatayla kapanırsa,
  eski oturum bırakılır ve yeni oturum açılır; dinleyiciye dökümün son bölümü verilir. Durmadan önce 10 kez,
  yaklaşık 48 sn denenir.
- Başlatırken: Google kurulumu kendi hatasıyla kapatırsa 3 kez daha denenir.
- İnternet kesintisinde (yanıt gelmez) eski oturum bırakılmaz; bağlantı dönünce geri yüklenir.
- Dökümde neden yazılır: "Google bağlantıyı kapattı (Internal error encountered.). Bağlantı yenilendi."

### Buradan denenemeyen, yalnızca kullanıcının görebileceği şeyler

Dinleyici emre gerçekten uyuyor mu; yazıyla iletilen isteğe de "Tamam" diyebilir (soruda 5 Ekim'de bir kez oldu);
bir anlatım cümlesi emir sanılıp gereksiz yere istek iletilebilir; dinleyici "sen" diyor ve daha sıcak mı; daha çok
konuşmaya başladı mı (ders sırasında gereksiz tepki, uzayan cevaplar). Şikâyet gelirse önce dökümdeki
"… istek yeniden iletildi" satırlarına ve soluk ("susturuldu") satırlara bakılır.

Bağlantı: Google gerçekten hata verdiğinde sayfa kendiliğinden toparlıyor mu. Toparladıysa dökümde "Google bağlantıyı
kapattı (…). Bağlantı yenilendi." satırı olur; yine "Durdu" ekranı gelirse hata 48 sn'den uzun sürmüştür ya da
neden başkadır, o ekranın ve dökümün son satırlarının görüntüsü istenir.
