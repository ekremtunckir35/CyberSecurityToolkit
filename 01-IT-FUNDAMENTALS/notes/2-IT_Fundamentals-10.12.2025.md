# IT Fundamentals-3 Ders Notu
## Siber Güvenlik ve Bilgisayar Temelleri

**Kaynak transkript:** `2-10.12.2025 - IT Fundamentals-3.docx`

> Not: Bu doküman, ham ders transkriptindeki konuşma/OCR hataları anlam korunarak düzeltilerek hazırlanmıştır. Örnek düzeltmeler: `kuyuz -> quiz`, `trahekmi -> TryHackMe`, `Regec 45 -> RJ45`, `SIM -> SIEM`, `FET -> FAT`, `XFAT -> exFAT`.

---

# ADIM 1 - Metin Analizi: Ana Başlıklar ve Alt Konular

Bu ders kaydında geçen ana konular:

1. **Ders işleyişi ve pekiştirme sistemi**
   - Quiz, etüt, TryHackMe, laboratuvar çalışmaları, günlük tekrar
2. **Siber güvenliğe giriş**
   - Cyber/Siber, Cyberspace/Siber Uzay, Communication/İletişim, Cyber Security/Siber Güvenlik
3. **Standartlar ve kurumlar**
   - NIST, ISO, IEEE, ASCII, protokoller, RJ45, NIC/Ethernet kartı, güvenlik açıklarına standart kod verilmesi
4. **Siber güvenlik prensipleri**
   - Confidentiality/Gizlilik, Integrity/Bütünlük, Availability/Erişilebilirlik, Authentication/Kimlik Doğrulama, Non-repudiation/İnkar Edilemezlik
5. **Gerçek siber güvenlik olayları**
   - Microsoft/CrowdStrike benzeri kesinti, Cloudflare kesintisi, Adobe veri sızıntısı, Estonya 2007, Stuxnet, Lockheed Martin/F-35, Edward Snowden/NSA, FireEye, Rusya-Ukrayna siber casusluk, nation-state saldırılar
6. **Siber savunma ve tespit**
   - Firewall, EDR, SIEM, SOC Analyst, Incident Response, log inceleme, 7/24 monitoring, VPN, anonimlik, zombi bilgisayarlar, misconfiguration
7. **Dijitalleşme ve sosyal medya riski**
   - Reconnaissance/Keşif, sosyal medya üzerinden bilgi toplama, kahin çadırı videosu analojisi, tatil fotoğrafı paylaşma riski
8. **Kritik altyapılar**
   - Elektrik, doğalgaz, petrol boru hatları, finans, taşımacılık, savunma, enerji, iletişim, SCADA, OT Security
9. **AI, kuantum bilgisayarlar ve gelecek roller**
   - AI Security, SOC Level 1 otomasyonu, ChatGPT, Gemini, Machine Learning, Quantum Computer, Qubit, NIST kuantum çalışmaları, insan faktörü
10. **Bilgisayar bileşenleri ve çalışma mantığı**
    - Desktop, laptop, smart TV, game console, digital camera, tablet, phone, sensor, wearable technology, industrial computer, Linux kernel, input/output/storage, CPU, RAM, ROM, flash memory, binary, analog/digital
11. **Depolama sistemleri ve dosya sistemleri**
    - Hard disk, SSD, NAS, SAN, cloud storage, backup, ransomware, file system, FAT16, FAT32, NTFS, exFAT, EXT3, EXT4, XFS
12. **Anakart ve temel donanım**
    - Motherboard, power supply, CPU, RAM, GPU, buzzer, keyboard, mouse, speaker, hard disk, işletim sistemi kurulumu

---

# BÖLÜM 1 - Dersin İşleyişi: Quiz, TryHackMe ve Laboratuvarlar

## Bu nedir?

Dersin başında eğitmen, öğrenmenin sadece canlı derste kalmaması gerektiğini anlatıyor. Bunun için günlük **quiz**, etüt çalışmaları, TryHackMe odaları, ek laboratuvar uygulamaları ve tekrar sistemleri kullanılacak.

## Bunu neden öğreniyoruz?

Siber güvenlik ezberle öğrenilecek bir alan değildir. Bilgiyi tekrar etmezsen unutursun. Uygulama yapmazsan teorik bilgi işe yaramaz.

## Günlük hayat analojisi

Siber güvenlik öğrenmek spor salonuna gitmek gibidir. Bir gün çalışıp bırakırsan gelişmezsin. Her gün kısa tekrar yaparsan kas hafızası oluşur. Quiz zihinsel tekrar, TryHackMe ise gerçek antrenman sahasıdır.

## Kavramlar

| Kavram | Açıklama |
|---|---|
| Quiz | Öğrenilen konuyu kısa sorularla tekrar etme |
| TryHackMe | Siber güvenlik pratik platformu |
| Lab | Gerçek sistem benzeri ortamda uygulama |
| Etüt | Canlı ders dışı tekrar / çözüm oturumu |

> **HATIRLA:** Siber güvenlikte “dinledim, anladım” yeterli değildir. “Yaptım, hata aldım, düzelttim” seviyesine gelmen gerekir.

## KARIŞTIRMA!

| Kavram | Ne değildir? | Doğru anlam |
|---|---|---|
| Quiz | Sadece sınav değildir | Hatırlatma aracıdır |
| TryHackMe | Sadece oyun değildir | Pratik siber güvenlik laboratuvarıdır |
| Lab | Sadece izlenecek video değildir | Deneyerek öğrenme ortamıdır |

## Kendini Test Et

**Soru 1:** Quiz’in temel amacı nedir?  
**Cevap:** Ölçmekten çok tekrar ve kalıcılık sağlamaktır.

**Soru 2:** TryHackMe neden önemlidir?  
**Cevap:** Siber güvenlik araçlarını gerçekçi senaryolarda kullanmayı öğretir.

**Soru 3:** Sadece ders dinlemek neden yetmez?  
**Cevap:** Çünkü siber güvenlik uygulamalı bir alandır; komut, araç ve hata çözümü pratiği gerekir.

---

# BÖLÜM 2 - Cyber, Cyberspace ve Cyber Security

## Bu nedir?

**Cyber (Siber)** kelimesi, bilgisayarlar, ağlar, dijital sistemler ve bunların oluşturduğu alanla ilgilidir.

**Cyberspace (Siber Uzay)** bilgisayarların, sunucuların, telefonların, ağ cihazlarının ve internet üzerinden iletişim kuran tüm sistemlerin oluşturduğu dijital alandır.

Bir cihazın siber uzayın parçası olabilmesi için başka cihazlarla **Communication (İletişim)** kurabilmesi gerekir. Bu iletişim kablolu, kablosuz veya farklı teknolojilerle olabilir.

## Cyber Security (Siber Güvenlik) nedir?

Siber güvenlik; kişilerin, şirketlerin, kurumların ve ülkelerin bilgisayar sistemlerinde bulunan bilgilerini koruma disiplinidir.

Koruma şunlara karşı yapılır:

- Hacker saldırıları
- Veri hırsızlığı
- Sistem kesintisi
- Bilgi manipülasyonu
- Fidye yazılımı
- Casusluk
- Devlet destekli saldırılar

## Bunu neden öğreniyoruz?

Artık para, sağlık kayıtları, kimlik bilgileri, banka bilgileri, şirket sırları ve devlet sistemleri dijital ortamda tutuluyor. Veri dijitalleştiyse saldırı yüzeyi de büyümüştür.

## Günlük hayat analojisi

Eskiden önemli belgeler çelik kasada saklanırdı. Şimdi aynı belgeler sunucuda, bulutta veya bilgisayarda duruyor. Eskiden hırsızın binaya girmesi gerekirdi. Şimdi saldırgan dünyanın başka bir ülkesinden sisteme girmeye çalışabilir.

> **HATIRLA:** Siber güvenliğin amacı sadece “hacker yakalamak” değildir. Asıl amaç veriyi, sistemi ve erişimi korumaktır.

## KARIŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Cyber | Dijital sistemlerle ilgili alan |
| Cyberspace | Dijital sistemlerin oluşturduğu ortam |
| Cyber Security | Bu ortamı ve içindeki veriyi koruma disiplini |
| IT Security | Daha genel bilgi teknolojileri güvenliği |
| Information Security | Dijital veya fiziksel tüm bilgilerin güvenliği |

## Kendini Test Et

**Soru 1:** Bir cihazın siber uzayın parçası olması için ne gerekir?  
**Cevap:** Başka cihazlarla iletişim kurabilmesi gerekir.

**Soru 2:** Siber güvenlik kimleri korur?  
**Cevap:** Kişileri, şirketleri, kurumları ve ülkeleri.

**Soru 3:** Siber güvenlik sadece bilgisayar virüsleriyle mi ilgilenir?  
**Cevap:** Hayır. Veri gizliliği, sistem erişilebilirliği, saldırı tespiti, olay müdahalesi ve kritik altyapı güvenliğiyle de ilgilenir.

---

# BÖLÜM 3 - Standartlar: NIST, ISO, IEEE, ASCII, RJ45 ve NIC

## Bu nedir?

Teknoloji dünyasında herkes kendi kafasına göre hareket ederse sistemler birbirleriyle uyumsuz olur. Bu yüzden standartlar gerekir.

Ders içinde geçen kurum ve kavramlar:

- **NIST (National Institute of Standards and Technology)**
- **ISO**
- **IEEE**
- **ASCII**
- **RJ45**
- **NIC (Network Interface Card)**
- **Protocol (Protokol)**
- Güvenlik açıklarına verilen standart kodlar

## Standart nedir?

Standart, herkesin aynı kurala göre üretim veya işlem yapmasını sağlayan ortak anlaşmadır.

## Günlük hayat analojisi

Telefon şarj cihazlarını düşün. Eskiden Nokia ayrı uç, iPhone ayrı uç, Samsung ayrı uç kullanıyordu. Sonra Type-C gibi ortak standartlar yaygınlaştı. Bilgisayar dünyasında da benzer şekilde standartlar uyumluluk sağlar.

## Önemli kavramlar

| Kavram | Bu nedir? |
|---|---|
| NIST | Standart ve teknoloji alanında rehberler hazırlayan kurum |
| ISO | Uluslararası standartlar oluşturan yapı |
| IEEE | Elektrik, elektronik ve bilgisayar alanında standartlar geliştiren kurum |
| ASCII | Karakterlerin bilgisayarda temsil edilmesini sağlayan standart |
| RJ45 | Ethernet kablosunun takıldığı bağlantı ucu |
| NIC | Bilgisayarın ağa bağlanmasını sağlayan ağ kartı |
| Protocol | Cihazların nasıl konuşacağını belirleyen kurallar bütünü |

## Siber güvenlikte standart kod meselesi

Ders içinde güvenlik açıklarına standart kod verilmesinden bahsediliyor. Bu mantık pratikte **CVE (Common Vulnerabilities and Exposures)** yaklaşımına benzer. Bir açık çıktığında herkes ona kendi istediği ismi vermez. Ortak kod kullanılır. Böylece antivirüs firmaları, güvenlik araştırmacıları, yazılım üreticileri ve sistem yöneticileri aynı açıklıktan bahsettiklerini bilir.

## Bunu neden öğreniyoruz?

Siber güvenlikte standart bilmeyen kişi araçları kullanabilir ama sistemi anlayamaz. Gerçek iş hayatında NIST Framework, ISO 27001, CVE kodları, IEEE ağ standartları, TCP/IP protokolleri, RJ45 bağlantı ve NIC ayarları sürekli karşına çıkar.

## KARIŞTIRMA!

| Kavram | Karıştırılan kavram | Fark |
|---|---|---|
| RJ45 | Ethernet kablosu | RJ45 uçtur, Ethernet daha geniş ağ teknolojisidir |
| NIC | Modem | NIC bilgisayarın ağ kartıdır; modem internet servis bağlantısı sağlar |
| ASCII | Klavye | ASCII karakter standardıdır; klavye giriş cihazıdır |
| NIST | ISO | İkisi de standart üretir ama farklı kurum ve kapsamları vardır |

> **HATIRLA:** Standart yoksa uyumluluk yoktur. Uyumluluk yoksa sistemler birlikte çalışamaz.

## Kendini Test Et

**Soru 1:** RJ45 nedir?  
**Cevap:** Ethernet kablosunun bilgisayar veya ağ cihazına takılan bağlantı ucudur.

**Soru 2:** NIC ne işe yarar?  
**Cevap:** Bilgisayarın ağa bağlanmasını sağlar.

**Soru 3:** Güvenlik açıklarına standart kod verilmesi neden önemlidir?  
**Cevap:** Herkesin aynı güvenlik açığından bahsetmesini sağlar; takip, yama ve raporlama kolaylaşır.

---

# BÖLÜM 4 - CIA Üçlüsü: Gizlilik, Bütünlük, Erişilebilirlik

## Bu nedir?

Siber güvenliğin üç temel prensibi vardır:

1. **Confidentiality (Gizlilik)**
2. **Integrity (Bütünlük)**
3. **Availability (Erişilebilirlik)**

Bu üçü sağlanıyorsa güvenlikten bahsedebiliriz.

## Confidentiality (Gizlilik)

Bilginin sadece yetkili kişiler tarafından görülebilmesidir.

**Günlük hayat analojisi:** Banka kasandaki parayı sadece sen ve yetkili banka görevlisi görebilmeli. Herkes görebiliyorsa gizlilik bozulmuştur.

**Siber örnek:** Kredi kartı bilgilerinin çalınması gizlilik ihlalidir.

## Integrity (Bütünlük)

Bilginin izinsiz değiştirilmemesidir.

**Günlük hayat analojisi:** Öğretmen sınav notunu sisteme 80 olarak girdi. Birisi bunu 50 veya 100 yaptıysa bütünlük bozulmuştur.

**Siber örnek:** Bir mesajın yolda değiştirilmesi bütünlük ihlalidir.

## Availability (Erişilebilirlik)

Yetkili kişi, ihtiyaç duyduğu anda sisteme veya bilgiye ulaşabilmelidir.

**Günlük hayat analojisi:** Bankada paran var ama ATM çalışmıyor, mobil uygulama açılmıyor, şube kapalı. Para sende görünür ama erişemezsin. Bu erişilebilirlik problemidir.

**Siber örnek:** Cloudflare veya Microsoft/CrowdStrike benzeri kesintilerde sistem devre dışı kalırsa bu Availability problemidir.

## Bob, Alice ve Trudie örneği

Ders içinde Bob ve Alice iletişim kuran iki taraf olarak; Trudie ise araya giren kötü niyetli kişi olarak anlatılıyor.

| Senaryo | İhlal |
|---|---|
| Trudie mesajı okursa | Confidentiality ihlali |
| Trudie mesajı değiştirirse | Integrity ihlali |
| Trudie mesajın ulaşmasını engellerse | Availability ihlali |

## Ek prensipler

| Kavram | Açıklama |
|---|---|
| Authentication (Kimlik Doğrulama) | Kişinin gerçekten iddia ettiği kişi olup olmadığını doğrulama |
| Non-repudiation (İnkar Edilemezlik) | Bir işlemi yapan kişinin sonradan “ben yapmadım” diyememesi |

## Bunu neden öğreniyoruz?

Siber güvenlikte her olay bu üçlü üzerinden analiz edilir: Veri sızdı mı? Veri değişti mi? Sistem çalışıyor mu?

## KARIŞTIRMA!

| Kavram | Yanlış anlama | Doğru anlama |
|---|---|---|
| Gizlilik | Veriyi silmek | Yetkisiz kişilerin görmesini engellemek |
| Bütünlük | Dosyayı saklamak | Dosyanın değiştirilmediğini garanti etmek |
| Erişilebilirlik | Herkese açık yapmak | Yetkili kişinin ihtiyaç anında ulaşabilmesi |

> **HATIRLA:** CIA üçlüsü siber güvenliğin omurgasıdır. Bir saldırı mutlaka bu üçlüden en az birine zarar verir.

## Kendini Test Et

**Soru 1:** Kredi kartı bilgilerinin çalınması hangi prensibi bozar?  
**Cevap:** Confidentiality (Gizlilik).

**Soru 2:** Bir dosyanın içeriğinin değiştirilmesi hangi prensibi bozar?  
**Cevap:** Integrity (Bütünlük).

**Soru 3:** Bir bankanın internet şubesinin çalışmaması hangi prensibi bozar?  
**Cevap:** Availability (Erişilebilirlik).

---

# BÖLÜM 5 - Gerçek Siber Güvenlik Olayları

## Bu nedir?

Ders içinde birçok gerçek olaydan bahsediliyor. Bunlar siber güvenliğin sadece teorik olmadığını gösteriyor.

## Geçen olaylar

| Olay | Ders içindeki anlamı |
|---|---|
| Adobe veri sızıntısı | 153 milyon kaydın çalınması örneği |
| Estonya 2007 saldırısı | Dijital ülke altyapısının siber saldırıyla durması |
| Stuxnet | İran nükleer sistemlerine yönelik saldırı örneği |
| Lockheed Martin | F-35 planları dahil büyük veri hırsızlığı |
| Edward Snowden / NSA | Gizli izleme programları ve Zero Trust ihtiyacı |
| FireEye | Güvenlik firmasından veri/araç sızması |
| Rus hackerlar / Ukrayna | Siber casusluk ve istihbarat toplama |
| Microsoft / Cloudflare kesintileri | Erişilebilirlik problemi olarak güvenlik olayı |

## Estonya 2007 örneği

Estonya dijital dönüşümde ileri bir ülke olarak anlatılıyor. Rus hackerların saldırısı sonucu bankalar, sağlık sistemi ve birçok dijital sistem yaklaşık üç hafta ciddi sorun yaşamıştı. Bu olay, modern siber savaşın erken örneklerinden biri olarak değerlendiriliyor. Sonrasında NATO’nun siber güvenlik merkezi Estonya’da konumlanmıştır.

## Stuxnet örneği

Stuxnet, İran’ın nükleer programına zarar verdiği anlatılan önemli bir siber saldırı örneğidir. Ders içinde USB belleklerle sisteme girdiği ve İran tarafında farklı anlatımların bulunduğu belirtiliyor.

## Lockheed Martin ve F-35 örneği

Ders içinde Çinli hackerlar tarafından Lockheed Martin’den 50 TB’tan fazla veri çalındığı ve bu veriler içinde F-35 savaş uçaklarına ait planların bulunduğu anlatılıyor. Bu olay, endüstriyel casusluk ve savunma sanayi güvenliği açısından kritik örnek olarak verilmiş.

## Edward Snowden ve NSA

Edward Snowden’ın CIA ve NSA geçmişinden, NSA’in gizli izleme programlarından ve bu olayların **Zero Trust (Hiç Kimseye Güvenme)** yaklaşımını neden önemli hale getirdiğinden bahsediliyor.

## Bunu neden öğreniyoruz?

Siber güvenlik sadece “bilgisayarı korumak” değildir. Etkisi ekonomi, sağlık, savunma, enerji, diplomasi, kişisel mahremiyet ve ulusal güvenliğe kadar uzanır.

## Günlük hayat analojisi

Bir apartmanda sadece kendi dairenin kapısını kilitlemek yetmez. Elektrik panosu, su vanası, bina girişi, kamera sistemi ve yangın çıkışı da güvenli olmalıdır. Bir ülke için de durum aynıdır.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Veri sızıntısı | Bilginin dışarı çıkması |
| Siber casusluk | Bilginin gizlice toplanması |
| Sabotaj | Sisteme zarar verme |
| DDoS | Sistemi erişilemez hale getirme |
| Endüstriyel casusluk | Şirket/teknoloji sırlarının çalınması |

> **HATIRLA:** Büyük siber saldırılar genellikle tek adımlı değildir. Keşif, sızma, kalıcılık, veri toplama, veri çıkarma ve iz silme gibi aşamalar içerir.

## Kendini Test Et

**Soru 1:** Estonya 2007 saldırısı neden önemlidir?  
**Cevap:** Dijital altyapısı gelişmiş bir ülkenin siber saldırılarla ciddi şekilde durabileceğini göstermiştir.

**Soru 2:** Stuxnet hangi yönüyle önemlidir?  
**Cevap:** Siber saldırının fiziksel dünyadaki endüstriyel sistemlere zarar verebileceğini göstermiştir.

**Soru 3:** Snowden olayı hangi güvenlik yaklaşımını öne çıkarır?  
**Cevap:** Zero Trust yaklaşımını.

---

# BÖLÜM 6 - Savunma: Firewall, EDR, SIEM, SOC ve Incident Response

## Bu nedir?

Bir saldırıyı sadece engellemek yetmez. Aynı zamanda tespit etmek, analiz etmek, izole etmek, müdahale etmek, raporlamak ve tekrarını önlemek gerekir.

## Kavramlar

| Kavram | Bu nedir? |
|---|---|
| Firewall | Ağa giren ve çıkan trafiği kurallara göre kontrol eden güvenlik duvarı |
| EDR | Uç nokta cihazlarındaki tehditleri izleyen ve müdahale eden sistem |
| SIEM | Logları toplayıp korelasyon yapan güvenlik izleme sistemi |
| SOC Analyst | Güvenlik operasyon merkezinde olayları izleyen uzman |
| Incident Response | Olay müdahale süreci |
| Log | Sistemin tuttuğu olay kayıtları |
| Monitoring | Sistemi sürekli izleme |
| Misconfiguration | Yanlış yapılandırma |

## Ders içindeki örnek

Eğitmen, Finlandiya’daki bir kişinin Brezilya’daki bir banka için çalıştığını anlatıyor. Saat farkı sayesinde kişi bankanın sistemlerini izliyor. Büyük veri akışı veya anomali görürse sistemi izole ediyor. Bu gerçek hayattaki SOC/monitoring mantığını anlatır.

## Günlük hayat analojisi

Bir alışveriş merkezini düşün:

- Kapıdaki güvenlik: Firewall
- Kameralar: Monitoring
- Güvenlik kayıtları: Log
- Kamera görüntülerini izleyen ekip: SOC
- Hırsızlık olunca müdahale eden ekip: Incident Response
- Şüpheli kişiyi mağazadan çıkarma: İzolasyon

## VPN ve anonimlik

Saldırganlar VPN kullanarak izlerini gizleyebilir. Ancak VPN tek başına yüzde yüz anonimlik sağlamaz. Saldırganlar bazen birden fazla ülke, farklı hesaplar, ara sistemler veya zombi bilgisayarlar kullanabilir.

## Zombie bilgisayar nedir?

Kullanıcının farkında olmadan saldırgan tarafından kontrol edilen bilgisayardır. Sen bilgisayarında normal işini yaparken, arkada çalışan zararlı yazılım senin bilgisayarını saldırı aracı olarak kullanabilir.

## Bunu neden öğreniyoruz?

Şirketler saldırıları tamamen engelleyemeyebilir. Ama erken tespit ve doğru müdahale zararı azaltır.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Firewall | Ağ trafiğini kontrol eder |
| EDR | Bilgisayar/sunucu üzerindeki davranışları izler |
| SIEM | Logları merkezi olarak analiz eder |
| SOC | İnsan ve süreç tarafıdır |
| Incident Response | Olay olduktan sonraki müdahale sürecidir |

> **HATIRLA:** Güvenlik ürünü satın almak güvenlik sağlamak değildir. Doğru konfigürasyon, izleme ve müdahale yoksa araçlar dekor olur.

## Kendini Test Et

**Soru 1:** SIEM ne işe yarar?  
**Cevap:** Farklı sistemlerden log toplar, analiz eder ve güvenlik olaylarını tespit etmeye yardım eder.

**Soru 2:** EDR neyi korur?  
**Cevap:** Uç nokta cihazları; örneğin bilgisayarlar ve sunucular.

**Soru 3:** Zombie bilgisayar nedir?  
**Cevap:** Kullanıcının haberi olmadan saldırgan tarafından kontrol edilen bilgisayardır.

---

# BÖLÜM 7 - Sosyal Medya, Reconnaissance ve Dijital Ayak İzi

## Bu nedir?

**Reconnaissance (Keşif)**, saldırganın hedef hakkında bilgi toplama aşamasıdır.

Bilgiler şunlardan gelebilir:

- Instagram
- Twitter/X
- Facebook
- LinkedIn
- Tatil fotoğrafları
- Doğum günü paylaşımları
- Evcil hayvan isimleri
- Çalışılan şirket
- Kullanılan teknoloji
- Konum bilgisi

## Ders içindeki kahin çadırı videosu

Eğitmen bir video analojisinden bahsediyor: Bir çadırda kahin var. İnsanlar içeri giriyor. Kahin onlar hakkında şaşırtıcı bilgiler söylüyor. Aslında arkada bilgisayarcılar sosyal medya üzerinden kişinin bilgilerini araştırıyor ve kulaklıkla kahine iletiyor. Kahin doğaüstü güç kullanmıyor; sosyal medya keşfi yapılıyor.

## Tatil fotoğrafı örneği

Tatil fotoğrafını tatildeyken değil, döndükten sonra paylaşmak daha güvenlidir. Çünkü tatildeyken fotoğraf paylaşmak evinin boş olduğunu gösterebilir.

## Bunu neden öğreniyoruz?

Siber saldırılar her zaman teknik başlamaz. Çoğu saldırı önce insan hakkında bilgi toplayarak başlar.

## Günlük hayat analojisi

Kapının üzerine “Evde yokuz, 10 gün tatildeyiz” notu astığını düşün. Tatil fotoğrafını anlık paylaşmak dijital dünyada buna benzer.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Reconnaissance | Bilgi toplama aşaması |
| Exploitation | Açığı kullanma aşaması |
| Social Engineering | İnsan psikolojisini kullanarak kandırma |
| OSINT | Açık kaynaklardan bilgi toplama |

> **HATIRLA:** Saldırganın ilk silahı exploit olmayabilir. Bazen senin kendi paylaştığın bilgiler yeterlidir.

## Kendini Test Et

**Soru 1:** Reconnaissance ne demektir?  
**Cevap:** Hedef hakkında bilgi toplama aşamasıdır.

**Soru 2:** Tatil fotoğrafı neden risklidir?  
**Cevap:** Evde olmadığını gösterebilir.

**Soru 3:** Sosyal medyadaki evcil hayvan adı neden önemli olabilir?  
**Cevap:** Şifre tahmini veya güvenlik sorusu cevabı olarak kullanılabilir.

---

# BÖLÜM 8 - Kritik Altyapılar, SCADA ve OT Security

## Bu nedir?

**Critical Infrastructure (Kritik Altyapı)**, toplumun çalışması için hayati öneme sahip sistemlerdir.

Ders içinde geçen örnekler:

- Elektrik dağıtım sistemi
- Doğalgaz sistemi
- Petrol boru hatları
- Finans sektörü
- Taşımacılık
- Savunma sistemleri
- Enerji sektörü
- İletişim altyapısı

## SCADA ve OT nedir?

**SCADA**, endüstriyel sistemleri izlemek ve kontrol etmek için kullanılan yapılardır.

**OT (Operational Technology)** fiziksel makineleri, üretim hatlarını ve endüstriyel sistemleri yöneten teknolojilerdir.

## Günlük hayat analojisi

Bir şehir düşün: Elektrik yoksa hastane çalışmaz. Su sistemi çalışmazsa yaşam durur. Bankalar çalışmazsa ödeme sistemi çöker. İnternet giderse iletişim kopar. Kritik altyapılar toplumun sinir sistemidir.

## Bunu neden öğreniyoruz?

Siber saldırılar artık sadece web sitesi çökertmekle sınırlı değil. Elektrik, üretim, savunma ve enerji sistemleri de hedef olabilir.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| IT Security | Bilgi teknolojileri sistemlerini korur |
| OT Security | Endüstriyel ve fiziksel sistemleri korur |
| SCADA | Endüstriyel sistem izleme/kontrol altyapısıdır |
| IoT | İnternete bağlı günlük cihazları kapsar |

> **HATIRLA:** IT’de veri kaybı olabilir. OT’de fiziksel zarar, üretim durması veya can güvenliği riski olabilir.

## Kendini Test Et

**Soru 1:** Kritik altyapıya üç örnek ver.  
**Cevap:** Elektrik, doğalgaz, finans, iletişim, savunma, enerji.

**Soru 2:** OT Security neyi korur?  
**Cevap:** Endüstriyel makineleri ve fiziksel operasyon sistemlerini.

**Soru 3:** Stuxnet neden OT güvenliğiyle ilişkilidir?  
**Cevap:** Endüstriyel sistemlere zarar veren bir siber saldırı örneğidir.

---

# BÖLÜM 9 - AI, AI Security ve Kuantum Bilgisayarlar

## Bu nedir?

Ders içinde yapay zekanın siber güvenlik rollerini nasıl etkileyeceği tartışılıyor.

Geçen kavramlar:

- AI
- AI Security
- Machine Learning
- ChatGPT
- Gemini
- SOC Level 1
- Quantum Computer
- Qubit
- NIST quantum çalışmaları

## AI siber güvenlikte ne yapabilir?

Yapay zeka özellikle şu işleri destekleyebilir:

- Log analizi
- Alarm sınıflandırma
- Zafiyet raporu yorumlama
- Nessus gibi araç çıktılarının özetlenmesi
- Periyodik tarama raporlarının hazırlanması
- SOC Level 1 görevlerinin bir kısmı

## Ama insan neden hâlâ gerekli?

Karar verme, stratejik değerlendirme, etik sorumluluk ve karmaşık olay müdahalesi hâlâ insan gerektirir. Savunma tarafı AI kullanırsa, saldırgan taraf da AI kullanacaktır.

## AI Security nedir?

AI sistemlerinin güvenliğini sağlayan alandır.

Örnek riskler:

- Model manipülasyonu
- Veri zehirleme
- Prompt injection
- Hassas veri sızması
- AI ajanlarının yanlış karar vermesi
- Otomatik saldırı üretimi

## Quantum Computer nedir?

Kuantum bilgisayarlar klasik bilgisayarlardan farklı olarak **bit** yerine **qubit** kullanır.

- Klasik bilgisayar: Bit = 0 veya 1
- Kuantum bilgisayar: Qubit = 0, 1 veya kuantum durumlarına bağlı olasılıksal durumlar

## Günlük hayat analojisi

Klasik bilgisayar tek tek kapıları açıp bakar. Kuantum bilgisayar bazı problem türlerinde aynı anda birçok ihtimali değerlendirebilecekmiş gibi düşünülebilir.

## Bunu neden öğreniyoruz?

Gelecekte AI Security, Cloud Security, OT Security, Quantum-safe Cryptography ve SOC Automation gibi alanlar daha önemli hale gelecek.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| AI | Genel yapay zeka teknolojisi |
| AI Security | Yapay zeka sistemlerinin güvenliği |
| SOC Automation | Güvenlik operasyonlarının otomatikleştirilmesi |
| Quantum Computer | Kuantum prensipleriyle çalışan bilgisayar |
| Qubit | Kuantum bilgisayardaki bilgi birimi |

> **HATIRLA:** AI bazı işleri azaltabilir ama yeni güvenlik rolleri de doğurur.

## Kendini Test Et

**Soru 1:** AI SOC Level 1 işlerinin hepsini kesin olarak bitirir mi?  
**Cevap:** Hayır. Bazı rutin işleri otomatikleştirebilir ama insan kararına hâlâ ihtiyaç vardır.

**Soru 2:** AI Security neyi korur?  
**Cevap:** Yapay zeka sistemlerini, modellerini, verilerini ve kullanım süreçlerini.

**Soru 3:** Qubit nedir?  
**Cevap:** Kuantum bilgisayarlarda kullanılan bilgi birimidir.

---

# BÖLÜM 10 - Bilgisayar Türleri ve Yeni Nesil Cihazlar

## Bu nedir?

Bilgisayar artık sadece masaüstü veya dizüstü bilgisayar değildir. Günümüzde bilgisayar mantığıyla çalışan birçok cihaz vardır:

- Desktop Computer
- Laptop
- Smart TV
- Game Console
- Digital Camera
- Tablet
- Smartphone
- Sensor
- Smart Refrigerator
- Robot Vacuum
- Wearable Technology
- Smart Watch
- Industrial Control Panel
- IoT cihazları

## Wearable Technology nedir?

**Wearable Technology (Giyilebilir Teknoloji)** vücuda takılan veya giyilen akıllı cihazlardır. Akıllı saat, akıllı bileklik ve sağlık takip cihazları bu gruptadır.

## Endüstriyel bilgisayar örneği

Ders içinde küçük ekranlı, tuşlu, internete bağlanabilen endüstriyel cihazlardan bahsediliyor. Bunlar fabrika makinelerinde, boyama makinelerinde veya üretim sistemlerinde kullanılabilir. Bazıları Linux çekirdeği üzerine kurulmuş işletim sistemleriyle çalışabilir.

## Bunu neden öğreniyoruz?

Her internete bağlı cihaz potansiyel saldırı yüzeyidir. Bir robot süpürge bile ev haritası çıkarabilir, Wi-Fi ağına bağlanabilir, kamera/sensör taşıyabilir, güncelleme alabilir ve açığı varsa saldırı noktası olabilir.

## Günlük hayat analojisi

Evindeki her akıllı cihaz, binaya açılmış küçük bir kapı gibidir. Kapı sayısı arttıkça güvenlik ihtiyacı da artar.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Bilgisayar | Veri işleyen genel cihaz |
| IoT | İnternete bağlı nesne/cihaz |
| Sensor | Veri ölçen parça |
| Wearable | Vücuda takılan akıllı cihaz |
| Industrial Computer | Endüstriyel ortamda çalışan bilgisayar |

> **HATIRLA:** İnternete bağlı her cihaz “küçük bir bilgisayar” gibi düşünülmelidir. Küçük cihaz, küçük risk demek değildir.

## Kendini Test Et

**Soru 1:** Akıllı saat neden bilgisayar sayılabilir?  
**Cevap:** Veri toplar, işler, depolar ve başka cihazlarla iletişim kurar.

**Soru 2:** IoT cihazlarının güvenlik riski nedir?  
**Cevap:** Ağa bağlı oldukları için saldırı yüzeyi oluştururlar.

**Soru 3:** Endüstriyel bilgisayarlar nerede kullanılır?  
**Cevap:** Fabrika, üretim hattı, makine kontrol sistemleri gibi alanlarda.

---

# BÖLÜM 11 - Bilgisayar Nasıl Çalışır?

## Bu nedir?

Bilgisayar temel olarak veri alır, veriyi işler, veriyi depolar ve sonuç üretir.

Temel birimler:

- **Input Unit (Giriş Birimi)**
- **Processing Unit (İşlem Birimi)**
- **Output Unit (Çıkış Birimi)**
- **Storage Unit (Depolama Birimi)**

## Input Unit nedir?

Bilgisayara veri giren cihazlardır: keyboard, mouse, webcam, microphone, scanner, barcode reader.

## Output Unit nedir?

Bilgisayardan dışarı bilgi çıkaran cihazlardır: monitor, printer, plotter, speaker.

## Storage Unit nedir?

Verinin saklandığı yerdir: hard disk, SSD, flash bellek, NAS, cloud storage.

## Günlük hayat analojisi

Bir mutfak düşün:

- Malzemeler: Input
- Aşçı: CPU
- Tezgah: RAM
- Dolap: Storage
- Hazır yemek: Output

## Binary nedir?

**Binary (İkilik Sistem)** bilgisayarların 0 ve 1 ile çalışmasıdır.

- 0 = Kapalı / Yok
- 1 = Açık / Var

Bilgisayardaki metin, ses, video, resim, program ve işletim sistemi en temelde 0 ve 1’lerle temsil edilir.

## Analog ve Digital farkı

| Kavram | Açıklama |
|---|---|
| Analog | Sürekli değişen değerler |
| Digital | 0 ve 1 gibi ayrık değerler |
| Binary | Dijital sistemin 0 ve 1 tabanlı hali |

## Bunu neden öğreniyoruz?

Siber güvenlikte dosya, bellek, ağ paketi, şifreleme, veri kurtarma ve malware analizi gibi konuların temelinde binary mantık vardır.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Input | Bilgisayara veri girer |
| Output | Bilgisayardan veri çıkar |
| Storage | Veri saklanır |
| RAM | Geçici çalışma alanıdır |
| CPU | İşlem yapan birimdir |

> **HATIRLA:** Bilgisayar büyülü bir kutu değildir. Veri alır, işler, saklar ve sonuç üretir.

## Kendini Test Et

**Soru 1:** Klavye input mu output mu?  
**Cevap:** Input.

**Soru 2:** Ekran input mu output mu?  
**Cevap:** Output.

**Soru 3:** Binary sistem hangi rakamları kullanır?  
**Cevap:** 0 ve 1.

---

# BÖLÜM 12 - Depolama: RAM, ROM, Flash, NAS, SAN, Cloud

## Bu nedir?

Depolama, verinin saklanmasıdır. Ders içinde hem bireysel hem kurumsal depolama ele alınıyor.

## RAM nedir?

**RAM (Random Access Memory)** geçici bellektir. Bilgisayar açıkken çalışan programlar burada tutulur. Elektrik kesilirse RAM’deki veri gider.

## ROM nedir?

**ROM (Read Only Memory)** genelde kalıcı temel sistem bilgilerini tutan bellektir.

## Flash Memory nedir?

USB bellek, hafıza kartı gibi taşınabilir depolama türlerinde kullanılır.

## NAS nedir?

**NAS (Network Attached Storage)** ağa bağlı ortak depolama cihazıdır. Küçük ve orta ölçekli işletmeler için uygundur. Ethernet üzerinden bağlanır. Synology, Asus, Zyxel gibi markalar örnek verilmiştir.

## SAN nedir?

**SAN (Storage Area Network)** daha büyük ölçekli ve yüksek performanslı depolama altyapısıdır. Büyük veri transferi gereken yerlerde tercih edilir. Fiber bağlantılar ve veri merkezi yapılarıyla ilişkilidir.

## Cloud Storage nedir?

İnternet üzerinden kullanılan bulut depolama hizmetidir. Google Drive, OneDrive, Dropbox ve kurumsal bulut depolama servisleri bu mantıkla çalışır.

## Backup neden önemli?

Ders içinde ransomware örneği veriliyor. Eğer NAS içindeki dosyalar şifrelenirse, önceden alınmış temiz backup sayesinde geri dönüş yapılabilir.

## Günlük hayat analojisi

- RAM = Masanın üstü
- Hard Disk/SSD = Dosya dolabı
- NAS = Ofisin ortak dosya dolabı
- SAN = Büyük şirket arşiv merkezi
- Cloud = Şehir dışındaki profesyonel depo
- Backup = Yedek anahtar / fotokopi

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| RAM | Geçici bellek |
| Disk | Kalıcı depolama |
| NAS | Ağa bağlı ortak depolama |
| SAN | Büyük ölçekli yüksek performanslı depolama |
| Cloud | İnternet üzerinden depolama |
| Backup | Verinin yedeği |

> **HATIRLA:** Backup yoksa ransomware sonrası pazarlık masasına oturursun. Backup varsa geri dönüş şansın vardır.

## Kendini Test Et

**Soru 1:** RAM kalıcı mıdır?  
**Cevap:** Hayır, geçicidir.

**Soru 2:** NAS en çok hangi tür işletmelerde kullanılır?  
**Cevap:** Küçük ve orta ölçekli işletmelerde.

**Soru 3:** Ransomware’e karşı backup neden önemlidir?  
**Cevap:** Şifrelenen veriler yerine temiz yedekten geri dönülebilir.

---

# BÖLÜM 13 - File System: FAT16, FAT32, NTFS, exFAT

## Bu nedir?

**File System (Dosya Sistemi)** dosyaların diskte nasıl saklanacağını, bulunacağını ve yönetileceğini belirleyen yapıdır.

Bir dosya sistemi şunları tutar:

- Dosya adı
- Dosya boyutu
- Dosya türü
- Oluşturulma tarihi
- Konumu
- Dosya yolu
- Hiyerarşik yapısı

## FAT16 nedir?

Eski bir dosya sistemidir. 16 bitlik adresleme mantığına dayanır. Günümüz ihtiyaçları için yetersiz kalmıştır.

## FAT32 nedir?

FAT16’dan sonra gelen dosya sistemidir. Ancak önemli bir sınırı vardır: tek dosya boyutu yaklaşık 4 GB ile sınırlıdır. Bu yüzden FAT32 formatlı USB belleğe 4 GB’tan büyük Windows ISO dosyası atmaya çalışırsan hata alabilirsin.

## NTFS nedir?

Windows tarafında daha modern ve güçlü dosya sistemidir. 4 GB sınırı problemini ortadan kaldırır.

## exFAT nedir?

Flash bellekler ve harici diskler için daha esnek kullanılan dosya sistemi türüdür. Büyük dosyalarla çalışmak için FAT32’ye göre daha uygundur.

## Linux dosya sistemleri

Ders içinde Linux tarafında EXT3, EXT4 ve XFS dosya sistemleri geçiyor.

## macOS tarafı

Transkriptte “High Sierra” ifadesi geçiyor; burada muhtemelen macOS High Sierra ile gelen APFS tarzı modern dosya sistemi yaklaşımına işaret ediliyor.

## Günlük hayat analojisi

Dosya sistemi bir kütüphane katalog sistemidir. Kitaplar raflarda durur ama hangi kitabın hangi rafta olduğunu katalog sistemi bilir. Dosya sistemi yoksa bilgisayar dosyanın nerede olduğunu bulamaz.

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| Disk | Fiziksel depolama alanı |
| File System | Diskteki dosyaların düzenleme sistemi |
| Format | Diski belirli dosya sistemine göre hazırlama |
| FAT32 | Eski ve 4 GB sınırı olan sistem |
| NTFS | Windows için daha gelişmiş sistem |
| exFAT | Taşınabilir disklerde büyük dosyalar için kullanışlı |

> **HATIRLA:** USB belleğe büyük ISO dosyası atamıyorsan ilk bakacağın yer dosya sistemidir. FAT32 ise 4 GB sınırına takılmış olabilirsin.

## Kendini Test Et

**Soru 1:** FAT32’nin önemli sınırı nedir?  
**Cevap:** Tek dosya için yaklaşık 4 GB sınırı vardır.

**Soru 2:** NTFS hangi işletim sistemi ailesinde yaygındır?  
**Cevap:** Windows.

**Soru 3:** File System ne işe yarar?  
**Cevap:** Dosyaların diskte nasıl saklanacağını ve bulunacağını belirler.

---

# BÖLÜM 14 - Anakart, CPU, RAM, GPU ve Temel Donanım

## Bu nedir?

Bilgisayarın fiziksel bileşenleri bir araya gelerek sistemi oluşturur. Ders içinde özellikle **Motherboard (Anakart)** merkez yapı olarak anlatılıyor.

## Motherboard nedir?

Anakart, bilgisayardaki bileşenlerin birbirine bağlandığı ana devre kartıdır. CPU, RAM, GPU, disk, power supply kabloları, klavye, mouse, ekran, hoparlör ve ağ kartı anakarta doğrudan veya dolaylı bağlanır.

## CPU nedir?

**CPU (Central Processing Unit)** bilgisayarın işlemcisidir. Komutları işler.

## RAM nedir?

CPU’nun hızlı çalışmak için kullandığı geçici çalışma alanıdır.

## GPU nedir?

**GPU (Graphics Processing Unit)** grafik işlemlerinden sorumludur. Günümüzde yapay zeka ve paralel işlem için de kullanılır.

## Power Supply nedir?

Bilgisayara elektrik sağlayan güç kaynağıdır.

## Buzzer nedir?

Anakart üzerindeki küçük sesli uyarı birimidir. Sistem açılırken hata veya durum sesi verebilir.

## İşletim sistemi nerede durur?

İşletim sistemi hard disk veya SSD üzerine kurulur. Bilgisayar açıldığında sistem buradan yüklenir.

## Günlük hayat analojisi

Bilgisayar bir şehir gibi düşünülürse:

- Anakart = Şehrin yolları ve altyapısı
- CPU = Belediye yönetim merkezi
- RAM = Geçici çalışma masası
- Disk = Arşiv binası
- GPU = Görsel tasarım merkezi
- Power Supply = Elektrik santrali

## KARIŞTIRMA!

| Kavram | Fark |
|---|---|
| CPU | Genel işlem yapar |
| GPU | Grafik ve paralel işlemde güçlüdür |
| RAM | Geçici çalışma alanıdır |
| Disk | Kalıcı depolamadır |
| Anakart | Bileşenleri birbirine bağlar |
| Power Supply | Elektrik sağlar |

> **HATIRLA:** Bilgisayar kasası olmadan da anakart, CPU, RAM ve güç ile sistem çalışabilir. Ama görüntü, giriş ve depolama için ek bileşenlere ihtiyaç vardır.

## Kendini Test Et

**Soru 1:** Anakartın görevi nedir?  
**Cevap:** Bilgisayar bileşenlerini birbirine bağlamak.

**Soru 2:** İşletim sistemi genelde nereye kurulur?  
**Cevap:** Hard disk veya SSD üzerine.

**Soru 3:** Power Supply ne işe yarar?  
**Cevap:** Bilgisayara gerekli elektriği sağlar.

---

# BÖLÜM 15 - Siber Güvenlik ve Bilgi Güvenliği Farkı

## Bu nedir?

Ders içinde **Cyber Security (Siber Güvenlik)** ve **Information Security (Bilgi Güvenliği)** ayrımı yapılıyor.

## Cyber Security

Siber uzaydaki sistemleri, ağları, bilgisayarları ve dijital bilgiyi korur.

## Information Security

Bilginin bulunduğu her ortamı korur: dijital dosya, fiziksel evrak, arşiv, klasör, sunucu ve bulut ortamı.

## Günlük hayat analojisi

Bir şirketin müşteri sözleşmesini düşün:

- Kağıt olarak dolaptaysa: Information Security
- PDF olarak sunucudaysa: Information Security + Cyber Security
- İnternetten erişiliyorsa: Cyber Security daha kritik hale gelir

## Bunu neden öğreniyoruz?

Her bilgi güvenliği problemi siber problem olmayabilir. Ama dijital ortamda bulunan her hassas bilgi siber güvenlik kapsamına girer.

## KARIŞTIRMA!

| Kavram | Kapsam |
|---|---|
| Information Security | Fiziksel + dijital bilgi |
| Cyber Security | Dijital sistemler ve siber uzay |
| IT Security | Bilgi teknolojileri altyapısı |
| Data Security | Verinin korunması |

> **HATIRLA:** Siber güvenlik, bilgi güvenliğinin dijital savaş alanındaki kısmıdır.

## Kendini Test Et

**Soru 1:** Kağıt arşiv güvenliği hangi alanla ilgilidir?  
**Cevap:** Information Security.

**Soru 2:** Sunucudaki müşteri verilerinin korunması hangi alanla ilgilidir?  
**Cevap:** Cyber Security ve Information Security.

**Soru 3:** Siber güvenlik sadece veriyle mi ilgilenir?  
**Cevap:** Hayır, sistemleri, ağları, kullanıcıları ve erişilebilirliği de korur.

---

# GENEL TEKRAR VE ÖZET

## Tek cümlelik büyük özet

Bu ders; siber güvenliğin temel amacını, CIA üçlüsünü, standartların önemini, gerçek siber saldırı örneklerini, savunma mekanizmalarını, sosyal medya risklerini, AI/kuantum etkisini ve bilgisayarın donanım-depolama-dosya sistemi temelini anlatıyor.

## Tüm konuların kısa özeti

| Konu | Tek cümlelik özet |
|---|---|
| Quiz / TryHackMe | Öğrenmeyi kalıcı hale getiren uygulama sistemidir. |
| Cyberspace | İletişim kuran dijital cihazların oluşturduğu alandır. |
| Cyber Security | Bu alanı, veriyi ve sistemleri saldırılardan koruma disiplinidir. |
| NIST / ISO / IEEE | Teknolojide ortak kurallar ve standartlar sağlar. |
| CIA Triad | Gizlilik, bütünlük ve erişilebilirlik güvenliğin temelidir. |
| Authentication | Kişinin kim olduğunu doğrular. |
| Non-repudiation | Yapılan işlemin inkar edilmesini önler. |
| Firewall | Ağ geçişlerini kontrol eder. |
| EDR | Bilgisayar ve sunucu üzerindeki tehditleri izler. |
| SIEM | Logları toplar ve güvenlik olaylarını analiz eder. |
| SOC | Güvenlik olaylarını izleyen operasyon merkezidir. |
| Reconnaissance | Saldırganın hedef hakkında bilgi toplamasıdır. |
| Critical Infrastructure | Toplumun çalışması için gerekli hayati sistemlerdir. |
| AI Security | Yapay zeka sistemlerini koruyan güvenlik alanıdır. |
| Quantum Computer | Qubit kullanan yeni nesil bilgisayar yaklaşımıdır. |
| Input / Output | Bilgisayara veri girer ve sonuç dışarı çıkar. |
| Binary | Bilgisayarların 0 ve 1 ile çalışma mantığıdır. |
| RAM | Geçici çalışma belleğidir. |
| ROM | Kalıcı temel bellektir. |
| NAS | Ağa bağlı ortak depolamadır. |
| SAN | Büyük ölçekli depolama ağıdır. |
| Cloud Storage | İnternet üzerinden depolamadır. |
| File System | Dosyaların diskte nasıl tutulacağını belirler. |
| FAT32 | 4 GB dosya sınırı olan eski dosya sistemidir. |
| NTFS | Windows’ta kullanılan gelişmiş dosya sistemidir. |
| Motherboard | Bilgisayar bileşenlerini birbirine bağlayan ana karttır. |

## En kritik 10 bilgi

1. Siber güvenliğin temeli **CIA üçlüsüdür**.
2. Her dijital cihaz saldırı yüzeyi olabilir.
3. Standartlar olmadan cihazlar ve yazılımlar uyumlu çalışamaz.
4. Veri sızıntısı sadece teknik değil, ekonomik ve sosyal sonuçlar doğurur.
5. Sosyal medya saldırgan için keşif kaynağıdır.
6. Firewall tek başına güvenlik değildir.
7. SIEM ve log analizi olmadan saldırıyı fark etmeyebilirsin.
8. Backup yoksa ransomware felakete dönüşür.
9. AI bazı işleri otomatikleştirir ama insan faktörünü tamamen bitirmez.
10. Bilgisayarın temelini anlamadan siber güvenlikte derinleşmek zordur.
