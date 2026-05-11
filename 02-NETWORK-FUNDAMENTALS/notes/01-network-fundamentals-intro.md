# Network Fundamentals-1 

<div align="center">

![Ders İnfografiği](../assets/01-it-to-network-security-overview.png)

</div>

---


## 1. Konu Haritası

### Ana başlıklar

1. IT Fundamentals'tan Network Fundamentals'a geçiş
2. Kütüphane dosyaları
   - Library
   - .lib, .obj, .dll, .exe
   - Static Library
   - Dynamic Link Library (DLL)
   - DLL Manipülasyonu / DLL Hijacking
3. Hash, imza ve davranış analizi
   - Kriptografik özet
   - Nessus
   - EDR / Sophos
   - Anomali tespiti
4. Programlama dilleri
   - Machine Language
   - Assembly
   - High Level Languages
   - Python, Java, C, C++, C#, JavaScript, PHP, Go, Rust vb.
5. Cloud Computing
   - On-premise
   - Public / Private / Community / Hybrid Cloud
   - IaaS / PaaS / SaaS
   - Pizza as a Service analojisi
6. Network Fundamentals başlangıcı
   - Network nedir?
   - Internet nedir?
   - ARPANET / MILNET
   - Protocol kavramı
7. IP ve IP Routing
   - IP
   - IP Address
   - Source / Destination
   - Paketleme
8. Router, ISP, LAN, Hosting, Cloud Provider
9. OSI ve TCP/IP modelleri
   - OSI 7 katman
   - TCP/IP 4 katman
   - Encapsulation / Decapsulation
   - DNS, HTTP, SMTP, POP3, FTP, Telnet
   - TCP / UDP
   - MAC Address
   - SSL / TLS / HTTPS

## 2. Bölüm: Kütüphane Dosyaları

### Bu nedir?

Kütüphane dosyası (Library File), bir programın tekrar tekrar ihtiyaç duyduğu hazır kod parçalarının saklandığı dosyadır.

Yani programcı her defasında aynı kodu sıfırdan yazmaz. Bir kere yazar, sonra ihtiyaç olduğunda çağırır.

### Günlük hayat analojisi

Bir mutfakta sürekli aynı sosu yapıyorsun diyelim. Her yemek için sosu baştan hazırlamak yerine sosu kavanoza koyarsın. Ne zaman gerekirse kavanozu açıp kullanırsın.

Kütüphane dosyası da yazılım dünyasında bu kavanozdur.

### Metinde geçen dosya türleri

| Dosya | Anlamı | Basit açıklama |
|---|---|---|
| .lib | Library | Hazır kod kütüphanesi |
| .obj | Object File | Derleme sırasında oluşan ara dosya |
| .dll | Dynamic Link Library | Program çalışırken çağrılan dinamik kütüphane |
| .exe | Executable | Doğrudan çalıştırılabilir dosya |

### Siber güvenlik açısından neden önemli?

Çünkü saldırganlar bu dosyaları değiştirebilir.

Örneğin bir program normalde güvenli bir abc.dll dosyasını çağıracakken, saldırgan aynı isimde zararlı bir DLL yerleştirirse program fark etmeden saldırganın kodunu çalıştırabilir.

Buna DLL Hijacking denir.

### KARMAŞTIRMA!

| Kavram | Ne değildir? | Doğru anlamı |
|---|---|---|
| .exe | Sadece uygulama ikonu değildir | Çalıştırılabilir program dosyasıdır |
| .dll | Tek başına her zaman çalışmaz | Genelde başka program tarafından çağrılır |
| .lib | Virüs demek değildir | Kod kütüphanesidir |
| DLL Hijacking | Sadece dosya silmek değildir | Programın çağırdığı DLL'i zararlı DLL ile değiştirmektir |

### HATIRLA

Her dosya uzantısı tek başına güvenli veya güvensiz değildir. Kritik olan şey: dosyanın içindeki kod ve davranıştır.

### Bunu neden öğreniyoruz?

Çünkü siber güvenlikte saldırılar sadece virüs dosyası şeklinde gelmez. Bazen saldırı, güvenilir bir uygulamanın çağırdığı küçük bir kütüphane dosyasının değiştirilmesiyle yapılır.

### Kendini test et

1. DLL ne işe yarar?  
Cevap: Program çalışırken ihtiyaç duyduğu hazır fonksiyonları sağlar.

2. DLL Hijacking nedir?  
Cevap: Bir programın çağıracağı gerçek DLL yerine saldırganın zararlı DLL'inin çalıştırılmasıdır.

3. .exe her zaman zararlı mıdır?  
Cevap: Hayır. .exe sadece çalıştırılabilir dosya demektir.

## 3. Bölüm: Hash, İmza ve Davranış Analizi

### Bu nedir?

Hash, bir dosyanın dijital parmak izidir. Bir dosyada küçücük bir değişiklik bile yapılsa hash değeri büyük ölçüde değişir.

### Günlük hayat analojisi

Bir insanın parmak izi gibi düşün. Kişi aynı görünse bile parmak izi değişmez. Dosyanın hash'i de dosyanın kimliği gibidir.

### Güvenlik araçları bunu nasıl kullanır?

Antivirüs, EDR veya zafiyet tarayıcıları bir dosyanın orijinal hash değeriyle sistemdeki hash değerini karşılaştırabilir.

Eğer farklıysa:

- Dosya değiştirilmiş olabilir.
- Güncelleme bozulmuş olabilir.
- Zararlı kod eklenmiş olabilir.

Metinde Nessus, ManageEngine, Sophos, EDR, vulnerability scanner ve hijack scanner gibi araçlardan bahsediliyor.

### Davranış analizi nedir?

Bir dosya sadece adına göre değil, yaptığı davranışa göre incelenir.

Örneğin:

- Normalde PDF açılması gerekir.
- Ama PDF açıldığında arka planda PowerShell çalışıyorsa bu anormaldir.
- Sophos gibi EDR araçları bunu şüpheli davranış olarak algılayabilir.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| Hash kontrolü | Dosyanın değişip değişmediğini anlamaya çalışır |
| İmza analizi | Bilinen zararlı kalıpları arar |
| Davranış analizi | Dosyanın sistemde ne yaptığını izler |
| EDR | Endpoint cihazlarda gelişmiş tehdit izleme yapar |

### HATIRLA

Güvenlik sadece dosya adına bakmaz. Dosyanın hash'ine, imzasına ve davranışına bakar.

### Bunu neden öğreniyoruz?

Çünkü modern saldırılar gizlenmeye çalışır. Zararlı yazılım bazen kendini görev yöneticisi açıldığında durdurur, bazen normal dosya gibi görünür, bazen PowerShell üzerinden çalışır.

### Kendini test et

1. Hash ne işe yarar?  
Cevap: Dosyanın değişip değişmediğini anlamaya yarar.

2. PDF açılınca PowerShell çalışması normal midir?  
Cevap: Hayır, bu anormal ve şüpheli bir davranıştır.

3. EDR neyi izler?  
Cevap: Endpoint cihazlardaki dosya, süreç ve davranışları izler.

## 4. Bölüm: Programlama Dilleri

### Bu nedir?

Programlama dili, bilgisayara ne yapacağını söylemek için kullanılan komut sistemidir.

Bilgisayar aslında yalnızca 1 ve 0 anlar. İnsanlar doğrudan 1 ve 0 ile çalışamadığı için programlama dilleri geliştirilmiştir.

### Katman mantığı

| Seviye | Açıklama |
|---|---|
| Machine Language | 1 ve 0'lardan oluşur |
| Assembly Language | Makine diline çok yakındır |
| High Level Language | İnsanların daha kolay yazdığı dillerdir |

### Günlük hayat analojisi

Bilgisayar sadece çok ilkel bir dil bilen biri gibi düşün. Sen ona doğrudan konuşamazsın. Programlama dili tercüman gibi çalışır.

### Metinde geçen diller

Python, Java, JavaScript, C, C++, C#, Pascal, Fortran, PHP, Perl, Go, Rust, Kotlin, Swift, Ruby, TypeScript, Scala, Haskell, Prolog, Datalog.

### Siber güvenlik açısından neden önemli?

Çünkü saldırı araçları, malware'ler, exploit'ler ve otomasyon scriptleri bu dillerle yazılır.

Metinde özellikle şu vurgu var:

- Çok küçük ve hedefli zararlılar için Assembly kullanılabilir.
- Python ile de zararlı kod yazılabilir.
- C/C++ gibi diller güçlüdür ama güvenlik açığı içerebilir.
- Şu dilde yazarsan hacklenmez iddiası doğru değildir.

### KARMAŞTIRMA!

| Yanlış düşünce | Doğrusu |
|---|---|
| C++ ile yazılırsa hacklenmez | Yanlış. Güvenlik dili değil, kodun kalitesi ve yapılandırma önemlidir |
| Python güvenli değildir | Yanlış. Dil değil, kullanılan kod ve kütüphaneler önemlidir |
| Assembly sadece eski bir dildir | Yanlış. Düşük seviye saldırılarda hâlâ önemlidir |
| Java ve JavaScript aynıdır | Yanlış. İsimleri benzer ama farklı teknolojilerdir |

### Java vs JavaScript

| Java | JavaScript |
|---|---|
| Genel amaçlı programlama dili | Web tarafında çok yaygın betik dilidir |
| Backend, masaüstü, Android gibi alanlarda kullanılır | Web arayüzü ve dinamik sayfa davranışlarında kullanılır |
| Daha kurumsal sistemlerde yaygındır | Tarayıcı tarafında çok yaygındır |

### HATIRLA

Güvenlik hangi dil sorusundan çok, kod nasıl yazıldı, nasıl güncellendi, nasıl korundu sorusudur.

### Bunu neden öğreniyoruz?

Çünkü siber güvenlikte saldırganın kullandığı aracı anlamak için kod mantığını bilmek gerekir. Ayrıca savunma tarafında log analizi, otomasyon, script yazımı ve zafiyet analizi için programlama bilgisi kritik hale gelir.

### Kendini test et

1. Bilgisayar en temelde hangi dili anlar?  
Cevap: 1 ve 0'lardan oluşan makine dilini.

2. Java ve JavaScript aynı mıdır?  
Cevap: Hayır, farklı dillerdir.

3. Bir programlama dili tamamen güvenli midir?  
Cevap: Hayır. Her dilde hatalı kod veya zafiyet olabilir.

## 5. Bölüm: Cloud Computing

### Bu nedir?

Cloud Computing (Bulut Bilişim), sunucu, depolama, uygulama ve altyapı hizmetlerini kendi şirketinde kurmak yerine internet üzerinden hizmet olarak kullanmaktır.

### On-premise nedir?

On-premise, sistemlerin şirketin kendi fiziksel ortamında kurulmasıdır.

Örneğin:

- Şirket içinde server odası
- Kendi firewall cihazı
- Kendi yedekleme sistemi
- Kendi bakım personeli

### Cloud nedir?

Cloud'da bu altyapının önemli kısmı AWS, Azure, Google Cloud gibi sağlayıcılardan hizmet olarak alınır.

Metinde özellikle AWS, Microsoft Azure, Google Cloud Platform, Office 365, Google Docs, Salesforce, Cloudflare gibi örnekler geçiyor.

### Günlük hayat analojisi

Evde yemek yapmak ile restorana gitmek arasındaki fark gibi.

Evde yaparsan malzemeyi alırsın, fırını kullanırsın, masayı hazırlarsın ve bulaşığı yıkarsın. Restoranda ise sadece sipariş verirsin ve hizmeti kullanırsın.

### IaaS / PaaS / SaaS

| Model | Açılım | Sen ne yönetirsin? | Örnek |
|---|---|---|---|
| IaaS | Infrastructure as a Service | OS, uygulama, veri | Azure VM, AWS EC2 |
| PaaS | Platform as a Service | Uygulama ve veri | Google App Engine |
| SaaS | Software as a Service | Sadece kullanırsın | Office 365, Gmail |

### Pizza analojisi

| Model | Pizza örneği |
|---|---|
| On-premise | Her şeyi evde kendin yaparsın |
| IaaS | Hazır pizza alır, evde pişirirsin |
| PaaS | Sipariş verirsin, eve gelir, masayı sen hazırlarsın |
| SaaS | Restorana gidersin, her şey hazırdır |

### Cloud Deployment Modelleri

| Model | Açıklama |
|---|---|
| Private Cloud | Sadece bir kuruma özel |
| Public Cloud | Genel kullanıma açık bulut altyapısı |
| Community Cloud | Benzer amaçlı kurumların ortak bulutu |
| Hybrid Cloud | Public + Private birlikte kullanılır |

### Siber güvenlik açısından neden önemli?

Cloud daha güvenli olabilir ama otomatik olarak güvenli değildir. En büyük risklerden biri Misconfiguration (Hatalı Yapılandırma)'dır.

### KARMAŞTIRMA!

| Kavram | Yanlış anlama | Doğru anlam |
|---|---|---|
| Cloud | Fiziksel olmayan sihirli ortam | Arkada fiziksel veri merkezleri vardır |
| SaaS | Yazılım satın almak | Yazılımı hizmet olarak kullanmaktır |
| IaaS | Her şey hazır | Altyapı hazırdır, üstünü sen yönetirsin |
| PaaS | Sadece hosting | Uygulama geliştirme ve çalıştırma platformudur |

### HATIRLA

Cloud maliyeti düşürebilir ama yanlış seçilirse pahalıya da patlayabilir. Güvenlik avantajı sağlar ama yanlış yapılandırma felaket doğurur.

### Bunu neden öğreniyoruz?

Çünkü modern şirket sistemleri artık sadece lokal serverlardan oluşmuyor. Cloud, hybrid yapı, SaaS uygulamaları ve public servisler saldırı yüzeyinin parçasıdır.

### Kendini test et

1. On-premise ne demektir?  
Cevap: Sistemlerin şirketin kendi fiziksel ortamında kurulmasıdır.

2. Office 365 hangi modele örnektir?  
Cevap: SaaS.

3. Cloud'daki en büyük güvenlik risklerinden biri nedir?  
Cevap: Misconfiguration yani hatalı yapılandırma.

## 6. Bölüm: Network Nedir?

### Bu nedir?

Network (Ağ), birbirleriyle iletişim kurabilen cihazların oluşturduğu yapıdır.

Bu cihazlar bilgisayar, telefon, sunucu, yazıcı, akıllı TV, router ve IoT cihazları olabilir.

### Günlük hayat analojisi

Bir mahalledeki evleri yollar bağlar. İnsanlar bu yollar üzerinden birbirine gider. Network de cihazların birbirine ulaşmasını sağlayan dijital yol sistemidir.

### Network sadece internet değildir

Evindeki telefon, laptop ve yazıcı aynı Wi-Fi'a bağlıysa bu da network'tür. İnternet ise en büyük network'tür.

### Internet nedir?

Internet, ağların ağıdır. Metinde Network of Networks olarak geçiyor.

### ARPANET / MILNET

Metinde internetin tarihsel gelişiminde 1960'lar, ARPANET, MILNET, akademik ve askeri ağlar, 1983 civarı askeri ve sivil ağ ayrımı gibi konular geçiyor.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| Network | Cihazların iletişim kurduğu ağ |
| Internet | Birçok ağın birleşiminden oluşan küresel ağ |
| LAN | Yerel ağ |
| ISP | İnternet servis sağlayıcı |

### HATIRLA

Her internet bir network'tür ama her network internet değildir.

### Bunu neden öğreniyoruz?

Çünkü siber saldırılar ağ üzerinden ilerler. Hangi cihazın kiminle konuştuğunu anlamadan saldırıyı da savunmayı da anlayamazsın.

### Kendini test et

1. Evdeki Wi-Fi ağı network müdür?  
Cevap: Evet.

2. Internet ne demektir?  
Cevap: Ağların ağıdır.

3. LAN nedir?  
Cevap: Yerel ağdır.

## 7. Bölüm: Protocol Nedir?

### Bu nedir?

Protocol (Protokol), iki cihazın nasıl iletişim kuracağını belirleyen kurallar bütünüdür.

### Günlük hayat analojisi

Devlet başkanı başka ülkeye gittiğinde her şey önceden belirlenir: kim karşılayacak, nerede oturulacak, kim konuşacak, fotoğraf nerede çekilecek. Bilgisayarda da aynı mantık vardır.

### Neden protokol gerekir?

Çünkü cihazların ortak dil konuşması gerekir. Sen cve.org yazarsın ama bilgisayar karakterlerden değil, sayısal adreslerden anlar. Bu yüzden DNS, IP, HTTP gibi protokoller devreye girer.

### Metinde geçen protokoller

IP, TCP, UDP, HTTP, HTTPS, DNS, SMTP, POP3, IMAP, FTP, Telnet, SSL/TLS, ARP, ICMP, SNMP.

### KARMAŞTIRMA!

| Kavram | Görevi |
|---|---|
| HTTP | Web sayfası iletişimi |
| DNS | Alan adını IP adresine çevirir |
| SMTP | Mail gönderir |
| POP3 / IMAP | Mail alır |
| FTP | Dosya transferi |
| TCP | Güvenilir taşıma |
| UDP | Hızlı taşıma |

### HATIRLA

Protokol yoksa iletişim kaosa döner.

### Bunu neden öğreniyoruz?

Çünkü saldırılar çoğu zaman protokol mantığındaki zayıflıkları kullanır. HTTP header, TCP port, DNS sorgusu, IP routing gibi kavramları bilmeden ağ güvenliği öğrenilemez.

### Kendini test et

1. DNS ne yapar?  
Cevap: Alan adını IP adresine çevirir.

2. SMTP ne için kullanılır?  
Cevap: E-posta göndermek için.

3. Protokol neden gereklidir?  
Cevap: Cihazların ortak kurallarla haberleşmesini sağlar.

## 8. Bölüm: IP ve IP Address

### Bu nedir?

IP (Internet Protocol), verinin ağ üzerinde nasıl taşınacağını belirleyen protokoldür. IP Address (IP Adresi) ise cihazın ağdaki adresidir.

### Günlük hayat analojisi

Bir kargo gönderirken alıcı adresi ve gönderen adresi yazılır. IP paketinde de Source IP ve Destination IP bulunur.

### Source ve Destination

| Kavram | Anlamı |
|---|---|
| Source | Paketin çıktığı kaynak |
| Destination | Paketin gideceği hedef |

### Paket mantığı

Büyük veri tek parça gönderilmez. Parçalara bölünür. Paketler farklı yollarla gidebilir. Karşı tarafta tekrar birleştirilir.

### HATIRLA

İnternette veri tek büyük blok olarak değil, küçük paketler halinde taşınır.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| IP | Protokolün adı |
| IP Address | Cihazın ağdaki adresi |
| IP Routing | Paketin hangi yoldan gideceğinin belirlenmesi |
| IP Header | IP paketinin adres ve kontrol bilgilerini taşıyan başlığı |

### Bunu neden öğreniyoruz?

Çünkü firewall, router, IDS/IPS, SIEM, EDR logları IP bilgisi olmadan okunamaz.

### Kendini test et

1. IP adresi neye benzer?  
Cevap: Ev adresine.

2. Source IP nedir?  
Cevap: Paketin çıktığı cihazın IP adresidir.

3. Destination IP nedir?  
Cevap: Paketin gideceği cihazın IP adresidir.

## 9. Bölüm: Router, ISP, LAN ve Hosting

### Router nedir?

Router (Yönlendirici), farklı ağları birbirine bağlayan cihazdır. Ev ağı ile interneti konuşturur.

### Modem ile router aynı şey mi?

Hayır.

| Cihaz | Görev |
|---|---|
| Modem | Sinyal dönüştürür |
| Router | Ağlar arasında yönlendirme yapar |

Evde kullandığın cihaz çoğu zaman modem + router birleşimidir.

### ISP nedir?

ISP (Internet Service Provider), internet servis sağlayıcıdır. Örnekler: Türk Telekom, Turkcell, Vodafone, Türksat.

### LAN nedir?

LAN (Local Area Network), yerel ağdır. Şirket içindeki bilgisayarlar, yazıcılar ve sunucular aynı LAN içinde olabilir.

### Hosting nedir?

Web sitesinin dosyalarının tutulduğu sunucu hizmetidir. Bir web sitesinin domain adı, web dosyaları, sunucusu ve hosting hizmeti vardır.

### Cloudflare örneği

Metinde Cloudflare'dan bahsediliyor. Cloudflare hem CDN/platform hem de WAF yani Web Application Firewall hizmeti sunabilir.

### Bunu neden öğreniyoruz?

Çünkü siber güvenlikte saldırı yolu genellikle şöyledir:

Kullanıcı -> Router -> ISP -> Internet -> Hosting/Cloud -> Server

Bu zincirdeki her nokta saldırı veya savunma noktasıdır.

### Kendini test et

1. Router ne yapar?  
Cevap: Farklı ağları birbirine yönlendirir.

2. ISP nedir?  
Cevap: İnternet servis sağlayıcıdır.

3. LAN ne demektir?  
Cevap: Yerel ağdır.

## 10. Bölüm: OSI Modeli

### Bu nedir?

OSI Model (Open Systems Interconnection), ağ iletişimini 7 katmana ayıran referans modelidir.

Metinde OSI modelinin ISO tarafından standartlaştırıldığı ve network üreticileri, güvenlik uzmanları, saldırganlar ve öğrenciler için temel referans olduğu vurgulanıyor.

### OSI 7 Katman

| Katman | İngilizce | Türkçe |
|---|---|---|
| 7 | Application | Uygulama |
| 6 | Presentation | Sunum |
| 5 | Session | Oturum |
| 4 | Transport | Taşıma |
| 3 | Network | Ağ |
| 2 | Data Link | Veri Bağlantı |
| 1 | Physical | Fiziksel |

### Günlük hayat analojisi: kargo

Bir hediye göndereceksin: hediyeyi hazırlarsın, paketlersin, kutuya koyarsın, adres yazarsın, kargo firmasına verirsin, araçla taşınır ve karşı taraf açar.

OSI modeli de verinin bu şekilde katman katman hazırlanmasını ve açılmasını anlatır.

### Encapsulation / Decapsulation

Encapsulation, veri gönderilirken her katmanda üzerine yeni bilgi eklenmesidir. Decapsulation, karşı tarafta bu bilgilerin katman katman açılmasıdır.

### HATIRLA

Gönderirken veri 7'den 1'e iner. Alıcı tarafta 1'den 7'ye çıkar.

### OSI katmanları ve siber güvenlik

| Katman | Güvenlik açısından örnek |
|---|---|
| Application | HTTP saldırıları, web açıkları |
| Presentation | Şifreleme, encoding sorunları |
| Session | Oturum kaçırma |
| Transport | TCP/UDP portları |
| Network | IP routing, ICMP, firewall kuralları |
| Data Link | MAC adresi, ARP saldırıları |
| Physical | Kablo, fiziksel erişim, donanım |

### Kendini test et

1. OSI kaç katmandır?  
Cevap: 7 katmandır.

2. Encapsulation nedir?  
Cevap: Veriye katman katman başlık bilgisi eklenmesidir.

3. Network katmanında hangi adresleme öne çıkar?  
Cevap: IP adresleme.

## 11. Bölüm: TCP/IP Modeli

### Bu nedir?

TCP/IP Model, pratikte internet iletişiminde kullanılan 4 katmanlı modeldir.

### OSI vs TCP/IP

| OSI | TCP/IP |
|---|---|
| Application + Presentation + Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link + Physical | Network Access / Data Link |

### Neden iki model var?

OSI eğitim için çok açıklayıcıdır. TCP/IP ise pratikte daha çok kullanılan modeldir.

### KARMAŞTIRMA!

| OSI | TCP/IP |
|---|---|
| Teorik ve öğretici model | Pratik internet modeli |
| 7 katman | 4 katman |
| Detaylı ayrım yapar | Bazı katmanları birleştirir |

### HATIRLA

OSI öğrenmeden TCP/IP'nin mantığı tam oturmaz. TCP/IP bilmeden gerçek ağ trafiği analiz edilemez.

### Kendini test et

1. TCP/IP kaç katmandır?  
Cevap: 4 katmandır.

2. OSI'deki Application, Presentation, Session TCP/IP'de hangi katmana denk gelir?  
Cevap: Application katmanı.

3. TCP/IP'de Network katmanı hangi isimle geçebilir?  
Cevap: Internet katmanı.

## 12. Bölüm: TCP ve UDP

### TCP nedir?

TCP (Transmission Control Protocol), güvenilir veri taşıma protokolüdür. Veri paketlerini takip eder. Eksik paket varsa tekrar ister.

### UDP nedir?

UDP (User Datagram Protocol), hızlı ama güvenilirlik kontrolü zayıf taşıma protokolüdür. Paket eksik giderse çoğu zaman tekrar istemez.

### Günlük hayat analojisi

TCP, kargo tesliminde imza alan kargo firması gibidir. UDP ise hızlıca kapıya bırakıp giden kurye gibidir.

### TCP vs UDP

| Özellik | TCP | UDP |
|---|---|---|
| Güvenilirlik | Yüksek | Düşük |
| Hız | Daha yavaş | Daha hızlı |
| Kontrol | Paketleri takip eder | Takip zayıftır |
| Kullanım | Web, mail, dosya transferi | Video, ses, DNS sorguları |

### HATIRLA

TCP güvenilirlik ister. UDP hız ister.

### Bunu neden öğreniyoruz?

Çünkü port tarama, firewall kuralı, log analizi ve saldırı tespiti TCP/UDP ayrımı olmadan yapılamaz.

### Kendini test et

1. TCP neden daha güvenilirdir?  
Cevap: Paketlerin ulaşıp ulaşmadığını kontrol eder.

2. UDP neden hızlıdır?  
Cevap: TCP kadar kontrol yapmaz.

3. Video akışında neden UDP tercih edilebilir?  
Cevap: Hız daha önemlidir, küçük kayıplar tolere edilebilir.

## 13. Bölüm: DNS, HTTP, HTTPS, SSL/TLS

### DNS nedir?

DNS (Domain Name System), alan adını IP adresine çevirir. Sen google.com yazarsın, DNS bunun IP adresini bulur.

### HTTP nedir?

HTTP (Hypertext Transfer Protocol), web sayfalarının iletilmesini sağlayan protokoldür.

### HTTPS nedir?

HTTPS, HTTP'nin güvenli halidir. Buradaki S, Secure anlamına gelir.

### SSL/TLS nedir?

SSL/TLS, iki taraf arasındaki iletişimi şifrelemek ve doğrulamak için kullanılan güvenlik mekanizmasıdır.

### Günlük hayat analojisi

HTTP açık kartpostal gibidir. HTTPS ise kapalı ve mühürlü zarf gibidir.

### HATIRLA

Kilit simgesi tek başına site güvenilirdir demek değildir. Ama bağlantının şifreli olduğunu gösterir.

### Kendini test et

1. DNS neyi çevirir?  
Cevap: Alan adını IP adresine çevirir.

2. HTTPS'deki S ne demektir?  
Cevap: Secure.

3. SSL/TLS ne sağlar?  
Cevap: Şifreli ve doğrulanmış iletişim sağlar.

## 14. Bölüm: MAC Address

### Bu nedir?

MAC Address, ağ kartının fiziksel adresidir. Fabrika tarafından cihaza atanır.

### IP ile farkı nedir?

| IP Address | MAC Address |
|---|---|
| Mantıksal adrestir | Fiziksel adrestir |
| Değişebilir | Genelde cihaza gömülüdür |
| Ağlar arası yönlendirmede kullanılır | Yerel ağ içinde kullanılır |

### HATIRLA

MAC adresi genellikle yerel ağın dışına çıkmaz. Router'dan sonra adresleme mantığı değişir.

### Kendini test et

1. MAC adresi nerede kullanılır?  
Cevap: Yerel ağ iletişiminde.

2. IP adresi değişebilir mi?  
Cevap: Evet.

3. MAC adresi IP ile aynı şey midir?  
Cevap: Hayır.

## 15. Genel Tekrar ve Özet

| Konu | Tek cümlelik özet |
|---|---|
| Kütüphane dosyaları | Programların tekrar kullandığı hazır kod parçalarıdır |
| DLL Hijacking | Zararlı DLL'in meşru DLL yerine çalıştırılmasıdır |
| Hash | Dosyanın dijital parmak izidir |
| Davranış analizi | Dosyanın sistemde ne yaptığını izler |
| Programlama dilleri | Bilgisayara komut vermek için kullanılır |
| Cloud | IT kaynaklarının internet üzerinden hizmet olarak alınmasıdır |
| IaaS | Altyapı hizmetidir |
| PaaS | Uygulama çalıştırma platformudur |
| SaaS | Hazır yazılım hizmetidir |
| Network | Cihazların iletişim kurduğu yapıdır |
| Internet | Ağların ağıdır |
| Protocol | İletişim kurallarıdır |
| IP | Verinin ağda nasıl taşınacağını belirler |
| Router | Ağlar arasında yönlendirme yapar |
| OSI | Ağ iletişimini 7 katmanda açıklar |
| TCP/IP | İnternetin pratik iletişim modelidir |
| TCP | Güvenilir veri taşır |
| UDP | Hızlı veri taşır |
| DNS | Alan adını IP'ye çevirir |
| HTTPS | Güvenli web iletişimi sağlar |
| MAC | Ağ kartının fiziksel adresidir |

## En kritik mesaj

Siber güvenlik öğrenmek istiyorsan önce sistemi anlamak zorundasın.

Sistem; donanım, yazılım, cloud, network, protokol, IP, port, router ve katmanlardan oluşur.

Saldırgan bu katmanların birinden girer. Savunmacı da bu katmanları bilerek savunma kurar.