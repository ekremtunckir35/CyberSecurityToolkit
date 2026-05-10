# IT Fundamentals-4 Ders Kaydı — Sıfırdan Anlaşılır Ders Notu

**Kaynak:** 11.12.2025 IT Fundamentals-4 ham ders transkripti.

## ADIM 1 — Ana Başlıklar

- 1. Bilgisayarın Temel Donanım Yapısı
- 2. CPU, GPU, Core ve Processing Mantığı
- 3. Anakart, BIOS, CMOS Pili ve Front Panel Bağlantıları
- 4. Depolama, SSD, NVMe ve Güvenlik Desteği
- 5. Isınma, Soğutma ve Server Mantığı
- 6. IoT — Nesnelerin İnterneti
- 7. Bluetooth, Wi-Fi, Repeater ve Access Point
- 8. Hücresel Teknoloji: 1G, 2G, 3G, 4G, 5G
- 9. Mobil Cihaz Güvenliği
- 10. USB, Halka Açık Şarj, Juice Jacking ve Data Blocker
- 11. Rooting, Jailbreaking ve PIN Brute Force
- 12. Network Components: NIC, Switch, Hub, Router, Modem, Firewall

# 1. Bilgisayarın Temel Donanım Yapısı

**Konular arası bağlantı:** Önceki derste Processing Device konusu açılmıştı. Bu bölümde bilgisayarın işlem yapabilmesi için hangi fiziksel parçalara ihtiyaç duyduğunu netleştiriyoruz.

**Bunu neden öğreniyoruz?** Siber güvenlikte sistemi korumadan önce sistemin hangi parçalardan oluştuğunu bilmek gerekir. USB, BIOS, ağ kartı, depolama veya ekran kartı gibi parçaların her biri saldırı yüzeyi olabilir.

## Kavramlar

### Bilgisayar
**Bu nedir?** Veri alan, işleyen, saklayan ve çıktı üreten elektronik sistemdir. En temel düzeyde anakart, CPU ve RAM ile çalışabilir; kullanıcı için faydalı hale gelmesi için depolama, ekran, giriş/çıkış birimleri ve çoğu zaman ağ bağlantısı gerekir.

### Anakart (Motherboard / Mainboard)
**Bu nedir?** CPU, RAM, disk, ekran kartı, USB portları, ses ve ağ birimleri gibi parçaları birbirine bağlayan ana devre kartıdır.

### CPU (Central Processing Unit / Merkezi İşlem Birimi)
**Bu nedir?** Bilgisayarın genel işlem yapan beynidir. Komutları alır, işler ve sonucu ilgili birime gönderir.

### RAM (Random Access Memory)
**Bu nedir?** Programların çalışırken kullandığı geçici bellektir. Elektrik kesilince içindeki veri silinir.

### Depolama (Storage)
**Bu nedir?** HDD, SSD veya NVMe gibi veriyi kalıcı saklayan birimlerdir. İşletim sistemi, programlar ve dosyalar burada tutulur.

### GPU (Graphics Processing Unit)
**Bu nedir?** Görüntü, video, oyun, 3D modelleme ve render gibi grafiksel işlemleri üstlenen özel işlem birimidir.

## Günlük Hayat Analojisi
Bilgisayarı mutfak gibi düşün: anakart mutfağın zemini ve tezgâh düzeni, CPU aşçı, RAM aşçının anlık kullandığı tezgâh, SSD/HDD kiler, ekran kartı da yemeğin sunum kısmıdır.

> **KARIŞTIRMA!**
> - **Bilgisayarın çalışması:** Anakart + CPU + RAM ile temel elektriksel çalışma mümkündür.
> - **Kullanıcının işini görmesi:** Depolama, işletim sistemi, ekran, klavye, mouse, ağ bağlantısı gibi ek parçalar gerekir.
> - **Her cihaz aynı olmak zorunda mı?:** Hayır. Tarım cihazı, akıllı TV, oyun bilgisayarı, laptop ve server farklı ihtiyaçlara göre tasarlanır.

> **HATIRLA:** Temel üçlü: Anakart + CPU + RAM. Kullanıcı deneyimi için depolama, ekran, giriş/çıkış ve ağ bileşenleri eklenir.

## KENDİNİ TEST ET

**Soru 1:** Bir bilgisayarın temel çalışması için hangi üç parça gerekir?
**Cevap:** Anakart, CPU ve RAM.

**Soru 2:** RAM ile SSD arasındaki temel fark nedir?
**Cevap:** RAM geçici bellektir; SSD kalıcı depolamadır.

**Soru 3:** Neden her bilgisayarda aynı parçalar bulunmaz?
**Cevap:** Çünkü kullanım amacı farklıdır; endüstri cihazı, oyun bilgisayarı ve akıllı TV aynı ihtiyaca sahip değildir.

# 2. CPU, GPU, Core ve Processing Mantığı

**Konular arası bağlantı:** Bilgisayarın temel parçalarını gördük. Şimdi özellikle işlem yapan parçaları ve bilgisayarın veriyi nasıl işlediğini inceliyoruz.

**Bunu neden öğreniyoruz?** Şifre kırma, log analizi, zararlı yazılım analizi, yapay zekâ ve render gibi işlemlerde işlem gücü doğrudan önemlidir.

## Kavramlar

### Processing (İşleme)
**Bu nedir?** Gelen verinin anlamlı sonuca dönüştürülmesidir. 2+2 işlemi, rota hesaplama, sesin MP3’e çevrilmesi veya 3D modelin render edilmesi birer processing örneğidir.

### CPU
**Bu nedir?** Genel amaçlı işlemleri yapar. Klavyeden gelen karakteri işler, program çalıştırır, veriyi RAM veya diskten alır.

### GPU
**Bu nedir?** CPU’nun grafik yükünü azaltır. Kendine ait işlemcisi ve belleği bulunur. 2D/3D görüntü, video ve oyun işlemlerinde kullanılır.

### Core (Çekirdek)
**Bu nedir?** İşlemcinin içindeki bağımsız iş yapan birimdir. 4, 8, 16 çekirdekli işlemciler aynı anda daha fazla iş parçacığı çalıştırabilir.

### Render
**Bu nedir?** Çizilmiş 3D nesne veya video sahnesinin son görüntüye dönüştürülmesidir. Güçlü GPU ile çok hızlanır.

### Yapay zekâ ve veri
**Bu nedir?** Yapay zekâ dijital ortamdaki veriler üzerinden yorum yapar. Dijitalleştirilmemiş bir bilgiye erişemez; bu yüzden çıktıları her zaman doğrulanmalıdır.

## Günlük Hayat Analojisi
CPU ofis yöneticisi gibidir; her işi koordine eder. GPU ise grafik departmanı gibidir; özellikle görüntü ve paralel hesaplama işlerinde uzmanlaşmıştır.

> **KARIŞTIRMA!**
> - **CPU:** Genel sistem işlemleri, komutlar, program çalıştırma.
> - **GPU:** Grafik, video, 3D modelleme, paralel hesaplama.
> - **Core:** CPU veya GPU içindeki işçi birimdir; işlemcinin kendisiyle karıştırılmamalıdır.

> **HATIRLA:** CPU genel beyin, GPU grafik ve paralel işlem uzmanıdır. İkisi rakip değil, birlikte çalışan parçalardır.

## KENDİNİ TEST ET

**Soru 1:** GPU neden oyunlarda önemlidir?
**Cevap:** Grafiksel işlemleri çok hızlı yaparak CPU’nun yükünü azaltır.

**Soru 2:** Core nedir?
**Cevap:** İşlemcinin içinde işi yapan çekirdek birimdir.

**Soru 3:** Yapay zekâ neden her şeyi bilemez?
**Cevap:** Dijital ortama aktarılmamış veya erişemediği bilgiyi doğrudan bilemez.

# 3. Anakart, BIOS, CMOS Pili ve Front Panel Bağlantıları

**Konular arası bağlantı:** CPU ve GPU tek başına çalışmaz; bütün parçaları bir araya getiren yapı anakarttır. Bu bölümde anakart üzerindeki temel mantığı inceliyoruz.

**Bunu neden öğreniyoruz?** Fiziksel donanım güvenliği, BIOS ayarları, USB portları ve bağlantı hataları siber güvenlikte doğrudan risk üretir.

## Kavramlar

### BIOS (Basic Input/Output System)
**Bu nedir?** Bilgisayar açılırken donanımları tanıyan ve işletim sisteminin başlatılmasına yardım eden temel yazılımdır.

### ROM (Read Only Memory)
**Bu nedir?** BIOS gibi kalıcı bilgilerin tutulabildiği bellek türüdür.

### CMOS / BIOS Pili
**Bu nedir?** BIOS ayarlarını ve sistem saatini koruyan küçük pildir. Bitince saat sıfırlanabilir veya F1/CMOS uyarısı görülebilir.

### Front Panel
**Bu nedir?** Kasanın power düğmesi, reset tuşu, power LED, HDD LED, ön USB, mikrofon/kulaklık gibi bağlantılarının anakarta bağlandığı bölümdür.

### USB bağlantı hatası
**Bu nedir?** USB’de 5V, Ground, Data+ ve Data- hatları vardır. Yanlış bağlantı USB belleği veya cihazı yakabilir.

## Günlük Hayat Analojisi
Anakartı şehir gibi düşün: veri yolları caddeler, BIOS şehrin haritası, CMOS pili haritanın unutulmamasını sağlayan küçük enerji kaynağıdır.

> **KARIŞTIRMA!**
> - **BIOS:** Açılış yazılımı.
> - **ROM:** BIOS’un tutulduğu kalıcı bellek türü.
> - **CMOS pili:** BIOS ayarlarını ve saati koruyan fiziksel pil.

> **HATIRLA:** Anakart şehir, BIOS harita, CMOS pili ise bu haritanın unutulmamasını sağlayan küçük enerji kaynağıdır.

## KENDİNİ TEST ET

**Soru 1:** BIOS ne işe yarar?
**Cevap:** Açılışta donanımı kontrol eder ve sistemi başlatmaya yardım eder.

**Soru 2:** CMOS pili biterse ne olabilir?
**Cevap:** Saat/BIOS ayarları sıfırlanabilir ve sistem uyarı verebilir.

**Soru 3:** USB bağlantısında yanlış voltaj verilirse ne olur?
**Cevap:** Bağlı cihaz zarar görebilir veya yanabilir.

# 4. Depolama, SSD, NVMe ve Güvenlik Desteği

**Konular arası bağlantı:** Bilgisayarın çalışması için işlem gerekir; ama verinin kalıcı kalması için depolama gerekir.

**Bunu neden öğreniyoruz?** Eski sistemleri hızlandırmak mümkün olabilir; fakat güvenlik desteği bitmiş işletim sistemi hâlâ risklidir.

## Kavramlar

### HDD (Hard Disk Drive)
**Bu nedir?** Manyetik plakalarla çalışan eski tip kalıcı disk sistemidir.

### SSD (Solid State Drive)
**Bu nedir?** Hareketli parça içermeyen, HDD’ye göre çok daha hızlı kalıcı depolama birimidir.

### NVMe
**Bu nedir?** Anakart üzerindeki M.2/PCIe hattıyla çok hızlı çalışan modern SSD protokolüdür.

### Security Support
**Bu nedir?** İşletim sistemi üreticisinin güvenlik güncellemesi sağlamasıdır. Destek bittiyse sistem teknik olarak çalışsa bile risklidir.

### Eski bilgisayara SSD takma örneği
**Bu nedir?** Yavaşlığın ana sebebi HDD ise SSD değişimi eski bilgisayarı birkaç yıl daha kullanılabilir hale getirebilir.

## Günlük Hayat Analojisi
HDD eski arşiv dolabı, SSD hızlı çekmece, NVMe ise masanın üstündeki çok hızlı erişilen özel dosya alanı gibidir.

> **KARIŞTIRMA!**
> - **Performans problemi:** Bilgisayar yavaş açılır, HDD yavaştır, SSD çözüm olabilir.
> - **Güvenlik problemi:** İşletim sistemi artık güvenlik güncellemesi almıyorsa risk devam eder.
> - **Çalışıyor:** Güvenli olduğu anlamına gelmez.

> **HATIRLA:** SSD hız kazandırır; ama güvenlik güncellemesi almayan işletim sistemi güvenli hale gelmez.

## KENDİNİ TEST ET

**Soru 1:** SSD neden HDD’den hızlıdır?
**Cevap:** Mekanik parça kullanmaz, veriye elektronik olarak erişir.

**Soru 2:** NVMe’nin farkı nedir?
**Cevap:** Anakarta doğrudan ve çok hızlı veri yolu üzerinden bağlanır.

**Soru 3:** Security Support neden kritiktir?
**Cevap:** Güvenlik açıklarının üretici tarafından kapatılmasını sağlar.

# 5. Isınma, Soğutma ve Server Mantığı

**Konular arası bağlantı:** İşlem gücü arttıkça enerji tüketimi ve ısı artar. Bu yüzden performans kadar soğutma da kritiktir.

**Bunu neden öğreniyoruz?** Isınma sadece konfor problemi değildir; sistem kapanması, veri kaybı ve hizmet kesintisi oluşturabilir. Bu da Availability (Erişilebilirlik) riskidir.

## Kavramlar

### Isınma
**Bu nedir?** CPU/GPU gibi parçaların elektrik tüketimi nedeniyle sıcaklık üretmesidir.

### Core Temp
**Bu nedir?** İşlemci sıcaklığını izlemek için kullanılan uygulama örneğidir.

### Termal kapanma
**Bu nedir?** CPU belirli sıcaklığa ulaşınca sistemin kendini korumak için kapanmasıdır.

### Server
**Bu nedir?** 7/24 çalışmak ve çok sayıda kullanıcıya hizmet vermek için tasarlanmış bilgisayardır.

### Soğutma yöntemleri
**Bu nedir?** Fan, alüminyum/bakır soğutucu, sıvı soğutma ve sunucu odası iklimlendirmesi kullanılabilir.

## Günlük Hayat Analojisi
Bilgisayarı araba motoru gibi düşün: motor aşırı ısınırsa araç durur. CPU aşırı ısınırsa bilgisayar kapanır veya performans düşürür.

> **KARIŞTIRMA!**
> - **Laptop:** Taşınabilirlik için tasarlanmıştır; 7/24 yoğun server iş yükü için uygun değildir.
> - **Masaüstü:** Parça değişimi ve soğutma daha esnektir.
> - **Server:** Sürekli çalışma, güçlü soğutma ve çok kullanıcı için tasarlanır.

> **HATIRLA:** Isı kontrolü performans değil, aynı zamanda erişilebilirlik ve sistem sürekliliği meselesidir.

## KENDİNİ TEST ET

**Soru 1:** CPU çok ısınırsa ne olabilir?
**Cevap:** Sistem performansı düşebilir veya kendini kapatabilir.

**Soru 2:** Server neden laptop gibi olmaz?
**Cevap:** Soğutma, genişleme ve 7/24 çalışma ihtiyaçları farklıdır.

**Soru 3:** Isınma CIA üçlüsünde en çok hangi alanı etkiler?
**Cevap:** Availability (Erişilebilirlik).

# 6. IoT — Nesnelerin İnterneti

**Konular arası bağlantı:** Bilgisayar artık sadece masaüstü veya laptop değildir. İnternete çıkan akıllı cihazlar da bilgisayar gibi davranır.

**Bunu neden öğreniyoruz?** IoT cihazları hayatı kolaylaştırır ama aynı zamanda çok büyük veri toplar. Bu veri gizlilik, takip ve saldırı yüzeyi riskini büyütür.

## Kavramlar

### IoT (Internet of Things / Nesnelerin İnterneti)
**Bu nedir?** İnternete bağlanabilen fiziksel cihazların veri topladığı, paylaştığı ve bazen otomatik aksiyon aldığı ekosistemdir.

### Sensör
**Bu nedir?** Sıcaklık, ses, görüntü, hareket, konum, barkod, nabız gibi fiziksel verileri ölçen parçadır.

### Akıllı ev
**Bu nedir?** Isıtma, klima, robot süpürge, kapı kilidi, kamera ve aydınlatma gibi cihazların merkezi veya uzaktan yönetilmesidir.

### IP kamera
**Bu nedir?** IP alarak ağa bağlanan ve uzaktan izlenebilen kamera türüdür.

### Akıllı şehir
**Bu nedir?** Trafik ışıkları, sokak lambaları, otopark, elektrik şebekesi ve ulaşım sistemlerinin veriyle yönetilmesidir.

### Sağlık IoT
**Bu nedir?** Akıllı saat veya sensörlerle nabız, hareket, uyku veya acil durum bilgisinin izlenmesidir.

### Tarım ve hayvancılık IoT
**Bu nedir?** Hayvanlara veya tarım alanlarına takılan sensörlerle üretim, sağlık ve çevre verilerinin ölçülmesidir.

## Günlük Hayat Analojisi
IoT’yi mahalle haberleşme ağı gibi düşün: herkes bir bilgi gönderir; merkez bu bilgileri toplar, analiz eder ve kimi zaman cihazlara yeni komut gönderir.

> **KARIŞTIRMA!**
> - **Normal cihaz:** İnternete bağlanmaz, veri paylaşmaz.
> - **Akıllı/IoT cihaz:** IP alabilir, veri toplar, internete veya uygulamaya bağlanır.
> - **Kolaylık:** Güvenlik anlamına gelmez; veri toplama ve saldırı riski vardır.

> **HATIRLA:** IP alabilen ve internete çıkabilen her cihaz IoT ekosisteminin parçası olabilir.

## KENDİNİ TEST ET

**Soru 1:** IoT nedir?
**Cevap:** İnternete bağlı nesnelerin veri toplayıp paylaşmasıdır.

**Soru 2:** Sensör ne işe yarar?
**Cevap:** Fiziksel dünyadan ölçüm/veri toplar.

**Soru 3:** IoT neden güvenlik riski oluşturur?
**Cevap:** Çok sayıda cihaz veri toplar ve internete bağlıdır; zayıf güvenlik saldırı yüzeyi yaratır.

# 7. Bluetooth, Wi-Fi, Repeater ve Access Point

**Konular arası bağlantı:** IoT ve mobil cihazların çoğu kablosuz çalışır. Bu bölümde kablosuz teknolojilerin farkını öğreniyoruz.

**Bunu neden öğreniyoruz?** Kablosuz ağlar sniffing, sahte ağ, zayıf parola, Bluetooth zafiyeti ve yetkisiz erişim gibi saldırılar için kritik alandır.

## Kavramlar

### Bluetooth
**Bu nedir?** Kısa mesafede düşük enerjiyle veri aktarımı sağlayan kablosuz teknolojidir.

### Bluetooth Low Energy (BLE)
**Bu nedir?** Düşük enerji tüketimiyle çalışan Bluetooth türüdür; akıllı saat, sensör ve IoT cihazlarında yaygındır.

### Wi-Fi
**Bu nedir?** Cihazların kablosuz olarak yerel ağa ve internete bağlanmasını sağlar.

### IEEE 802.11
**Bu nedir?** Wi-Fi teknolojileri için kullanılan standart ailesidir.

### 2.4 GHz
**Bu nedir?** Daha uzun menzil ve daha iyi duvar aşma sağlar, genelde daha düşük hız ve daha fazla parazit vardır.

### 5 GHz
**Bu nedir?** Daha hızlıdır ama menzili daha kısadır ve engellerden daha çok etkilenir.

### Repeater / Range Extender
**Bu nedir?** Mevcut Wi-Fi sinyalini alıp tekrar ederek menzili artırır.

### Access Point
**Bu nedir?** Genellikle kabloyla ağa bağlanıp yeni kablosuz erişim noktası oluşturur.

## Günlük Hayat Analojisi
Bluetooth iki kişinin yakından konuşması gibidir. Wi-Fi ise evin içinde yapılan telsiz yayın gibidir. Repeater sesi tekrarlayan kişi, Access Point ise yeni hoparlör kurmak gibidir.

> **KARIŞTIRMA!**
> - **Bluetooth:** Kısa mesafe, düşük enerji, kulaklık/saat/sensör.
> - **Wi-Fi:** Daha hızlı ağ ve internet bağlantısı.
> - **Repeater:** Var olan Wi-Fi sinyalini tekrarlar.
> - **Access Point:** Kablolu ağdan yeni kablosuz yayın oluşturur.

> **HATIRLA:** Bluetooth kısa mesafe; Wi-Fi ağ bağlantısı; repeater sinyal tekrarı; access point yeni erişim noktasıdır.

## KENDİNİ TEST ET

**Soru 1:** Bluetooth hangi kullanım için uygundur?
**Cevap:** Kısa mesafeli düşük enerjili bağlantılar için.

**Soru 2:** 5 GHz neden daha hızlı ama kısa menzillidir?
**Cevap:** Yüksek frekans daha hızlı veri taşır ama engellerde daha çabuk zayıflar.

**Soru 3:** Repeater ile Access Point farkı nedir?
**Cevap:** Repeater mevcut sinyali tekrarlar; Access Point yeni kablosuz erişim noktası oluşturur.

# 8. Hücresel Teknoloji: 1G, 2G, 3G, 4G, 5G

**Konular arası bağlantı:** Wi-Fi olmayan yerlerde mobil cihazlar SIM kart ve baz istasyonları üzerinden haberleşir.

**Bunu neden öğreniyoruz?** Mobil ağlar artık sadece telefon görüşmesi için değil; IoT, otonom araç, endüstri, akıllı şehir ve kritik sistemler için altyapıdır.

## Kavramlar

### Cellular Technology
**Bu nedir?** Mobil cihazların baz istasyonları ve operatör altyapısı üzerinden iletişim kurmasını sağlayan teknolojidir.

### 1G
**Bu nedir?** 1980’lerde analog sesli arama dönemidir.

### 2G
**Bu nedir?** 1990’larda dijital ses, SMS ve basit veri servislerini getirmiştir.

### 3G
**Bu nedir?** 2000’lerde mobil internet ve erken akıllı telefon kullanımını yaygınlaştırmıştır.

### 4G
**Bu nedir?** 2010’larda hızlı mobil geniş bant, video, oyun, alışveriş ve uygulama kullanımını yaygınlaştırmıştır.

### 5G
**Bu nedir?** Yüksek hız, düşük gecikme, enerji verimliliği ve çok sayıda cihaz bağlantısı sağlayan yeni nesil mobil ağdır.

### Broadband / Geniş bant
**Bu nedir?** Daha yüksek veri taşıma kapasitesi anlamına gelir.

## Günlük Hayat Analojisi
Hücresel ağı posta sistemi gibi düşün: telefon mektubu hazırlar, baz istasyonu posta şubesi gibi alır, operatör dağıtır, internet küresel posta ağıdır.

> **KARIŞTIRMA!**
> - **Wi-Fi:** Yerel modem veya access point üzerinden çalışır.
> - **Hücresel ağ:** Mobil operatör ve SIM kart üzerinden çalışır.
> - **5G:** Sadece hızlı telefon interneti değil, endüstri ve IoT altyapısıdır.

> **HATIRLA:** Yeni nesil mobil ağlar daha fazla cihazı daha düşük gecikmeyle bağlamak için gelişir.

## KENDİNİ TEST ET

**Soru 1:** 2G’nin 1G’den farkı nedir?
**Cevap:** Dijital ses, SMS ve basit veri desteği getirmiştir.

**Soru 2:** 5G neden IoT için önemlidir?
**Cevap:** Çok sayıda cihazı düşük gecikme ve yüksek hızla bağlayabilir.

**Soru 3:** Wi-Fi ile hücresel ağ farkı nedir?
**Cevap:** Wi-Fi yerel ağdır; hücresel ağ mobil operatör altyapısını kullanır.

# 9. Mobil Cihaz Güvenliği

**Konular arası bağlantı:** Mobil cihazlar Wi-Fi, Bluetooth, hücresel ağ, uygulamalar ve bulut servisleriyle sürekli bağlantıdadır. Bu yüzden yüksek değerli hedeftir.

**Bunu neden öğreniyoruz?** Telefon artık banka, kamera, e-posta, şirket dosyası, 2FA kodu ve konum geçmişi taşıyan cep bilgisayarıdır.

## Kavramlar

### Malware (Malicious Software / Zararlı Yazılım)
**Bu nedir?** Cihaza zarar vermek, veri çalmak veya kontrol ele geçirmek için yazılmış kötü amaçlı yazılımdır.

### Spyware (Casus Yazılım)
**Bu nedir?** Kullanıcıyı gizlice izleyip bilgilerini saldırgana gönderen yazılımdır.

### Zero Day Vulnerability
**Bu nedir?** Henüz bilinmeyen veya yamalanmamış güvenlik açığıdır.

### Phishing (Oltalama)
**Bu nedir?** Kullanıcıyı kandırarak bilgi çalma saldırısıdır.

### Smishing
**Bu nedir?** SMS üzerinden yapılan phishing saldırısıdır.

### Social Engineering (Sosyal Mühendislik)
**Bu nedir?** Teknik açık yerine insan psikolojisini hedef alan saldırıdır.

### Drive-by Download
**Bu nedir?** Site ziyareti veya dosya indirme sırasında fark ettirmeden zararlı indirilmesidir.

### Wi-Fi Sniffing
**Bu nedir?** Kablosuz ağ trafiğinin dinlenmesidir.

### BYOD (Bring Your Own Device)
**Bu nedir?** Çalışanın kendi cihazını iş yerinde kullanmasıdır; cihazdaki zararlı şirket ağına taşınabilir.

### Physical Threats
**Bu nedir?** Cihazın kaybolması veya çalınmasıdır.

## Günlük Hayat Analojisi
Telefon cüzdan, anahtar, kimlik, fotoğraf albümü ve ofis bilgisayarının birleşimi gibidir. Birini kaybetmek artık sadece cihaz kaybı değildir.

> **KARIŞTIRMA!**
> - **Malware:** Genel zararlı yazılım ailesi.
> - **Spyware:** Casusluk ve veri izleme odaklı zararlı.
> - **Phishing:** Kullanıcıyı kandırma saldırısı.
> - **Zero Day:** Henüz bilinmeyen/yamalanmamış açık.

> **HATIRLA:** Mobil cihaz cepte taşınan kurumsal ve kişisel veri deposudur. Uygulama yükleme, halka açık Wi-Fi ve SMS linkleri kontrolsüz kullanılmamalıdır.

## KENDİNİ TEST ET

**Soru 1:** Spyware ne yapar?
**Cevap:** Kullanıcıyı gizlice izler ve verileri saldırgana gönderebilir.

**Soru 2:** Smishing nedir?
**Cevap:** SMS üzerinden yapılan oltalama saldırısıdır.

**Soru 3:** BYOD neden risklidir?
**Cevap:** Kişisel cihazdaki zararlı yazılım şirket ağına taşınabilir.

# 10. USB, Halka Açık Şarj, Juice Jacking ve Data Blocker

**Konular arası bağlantı:** Mobil cihazlar sadece ağdan değil, fiziksel bağlantı üzerinden de hedef alınabilir.

**Bunu neden öğreniyoruz?** Halka açık USB portları, bilinmeyen kablolar ve promosyon USB bellekler gerçek saldırı yüzeyidir.

## Kavramlar

### Malicious Charging
**Bu nedir?** Kötü amaçlı şarj noktası veya kablo üzerinden saldırı yapılmasıdır.

### Juice Jacking
**Bu nedir?** USB şarj portu veya kablosu üzerinden veri çalma ya da zararlı yazılım yükleme saldırısıdır.

### Zararlı USB kablosu
**Bu nedir?** Normal kablo gibi görünüp içine çip, Wi-Fi modülü veya SIM destekli parça gizlenmiş kablodur.

### USB Data Blocker
**Bu nedir?** USB veri hatlarını kesip sadece elektrik geçiren aparattır.

### Fuar USB belleği riski
**Bu nedir?** Ücretsiz verilen USB bellekler zararlı yazılım taşıyabilir; kurumsal cihazlarda kullanılmamalıdır.

### FBI uyarısı
**Bu nedir?** Halka açık USB şarj istasyonlarından kaçınma, kendi adaptörünü kullanma uyarısı örneği verilmiştir.

## Günlük Hayat Analojisi
Halka açık USB’ye telefon takmak, tanımadığın birinin bilgisayarına kabloyla bağlanmak gibidir. Çünkü USB sadece enerji değil, veri de taşıyabilir.

> **KARIŞTIRMA!**
> - **Kendi adaptörün + priz:** Genelde daha güvenlidir.
> - **Halka açık USB portu:** Veri hattı nedeniyle risklidir.
> - **Data Blocker:** Veri hatlarını keserek sadece şarj yaptırır.
> - **Bilinmeyen USB kablo:** İçinde zararlı donanım olabilir.

> **HATIRLA:** USB sadece şarj kablosu değildir; veri yolu da olabilir. Halka açık USB yerine kendi adaptörünü veya data blocker kullan.

## KENDİNİ TEST ET

**Soru 1:** Juice Jacking nedir?
**Cevap:** USB üzerinden veri çalma veya zararlı yükleme saldırısıdır.

**Soru 2:** USB Data Blocker ne yapar?
**Cevap:** Veri iletimini keser, sadece şarja izin verir.

**Soru 3:** Fuar USB belleği neden kullanılmamalı?
**Cevap:** İçine zararlı yazılım yerleştirilmiş olabilir.

# 11. Rooting, Jailbreaking ve PIN Brute Force

**Konular arası bağlantı:** Mobil güvenlikte üreticinin koyduğu sınırlar önemlidir. Rooting ve jailbreaking bu sınırları kaldırır.

**Bunu neden öğreniyoruz?** Kısıtları kaldırmak özgürlük gibi görünse de saldırganların sisteme daha kolay sızmasına neden olabilir.

## Kavramlar

### Rooting
**Bu nedir?** Android cihazda en üst seviye yetkiyi elde etme işlemidir.

### Jailbreaking
**Bu nedir?** iOS cihazlarda Apple’ın güvenlik ve kullanım kısıtlarını kaldırma işlemidir.

### Super User
**Bu nedir?** Sistemde en yetkili kullanıcı seviyesidir; dosya, ayar ve sistem uygulamalarına sınırsız erişebilir.

### Brute Force
**Bu nedir?** Doğru PIN veya şifre bulunana kadar olasılıkların hızlıca denenmesidir.

### PIN kırma video örneği
**Bu nedir?** Transkriptte Android PIN’inin başka cihaz ve bilgisayar destekli hızlı denemelerle kırıldığı bir video gösterilmiştir.

## Günlük Hayat Analojisi
Telefonu apartman gibi düşün: normal kullanıcı sadece kendi dairesine girer. Root/jailbreak sonrası elektrik odası, güvenlik odası ve yönetim paneli dahil her kapı açılır.

> **KARIŞTIRMA!**
> - **Rooting:** Android tarafındaki yetki yükseltme.
> - **Jailbreaking:** iOS tarafındaki kısıt kaldırma.
> - **Brute Force:** Şifre/PIN için çok sayıda deneme yapma yöntemi.

> **HATIRLA:** Rooting ve jailbreaking güvenlik kalkanlarını düşürür. Bankacılık ve kurumsal kullanımda ciddi risk kabul edilmelidir.

## KENDİNİ TEST ET

**Soru 1:** Rooting hangi sistemle ilişkilidir?
**Cevap:** Android.

**Soru 2:** Jailbreaking ne yapar?
**Cevap:** iOS kısıtlarını kaldırır.

**Soru 3:** Brute force nedir?
**Cevap:** Doğru şifreyi bulana kadar çok sayıda olasılığı denemektir.

# 12. Network Components: NIC, Switch, Hub, Router, Modem, Firewall

**Konular arası bağlantı:** Mobil ve IoT cihazların güvenliğini anlamak için ağ bileşenlerini bilmek gerekir.

**Bunu neden öğreniyoruz?** Nmap, Wireshark, firewall kuralları, MITM, MAC spoofing, LAN/WAN ve paket analizi ağ temeli olmadan anlaşılamaz.

## Kavramlar

### Network (Ağ)
**Bu nedir?** Birden fazla cihazın birbirleriyle iletişim kurabildiği yapıdır.

### NIC (Network Interface Card)
**Bu nedir?** Bilgisayarın ağa bağlanmasını sağlayan ağ arayüz kartıdır.

### Ethernet Kartı
**Bu nedir?** Kablolu ağ bağlantısı sağlayan NIC türüdür. Günümüzde çoğunlukla anakarta tümleşik gelir.

### Wireless Adapter
**Bu nedir?** Cihazı kablosuz ağa bağlayan adaptördür. USB veya dahili kart şeklinde olabilir.

### MAC Address
**Bu nedir?** Ağ kartına üretim aşamasında verilen benzersiz fiziksel adrestir.

### IP Address
**Bu nedir?** Ağ iletişiminde kullanılan mantıksal adrestir.

### Switch
**Bu nedir?** Aynı ağdaki cihazları MAC adresine göre akıllıca birbirine bağlar.

### Hub
**Bu nedir?** Gelen veriyi bağlı tüm cihazlara dağıtan eski ve akılsız ağ cihazıdır.

### Router
**Bu nedir?** Farklı ağları birbirine bağlayan yönlendiricidir. Ev ağı ile internet arasındaki geçişi sağlar.

### Modem
**Bu nedir?** Servis sağlayıcıdan gelen sinyali bilgisayarın anlayacağı dijital veriye dönüştürür.

### Firewall
**Bu nedir?** Trafiği güvenlik kurallarına göre izin/engelle mantığıyla kontrol eder.

### Wireless Access Point
**Bu nedir?** Kablolu ağı kablosuz erişime açar veya kablosuz alanı genişletir.

### Cable Modem
**Bu nedir?** Kablo TV/Kablonet altyapısı üzerinden internet sağlayan modem türüdür.

### LAN
**Bu nedir?** Local Area Network; ev, ofis veya okul gibi yerel ağdır.

### WAN
**Bu nedir?** Wide Area Network; geniş alan ağıdır. İnternet en büyük örnektir.

### ARP
**Bu nedir?** IP adresinin hangi MAC adresine ait olduğunu öğrenmek için kullanılan protokoldür.

### Broadcast
**Bu nedir?** Ağdaki herkese gönderilen genel yayındır.

### MAC Spoofing
**Bu nedir?** Saldırganın kendi MAC adresini başka cihazın MAC adresi gibi göstermesidir.

## Günlük Hayat Analojisi
Ağı şehir ulaşımı gibi düşün: bilgisayar ev, IP adresi ev adresi, MAC kimlik numarası, switch mahalle kavşağı, router şehirler arası yol ayrımı, firewall güvenlik kontrol noktasıdır.

> **KARIŞTIRMA!**
> - **Hub:** Veriyi herkese gönderir.
> - **Switch:** Veriyi hedef cihaza gönderir.
> - **Router:** Farklı ağları bağlar.
> - **Modem:** Sinyali dönüştürür.
> - **Firewall:** Trafiği güvenlik kuralına göre filtreler.

> **HATIRLA:** Switch aynı ağ içinde, router farklı ağlar arasında çalışır. Modem sinyali dönüştürür, firewall trafiği kontrol eder.

## KENDİNİ TEST ET

**Soru 1:** Switch ile Hub arasındaki fark nedir?
**Cevap:** Hub veriyi herkese gönderir; Switch sadece hedefe gönderir.

**Soru 2:** Router ne işe yarar?
**Cevap:** Farklı ağları birbirine bağlar ve trafiği yönlendirir.

**Soru 3:** MAC adresi ile IP adresi farkı nedir?
**Cevap:** MAC fiziksel donanım adresidir; IP mantıksal ağ adresidir.

# GENEL TEKRAR VE ÖZET

| Kavram | Kısa Tanım |
|---|---|
| CPU | Merkezi işlem birimi |
| GPU | Grafik işlem birimi |
| RAM | Geçici bellek |
| SSD | Hızlı kalıcı disk |
| NVMe | Çok hızlı SSD protokolü |
| BIOS | Açılış yazılımı |
| CMOS pili | BIOS ayarlarını koruyan pil |
| IoT | İnternete bağlı nesneler |
| BLE | Düşük enerjili Bluetooth |
| IEEE 802.11 | Wi-Fi standardı |
| Repeater | Wi-Fi sinyal tekrarlayıcı |
| Access Point | Kablosuz erişim noktası |
| 5G | Yeni nesil hücresel ağ |
| Malware | Zararlı yazılım |
| Spyware | Casus yazılım |
| Zero Day | Bilinmeyen/yamalanmamış açık |
| Phishing | Oltalama |
| Smishing | SMS oltalama |
| BYOD | Kendi cihazını işe getirme |
| Juice Jacking | USB şarj saldırısı |
| Rooting | Android yetki kırma |
| Jailbreaking | iOS kısıt kırma |
| NIC | Ağ kartı |
| MAC | Donanımsal ağ adresi |
| IP | Mantıksal ağ adresi |
| Switch | Akıllı ağ anahtarı |
| Hub | Eski tip dağıtıcı |
| Router | Ağ yönlendirici |
| Modem | Sinyal dönüştürücü |
| Firewall | Güvenlik duvarı |
| LAN | Yerel ağ |
| WAN | Geniş alan ağı |
| ARP | IP-MAC eşleştirme protokolü |
| Broadcast | Genel yayın |

## En Kritik Siber Güvenlik Çıkarımları

- Eski ama çalışan sistem güvenli olmak zorunda değildir; security support bitmişse risk vardır.
- USB sadece şarj değildir; veri de taşır ve saldırı yüzeyi oluşturur.
- IoT cihazları kolaylık sağlar ama sürekli veri topladığı için gizlilik ve güvenlik riski üretir.
- Mobil cihaz cepte taşınan mini bilgisayardır; banka, e-posta, kamera, konum ve şirket verisi aynı cihazda olabilir.
- Ağ bileşenlerini bilmeden siber güvenlik öğrenilemez; Switch, Router, Modem, Firewall, IP ve MAC temel kavramlardır.
- Rooting/Jailbreaking cihazı özgürleştirir gibi görünür ama güvenlik kalkanlarını indirir.
- Halka açık Wi-Fi ve şarj noktaları güvenli varsayılmamalıdır.
