# NETWORK FUNDAMENTALS - 4
## Data Link Layer Tekrarı -> Wireless LAN -> Network Layer -> IPv4 Girişi


---

# ADIM 1 - Ana Başlıklar

Bu derste geçen ana konular:

1. OSI Modeli ve PDU Mantığı
2. Encapsulation / Decapsulation
3. Data Link Layer Tekrarı
4. Ethernet Frame, MAC Address, FCS
5. Broadcast, Unicast, Multicast
6. Broadcast Domain ve Collision Domain
7. ARP Protokolü
8. VLAN Mantığı
9. Bandwidth Kavramı
10. Wireless LAN, SSID, BSSID, ESSID
11. Kablosuz Ağ Saldırıları
12. Captive Portal
13. Wi-Fi Standartları
14. Network Layer
15. IP Protocol, IPv4, IPv6
16. TTL, Hop, Routing
17. Private IP, Public IP, NAT
18. Loopback ve APIPA
19. IP Sınıfları ve CIDR Girişi

---

# 1. OSI Modeli ve PDU Mantığı

## Bu nedir?

OSI Modeli, ağ iletişimini 7 katmana bölen öğretici bir modeldir.

Katmanlar:

1. Physical - Fiziksel
2. Data Link - Veri Bağlantı
3. Network - Ağ
4. Transport - Taşıma
5. Session - Oturum
6. Presentation - Sunum
7. Application - Uygulama

Eğitmen burada şu ezber cümlesini verdi:

> Please Don't Throw Sausage Pizza Away

Yani:

- Physical
- Data Link
- Network
- Transport
- Session
- Presentation
- Application

## PDU nedir?

PDU (Protocol Data Unit), verinin her katmanda aldığı isimdir.

| Katman | Verinin Adı |
|---|---|
| 7-6-5 | Data |
| 4 | Segment / Datagram |
| 3 | Packet |
| 2 | Frame |
| 1 | Bits / Signal |

## Günlük hayat analojisi

Bir kargo düşün:

- İçindeki ürün = Data
- Ürün kutusu = Segment
- Kargo etiketi = Packet
- Dış ambalaj = Frame
- Kamyona yüklenmesi = Bit / Signal

## Bunu neden öğreniyoruz?

Çünkü ağda veri tek parça büyülü şekilde gitmez. Her katmanda üzerine yeni bilgi eklenir. Siber güvenlikte paket analizi, Wireshark, firewall, IDS/IPS ve pentest çalışmalarında bu yapı temel bilgidir.

> HATIRLA: Data -> Segment -> Packet -> Frame -> Bit

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Segment | TCP ile kullanılan taşıma katmanı birimi |
| Datagram | UDP ile kullanılan taşıma katmanı birimi |
| Packet | Network Layer'daki IP'li yapı |
| Frame | Data Link Layer'daki MAC'li yapı |

## Kendini Test Et

Soru 1: Network Layer'da verinin adı nedir?  
Cevap: Packet.

Soru 2: Data Link Layer'da verinin adı nedir?  
Cevap: Frame.

Soru 3: Transport Layer'da TCP kullanılıyorsa veriye ne denir?  
Cevap: Segment.

---

# 2. Encapsulation ve Decapsulation

## Bu nedir?

Encapsulation (Sarmalama), verinin gönderici tarafta yukarıdan aşağı katmanlara inerken her katmanda yeni başlık bilgileri almasıdır.

Decapsulation (Ters Sarmalama), alıcı tarafta verinin aşağıdan yukarı çıkarken bu başlıkların tek tek açılmasıdır.

## Günlük hayat analojisi

Bir kitap gönderiyorsun:

1. Kitap hazırlanır.
2. Küçük kutuya konur.
3. Büyük kutuya konur.
4. Üzerine adres etiketi yapıştırılır.
5. Güvenlik bandı eklenir.
6. Kargo aracına yüklenir.

Alıcı tarafta tam tersi yapılır.

## Teknik süreç

Gönderici taraf:

```text
Data
-> TCP/UDP Header eklenir = Segment
-> IP Header eklenir = Packet
-> Ethernet Header + Trailer eklenir = Frame
-> Elektrik / ışık / radyo sinyali = Bits
```

Alıcı taraf:

```text
Bits
-> Frame
-> Packet
-> Segment
-> Data
```

## Bunu neden öğreniyoruz?

Wireshark'ta bir paketi incelerken aslında bu katmanları görürsün. Ethernet başlığı, IP başlığı, TCP/UDP başlığı ve uygulama verisi ayrı ayrı analiz edilir.

> HATIRLA: Gönderirken veri paketlenir. Alırken paket açılır.

## KARMAŞTIRMA!

| Encapsulation | Decapsulation |
|---|---|
| Gönderici tarafta olur | Alıcı tarafta olur |
| Başlık eklenir | Başlık çıkarılır |
| Yukarıdan aşağı gider | Aşağıdan yukarı gider |

## Kendini Test Et

Soru 1: Encapsulation hangi yönde gerçekleşir?  
Cevap: Application'dan Physical'a doğru, yani yukarıdan aşağı.

Soru 2: Decapsulation hangi tarafta olur?  
Cevap: Alıcı tarafta.

Soru 3: Ethernet Header hangi katmanda eklenir?  
Cevap: Data Link Layer'da.

---

# 3. Data Link Layer

## Bu nedir?

Data Link Layer, OSI modelinin 2. katmanıdır. Temel görevi, Network Layer'dan gelen paketi fiziksel ortamda taşınabilir hale getirmektir.

Bu katmanın en önemli konusu: MAC Address (Fiziksel Adres).

## Alt katmanları

| Alt Katman | Görev |
|---|---|
| LLC (Logical Link Control) | Network Layer'a yakın çalışır |
| MAC (Media Access Control) | Physical Layer'a yakın çalışır |

## Günlük hayat analojisi

Bir apartmanda daire numarası gibi düşün:

- IP adresi = Şehrin / mahallenin adresi
- MAC adresi = Apartman içindeki fiziksel daire kimliği

## Bunu neden öğreniyoruz?

Yerel ağda cihazların birbirini bulması MAC adresleriyle olur. Switch'ler MAC adresleriyle çalışır. ARP, Ethernet, VLAN gibi konular bu katmana dayanır.

> HATIRLA: Layer 2 = MAC, Layer 3 = IP, Layer 4 = Port

## KARMAŞTIRMA!

| Layer | Ana Kavram |
|---|---|
| Layer 2 | MAC Address |
| Layer 3 | IP Address |
| Layer 4 | Port |

## Kendini Test Et

Soru 1: Data Link Layer'ın en önemli adresleme türü nedir?  
Cevap: MAC Address.

Soru 2: Switch klasik olarak hangi katmanda çalışır?  
Cevap: Layer 2.

Soru 3: Router klasik olarak hangi katmanda çalışır?  
Cevap: Layer 3.

---

# 4. Ethernet Frame ve MAC Address

## Bu nedir?

Ethernet Frame, Data Link Layer'da oluşturulan veri yapısıdır.

Bir Ethernet Frame içinde şunlar bulunur:

- Destination MAC Address
- Source MAC Address
- EtherType
- Payload
- FCS / Trailer

## MAC Address nedir?

MAC adresi, ağ kartının fiziksel kimliğidir.

- 48 bit uzunluğundadır.
- 6 byte'tır.
- İlk 24 bit üretici bilgisidir.
- Son 24 bit cihazı benzersiz yapan kısımdır.

Örnek üreticiler: Realtek, Broadcom, Cisco, Apple, Fortinet.

## FCS nedir?

FCS (Frame Check Sequence), frame'in bozulup bozulmadığını kontrol eden sayısal değerdir.

## Günlük hayat analojisi

Bir kargo paketinde:

- Alıcı adresi = Destination MAC
- Gönderen adresi = Source MAC
- Paket içeriği = Payload
- Güvenlik mührü = FCS

## Bunu neden öğreniyoruz?

Wireshark'ta Ethernet Frame incelerken MAC adreslerini, payload'u ve hata kontrol alanını görürsün.

> HATIRLA: Frame = Ethernet Header + Payload + Trailer

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Header | Baş tarafa eklenen bilgi |
| Trailer | Son tarafa eklenen kontrol bilgisi |
| Payload | Taşınan asıl yük |
| FCS | Hata kontrol değeri |

## Kendini Test Et

Soru 1: MAC adresi kaç bittir?  
Cevap: 48 bit.

Soru 2: FCS ne işe yarar?  
Cevap: Frame'in bozulup bozulmadığını kontrol eder.

Soru 3: Payload ne demektir?  
Cevap: Frame içinde taşınan asıl veri/yük.

---

# 5. Broadcast, Unicast, Multicast

## Bu nedir?

Ağda veri gönderiminin üç temel türü vardır:

| Tür | Anlamı |
|---|---|
| Unicast | Tek kişiye gönderim |
| Multicast | Belirli gruba gönderim |
| Broadcast | Herkese gönderim |

## Günlük hayat analojisi

Sınıftaki öğretmen:

- Bir öğrenciyle konuşursa = Unicast
- Sadece 5 öğrenciyle konuşursa = Multicast
- Tüm sınıfa seslenirse = Broadcast

## Ağ örneği

ARP ilk aşamada broadcast yapar:

```text
Bu IP kimin?
```

Cevap veren cihaz ise unicast döner:

```text
Bu IP benim, MAC adresim şu.
```

## Bunu neden öğreniyoruz?

Broadcast trafiği büyürse ağ yavaşlar. VLAN ve subnet tasarımı broadcast'i kontrol altına almak için kullanılır.

> HATIRLA: ARP Request = Broadcast, ARP Reply = Unicast

## KARMAŞTIRMA!

| Kavram | Yanlış Anlama | Doğrusu |
|---|---|---|
| Broadcast | Her zaman kötü | Hayır, gerekli ama kontrol edilmeli |
| Multicast | Broadcast ile aynı | Hayır, sadece belirli gruba gider |
| Unicast | Sadece internette olur | Hayır, yerel ağda da olur |

## Kendini Test Et

Soru 1: Broadcast ne demektir?  
Cevap: Ağdaki herkese gönderim.

Soru 2: Unicast ne demektir?  
Cevap: Tek hedefe gönderim.

Soru 3: ARP Request genelde nasıl gönderilir?  
Cevap: Broadcast olarak.

---

# 6. Broadcast Domain ve Collision Domain

## Broadcast Domain nedir?

Broadcast Domain, broadcast paketinin ulaşabildiği ağ alanıdır. Router'ın her bir bacağı ayrı bir broadcast domain oluşturur.

## Collision Domain nedir?

Collision Domain, paketlerin çakışma ihtimali olan alandır. Hub kullanılırsa tüm hub tek collision domain olur. Switch kullanılırsa her port ayrı collision domain kabul edilir.

## Günlük hayat analojisi

Dar bir köprü düşün: Aynı anda iki keçi geçmeye çalışırsa çarpışır. Bu collision domain'dir.

Bir okul anons sistemi düşün: Müdür tüm sınıflara anons yaparsa broadcast domain oluşur.

## Bunu neden öğreniyoruz?

Ağ performansını anlamak için bu iki kavram kritik. Büyük ağlarda broadcast domain küçük tutulmazsa ağ tıkanabilir.

> HATIRLA: Router broadcast domain'i böler. Switch collision domain'i böler.

## KARMAŞTIRMA!

| Kavram | İlgili Cihaz |
|---|---|
| Broadcast Domain | Router / VLAN |
| Collision Domain | Hub / Switch Port |

## Kendini Test Et

Soru 1: Hub'ın tamamı kaç collision domain kabul edilir?  
Cevap: Tek collision domain.

Soru 2: Switch'in her portu ne kabul edilir?  
Cevap: Ayrı collision domain.

Soru 3: Router'ın her bacağı ne oluşturur?  
Cevap: Ayrı broadcast domain.

---

# 7. ARP Protokolü

## Bu nedir?

ARP (Address Resolution Protocol), IP adresinden MAC adresini bulmak için kullanılır.

Soru şudur:

```text
Bu IP adresi kimde? MAC adresin nedir?
```

## ARP nasıl çalışır?

1. Bilgisayar hedef IP'yi bilir.
2. Hedef MAC'i bilmez.
3. Broadcast gönderir.
4. Hedef cihaz cevap verir.
5. IP-MAC eşleşmesi ARP tablosuna yazılır.

## ARP tablosu

ARP tablosu RAM'de tutulur.

Komutlar:

```bash
arp -a
arp -d
arp -s
```

| Komut | Görev |
|---|---|
| arp -a | ARP tablosunu gösterir |
| arp -d | ARP kaydını siler |
| arp -s | Statik ARP kaydı ekler |

## Dinamik ve Statik ARP

| Tür | Açıklama |
|---|---|
| Dinamik ARP | Sistem otomatik öğrenir, süre sonra silinir |
| Statik ARP | Kullanıcı elle tanımlar, sistem kapanana kadar kalabilir |

## Günlük hayat analojisi

Askerde mektup dağıtılıyor: "Mehmetoğlu Nuri kim?" Herkese seslenilir. Mehmetoğlu Nuri çıkar ve "Benim" der. Bu ARP Request ve ARP Reply mantığıdır.

## Bunu neden öğreniyoruz?

ARP, yerel ağ iletişiminin temelidir. ARP Spoofing / ARP Poisoning gibi saldırılar da bu mantığı kötüye kullanır.

> HATIRLA: IP biliyorsan ama MAC bilmiyorsan ARP devreye girer.

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| IP Address | Mantıksal adres |
| MAC Address | Fiziksel adres |
| ARP | IP'den MAC bulur |

## Kendini Test Et

Soru 1: ARP ne işe yarar?  
Cevap: IP adresinden MAC adresini bulur.

Soru 2: ARP tablosu nerede tutulur?  
Cevap: RAM'de.

Soru 3: ARP Request nasıl gönderilir?  
Cevap: Broadcast olarak.

---

# 8. VLAN

## Bu nedir?

VLAN (Virtual LAN), fiziksel olarak aynı switch'e bağlı cihazları mantıksal olarak farklı ağlara bölme yöntemidir.

## Neden kullanılır?

- Broadcast trafiğini azaltır.
- Güvenliği artırır.
- Departmanları ayırır.
- Fiziksel kablolama maliyetini azaltır.
- Yönetimi kolaylaştırır.

## Ders örnekleri

Bir şirkette bölümler: Engineering, Marketing, Accounting, Human Resources. Hepsi aynı switch'e bağlı olabilir ama VLAN ile ayrı ağlarda çalışabilir.

## Okul analojisi

Bir okulda öğrenciler, öğretmenler, yönetim ve misafirler aynı ağa bağlanırsa risk artar. VLAN ile ayrılırsa her grup kendi alanında kalır.

## Siber güvenlik açısından önemi

Bir saldırgan Marketing VLAN'ındaki bir cihaza sızarsa, doğru yapılandırmada Engineering veya Accounting sistemlerine doğrudan erişemez.

## Bunu neden öğreniyoruz?

Kurumsal ağlarda segmentasyon güvenliğin temelidir. VLAN bilmeden güvenli ağ tasarımı yapılamaz.

> HATIRLA: VLAN = Aynı switch üzerinde sanal ağ bölme.

## KARMAŞTIRMA!

| Fiziksel LAN | VLAN |
|---|---|
| Ayrı kablo/switch gerekebilir | Aynı switch üzerinde mantıksal ayrım yapılır |
| Maliyetli olabilir | Daha esnektir |
| Fiziksel sınırlara bağlıdır | Yazılımla yönetilir |

## Kendini Test Et

Soru 1: VLAN ne işe yarar?  
Cevap: Ağı sanal olarak bölümlere ayırır.

Soru 2: VLAN güvenliği nasıl artırır?  
Cevap: Departmanları birbirinden izole eder.

Soru 3: VLAN broadcast trafiğini etkiler mi?  
Cevap: Evet, broadcast domain'i küçültür.

---

# 9. Bandwidth

## Bu nedir?

Bandwidth (Bant Genişliği), bir bağlantı üzerinden saniyede taşınabilecek veri miktarıdır. Genelde Mbps veya Gbps ile ifade edilir.

Örnek: 100 Mbps, 500 Mbps, 1000 Mbps.

## Günlük hayat analojisi

İki boru düşün: İnce borudan az su geçer. Kalın borudan daha çok su geçer. Suyun akış hızı benzer olabilir ama geniş boru aynı sürede daha fazla su taşır.

## Download ve Upload

| Kavram | Anlamı |
|---|---|
| Download | İnternetten sana gelen veri |
| Upload | Senden internete giden veri |

ISP'ler genelde download hızını öne çıkarır. Upload hızı çoğunlukla daha düşüktür.

## Bunu neden öğreniyoruz?

Ağ performansı, dosya aktarımı, video izleme, cloud sistemleri, VPN ve pentest veri transferlerinde bandwidth doğrudan etkilidir.

> HATIRLA: Mbps = Megabit per second. Megabit ile Megabyte aynı şey değildir.

## KARMAŞTIRMA!

| Mbps | MB/s |
|---|---|
| Megabit/saniye | Megabyte/saniye |
| İnternet hızında kullanılır | Dosya boyutunda daha sık görülür |
| 8 bit = 1 byte | 1 MB = 8 Mb |

## Kendini Test Et

Soru 1: Bandwidth ne demektir?  
Cevap: Bağlantının veri taşıma kapasitesi.

Soru 2: ISP'ler genelde hangi hızı reklam eder?  
Cevap: Download hızını.

Soru 3: Upload ne zaman önemlidir?  
Cevap: Dosya yükleme, cloud, sunucu, canlı yayın gibi durumlarda.

---

# 10. Wireless LAN, SSID, BSSID, ESSID

## Wireless LAN nedir?

Wireless LAN, cihazların kablo yerine radyo sinyalleriyle ağa bağlanmasıdır. Standart adı IEEE 802.11'dir.

## SSID nedir?

SSID (Service Set Identifier), kablosuz ağın görünen adıdır. Örnek: Ev Wi-Fi, Cafe Free, Hotel ABC, ABC Company.

## BSSID nedir?

BSSID (Basic Service Set Identifier), Access Point'in MAC adresidir. Kullanıcı genelde görmez.

## ESSID nedir?

ESSID (Extended Service Set Identifier), birden fazla Access Point'in aynı ağ adıyla çalışmasıdır. Örneğin AVM'de yürürken Wi-Fi kopmaz. Çünkü farklı Access Point'ler aynı SSID ile hizmet verir.

## Günlük hayat analojisi

Bir otelde aynı isimli Wi-Fi her katta çalışıyorsa:

- Ağ adı = SSID
- Her kattaki cihazın MAC'i = BSSID
- Tüm otelde aynı isimle genişletilmiş ağ = ESSID

## Bunu neden öğreniyoruz?

Kablosuz ağ analizinde SSID, BSSID ve ESSID ayrımı önemlidir. Evil Twin, Rogue AP ve Wi-Fi pentest konularında bu kavramlar temel olur.

> HATIRLA: SSID = Wi-Fi adı, BSSID = Access Point MAC adresi, ESSID = Genişletilmiş Wi-Fi ağı.

## KARMAŞTIRMA!

| Kavram | Kullanıcı Görür mü? | Format |
|---|---|---|
| SSID | Evet | Metin |
| BSSID | Genelde hayır | MAC adresi |
| ESSID | Evet | Metin |

## Kendini Test Et

Soru 1: SSID nedir?  
Cevap: Kablosuz ağın görünen adı.

Soru 2: BSSID nedir?  
Cevap: Access Point'in MAC adresi.

Soru 3: ESSID ne zaman kullanılır?  
Cevap: Aynı ağ birden fazla Access Point ile genişletildiğinde.

---

# 11. Kablosuz Ağ Saldırıları

## Başlıca saldırılar

Derste geçen temel kablosuz ağ saldırıları:

1. Denial of Service (DoS)
2. Rogue Access Point
3. Misconfiguration
4. Traffic Interception
5. Crypto Attacks
6. Client Duping / Evil Twin Mantığı

## DoS nedir?

Kablosuz ağı gereksiz trafikle doldurup meşru kullanıcıların hizmet alamamasına neden olur.

## Rogue Access Point nedir?

Yetkisiz erişim noktasıdır. Örneğin bir çalışan switch'e kendi Access Point'ini takarsa kurum ağına kontrolsüz kablosuz giriş açabilir.

## Evil Twin mantığı

Saldırgan gerçek ağa benzeyen sahte SSID oluşturur.

Gerçek ağ:

```text
ABC Company
```

Sahte ağ:

```text
ABC Company
```

Kullanıcı sahte ağa bağlanırsa saldırgan trafiği izleyebilir.

## Misconfiguration nedir?

Hatalı yapılandırmadır. Örnekler:

- Zayıf parola
- Eski şifreleme
- WEP gibi eski protokoller
- Açık Wi-Fi
- Varsayılan modem ayarları

## Bunu neden öğreniyoruz?

Kablosuz ağlar fiziksel kablo gerektirmediği için saldırı yüzeyi daha geniştir. Sinyal duvardan, sokaktan, otoparktan, hatta özel ekipmanlarla uzak mesafeden yakalanabilir.

> HATIRLA: Halka açık Wi-Fi üzerinden bankacılık işlemi yapmak ciddi risktir.

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Rogue AP | Yetkisiz Access Point |
| Evil Twin | Gerçek ağa benzeyen sahte ağ |
| Misconfiguration | Hatalı yapılandırma |
| Interception | Trafiği yakalama/dinleme |

## Kendini Test Et

Soru 1: Rogue AP nedir?  
Cevap: Yetkisiz kurulan erişim noktası.

Soru 2: Evil Twin saldırısında amaç nedir?  
Cevap: Kullanıcıyı sahte ağa bağlatmak.

Soru 3: Kablosuz ağda en temel güvenlik önlemlerinden biri nedir?  
Cevap: Güçlü parola ve güncel şifreleme protokolü kullanmak.

---

# 12. Captive Portal

## Bu nedir?

Captive Portal, otel, kafe, havaalanı veya kurum Wi-Fi'sine bağlanırken karşına çıkan giriş/kayıt ekranıdır.

Örnek bilgiler isteyebilir:

- Ad soyad
- E-posta
- Telefon
- TC kimlik bilgisi
- SMS doğrulama
- Kullanıcı adı / parola

## Neden kullanılır?

- Kullanıcıyı tanımlamak
- Log tutmak
- Hukuki sorumluluğu azaltmak
- Misafir ağını kontrol etmek
- KVKK ve güvenlik süreçlerini desteklemek

## Günlük hayat analojisi

Bir binaya girerken güvenlik görevlisinin kimlik istemesi gibidir. Wi-Fi'ye bağlanmadan önce sistem seni tanır.

## Bunu neden öğreniyoruz?

Kurumsal ağlarda "kim ne zaman internete çıktı?" sorusunun cevabı güvenlik ve hukuk açısından önemlidir.

> HATIRLA: Captive Portal sadece internet vermek için değil, kullanıcıyı kayıt altına almak için de kullanılır.

## KARMAŞTIRMA!

| Açık Wi-Fi | Captive Portal |
|---|---|
| Herkes doğrudan bağlanabilir | Önce kayıt/giriş gerekir |
| Log takibi zayıf olabilir | Kullanıcı bazlı takip yapılabilir |
| Risklidir | Daha kontrollüdür |

## Kendini Test Et

Soru 1: Captive Portal nerelerde karşımıza çıkar?  
Cevap: Otel, kafe, havaalanı, kurum Wi-Fi ağlarında.

Soru 2: Captive Portal'ın güvenlik amacı nedir?  
Cevap: Kullanıcıyı tanımlamak ve log tutmak.

Soru 3: Captive Portal tamamen güvenlik sağlar mı?  
Cevap: Hayır, sadece kontrol ve kayıt mekanizması sağlar.

---

# 13. Wi-Fi Standartları

## Bu nedir?

Wi-Fi teknolojisi IEEE 802.11 ailesiyle gelişmiştir.

| Standart | Yaygın Ad | Özellik |
|---|---|---|
| 802.11 | Wi-Fi 0 | 1-2 Mbps |
| 802.11b | Wi-Fi 1 | 2.4 GHz |
| 802.11a | Wi-Fi 2 | 5 GHz |
| 802.11g | Wi-Fi 3 | 54 Mbps |
| 802.11n | Wi-Fi 4 | MIMO |
| 802.11ac | Wi-Fi 5 | MU-MIMO |
| 802.11ax | Wi-Fi 6 | OFDMA |
| Wi-Fi 6E | Extended | 6 GHz |
| 802.11be | Wi-Fi 7 | Çok yüksek hız |
| 802.11bn | Wi-Fi 8 | Geliştirme aşaması |

## MIMO nedir?

MIMO (Multiple Input Multiple Output), birden fazla antenle aynı anda daha fazla veri iletimidir.

## MU-MIMO nedir?

Multi User MIMO, birden fazla kullanıcıya aynı anda daha verimli hizmet verilmesidir.

## 2.4 GHz vs 5 GHz

| 2.4 GHz | 5 GHz |
|---|---|
| Daha uzun menzil | Daha yüksek hız |
| Duvarlardan daha iyi geçer | Duvarlarda daha çok zayıflar |
| Daha kalabalık frekans | Daha az parazit olabilir |

## Bunu neden öğreniyoruz?

Kablosuz ağ performansı sadece modem hızına bağlı değildir. Modem, repeater, network kartı ve ortam şartları birlikte değerlendirilmelidir.

> HATIRLA: Modem Wi-Fi 7 olsa bile cihazın network kartı eskiyse Wi-Fi 7 hızını alamazsın.

## KARMAŞTIRMA!

| Yanlış Düşünce | Doğrusu |
|---|---|
| Modem hızlıysa her şey hızlıdır | Cihaz, repeater ve ağ kartı da uyumlu olmalı |
| 5 GHz her zaman daha iyidir | Mesafe ve duvar varsa 2.4 GHz daha stabil olabilir |
| Wi-Fi standardı sadece hızdır | Güvenlik ve verimlilik de gelişir |

## Kendini Test Et

Soru 1: MIMO ne demektir?  
Cevap: Multiple Input Multiple Output.

Soru 2: 2.4 GHz'in avantajı nedir?  
Cevap: Daha uzun menzil ve duvarlardan daha iyi geçiş.

Soru 3: Wi-Fi 6E hangi yeni bandı kullanır?  
Cevap: 6 GHz.

---

# 14. Network Layer

## Bu nedir?

Network Layer, OSI modelinin 3. katmanıdır. En önemli konusu IP Address'tir.

Temel görevleri:

- Paketleri yönlendirmek
- Kaynak ve hedef IP bilgilerini taşımak
- Router üzerinden rota belirlemek
- Farklı ağlar arasında iletişim sağlamak

## Router nedir?

Router, farklı ağları birbirine bağlayan Layer 3 cihazıdır.

## Hop nedir?

Bir paketin geçtiği her router/adım bir hop olarak adlandırılır.

## Günlük hayat analojisi

Bir şehirden başka şehre kargo gönderiyorsun:

- Her aktarma merkezi = Hop
- Yol planı = Routing
- Alıcı şehir/adres = Destination IP

## Bunu neden öğreniyoruz?

İnternette veri bir noktadan diğerine router'lar üzerinden gider. Siber güvenlikte traceroute, routing, firewall, NAT ve IP analizi bu katmana dayanır.

> HATIRLA: Layer 3 = IP + Routing + Router

## KARMAŞTIRMA!

| Data Link Layer | Network Layer |
|---|---|
| MAC ile ilgilenir | IP ile ilgilenir |
| Yerel ağ seviyesinde çalışır | Ağlar arası iletişim sağlar |
| Switch ağırlıklıdır | Router ağırlıklıdır |

## Kendini Test Et

Soru 1: Network Layer hangi katmandır?  
Cevap: 3. katman.

Soru 2: Network Layer'ın en önemli protokolü nedir?  
Cevap: IP.

Soru 3: Hop nedir?  
Cevap: Paketin geçtiği her router/adım.

---

# 15. IP Protocol, IPv4 ve IPv6

## IP nedir?

IP (Internet Protocol), cihazların ağ üzerinde adreslenmesini ve paketlerin yönlendirilmesini sağlar.

## IPv4 nedir?

IPv4, 32 bitlik adresleme yapısıdır.

Örnek:

```text
85.171.144.10
```

IPv4 dört oktetten oluşur:

```text
8 bit + 8 bit + 8 bit + 8 bit = 32 bit
```

Her oktet 0-255 arasında değer alır.

## IPv4 neden yetersiz?

IPv4 teorik olarak yaklaşık 4.3 milyar adres üretir. Günümüzde telefonlar, bilgisayarlar, sunucular, IoT cihazları ve kurum ağları düşünüldüğünde bu sayı yetersizdir.

## IPv6 nedir?

IPv6, IPv4 adres yetersizliğini çözmek için geliştirilmiştir. Çok daha büyük adres alanı sağlar.

## Bunu neden öğreniyoruz?

IP adresleme bilmeden subnetting, NAT, routing, firewall rule yazımı ve pentest ağ keşfi anlaşılamaz.

> HATIRLA: IPv4 = 32 bit. IPv6 = çok daha geniş adres alanı.

## KARMAŞTIRMA!

| IPv4 | IPv6 |
|---|---|
| 32 bit | 128 bit |
| Noktalı decimal gösterim | Hexadecimal gösterim |
| Adres sayısı sınırlı | Çok geniş adres alanı |

## Kendini Test Et

Soru 1: IPv4 kaç bittir?  
Cevap: 32 bit.

Soru 2: IPv4 kaç oktetten oluşur?  
Cevap: 4 oktet.

Soru 3: Bir oktet hangi aralıkta değer alır?  
Cevap: 0-255.

---

# 16. TTL ve Routing

## TTL nedir?

TTL (Time To Live), paketin ağda sonsuza kadar dolaşmasını engelleyen sayaçtır. Her router geçişinde TTL değeri 1 azalır. TTL sıfır olursa paket düşürülür.

## Ders örneği

Ping çıktısında TTL görülebilir:

```bash
ping google.com
```

Windows sistemlerde başlangıç TTL değeri genelde 128 olabilir. Linux/macOS sistemlerde genelde 64 olabilir. Network cihazlarında 255 görülebilir.

## Traceroute / Tracert

Paketin hangi router'lardan geçtiğini görmek için kullanılır.

Windows:

```bash
tracert tryhackme.com
```

Linux/macOS:

```bash
traceroute tryhackme.com
```

## Günlük hayat analojisi

Bir kargo için "en fazla 10 aktarma merkezi gezsin" kuralı koymak gibidir. 10 aktarmada teslim edilemezse kargo iptal edilir.

## Bunu neden öğreniyoruz?

TTL ve traceroute, ağ sorunlarını tespit etmekte kritik araçlardır. Ayrıca hedef sistemin işletim sistemi hakkında dolaylı fikir verebilir.

> HATIRLA: TTL her hop'ta azalır. TTL biterse paket düşer.

## KARMAŞTIRMA!

| TTL | Hop |
|---|---|
| Paketin kalan yaşam sayacı | Paketin geçtiği router/adım |
| Azalır | Sayılır |
| Sıfırlanınca paket düşer | Rota analizinde kullanılır |

## Kendini Test Et

Soru 1: TTL ne işe yarar?  
Cevap: Paketin sonsuz döngüde kalmasını engeller.

Soru 2: TTL her router'da ne olur?  
Cevap: 1 azalır.

Soru 3: Tracert ne gösterir?  
Cevap: Paketin geçtiği hop/router noktalarını.

---

# 17. Private IP, Public IP ve NAT

## Private IP nedir?

Yerel ağ içinde kullanılan özel IP adresleridir.

Private IP blokları:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

## Public IP nedir?

İnternette görünen genel IP adresidir. Evdeki veya şirketteki router/modem dış dünyaya public IP ile çıkar.

## NAT nedir?

NAT (Network Address Translation), private IP'lerin public IP üzerinden internete çıkmasını sağlar.

## Günlük hayat analojisi

Bir apartmanda herkesin kendi daire numarası vardır. Ama dışarıdan bakıldığında tek bina adresi görünür.

- Daire numarası = Private IP
- Bina adresi = Public IP
- Apartman görevlisi/yönlendirme = NAT

## Bunu neden öğreniyoruz?

IPv4 adres yetersizliğinin pratik çözümü NAT'tır. Ayrıca firewall, port forwarding, VPN ve iç/dış ağ ayrımı NAT bilgisi olmadan anlaşılamaz.

> HATIRLA: İç ağ = Private IP. İnternet = Public IP. Dönüşüm = NAT.

## KARMAŞTIRMA!

| Private IP | Public IP |
|---|---|
| Yerel ağ içinde kullanılır | İnternette görünür |
| Aynı private IP farklı evlerde olabilir | Public IP benzersiz olmalıdır |
| Router arkasındadır | ISP tarafından verilir |

## Kendini Test Et

Soru 1: 192.168.1.10 private IP midir?  
Cevap: Evet.

Soru 2: NAT ne işe yarar?  
Cevap: Private IP'leri public IP üzerinden internete çıkarır.

Soru 3: Public IP'yi genelde kim verir?  
Cevap: ISP, yani internet servis sağlayıcı.

---

# 18. Loopback ve APIPA

## Loopback nedir?

127.0.0.1, cihazın kendi kendisiyle konuşması için kullanılan adrestir. Diğer adı localhost'tur.

Geliştiriciler web uygulamalarını test ederken sık kullanır.

## APIPA nedir?

DHCP'den IP alamayan cihaz, kendisine geçici olarak şu bloktan IP verebilir:

```text
169.254.x.x
```

Bu APIPA adresidir.

## Günlük hayat analojisi

Loopback: Kendi kendine not yazmak gibi.

APIPA: Resmi adres alamayınca geçici masa numarası vermek gibi.

## Bunu neden öğreniyoruz?

IP sorunlarını teşhis ederken 127.0.0.1 ve 169.254.x.x adresleri çok şey söyler.

> HATIRLA: 127.0.0.1 = Ben kendim. 169.254.x.x = DHCP'den IP alamadım.

## KARMAŞTIRMA!

| Adres | Anlamı |
|---|---|
| 127.0.0.1 | Loopback / localhost |
| 169.254.x.x | APIPA / geçici otomatik IP |
| 192.168.x.x | Private IP |

## Kendini Test Et

Soru 1: 127.0.0.1 neyi ifade eder?  
Cevap: Cihazın kendisini.

Soru 2: 169.254.x.x ne zaman görülür?  
Cevap: DHCP'den IP alınamazsa.

Soru 3: localhost ne demektir?  
Cevap: Yerel cihazın kendisi.

---

# 19. IP Sınıfları ve CIDR Girişi

## IP sınıfları

| Sınıf | Aralık | Kullanım |
|---|---|---|
| A | 1-126 | Büyük ağlar |
| B | 128-191 | Orta ağlar |
| C | 192-223 | Küçük ağlar |
| D | 224-239 | Multicast |
| E | 240-255 | Araştırma/geliştirme |

## CIDR nedir?

CIDR (Classless Inter-Domain Routing), subnet mask'i kısa yazma yöntemidir.

Örnek:

```text
255.255.255.0
```

bunun CIDR karşılığı:

```text
/24
```

Çünkü 255.255.255.0 içinde 24 tane 1 biti vardır.

## Örnek

```text
192.168.1.0/24
```

Bu ifade şunu anlatır:

- Ağ: 192.168.1.0
- Subnet mask: 255.255.255.0
- CIDR: /24

## Bunu neden öğreniyoruz?

Subnetting, ağ bölme, firewall kuralı yazma, VPN tanımı ve pentest scope belirleme CIDR bilgisi olmadan yapılamaz.

> HATIRLA: /24 = 255.255.255.0

## KARMAŞTIRMA!

| Gösterim | Anlamı |
|---|---|
| 255.255.255.0 | Subnet mask |
| /24 | CIDR gösterimi |
| 192.168.1.0/24 | Ağ bloğu |

## Kendini Test Et

Soru 1: /24 neye karşılık gelir?  
Cevap: 255.255.255.0.

Soru 2: CIDR neden kullanılır?  
Cevap: Subnet mask'i kısa ve pratik göstermek için.

Soru 3: 10.0.0.0/8 private IP bloğu mudur?  
Cevap: Evet.

---

# GENEL TEKRAR VE ÖZET

Bu derste önce Data Link Layer tekrar edildi; MAC adresi, Ethernet Frame, ARP, broadcast ve VLAN konuları işlendi. Sonra Wireless LAN tarafında SSID, BSSID, ESSID, Wi-Fi standartları ve kablosuz saldırılar anlatıldı. Dersin sonunda Network Layer konusuna geçildi; IP protokolü, IPv4, IPv6, TTL, routing, NAT, private/public IP, loopback, APIPA ve CIDR kavramlarına giriş yapıldı.

## Tüm konular tek cümleyle

Ağ iletişiminde veri, OSI katmanlarında paketlenerek ilerler; yerel ağda MAC ve ARP, ağlar arası iletişimde IP ve routing, kurumsal tasarımda VLAN/NAT/Wi-Fi güvenliği kritik rol oynar.

## En kritik 10 bilgi

1. Layer 2'nin ana konusu MAC'tir.
2. Layer 3'ün ana konusu IP'dir.
3. Layer 4'ün ana konusu porttur.
4. ARP, IP'den MAC bulur.
5. Broadcast herkese gider.
6. Router broadcast domain'i böler.
7. VLAN, ağı sanal olarak parçalara ayırır.
8. SSID Wi-Fi adıdır.
9. NAT, private IP'leri public IP ile internete çıkarır.
10. TTL, paketin sonsuza kadar dolaşmasını engeller.
