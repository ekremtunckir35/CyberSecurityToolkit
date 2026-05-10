# IT Fundamentals-5 Ders Kaydı - Sıfırdan Öğrenme Rehberi

**Kaynak:** `4-12.12.2025_-_IT_Fundamentals-5.docx` transkripti temel alınarak hazırlanmıştır.

Bu doküman, ham ders kaydı metnindeki konuları hiçbir teknik altyapısı olmayan bir öğrencinin anlayabileceği sıraya koyar. Her bölümde kavram tanımı, öğrenme nedeni, günlük hayat analojisi, karıştırılan kavramlar, hatırlatma kutusu ve kendini test et soruları vardır.

## Ana Başlıklar

1. Güncel takip ve sertifika alışkanlığı
2. Bilgisayar donanımı
3. RAM, ROM ve BIOS
4. HDD, SSD ve NVMe
5. Bellek ölçü birimleri
6. NAS ve SAN
7. CPU ve GPU
8. Anakart ve North Bridge
9. IoT ve mobil cihazlar
10. Bluetooth, Wi-Fi ve hücresel teknoloji
11. Mobil cihaz tehditleri
12. Jailbreaking ve Rooting
13. Network temel mantığı
14. Network cihazları
15. İşletim sistemleri
16. GUI ve CLI
17. Linux, Kali Linux ve Debian
18. Windows
19. PowerShell riski
20. macOS, sanallaştırma ve dual boot
21. SolarWinds ve tedarik zinciri saldırısı

# 1. Siber Güvenlik Öğrencisi İçin Güncel Takip ve Sertifika Alışkanlığı
## Bu nedir?

Ders, öğrencinin haberleri, sosyal medya paylaşımlarını, Discord duyurularını, cheat sheetleri ve ücretsiz sertifika programlarını takip etmesi gerektiğini vurgular.
## Bunu neden öğreniyoruz?

Siber güvenlik sürekli değişir. Yeni açıklar, yeni saldırı teknikleri, yeni araçlar ve yeni sertifika fırsatları çıktığı için öğrenci güncel kalmalıdır.
## Günlük hayat analojisi

Bir doktor mezun olduktan sonra yeni tedavi yöntemlerini takip etmek zorundadır. Siber güvenlik uzmanı da yeni zafiyetleri ve savunma tekniklerini takip etmek zorundadır.
## Metinde geçen özel örnekler ve terimler

- Discord üzerinden sertifika paylaşımı
- Linux cheat sheetleri
- Ücretsiz sertifika programları
- Cisco
- IBM
- TryHackMe Learning Path
- TryHackMe yarışmaları ve katılım belgeleri

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Sertifika | Bir eğitimi/etkinliği tamamladığını gösterir; tek başına uzmanlık kanıtı değildir. |
| Cheat Sheet | Hızlı tekrar notudur; ayrıntılı ders kitabı değildir. |
| Learning Path | Adım adım öğrenme yoludur; rastgele video izlemek değildir. |

## HATIRLA

> Güncel kalmayan siber güvenlik öğrencisi teknik olarak hızla geriye düşer.

## KENDİNİ TEST ET

**Soru 1:** Siber güvenlik öğrencisi neden güncel kalmalıdır?

**Cevap:** Çünkü saldırılar, açıklar ve araçlar sürekli değişir.

**Soru 2:** Cheat sheet ne işe yarar?

**Cevap:** Komutları ve kavramları hızlı tekrar etmeye yarar.

**Soru 3:** TryHackMe neden önemlidir?

**Cevap:** Teorik bilgiyi lab ortamında uygulamaya dönüştürür.


# 2. Bilgisayarın Temel Donanım Parçaları
## Bu nedir?

Bir bilgisayarın çalışması için temel olarak anakart (Motherboard), işlemci (CPU) ve RAM gerekir. Depolama, ekran kartı, ses kartı ve çevre birimleri bu yapıyı tamamlar.
## Bunu neden öğreniyoruz?

Sistemlerin nasıl çalıştığını anlamayan kişi güvenlik olaylarını doğru yorumlayamaz.
## Günlük hayat analojisi

Bilgisayarı restoran gibi düşün: anakart bina ve bağlantılar, CPU baş aşçı, RAM çalışma tezgahı, disk depo, işletim sistemi restoran müdürüdür.
## Metinde geçen özel örnekler ve terimler

- Anakart
- CPU - Central Processing Unit
- RAM - Random Access Memory
- Ekran kartı
- Ses kartı
- Monitör, klavye, mouse, kulaklık

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| CPU | İşlem yapar. |
| RAM | Geçici veri tutar. |
| Hard Disk/SSD | Kalıcı veri tutar. |
| Anakart | Bütün parçaları birbirine bağlar. |

## HATIRLA

> Bilgisayar sadece kasa değildir; birlikte çalışan donanım parçalarından oluşan bir sistemdir.

## KENDİNİ TEST ET

**Soru 1:** Bilgisayarın üç temel parçası nedir?

**Cevap:** Anakart, işlemci ve RAM.

**Soru 2:** Anakartın görevi nedir?

**Cevap:** Donanım parçalarının iletişimini sağlamaktır.

**Soru 3:** CPU neden bilgisayarın beyni kabul edilir?

**Cevap:** Komutları işleyip hesaplama görevlerini yürüttüğü için.


# 3. RAM, ROM ve BIOS
## Bu nedir?

RAM (Random Access Memory) elektrik varken veri tutan geçici bellektir. ROM (Read Only Memory) cihazın temel bilgilerini barındıran daha kalıcı bellektir. BIOS (Basic Input Output System) bilgisayar açılırken ilk çalışan temel sistemdir.
## Bunu neden öğreniyoruz?

Açılış süreci, geçici bellek ve temel sistem kontrolleri anlaşılmadan bilgisayar mimarisi netleşmez.
## Günlük hayat analojisi

RAM mutfak tezgahıdır; iş bitince temizlenir. ROM fabrikadan gelen kullanım kılavuzudur. BIOS ise arabayı çalıştırmadan önce yapılan ilk kontrol gibidir.
## Metinde geçen özel örnekler ve terimler

- AMI BIOS
- Award BIOS
- American Megatrends
- Lenovo logosu
- Asus logosu
- HP logosu
- CR2032 pil
- Power On Self Test (POST)

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| RAM | Elektrik gidince silinir. |
| ROM | Temel kalıcı bilgileri tutar. |
| BIOS | ROM üzerinde bulunan açılış sistemidir. |
| POST | BIOS tarafından yapılan donanım sağlık testidir. |

## HATIRLA

> RAM geçicidir; BIOS bilgisayarın ilk uyanan parçasıdır; CR2032 pil BIOS ayarlarını korur.

## KENDİNİ TEST ET

**Soru 1:** RAM neden geçicidir?

**Cevap:** Elektrik kesildiğinde içindeki veriler silindiği için.

**Soru 2:** BIOS ne yapar?

**Cevap:** Bilgisayar açılırken donanımı kontrol eder ve açılışı başlatır.

**Soru 3:** POST nedir?

**Cevap:** Açılışta yapılan donanım sağlık testidir.


# 4. Kalıcı Depolama: HDD, SSD ve NVMe
## Bu nedir?

HDD mekanik ve manyetik disk yapısına sahiptir. SSD mekanik parça kullanmadan daha hızlı erişim sağlar. NVMe/M.2 diskler doğrudan anakarta takılarak daha yüksek okuma-yazma performansı sunar.
## Bunu neden öğreniyoruz?

İşletim sistemi, uygulamalar, loglar, oyunlar, videolar ve forensic imajlar kalıcı depolamada saklanır. Disk teknolojisi performansı doğrudan etkiler.
## Günlük hayat analojisi

HDD eski plak çalara benzer; diskin dönmesi ve kafanın doğru yere gelmesi gerekir. SSD ise raf numarasını bilen modern depo sistemi gibidir. NVMe, depo ile mutfak arasındaki direkt hızlı kapı gibidir.
## Metinde geçen özel örnekler ve terimler

- 3.5 inç HDD
- 5400 RPM
- 7200 RPM
- Sektörler
- Gramofon benzetmesi
- SATA bağlantısı
- Solid State Drive
- M.2 NVMe SSD
- Kali Linux ISO boyutu örneği

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| HDD | Mekaniktir ve görece yavaştır. |
| SSD | Mekanik parçası yoktur; SATA ile bağlanabilir. |
| NVMe/M.2 | Anakarta doğrudan takılır; çok hızlıdır. |

## HATIRLA

> Disk yavaşsa sanal makine, log analizi ve büyük veri işlemleri de yavaşlar.

## KENDİNİ TEST ET

**Soru 1:** HDD neden SSD’den yavaştır?

**Cevap:** Mekanik parça ve okuma kafası kullandığı için.

**Soru 2:** NVMe’nin avantajı nedir?

**Cevap:** Anakarta doğrudan bağlanıp yüksek hız sunmasıdır.

**Soru 3:** İşletim sistemi neden RAM’de kalıcı tutulmaz?

**Cevap:** RAM elektrik kesilince silinir.


# 5. Bellek Ölçü Birimleri
## Bu nedir?

En küçük birim bit’tir. 8 bit 1 byte eder. 1024 byte 1 KB, 1024 KB 1 MB, 1024 MB 1 GB, 1024 GB 1 TB olarak ilerler.
## Bunu neden öğreniyoruz?

Dosya boyutu, disk kapasitesi, ağ trafiği ve veri sızıntısı analizlerinde ölçü birimleri doğru anlaşılmalıdır.
## Günlük hayat analojisi

Bit tek tuğla, byte küçük paket, KB kutu, MB koli, GB oda, TB depo, PB lojistik merkezi gibi düşünülebilir.
## Metinde geçen özel örnekler ve terimler

- Bit
- Byte
- Kilobyte
- Megabyte
- Gigabyte
- Terabyte
- Petabyte
- Exabyte
- ASCII tablosu
- 0 ve 1 karakterleri

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Bit | 0 veya 1’in en küçük veri birimidir. |
| Byte | 8 bitten oluşur. |
| Klavyedeki 1 karakteri | Genellikle 1 byte olarak temsil edilir; tek bit değildir. |

## HATIRLA

> 8 bit = 1 byte. Bilgisayar bilimlerinde büyüme çoğunlukla 1024 tabanlıdır.

## KENDİNİ TEST ET

**Soru 1:** 1 byte kaç bittir?

**Cevap:** 8 bit.

**Soru 2:** 1 GB kaç MB kabul edilir?

**Cevap:** 1024 MB.

**Soru 3:** Klavyeden yazılan A tek bit midir?

**Cevap:** Hayır, genellikle 1 byte olarak temsil edilir.


# 6. NAS ve SAN Depolama Sistemleri
## Bu nedir?

NAS (Network Attached Storage) ağa bağlı depolamadır. SAN (Storage Area Network) büyük kurumlar ve veri merkezleri için kullanılan yüksek hızlı depolama ağıdır.
## Bunu neden öğreniyoruz?

Kurumsal veriler çoğu zaman merkezi depolama sistemlerinde tutulur. Saldırganlar tek kullanıcı yerine bu merkezi sistemleri hedefleyebilir.
## Günlük hayat analojisi

NAS evdeki ortak dolap gibidir. SAN ise büyük bir şirketin profesyonel arşiv ve lojistik deposu gibidir.
## Metinde geçen özel örnekler ve terimler

- NAS cihazı
- 4 veya 6 TB diskler
- 8 diskli yapı
- 48 TB kapasite
- Data center
- Hosting firmaları
- Fiber optik bağlantı

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| NAS | Küçük/orta ölçekli ağ depolama için uygundur. |
| SAN | Büyük veri merkezi ve yüksek performanslı depolama için uygundur. |
| Harici disk | Genellikle tek cihaza bağlı bireysel depolamadır. |

## HATIRLA

> Merkezi veri depoları saldırganlar için yüksek değerli hedeflerdir.

## KENDİNİ TEST ET

**Soru 1:** NAS ne demektir?

**Cevap:** Network Attached Storage - ağa bağlı depolama.

**Soru 2:** SAN nerede kullanılır?

**Cevap:** Büyük kurumlar ve veri merkezlerinde.

**Soru 3:** Saldırganlar neden merkezi depolara saldırır?

**Cevap:** Tek noktadan çok fazla veriye erişebilecekleri için.


# 7. CPU ve GPU
## Bu nedir?

CPU (Central Processing Unit) genel işlem merkezidir. GPU (Graphics Processing Unit) görsel ve paralel işlemler için tasarlanmıştır. GPU’ların paralel işlem gücü kripto madenciliğinde ve parola kırmada kullanılabilir.
## Bunu neden öğreniyoruz?

İşlem gücünün nasıl dağıldığını bilmek performans, parola kırma, grafik işleme ve güvenlik analizlerinde önemlidir.
## Günlük hayat analojisi

CPU baş aşçı gibidir; farklı görevleri yönetir. GPU ise aynı anda yüzlerce küçük işi yapan büyük mutfak ekibi gibidir.
## Metinde geçen özel örnekler ve terimler

- ALU - Arithmetic Logic Unit
- Control Unit
- Registers
- Blockchain
- Bitcoin madenciliği
- Mining rig
- Birden fazla ekran kartı
- iPhone 17 sıraya girme benzetmesi

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| CPU | Genel amaçlı işlem yapar. |
| GPU | Görsel/paralel işlem yapar. |
| RAM | Sistem belleğidir. |
| VRAM | Ekran kartı belleğidir. |

## HATIRLA

> CPU genel komutandır; GPU çok sayıda paralel işi hızlı yapabilen özel ekiptir.

## KENDİNİ TEST ET

**Soru 1:** CPU’nun görevi nedir?

**Cevap:** Genel işlemleri yürütmek.

**Soru 2:** GPU’nun asıl görevi nedir?

**Cevap:** Görsel verileri ve paralel işlemleri yürütmek.

**Soru 3:** GPU kripto madenciliğinde neden kullanıldı?

**Cevap:** Çok sayıda paralel işlem yapabildiği için.


# 8. Anakart ve North Bridge
## Bu nedir?

Anakart bütün donanım birimlerinin bağlandığı ana platformdur. North Bridge (Kuzey Köprüsü), özellikle CPU ve RAM arasındaki yoğun trafiği yönetir.
## Bunu neden öğreniyoruz?

Donanım parçalarının fiziksel ve mantıksal iletişimi anlaşılmadan sistem davranışı analiz edilemez.
## Günlük hayat analojisi

Anakart şehir yolları, North Bridge ise en yoğun kavşaktaki trafik polisi gibidir.
## Metinde geçen özel örnekler ve terimler

- USB
- Ethernet
- SATA
- LPT portu
- Nokta vuruşlu yazıcılar
- Klavye-mouse bağlantıları
- CD-ROM/DVD-ROM
- BIOS pili

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Anakart | Donanımları bağlar. |
| CPU | İşlem yapar. |
| North Bridge | CPU-RAM trafiğini yönetir. |
| BIOS pili | BIOS ayarlarının korunmasına yardım eder. |

## HATIRLA

> Anakart bilgisayarın iletişim omurgasıdır.

## KENDİNİ TEST ET

**Soru 1:** Anakartın görevi nedir?

**Cevap:** Donanımları bağlayıp iletişimlerini sağlamaktır.

**Soru 2:** North Bridge ne işe yarar?

**Cevap:** CPU ile RAM arasındaki trafiği yönetir.

**Soru 3:** SATA ne için kullanılır?

**Cevap:** Depolama cihazlarını bağlamak için.


# 9. IoT ve Mobil Cihazlar
## Bu nedir?

IoT (Internet of Things - Nesnelerin İnterneti), internete bağlanan akıllı nesnelerin oluşturduğu ekosistemdir. Bu cihazlar veri toplar, merkeze gönderir, analiz sonucunda komut alabilir.
## Bunu neden öğreniyoruz?

İnternete bağlanan her cihaz yeni bir saldırı yüzeyi oluşturur. IoT yaygınlaştıkça güvenlik yönetimi zorlaşır.
## Günlük hayat analojisi

Evde tek kapı varsa güvenlik kolaydır. 30 kapı, pencere ve garaj varsa güvenlik karmaşıklaşır. IoT cihaz sayısı arttıkça risk de artar.
## Metinde geçen özel örnekler ve terimler

- Akıllı saat
- Akıllı kulaklık
- Akıllı gözlük
- Robot süpürge
- Akıllı klima
- Akıllı ev
- Akıllı araba
- Trafik ışıkları
- Sağlık cihazları
- Giyilebilir teknolojiler

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| IoT | İnternete bağlı nesneler. |
| Mobil cihaz | Telefon/tablet gibi taşınabilir cihaz. |
| Akıllı cihaz | Veri toplayıp bağlantı kurabilen cihaz. |
| IP alan cihaz | Ağda tanımlanabilen cihazdır. |

## HATIRLA

> IoT cihazı küçük olabilir ama güvenlik riski küçük değildir.

## KENDİNİ TEST ET

**Soru 1:** IoT ne demektir?

**Cevap:** Internet of Things - Nesnelerin İnterneti.

**Soru 2:** IoT neden risklidir?

**Cevap:** Veri toplar, gönderir ve ağ üzerinden erişilebilir.

**Soru 3:** Akıllı trafik ışığı neden IoT örneğidir?

**Cevap:** Veri toplayıp analiz sonucuna göre davranış değiştirebildiği için.


# 10. Bluetooth, Wi-Fi ve Hücresel Teknoloji
## Bu nedir?

Bluetooth kısa mesafede düşük güçle çalışır. Wi-Fi, IEEE 802.11 standardına dayanır ve 2.4 GHz, 5 GHz, yeni nesilde 6 GHz bantlarını kullanabilir. Hücresel teknoloji SIM kart üzerinden 1G’den 5G’ye gelişmiştir.
## Bunu neden öğreniyoruz?

Kablosuz bağlantılar pratik olsa da güvenlik, menzil, hız ve kararlılık açısından doğru anlaşılmalıdır.
## Günlük hayat analojisi

Bluetooth kısa mesafe telsiz, Wi-Fi ev/ofis içi kablosuz ağ, hücresel bağlantı ise şehir genelindeki mobil iletişim ağı gibidir.
## Metinde geçen özel örnekler ve terimler

- Bluetooth 6.0
- IEEE 802.11
- 2.4 GHz
- 5 GHz
- 6 GHz
- 1G
- 3G
- 4G
- 5G
- SIM kart
- Information is Beautiful ve Hindistan SIM verisi örneği

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Bluetooth | Kısa mesafe ve düşük güç. |
| Wi-Fi | Yerel kablosuz ağ. |
| Hücresel | SIM kart ve baz istasyonu üzerinden bağlantı. |
| Ethernet | Kablolu ağ bağlantısı. |

## HATIRLA

> Kablolu bağlantı çoğu durumda kablosuz bağlantıdan daha stabil ve hızlıdır.

## KENDİNİ TEST ET

**Soru 1:** Wi-Fi hangi standart ailesine dayanır?

**Cevap:** IEEE 802.11.

**Soru 2:** Bluetooth’un avantajı nedir?

**Cevap:** Kısa mesafede düşük güç tüketmesi.

**Soru 3:** Hücresel bağlantı neyle çalışır?

**Cevap:** SIM kart ve mobil ağ altyapısı ile.


# 11. Mobil Cihaz Tehditleri
## Bu nedir?

Mobil cihazlar zararlı yazılım, casus yazılım, phishing, sosyal mühendislik, browser açıkları, eski işletim sistemi açıkları, Wi-Fi dinleme, BYOD riski ve fiziksel kayıp/çalınma gibi tehditlerle karşılaşır.
## Bunu neden öğreniyoruz?

Telefonlar artık kişisel veri merkezi gibidir. Banka, e-posta, fotoğraf, konum ve 2FA bilgileri mobil cihazlarda tutulur.
## Günlük hayat analojisi

Telefon cebindeki küçük kasa gibidir. Kasa çalınırsa ya da anahtarı ele geçirilirse içindeki her şey risk altına girer.
## Metinde geçen özel örnekler ve terimler

- Malware
- Spyware
- Zero Day Vulnerability
- Phishing
- Social Engineering
- Drive-by Download
- Chrome açıklıkları
- iOS/Android açıkları
- Jeff Bezos video ile hacklenme örneği
- 32-35 saniyede PIN kırma videosu

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Malware | Genel zararlı yazılım. |
| Spyware | Kullanıcıyı izleyen zararlı. |
| Phishing | Kandırarak bilgi çalma. |
| Zero Day | Henüz düzeltilmemiş veya yeni keşfedilmiş açık. |
| Fiziksel tehdit | Cihazın kaybolması veya çalınması. |

## HATIRLA

> Mobil cihaz küçük değildir; kişisel ve kurumsal veri taşıyan kritik bir uç noktadır.

## KENDİNİ TEST ET

**Soru 1:** Zero Day nedir?

**Cevap:** Yeni keşfedilmiş veya henüz düzeltilmemiş güvenlik açığıdır.

**Soru 2:** Phishing nedir?

**Cevap:** Kullanıcıyı kandırarak bilgi çalma saldırısıdır.

**Soru 3:** Cihaz kaybı neden risktir?

**Cevap:** Fiziksel erişim saldırgana veri ele geçirme imkanı verebilir.


# 12. Jailbreaking ve Rooting
## Bu nedir?

Jailbreaking iOS cihazlarda Apple sınırlarının kaldırılmasıdır. Rooting Android cihazlarda en üst kullanıcı yetkisine erişmektir.
## Bunu neden öğreniyoruz?

Mobil cihazlarda yetki sınırlarının kaldırılması cihazı esnekleştirir ama güvenlik riskini artırır.
## Günlük hayat analojisi

Telefon kiralık ev gibidir. Normal kullanıcı evde yaşar ama duvarları kıramaz. Root/Jailbreak yapınca duvarları da değiştirebilir; özgürlük artar ama risk de artar.
## Metinde geçen özel örnekler ve terimler

- iOS Jailbreaking
- Android Rooting
- Kaldırılamayan sistem uygulamaları
- Root kullanıcı yetkisi

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Jailbreaking | iOS tarafındaki sınır kaldırma işlemidir. |
| Rooting | Android tarafındaki en üst yetki alma işlemidir. |
| Admin | Bilgisayar sistemlerindeki yönetici yetkisidir. |
| Root | Linux/Unix dünyasında en yetkili kullanıcıdır. |

## HATIRLA

> Daha fazla yetki, daha fazla sorumluluk ve daha fazla risk demektir.

## KENDİNİ TEST ET

**Soru 1:** Jailbreaking hangi sistemde kullanılır?

**Cevap:** iOS.

**Soru 2:** Rooting hangi sistemde kullanılır?

**Cevap:** Android.

**Soru 3:** Root edilmiş cihaz neden risklidir?

**Cevap:** Zararlı uygulamalar daha yüksek yetkiyle çalışabilir.


# 13. Network Temel Mantığı
## Bu nedir?

Network, birden fazla cihazın kablolu veya kablosuz iletişim kurduğu yapıdır. İnternete çıkması şart değildir. Trusted Network iç ağ, Untrusted Network internet/dış ağ olarak düşünülür.
## Bunu neden öğreniyoruz?

Siber güvenlik mühendisliğinin ana çalışma alanı ağlardır. Saldırı ve savunma çoğu zaman ağ trafiği üzerinde gerçekleşir.
## Günlük hayat analojisi

Bir şirketi kale gibi düşün. Dış duvarlar sağlam olabilir ama içerideki biri kapıyı açarsa dış savunma yetmez.
## Metinde geçen özel örnekler ve terimler

- Trusted Network
- Untrusted Network
- İnsan en zayıf halka
- Sosyal mühendislik
- Memnuniyetsiz çalışan
- İç tehdit

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| İç ağ | Güvenilir kabul edilir ama yüzde yüz güvenli değildir. |
| İnternet | Untrusted kabul edilir. |
| Yüzde yüz güvenlik | Gerçekte yoktur. |
| İnsan faktörü | Manipülasyon ve hata riski taşır. |

## HATIRLA

> İçerisi güvenlidir varsayımı tehlikelidir. Güven sınırlı ve kontrollü verilmelidir.

## KENDİNİ TEST ET

**Soru 1:** Network nedir?

**Cevap:** Cihazların iletişim kurduğu ağ yapısıdır.

**Soru 2:** İnternet neden untrusted kabul edilir?

**Cevap:** Kontrolümüz dışında ve saldırganlara açık olduğu için.

**Soru 3:** En zayıf halka neden insandır?

**Cevap:** Hata yapabilir veya manipüle edilebilir.


# 14. Network Cihazları: NIC, Hub, Switch, Router, Firewall, WAP ve Modem
## Bu nedir?

NIC bilgisayarı ağa bağlar. Hub gelen veriyi herkese yollar. Switch MAC adresiyle LAN içinde iletim yapar. Router IP adresiyle farklı ağları bağlar. Firewall trafiği filtreler. WAP kablolu ağı kablosuza çevirir. Modem telefon/kablo sinyalini internet erişimine dönüştürür.
## Bunu neden öğreniyoruz?

Ağ cihazlarının görevleri bilinmezse güvenlik topolojisi, trafik akışı ve saldırı yüzeyi doğru analiz edilemez.
## Günlük hayat analojisi

Hub sınıfta herkese bağıran kişi, Switch kimin nerede oturduğunu bilen sınıf başkanı, Router mahalleler arası postacı, Firewall güvenlik görevlisi, WAP kablolu interneti kablosuz yayına çeviren istasyondur.
## Metinde geçen özel örnekler ve terimler

- RJ45 konnektör
- Ethernet kablosu
- 8 bakır pin
- RJ45 pensesi
- USB-RJ45 dönüştürücü
- USB Wireless Adapter
- ADSL
- DSL
- Kablo modem
- Wireless Access Point
- LAN
- WAN

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Hub | Geleni herkese gönderir. |
| Switch | MAC adresiyle doğru cihaza yollar. |
| Router | IP adresiyle farklı ağları bağlar. |
| Firewall | Trafiği güvenlik kurallarına göre filtreler. |
| WAP | Kablolu ağı kablosuz erişilebilir hale getirir. |

## HATIRLA

> Switch MAC adresiyle, Router IP adresiyle, Firewall güvenlik politikasıyla çalışır.

## KENDİNİ TEST ET

**Soru 1:** Switch hangi adres türünü kullanır?

**Cevap:** MAC adresi.

**Soru 2:** Router ne işe yarar?

**Cevap:** Farklı ağları birbirine bağlar.

**Soru 3:** WAP ne yapar?

**Cevap:** Kablolu ağı kablosuz hale getirir.


# 15. İşletim Sistemleri
## Bu nedir?

Operating System (İşletim Sistemi), donanım ile kullanıcı/uygulama arasında tercümandır. Uygulamalar doğrudan donanıma değil işletim sistemi üzerine kurulur.
## Bunu neden öğreniyoruz?

İşletim sistemi güvenlik, dosya, kullanıcı, ağ ve donanım yönetiminin merkezidir.
## Günlük hayat analojisi

İşletim sistemi ülkenin anayasası gibidir. İnsanların, kurumların ve kaynakların nasıl çalışacağını belirler.
## Metinde geçen özel örnekler ve terimler

- Windows
- Linux
- macOS
- Android
- iOS
- Chrome OS
- FortiOS
- FreeBSD
- OpenBSD
- NetBSD
- Oracle Solaris
- Proxmox
- Apple watchOS
- Apple tvOS
- Apple visionOS

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Donanım | Fiziksel parçadır. |
| İşletim sistemi | Donanımı ve uygulamaları yöneten temel yazılımdır. |
| Uygulama | İşletim sistemi üzerinde çalışan programdır. |
| Driver | Donanımı işletim sistemine tanıtan yazılımdır. |

## HATIRLA

> Uygulamalar doğrudan donanım üzerinde değil işletim sistemi üzerinde çalışır.

## KENDİNİ TEST ET

**Soru 1:** İşletim sistemi ne yapar?

**Cevap:** Donanım, kullanıcı ve uygulamalar arasındaki iletişimi yönetir.

**Soru 2:** Uygulamalar doğrudan donanıma mı kurulur?

**Cevap:** Hayır, işletim sistemi üzerine kurulur.

**Soru 3:** File management nedir?

**Cevap:** Dosya oluşturma, silme, adlandırma, taşıma ve saklama işlemleridir.


# 16. GUI ve CLI
## Bu nedir?

GUI (Graphical User Interface) görsel arayüzdür. CLI (Command Line Interface) komut satırı arayüzüdür. Windows CMD, PowerShell, Linux Terminal ve macOS Terminal CLI örnekleridir.
## Bunu neden öğreniyoruz?

Siber güvenlik araçlarının büyük kısmı komut satırında çalışır. GUI kolaydır ama CLI daha güçlü ve esnektir.
## Günlük hayat analojisi

GUI restoranda menüden seçmek gibidir. CLI mutfağa gidip aşçıya tam tarifi vermek gibidir.
## Metinde geçen özel örnekler ve terimler

- DOS
- Windows 95
- User Friendly
- CMD
- PowerShell
- Linux Terminal
- macOS Terminal

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| GUI | Görsel arayüzdür. |
| CLI | Komut satırıdır. |
| CMD | Windows komut satırı aracıdır. |
| PowerShell | Windows’un daha güçlü komut ve otomasyon kabuğudur. |
| Terminal | Linux/macOS komut ortamıdır. |

## HATIRLA

> GUI’de yapılan çoğu şey CLI’de yapılır; CLI’de yapılan her şey GUI’de olmayabilir.

## KENDİNİ TEST ET

**Soru 1:** GUI nedir?

**Cevap:** Grafiksel kullanıcı arayüzü.

**Soru 2:** CLI nedir?

**Cevap:** Komut satırı arayüzü.

**Soru 3:** Linux eğitiminde CLI neden önemlidir?

**Cevap:** Birçok güvenlik aracı terminalden çalıştığı için.


# 17. Linux, Kali Linux ve Debian
## Bu nedir?

Linux açık kaynaklı bir çekirdektir. Distro (Distribution - Dağıtım), Linux çekirdeği üzerine hazırlanmış işletim sistemi paketidir. Kali Linux, Offensive Security tarafından güvenlik ve penetration testing için hazırlanmış Debian tabanlı dağıtımdır.
## Bunu neden öğreniyoruz?

Linux siber güvenlik, sunucu yönetimi, pentest, forensic ve otomasyon için temel beceridir.
## Günlük hayat analojisi

Debian boş bir atölye gibidir; araçları sen yerleştirirsin. Kali Linux ise güvenlik araçları yerleştirilmiş hazır takım çantası gibidir.
## Metinde geçen özel örnekler ve terimler

- Linus Torvalds
- Unix
- Linux is not Unix
- Open Source
- Community
- Kali Linux
- Offensive Security
- Debian
- Ubuntu
- Fedora
- TryHackMe AttackBox
- 600’den fazla güvenlik aracı

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Linux | Çekirdek ve ekosistemdir. |
| Distro | Linux üzerine hazırlanmış dağıtımdır. |
| Debian | Genel amaçlı dağıtımdır. |
| Kali Linux | Güvenlik araçları hazır gelen Debian tabanlı dağıtımdır. |
| AttackBox | TryHackMe’nin hazır lab ortamıdır. |

## HATIRLA

> Kali Linux sihirli hacker sistemi değildir; hazır güvenlik araçları olan Linux dağıtımıdır.

## KENDİNİ TEST ET

**Soru 1:** Linux neden önemlidir?

**Cevap:** Birçok güvenlik aracı Linux üzerinde çalışır.

**Soru 2:** Kali Linux’un Debian’dan farkı nedir?

**Cevap:** Siber güvenlik araçları hazır gelir.

**Soru 3:** Distro ne demektir?

**Cevap:** Linux dağıtımıdır.


# 18. Windows, Dosya Uzantıları ve Kapalı Kaynak Riski
## Bu nedir?

Windows Microsoft tarafından geliştirilen kapalı kaynaklı işletim sistemidir. Dosyalar uzantılarına göre yorumlanır: .exe çalıştırılabilir dosya, .zip arşiv, .txt metin, .html web sayfası, .png görsel dosyasıdır.
## Bunu neden öğreniyoruz?

Windows çok yaygın olduğu için saldırganlar tarafından sık hedeflenir. Dosya uzantıları ve kapalı kaynak modeli güvenlik analizinde önemlidir.
## Günlük hayat analojisi

Windows büyük ve popüler bir alışveriş merkezi gibidir. Herkes kullandığı için saldırganların ilgisi de fazladır.
## Metinde geçen özel örnekler ve terimler

- Windows 3.1
- Windows 95
- Windows 98 SE
- Windows ME
- Windows XP
- Windows Vista
- Windows 7
- Windows 8/8.1
- Windows 10
- Windows 11
- Stuxnet
- İran nükleer santrali
- Pardus
- TÜBİTAK
- Almanya’nın Linux tabanlı sistem çalışmaları

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| exe | Çalıştırılabilir dosyadır. |
| zip | Sıkıştırılmış dosyadır. |
| txt | Düz metin dosyasıdır. |
| html | Web sayfası dosyasıdır. |
| png | Şeffaflık destekleyen görsel dosyası olabilir. |

## HATIRLA

> Windows yaygındır; yaygınlık güvenlik anlamına gelmez.

## KENDİNİ TEST ET

**Soru 1:** Windows açık kaynak mı?

**Cevap:** Hayır, kapalı kaynaklıdır.

**Soru 2:** .exe nedir?

**Cevap:** Çalıştırılabilir Windows dosyasıdır.

**Soru 3:** PNG neden kullanılır?

**Cevap:** Şeffaf arka plan gibi özellikleri destekleyebildiği için.


# 19. PowerShell Güvenlik Riski
## Bu nedir?

PowerShell, Windows’un gelişmiş komut ve otomasyon kabuğudur. Yönetici yetkileriyle çalışabildiği için RCE (Remote Code Execution - Uzaktan Kod Çalıştırma) saldırılarında kötüye kullanılabilir.
## Bunu neden öğreniyoruz?

Güçlü yönetim araçları yanlış kullanıcıda açık bırakılırsa saldırgan için fırsat oluşturur.
## Günlük hayat analojisi

PowerShell büyük anahtar takımı gibidir. Sistem yöneticisi için faydalıdır; muhasebe kullanıcısının masasında gereksiz ve risklidir.
## Metinde geçen özel örnekler ve terimler

- CMD
- PowerShell
- Administrator olarak çalıştırma
- RCE
- Zararlı PowerShell komutları
- EDR tespitleri

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| CMD | Temel Windows komut satırıdır. |
| PowerShell | Daha güçlü komut ve otomasyon kabuğudur. |
| RCE | Uzaktan kod çalıştırma saldırısıdır. |
| Disable etmek | Gereksiz servisi/özelliği kapatmaktır. |

## HATIRLA

> Kullanılmayan güçlü araç açık bırakılmamalıdır.

## KENDİNİ TEST ET

**Soru 1:** PowerShell neden riskli olabilir?

**Cevap:** Yüksek yetkiyle güçlü komutlar çalıştırabilir.

**Soru 2:** RCE nedir?

**Cevap:** Uzaktan kod çalıştırma saldırısıdır.

**Soru 3:** Her kullanıcıda PowerShell açık olmalı mı?

**Cevap:** Hayır, ihtiyaç yoksa kapatılmalıdır.


# 20. macOS, Sanallaştırma ve Dual Boot
## Bu nedir?

macOS Apple tarafından geliştirilen kapalı kaynaklı işletim sistemidir. Kali Linux macOS veya Windows üzerinde VirtualBox/VMware ile sanal makine olarak çalıştırılabilir. Dual boot ise aynı bilgisayarda iki işletim sistemini açılışta seçerek kullanmaktır.
## Bunu neden öğreniyoruz?

Farklı işletim sistemlerini güvenli ve kontrollü kullanmak siber güvenlik öğreniminde önemlidir.
## Günlük hayat analojisi

Sanallaştırma evin içinde eğitim amaçlı küçük bir laboratuvar odası kurmak gibidir; ana evi bozmazsın. Dual boot ise eve iki ayrı giriş kapısı yapmak gibidir.
## Metinde geçen özel örnekler ve terimler

- macOS Terminal
- Finder
- VPN
- VirtualBox
- VMware
- Kali Linux VM
- Dual Boot
- Raspberry Pi üzerinde Debian
- TryHackMe AttackBox

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Sanallaştırma | Ana sistemi bozmadan sanal sistem çalıştırmaktır. |
| Dual Boot | Açılışta işletim sistemi seçmektir. |
| macOS | Apple cihazlarda çalışan kapalı kaynak sistemdir. |
| Kali VM | Sanal makinede çalışan Kali ortamıdır. |

## HATIRLA

> Yeni başlayan için sanallaştırma dual boot’tan daha kontrollü ve güvenlidir.

## KENDİNİ TEST ET

**Soru 1:** Sanallaştırma ne işe yarar?

**Cevap:** Ana sistemi bozmadan farklı işletim sistemi çalıştırmaya yarar.

**Soru 2:** Dual boot nedir?

**Cevap:** Aynı bilgisayarda birden fazla işletim sistemi kurup seçim yapmaktır.

**Soru 3:** Kali macOS içinde çalışabilir mi?

**Cevap:** Evet, sanallaştırma ile çalışabilir.


# 21. SolarWinds ve Tedarik Zinciri Saldırısı
## Bu nedir?

Supply Chain Attack (Tedarik Zinciri Saldırısı), hedef kuruma doğrudan saldırmak yerine hedefin güvendiği tedarikçiye saldırmaktır. SolarWinds örneğinde saldırganların güncelleme paketine zararlı yerleştirdiği anlatılır.
## Bunu neden öğreniyoruz?

Güvenlik sadece kendi sistemini korumak değildir; güvendiğin tedarikçinin güvenliği de seni etkiler.
## Günlük hayat analojisi

Binaya dışarıdan girmeye çalışanı güvenlik durdurabilir. Ama güvenilen kargo paketinin içine zararlı cihaz konursa paket içeri alınabilir.
## Metinde geçen özel örnekler ve terimler

- SolarWinds
- Google
- Microsoft
- Amerika devlet kurumları
- Güncelleme paketi
- Trusted vendor
- Supply Chain Attack

## KARIŞTIRMA!

| Kavram | Net farkı |
|---|---|
| Direct Attack | Hedefe doğrudan saldırıdır. |
| Supply Chain Attack | Tedarikçi üzerinden saldırıdır. |
| Update Package | Güncelleme paketidir. |
| Trusted Vendor | Güvenilen tedarikçidir. |

## HATIRLA

> Güvenilen kaynaktan gelen paket bile saldırı vektörü olabilir.

## KENDİNİ TEST ET

**Soru 1:** Tedarik zinciri saldırısı nedir?

**Cevap:** Güvenilen üçüncü taraf üzerinden yapılan saldırıdır.

**Soru 2:** SolarWinds örneğinde ne oldu?

**Cevap:** Güncelleme paketine zararlı kod yerleştirildi.

**Soru 3:** Neden tehlikelidir?

**Cevap:** Kurumlar güvenilir tedarikçiden gelen paketi sorgulamadan kabul edebilir.


# Genel Tekrar ve Özet

## Büyük Resim

Bu dersin ana zinciri şudur:

**Donanım -> İşletim Sistemi -> Ağ -> İnternet -> Kullanıcı -> Güvenlik Riski -> Savunma Stratejisi**

Siber güvenlikçi olmak için bilgisayarı sadece kullanmak yetmez. Bilgisayarın nasıl açıldığını, verinin nerede tutulduğunu, ağdan nasıl geçtiğini, işletim sisteminin neyi yönettiğini ve saldırganın hangi noktaları hedefleyebileceğini anlamak gerekir.

## En Kritik 10 Ders

1. Siber güvenlikte yüzde yüz güvenlik yoktur.
2. İnsan faktörü en zayıf halkadır.
3. Donanımı bilmeden sistem güvenliği tam anlaşılamaz.
4. RAM geçici, disk kalıcıdır.
5. BIOS bilgisayarın açılış kontrol merkezidir.
6. Switch MAC adresiyle, Router IP adresiyle çalışır.
7. Firewall trusted ve untrusted ağlar arasında güvenlik uygular.
8. IoT cihazları küçük görünür ama büyük risk oluşturabilir.
9. Linux ve CLI siber güvenlik öğrencisi için zorunlu beceridir.
10. Güvenilen güncelleme bile tedarik zinciri saldırısıyla zararlı hale gelebilir.

## Son Net Tavsiye

Bu dersin gerçek değeri kavramları tek tek ezberlemek değil, aralarındaki bağlantıyı görmektir. Donanım, işletim sistemi, ağ, kullanıcı ve güvenlik olayları ayrı konular gibi görünür; pratikte hepsi aynı sistemin parçalarıdır.
