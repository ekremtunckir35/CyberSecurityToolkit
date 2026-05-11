# Network Fundamentals-2 


**Ders odağı:** Network temelleri, internetin gelişimi, protokoller, IP routing, OSI/TCP-IP modeli ve Data Link Layer.

---

## 1. Dersin Ana Haritası

Bu derste geçen ana başlıklar:

1. Network neden öğrenilir?
2. Network nedir?
3. Endpoint / Host kavramı
4. İnternet = ağların ağı
5. Siber güvenlik ile network ilişkisi
6. ARPANET, MILNET ve internetin gelişimi
7. Fiber optik, Starlink, kablolu/kablosuz iletişim
8. Communication Protocol (İletişim Protokolü)
9. IP, IP Address, IP Routing
10. ISP, Home Router, Corporate Router, Edge Router
11. OSI modeli
12. TCP/IP modeli
13. Application, Presentation, Session katmanları
14. Transport Layer: TCP ve UDP
15. Network Layer: IP
16. Data Link Layer: MAC, Ethernet, Frame
17. Physical Layer: bitlerin sinyale dönüşmesi

> **Bağlantı:** Bu ders, önceki IT Fundamentals konularının üzerine ağ iletişimini ekler. Bilgisayarın tek başına nasıl çalıştığını öğrendikten sonra, şimdi cihazların birbirleriyle nasıl konuştuğunu öğreniyoruz.

---

## 2. Network Nedir?

### Bu nedir?

**Network (Ağ)**, iki veya daha fazla cihazın birbiriyle haberleşebildiği yapıdır.

Bu cihazlar bilgisayar, laptop, telefon, tablet, yazıcı, akıllı televizyon, robot süpürge, akıllı buzdolabı veya server olabilir.

### Günlük hayat analojisi

Network'ü bir **mahalle yolu** gibi düşün:

- Evler = cihazlar
- Yollar = kablolar / Wi-Fi
- Postacı = veri paketleri
- Adres = IP adresi
- Kapı numarası = MAC adresi

Bir evden diğer eve mektup gidebiliyorsa, orada iletişim vardır. Bilgisayarlarda da durum budur.

### Bunu neden öğreniyoruz?

Çünkü siber güvenlikte saldırılar çoğunlukla ağ üzerinden gerçekleşir. Bir saldırgan paketi dinleyebilir, değiştirebilir, engelleyebilir veya yanlış yere yönlendirebilir.

> **HATIRLA:** Siber güvenlikte “saldırı nereden geldi?” sorusunun cevabı çoğu zaman network bilgisinde saklıdır.

### KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Network | Cihazların haberleştiği yapı |
| Internet | Dünyadaki birçok ağın birleşimi |
| Wi-Fi | Ağa kablosuz bağlanma yöntemi |
| Ethernet | Ağa kabloyla bağlanma yöntemi |

### Kendini Test Et

**1. Network olması için en az kaç cihaz gerekir?**  
Cevap: En az iki cihaz gerekir.

**2. İnternete çıkmayan iki bilgisayar network oluşturabilir mi?**  
Cevap: Evet. İnternet şart değildir.

**3. Siber güvenlikte network neden önemlidir?**  
Cevap: Çünkü saldırıların büyük kısmı veri iletişimi sırasında gerçekleşir.

---

## 3. Endpoint / Host Nedir?

### Bu nedir?

**Endpoint (Son Nokta)** veya **Host**, kullanıcının ağa bağlanmak için kullandığı cihazdır. Laptop, telefon, masaüstü bilgisayar ve tablet endpoint örnekleridir.

### Günlük hayat analojisi

Endpoint'i **evin posta kutusu** gibi düşün. Posta kutusu, dış dünyadan gelen mektubun ulaştığı son noktadır. Bilgisayarda da veri paketlerinin geldiği son cihaz endpoint'tir.

### Bunu neden öğreniyoruz?

Çünkü saldırgan çoğu zaman endpoint'i hedef alır. Zararlı mail, malware, kimlik avı ve yetkisiz erişim çoğunlukla kullanıcı cihazı üzerinden başlar.

> **HATIRLA:** Endpoint zayıfsa, ağın geri kalanı da risk altındadır.

### KARMAŞTIRMA!

| Kavram | Farkı |
|---|---|
| Endpoint | Kullanıcının kullandığı son cihaz |
| Server | Hizmet veren cihaz |
| Router | Ağlar arasında yönlendirme yapan cihaz |
| Switch | Aynı ağdaki cihazları birbirine bağlayan cihaz |

### Kendini Test Et

**1. Telefon bir endpoint midir?**  
Cevap: Evet.

**2. Router endpoint midir?**  
Cevap: Genelde hayır; router yönlendirme cihazıdır.

**3. Endpoint güvenliği neden önemlidir?**  
Cevap: Saldırılar çoğu zaman kullanıcı cihazlarından başlar.

---

## 4. İnternet Nedir?

### Bu nedir?

**Internet**, ağların ağıdır. Ev ağı, şirket ağı, üniversite ağı ve servis sağlayıcı ağları birleşerek interneti oluşturur.

### Günlük hayat analojisi

- Ev ağı = mahalle yolu
- Şirket ağı = başka bir mahalle
- İnternet = şehirlerarası yollar + otoyollar + köprüler

Sen evinden YouTube'a bağlandığında aslında kendi mahallenden çıkıp başka bir şehirdeki binaya gidiyorsun.

### Ders içindeki örnek

Ders içinde internet kafeler örneği veriliyor. Bazı eski internet kafelerde dış internete çıkış yoktu; ama bilgisayarlar yerel ağda birbirleriyle haberleşebildiği için oyun oynanabiliyordu. Bu, internet olmadan da network olabileceğini gösterir.

### Bunu neden öğreniyoruz?

İnternete bağlı olan her cihaz, teorik olarak dış dünyayla temas halindedir. Bu da keşif, tarama, saldırı ve zararlı yazılım riskini artırır.

> **HATIRLA:** İnternete çıkmak konfor sağlar, ama saldırı yüzeyini büyütür.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| LAN | Yerel ağ |
| Internet | Ağların ağı |
| Offline network | Dış internete çıkmayan ağ |
| Isolated environment | İzole edilmiş güvenli ortam |

### Kendini Test Et

**1. İnternet olmadan network olur mu?**  
Cevap: Evet.

**2. İnternete bağlı olmayan sistem tamamen risksiz midir?**  
Cevap: Hayır. USB, iç tehdit veya fiziksel erişim gibi riskler devam eder.

**3. İnternet neden saldırı yüzeyini artırır?**  
Cevap: Cihaz dış dünyadan erişilebilir hale gelir.

---

## 5. Siber Güvenlikte Network Öğrenmenin Amacı

### Bu nedir?

Network öğrenmek, saldırının hangi noktada gerçekleştiğini anlamak için gereklidir. Ders içinde log takibi, zafiyet taraması, sızma testi, firewall loglarını inceleme, açık portları raporlama ve tekrar tarama gibi görevlerden bahsediliyor.

### Günlük hayat analojisi

Bir şirket binası düşün:

- Dış güvenlik noktası
- İç güvenlik kapısı
- Kartlı geçiş
- Parmak izi
- X-ray cihazı
- Yetkilendirme
- Farkındalık eğitimi

Bunların dijital karşılıkları firewall, kimlik doğrulama, MFA, antivirüs/EDR, access control ve security awareness eğitimidir.

### Bunu neden öğreniyoruz?

Security araçlarını ezbere kullanmak yetmez. Nmap ile açık port bulduğunda bunun ne anlama geldiğini, riski kimin düzelteceğini ve ne zaman yeniden kontrol edeceğini bilmelisin.

> **HATIRLA:** Siber güvenlik uzmanı her şeyi kendisi düzeltmez. Tespit eder, raporlar, takip eder.

### KARMAŞTIRMA!

| Rol | Görev |
|---|---|
| Security Analyst | Log inceler, alarm analiz eder |
| Pentester | Açıkları test eder |
| Network Admin | Router/switch/firewall yapılandırır |
| System Admin | Sunucu ve sistem yönetir |
| Firewall Admin | Firewall kurallarını yazar |

### Kendini Test Et

**1. Siber güvenlik uzmanı açık port bulursa her zaman kendisi mi kapatır?**  
Cevap: Hayır. Genelde raporlar ve ilgili ekibe yönlendirir.

**2. Log takibi neden önemlidir?**  
Cevap: Saldırı belirtileri loglarda görülebilir.

**3. Zafiyet taraması ne işe yarar?**  
Cevap: Sistemlerdeki güvenlik açıklarını tespit eder.

---

## 6. ARPANET, MILNET ve İnternetin Gelişimi

### Bu nedir?

Ders içinde internetin kökeni olarak **ARPANET** anlatılıyor. 1960'larda ağ teknolojileri gelişmeye başladı. ARPANET askeri ve akademik amaçlarla kullanıldı. 1977 sonrasında askeri ve sivil yapı ayrıldı. **MILNET (Military Network)** askeri taraf için devam etti. ARPANET'in sivil tarafı zamanla internete dönüştü.

### Günlük hayat analojisi

Başta tek bir büyük yol var. Hem askeri araçlar hem siviller aynı yolu kullanıyor. Sonra risk görülüyor ve askeri yol ayrılıyor. Bu ayrım güvenlik için yapılıyor.

### Bunu neden öğreniyoruz?

İnternet baştan itibaren güvenlik problemi taşıyan bir yapıdır. Başta amaç bağlantı kurmaktı; güvenlik sonradan daha kritik hale geldi.

> **HATIRLA:** İnternet önce iletişim için büyüdü, güvenlik sonradan zorunlu hale geldi.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| ARPANET | İnternetin öncülü |
| MILNET | Askeri amaçlı ayrılan ağ |
| Internet | Küresel ağların birleşimi |
| WWW | İnternet üzerinde çalışan web hizmeti |

### Kendini Test Et

**1. ARPANET neyin öncülüdür?**  
Cevap: İnternetin.

**2. MILNET neden ayrıldı?**  
Cevap: Askeri iletişimi sivil ağdan ayırmak ve güvenliği artırmak için.

**3. İnternetin temel problemi nedir?**  
Cevap: Çok geniş bağlantı sağlaması, saldırı yüzeyini de büyütür.

---

## 7. Fiber Optik, Starlink ve İletişim Altyapısı

### Bu nedir?

Ders içinde internetin büyük kısmının kıtalar arası **fiber optik kablolarla** taşındığı anlatılıyor. Ayrıca **Elon Musk / Starlink** örneği veriliyor. Starlink, uydu üzerinden internet sağlamayı hedefleyen bir sistem olarak ele alınıyor.

### Günlük hayat analojisi

Fiber optik kabloları şehirlerarası otoban gibi düşün. Starlink ise havadan çalışan alternatif yol gibidir.

### Ders içindeki özel örnek

Ukrayna-Rusya savaşı bağlamında insansız hava araçlarının sinyallerinin bozulabildiği, buna karşı bazı kısa mesafeli senaryolarda fiber kablo benzeri fiziksel bağlantıların kullanılabildiği anlatılıyor. Temel fikir şudur: radyo sinyali bozulabilir, kablo içinden giden sinyal daha zor manipüle edilir; fakat uzun mesafede pratik değildir.

### Bunu neden öğreniyoruz?

İletişim ortamı güvenliği doğrudan etkiler.

| Ortam | Risk |
|---|---|
| Kablosuz | Sinyal bozma, dinleme, araya girme |
| Kablolu | Fiziksel kesilme, kabloya erişim |
| Fiber | Fiziksel hasar, deniz altı kesintileri |
| Uydu | Gecikme, kapsama, sinyal kesintisi |

> **HATIRLA:** Güvenlik sadece yazılım değildir. Fiziksel iletişim ortamı da güvenliğin parçasıdır.

### Kendini Test Et

**1. Fiber optik ne taşır?**  
Cevap: Işık sinyalleriyle veri taşır.

**2. Kablosuz iletişim neden risklidir?**  
Cevap: Sinyal dinlenebilir, bozulabilir veya manipüle edilebilir.

**3. Starlink neye örnektir?**  
Cevap: Uydu tabanlı internet altyapısına.

---

## 8. Communication Protocol Nedir?

### Bu nedir?

**Protocol (Protokol)**, cihazların nasıl konuşacağını belirleyen kurallar bütünüdür.

Ders içinde IBM ve Digital örneği veriliyor. IBM kendi cihazları için kendi iletişim yapısını, Digital ise farklı bir yapıyı kullanıyordu. Farklı markalar birbiriyle konuşamayınca standart ihtiyacı doğdu. ISO gibi standart kuruluşları ortak modeller geliştirdi.

### Günlük hayat analojisi

Protokol = ortak dil. Bir kişi Türkçe, diğeri Japonca konuşursa anlaşamaz. Ama ikisi de İngilizce biliyorsa ortak dil oluşur. Bilgisayarlarda da protokoller bu ortak dili sağlar.

### Bunu neden öğreniyoruz?

Ağdaki her işlem bir protokole dayanır.

| İşlem | Protokol |
|---|---|
| Web sayfası açma | HTTP / HTTPS |
| Mail gönderme | SMTP |
| Mail alma | POP3 / IMAP |
| Dosya transferi | FTP |
| Uzak bağlantı | Telnet / SSH |
| Alan adı çözümleme | DNS |

> **HATIRLA:** Protokol yoksa cihazlar konuşamaz. Standart yoksa sistemler birlikte çalışamaz.

### KARMAŞTIRMA!

| Kavram | Anlam |
|---|---|
| Protocol | Kurallar bütünü |
| Port | Servisin kapı numarası |
| IP Address | Cihazın ağ adresi |
| MAC Address | Ağ kartının fiziksel adresi |

### Kendini Test Et

**1. Protokol ne demektir?**  
Cevap: İletişim kurallarının bütünüdür.

**2. HTTP ne için kullanılır?**  
Cevap: Web sayfalarına erişmek için.

**3. SMTP ne için kullanılır?**  
Cevap: Mail göndermek için.

---

## 9. IP, IP Address ve IP Routing

### IP nedir?

**IP (Internet Protocol)**, veri paketlerinin ağ üzerinde nasıl ilerleyeceğini belirleyen protokoldür.

### IP Address nedir?

**IP Address (IP Adresi)**, cihazın ağ üzerindeki adresidir. Ders içindeki örneğe göre evdeki bilgisayar `192.168.0.25`, başka bir ofiste aynı bilgisayar `192.168.1.45` alabilir. IP adresi bağlanılan ağa göre değişebilir.

### IP Routing nedir?

**IP Routing (IP Yönlendirme)**, bir paketin kaynaktan hedefe giderken hangi yolu izleyeceğinin belirlenmesidir.

Sen YouTube yazıp Enter'a bastığında arka planda DNS sorgusu, router'a yönelme, ISP ağına çıkış ve hedef server'a erişim gibi birçok işlem gerçekleşir.

### Günlük hayat analojisi

- IP adresi = ev adresi
- Routing = navigasyonun yol seçmesi
- Router = kavşaktaki yön tabelası

### Bunu neden öğreniyoruz?

Saldırı analizinde kaynak IP, hedef IP, routing, NAT, iç/dış ağ ayrımı ve firewall logları bu bilgiye dayanır.

> **HATIRLA:** IP adresi “nereye gideceğim?” sorusunun cevabıdır. MAC adresi ise yerel ağda “hangi fiziksel cihaza vereceğim?” sorusunun cevabıdır.

### KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| IP | Protokol |
| IP Address | Cihazın ağ adresi |
| Routing | Paketin yolunun belirlenmesi |
| Router | Yönlendirmeyi yapan cihaz |

### Kendini Test Et

**1. IP adresi her yerde aynı kalır mı?**  
Cevap: Hayır. Bağlandığın ağa göre değişebilir.

**2. Routing ne işe yarar?**  
Cevap: Paketin hedefe hangi yoldan gideceğini belirler.

**3. IP ile IP Address aynı şey midir?**  
Cevap: Hayır. IP protokoldür, IP Address adrestir.

---

## 10. ISP, Router ve Ağ Çıkışı

### ISP nedir?

**ISP (Internet Service Provider)**, internet servis sağlayıcısıdır. Türkiye örnekleri: Türk Telekom, Turkcell, Vodafone ve Türksat.

### Router nedir?

**Router (Yönlendirici)**, farklı ağları birbirine bağlayan cihazdır. Evdeki modem cihazının içinde genellikle router işlevi de bulunur.

### Router türleri

| Router türü | Açıklama |
|---|---|
| Home Router | Evdeki modem/router |
| Corporate Router | Şirket ağı için kullanılan router |
| Edge Router | Ağın dış dünyaya açılan sınır router'ı |
| Telecom Router | Telekom altyapısındaki büyük router'lar |
| Cloud Provider Router | AWS, Azure, Google Cloud gibi yapılarda kullanılan router'lar |

### Günlük hayat analojisi

Router = şehirlerarası otobüs terminali. Senin mahallenden çıkan yol doğrudan her şehre gitmez. Önce terminale gidersin, oradan doğru güzergaha yönlendirilirsin.

### Bunu neden öğreniyoruz?

Kurum güvenliğinde dış dünya ile iç ağ arasındaki geçiş noktaları kritiktir. Saldırgan router yapılandırmasını, firewall arkasındaki sistemleri, yanlış yönlendirme kurallarını veya açık servisleri hedefleyebilir.

> **HATIRLA:** Router sadece “internet dağıtan kutu” değildir. Ağlar arası trafiğin yöneticisidir.

### Kendini Test Et

**1. ISP ne demektir?**  
Cevap: Internet Service Provider, yani internet servis sağlayıcı.

**2. Router'ın temel görevi nedir?**  
Cevap: Farklı ağları birbirine bağlamak ve trafiği yönlendirmek.

**3. Home Router ile Corporate Router farkı nedir?**  
Cevap: Home Router ev kullanımı içindir; Corporate Router daha büyük ve kurumsal ağlar için kullanılır.

---

## 11. OSI Modeli

### Bu nedir?

**OSI Modeli (Open Systems Interconnection)**, ağ iletişimini 7 katmanda açıklayan referans modeldir. Ders içinde OSI'nin günümüzde daha çok eğitim, mülakat ve Security+ gibi sınavlar için önemli olduğu belirtiliyor.

### OSI katmanları

| Katman | İsim | Görev |
|---|---|---|
| 7 | Application | Kullanıcıya en yakın katman |
| 6 | Presentation | Formatlama, şifreleme, sıkıştırma |
| 5 | Session | Oturum yönetimi |
| 4 | Transport | TCP/UDP, taşıma |
| 3 | Network | IP, yönlendirme |
| 2 | Data Link | MAC, Ethernet, Frame |
| 1 | Physical | Bitleri sinyale çevirme |

### Günlük hayat analojisi

Bir kargo gönderiyorsun: mesajı yazarsın, dili/formatı düzenlenir, gönderim oturumu başlar, kargo yöntemi seçilir, adres belirlenir, paket yerel dağıtıma verilir ve fiziksel olarak taşınır.

### Bunu neden öğreniyoruz?

Sorun ve saldırı analizi katman mantığıyla yapılır:

- Kablo kopuksa Layer 1
- MAC/switch problemi varsa Layer 2
- IP routing problemi varsa Layer 3
- TCP/UDP port problemi varsa Layer 4
- Web uygulama problemi varsa Layer 7

> **HATIRLA:** “Layer 2”, “Layer 3” gibi ifadeler OSI modeline referanstır.

### KARMAŞTIRMA!

| OSI | TCP/IP karşılığı |
|---|---|
| Application + Presentation + Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link + Physical | Network Access / Link |

### Kendini Test Et

**1. OSI kaç katmandır?**  
Cevap: 7 katmandır.

**2. Data Link kaçıncı katmandır?**  
Cevap: 2. katmandır.

**3. Network Layer'da hangi temel kavram vardır?**  
Cevap: IP.

---

## 12. Application, Presentation ve Session

### Application Layer nedir?

Kullanıcının uygulamalarla iletişim kurduğu katmandır. Chrome, Firefox, WhatsApp, Discord, Gmail ve web browser örnekleri bu katmanla ilişkilidir.

### Presentation Layer nedir?

Verinin formatını düzenler. Format değiştirme, şifreleme/çözme ve sıkıştırma/açma işlemlerini yapar. ASCII, UTF-8, MP3, encryption/decryption ve sıkıştırılmış resimler bu bağlamda düşünülebilir.

### Session Layer nedir?

İki sistem arasında oturum oluşturur. Web sitesine bağlanmak, SQL bağlantısı kurmak veya RPC çağrısı yapmak örnek verilebilir.

### Günlük hayat analojisi

- Application = restoranda sipariş vermen
- Presentation = yemeğin tabakta sunuma hazırlanması
- Session = garsonun senin masanla mutfak arasında bağlantıyı sürdürmesi

### Bunu neden öğreniyoruz?

Kullanıcı “siteye girdim” der; ama arka planda DNS sorgusu, oturum açma, veri formatlama, şifreleme, TCP bağlantısı ve paketleme gibi birçok işlem olur.

> **HATIRLA:** Kullanıcı sadece sonucu görür. Network uzmanı arka plandaki süreci okur.

### Kendini Test Et

**1. Presentation Layer'ın üç temel görevi nedir?**  
Cevap: Formatlama, şifreleme, sıkıştırma.

**2. Session Layer ne yapar?**  
Cevap: Bağlantı/oturum oluşturur ve yönetir.

**3. Web browser hangi katmana yakındır?**  
Cevap: Application Layer.

---

## 13. Transport Layer: TCP ve UDP

### Bu nedir?

**Transport Layer**, verinin nasıl taşınacağını belirler. Bu katmanda iki temel protokol öne çıkar: **TCP (Transmission Control Protocol)** ve **UDP (User Datagram Protocol)**.

### TCP nedir?

TCP güvenilir iletişim sağlar. Bağlantı kurar, paketlerin ulaşıp ulaşmadığını kontrol eder, eksik paket varsa tekrar ister. Güvenilirlik önceliklidir.

### UDP nedir?

UDP hızlı iletişim sağlar. Daha az kontrol yapar, paket kaybını önemsemeyebilir. Video, ses, oyun ve bazı DNS işlemlerinde kullanılır.

### Günlük hayat analojisi

TCP = teslim tutanaklı kargo.  
UDP = hızlı kurye, kapıya bırakıp gider.

TCP'de “aldın mı?” kontrolü vardır. UDP'de “hızlı gitsin, birkaç küçük eksik sorun değil” mantığı vardır.

### Bunu neden öğreniyoruz?

Port tarama, servis analizi ve saldırı tespiti TCP/UDP farkını bilmeden anlaşılamaz.

> **HATIRLA:** TCP güvenilirlik, UDP hız odaklıdır.

### KARMAŞTIRMA!

| TCP | UDP |
|---|---|
| Güvenilir | Hızlı |
| Bağlantı odaklı | Bağlantısız |
| Kontrol mekanizması güçlü | Kontrol az |
| Web, mail, SSH | DNS, video, ses, oyun |

### Kendini Test Et

**1. TCP ne zaman tercih edilir?**  
Cevap: Verinin eksiksiz ulaşması önemliyse.

**2. UDP ne zaman tercih edilir?**  
Cevap: Hız önemliyse ve küçük kayıplar tolere edilebiliyorsa.

**3. Transport Layer'da veri birimine ne denir?**  
Cevap: Segment.

---

## 14. Network Layer: IP

### Bu nedir?

**Network Layer**, kaynak ve hedef IP bilgileriyle paketin yönlendirilmesini sağlar. Bu katmandaki veri birimi genellikle **packet (paket)** olarak adlandırılır.

### Günlük hayat analojisi

Network Layer = kargonun şehir ve adres bilgisi. Kargo hangi şehirden çıkacak, hangi şehre gidecek, hangi rotadan ilerleyecek burada belirlenir.

### Bunu neden öğreniyoruz?

Firewall, routing, subnetting ve saldırı analizi bu katmanla doğrudan ilişkilidir.

> **HATIRLA:** Layer 3 = IP ve routing dünyasıdır.

### Kendini Test Et

**1. Network Layer'da en kritik kavram nedir?**  
Cevap: IP.

**2. Bu katmanda veri birimi nedir?**  
Cevap: Packet.

**3. Source IP ne demektir?**  
Cevap: Paketi gönderen cihazın IP adresi.

---

## 15. Data Link Layer: MAC, Ethernet, Frame

### Bu nedir?

**Data Link Layer**, yerel ağ içindeki cihazlar arasında veri iletimini düzenler. Bu katmanda MAC adresleri kullanılır, Ethernet çalışır, paketler frame'lere bölünür ve hata kontrolü yapılır.

### MAC Address nedir?

**MAC Address**, ağ kartının fiziksel adresidir. IP adresi değişebilir; MAC adresi genelde cihaza/ağ kartına bağlıdır.

### Ethernet nedir?

**Ethernet**, kablolu ağlarda kullanılan yaygın Data Link protokolüdür.

### Frame nedir?

Network Layer'dan gelen packet, Data Link Layer'da **frame** haline getirilir.

### Günlük hayat analojisi

IP adresi = apartmanın adresi.  
MAC adresi = daire kapısındaki zil etiketi.

Router seni apartmana getirir. Switch/MAC bilgisi seni doğru daireye ulaştırır.

### Bunu neden öğreniyoruz?

Yerel ağ saldırılarının çoğu Layer 2'de gerçekleşir: ARP spoofing, MAC flooding, switch saldırıları, VLAN hopping ve yerel ağ dinleme gibi.

> **HATIRLA:** MAC adresi internette uçtan uca taşınmaz. Genellikle yerel ağ içinde anlamlıdır.

### KARMAŞTIRMA!

| IP Address | MAC Address |
|---|---|
| Ağ adresidir | Fiziksel ağ kartı adresidir |
| Değişebilir | Genelde sabittir |
| Layer 3 | Layer 2 |
| Routing için kullanılır | Yerel iletim için kullanılır |

### Kendini Test Et

**1. Data Link Layer kaçıncı katmandır?**  
Cevap: 2. katmandır.

**2. Bu katmanda veri birimi nedir?**  
Cevap: Frame.

**3. MAC adresi nerede önemlidir?**  
Cevap: Yerel ağ içinde.

---

## 16. Physical Layer

### Bu nedir?

**Physical Layer**, bitlerin fiziksel sinyallere çevrildiği katmandır. Veri elektrik sinyaline, radyo frekans sinyaline veya ışık sinyaline dönüşebilir.

### Günlük hayat analojisi

Physical Layer = kargonun gerçekten kamyona yüklenip yola çıkması. Üst katmanlarda plan yapılır; fiziksel katmanda gerçek taşıma olur.

### Bunu neden öğreniyoruz?

Kablo koparsa iletişim olmaz. Wi-Fi sinyali bozulursa bağlantı düşer. Fiber kesilirse geniş çaplı kesinti olabilir. Fiziksel erişim güvenlik riskidir.

> **HATIRLA:** Layer 1 bozuksa üst katmanlar çalışamaz.

### Kendini Test Et

**1. Physical Layer ne yapar?**  
Cevap: Bitleri fiziksel sinyallere çevirir.

**2. Fiber optikte veri nasıl taşınır?**  
Cevap: Işık sinyalleriyle.

**3. Wi-Fi hangi fiziksel ortamı kullanır?**  
Cevap: Radyo frekans sinyallerini.

---

# Genel Tekrar ve Özet

| Konu | Tek cümlelik özet |
|---|---|
| Network | Cihazların haberleştiği yapıdır. |
| Internet | Ağların küresel birleşimidir. |
| Endpoint | Kullanıcının ağa bağlandığı son cihazdır. |
| Protocol | Cihazların ortak iletişim kurallarıdır. |
| IP | Paketlerin ağda nasıl ilerleyeceğini belirler. |
| IP Address | Cihazın ağ üzerindeki adresidir. |
| Routing | Paketin hedefe gideceği yolu seçer. |
| ISP | İnternet hizmetini sağlayan kurumdur. |
| Router | Ağlar arasında yönlendirme yapar. |
| OSI | Ağ iletişimini 7 katmanda açıklar. |
| TCP/IP | Günümüzde kullanılan temel ağ modelidir. |
| TCP | Güvenilir taşıma sağlar. |
| UDP | Hızlı taşıma sağlar. |
| MAC | Yerel ağdaki fiziksel cihaz adresidir. |
| Frame | Data Link Layer'daki veri birimidir. |
| Physical Layer | Bitleri sinyale dönüştürür. |

## En Kritik Öğrenme Sonucu

Network öğrenmeden siber güvenlik öğrenmek eksik kalır. Çünkü saldırı, savunma, log analizi, zafiyet taraması, firewall, IDS/IPS, EDR ve pentest çalışmalarının tamamı ağ iletişiminin nasıl çalıştığını bilmeyi gerektirir.
