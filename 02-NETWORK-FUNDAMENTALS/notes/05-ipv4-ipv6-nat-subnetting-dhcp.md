## ADIM 1 - Ana Başlıklar

<div align="center">

![Ders İnfografiği](../assets/05-network-fundamentals-backbone.png)

</div>

---


Bu derste geçen ana konular:

1. Network dersinin amacı
2. Network nedir?
3. Internet nedir?
4. Protokol nedir?
5. OSI Modeli ve TCP/IP Modeli
6. Encapsulation / Decapsulation
7. Data Link Layer
8. MAC Address
9. Ethernet, Wireless, Token Ring
10. ARP Protocol
11. Broadcast / Unicast / Multicast
12. Broadcast Domain / Collision Domain
13. VLAN
14. Wireless LAN
15. Wireless saldırıları
16. Network Layer
17. IP Protocol
18. IPv4 / IPv6
19. Private IP / Public IP
20. NAT
21. CIDR ve subnet mantığı

---

# BÖLÜM 1 - Bu Network Dersini Neden Öğreniyoruz?

## Bu nedir?

Network bilgisi, siber güvenliğin altyapı bilgisidir. Eğitmen derste açıkça şunu vurguluyor:

> Amaç öğrenciyi Network Admin yapmak değil; firewall, EDR, saldırı analizi, log inceleme ve güvenlik modüllerini anlayacak temel network seviyesine getirmektir.

## Günlük hayat analojisi

Bir binanın elektrik tesisatını çekmeyeceksin ama binada elektrik arızası olduğunda hangi panoya bakacağını bilmen gerekir.

Network de böyledir:

- Kabloyu sen çekmeyebilirsin.
- Router'ı sen kurmayabilirsin.
- Ama saldırı geldiğinde trafiğin nereden geçtiğini anlamak zorundasın.

## Bunu neden öğreniyoruz?

Çünkü ileride:

- Firewall kurallarını anlayacaksın.
- EDR loglarını yorumlayacaksın.
- Saldırının hangi katmanda gerçekleştiğini analiz edeceksin.
- IP, MAC, DNS, ARP, TCP/UDP gibi kavramları güvenlik olaylarında kullanacaksın.

> **HATIRLA**  
> Siber güvenlikte network bilmeyen kişi, saldırının nereden geldiğini değil sadece "bir şey oldu"yu görür.

## KARMAŞTIRMA!

| Kavram | Ne değildir? | Doğru anlamı |
|---|---|---|
| Network öğrenmek | Network admin olmak değildir | Güvenlik analizi için altyapıyı anlamaktır |
| OSI Modeli | Her gün birebir kullanılan operasyon modeli değildir | Eğitim ve analiz için referans modeldir |
| TCP/IP Modeli | Sadece teori değildir | Günümüzde fiili kullanılan modeldir |

## Kendini Test Et

**1. Bu dersin amacı öğrenciyi network mühendisi yapmak mı?**  
Hayır. Amaç, siber güvenlikte kullanılacak temel network mantığını kazandırmaktır.

**2. Network bilgisi firewall'da neden gerekir?**  
Alt ağları, IP yapılarını ve trafik yönünü anlamak için gerekir.

**3. OSI Modeli neden öğrenilir?**  
Ağ trafiğini katman katman analiz etmek ve saldırının hangi seviyede gerçekleştiğini yorumlamak için.

---

# BÖLÜM 2 - Network Nedir?

## Bu nedir?

Network, birbirleriyle haberleşebilen en az iki cihazın oluşturduğu yapıdır.

Örnek:

- İki bilgisayarın kabloyla bağlanması
- Evde telefon, laptop, TV ve modemden oluşan yapı
- Şirket içindeki bilgisayarlar, serverlar, yazıcılar

## Günlük hayat analojisi

Bir insan kaynakları uzmanının iş çevresi vardır. Satın alma personelinin tedarikçi ağı vardır. Bunlara da "network" denebilir.

Bilgisayar dünyasında network:

> Cihazların birbirleriyle konuşabildiği dijital iletişim ortamıdır.

## Bunu neden öğreniyoruz?

Çünkü saldırılar çoğu zaman tek bir cihazda kalmaz. Ağ üzerinden yayılır.

Örneğin:

- Zararlı yazılım diğer bilgisayarlara geçebilir.
- Saldırgan bir VLAN'dan diğer sisteme geçmeye çalışabilir.
- ARP spoofing ile trafik dinlenebilir.

> **HATIRLA**  
> Network = Haberleşebilen cihazlar topluluğu.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| Network | Cihazların haberleştiği yapı |
| Internet | Network'lerin network'ü |
| LAN | Yerel ağ |
| WAN | Geniş alan ağı |

## Kendini Test Et

**1. En basit network kaç cihazla oluşur?**  
En az iki cihazla.

**2. Network sadece bilgisayarlar arasında mı olur?**  
Hayır. Telefon, yazıcı, kamera, server, router gibi cihazlar da network parçası olabilir.

**3. Siber güvenlikte network neden kritiktir?**  
Çünkü saldırılar, veri akışı ve savunma mekanizmaları network üzerinden işler.

---

# BÖLÜM 3 - Internet Nedir?

## Bu nedir?

Internet, "Network of Networks" yani ağların ağıdır.

Evindeki ağ, şirket ağı, üniversite ağı, servis sağlayıcı ağı ve veri merkezleri birbirine bağlanınca internet oluşur.

## Derste geçen özel örnekler

- ARPANET
- MILNET
- Amerikan askeriyesi
- Amerikan Savunma Bakanlığı
- CERN / İsviçre iddiası
- Dan Brown
- Digital Fortress / Dijital Kale
- Melekler ve Şeytanlar
- Elon Musk Starlink
- 1980 sonrası Personal Computer yaygınlaşması
- İlk solucan / worm örneği 1986 veya 1988 olarak anılıyor
- 2019-2020 civarı 4.1 milyar internet kullanıcısı / dünya nüfusunun yaklaşık %55'i

## Günlük hayat analojisi

Mahalle yolları LAN gibidir. Şehirler arası yollar WAN gibidir. Tüm ülkeleri bağlayan otoyol sistemi internet gibidir.

## Bunu neden öğreniyoruz?

Çünkü saldırılar artık sadece yerel ağda kalmaz. Global internet altyapısı üzerinden gelir:

- DNS sorguları
- Web bağlantıları
- VPN
- Cloud servisleri
- Mail serverlar
- Hosting şirketleri
- ISP altyapıları

> **HATIRLA**  
> Internet = Ağların birbirine bağlanmış küresel hali.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| LAN | Ev/ofis içi yerel ağ |
| Internet | Dünyadaki ağların birleşimi |
| ISP | Seni internete bağlayan servis sağlayıcı |
| Router | Ağlar arasında yönlendirme yapan cihaz |

## Kendini Test Et

**1. Internet neden "Network of Networks" olarak adlandırılır?**  
Çünkü birçok farklı ağın birleşiminden oluşur.

**2. ARPANET neye dönüşmüştür?**  
Gelişerek bugünkü internetin temelini oluşturmuştur.

**3. Starlink neden önemli örnektir?**  
Klasik kablo altyapısı olmadan uydu üzerinden internet erişimi sağlayabildiği için.

---

# BÖLÜM 4 - Protokol Nedir?

## Bu nedir?

Protocol, cihazların haberleşirken uyması gereken kurallar bütünüdür.

Derste geçen ifade:

> Protocol = Set of rules.

## Günlük hayat analojisi

İki insan konuşurken ortak dil gerekir. Sen Türkçe konuşurken karşı taraf seni anlamıyorsa iletişim olmaz.

Bilgisayarlar da ortak kurallar olmadan haberleşemez.

## Örnek protokoller

- IP - Internet Protocol
- TCP - Transmission Control Protocol
- UDP - User Datagram Protocol
- ICMP - Internet Control Message Protocol
- ARP - Address Resolution Protocol
- DNS - Domain Name System
- HTTP / HTTPS
- SMTP
- POP3
- IMAP
- FTP
- TFTP
- SNMP
- IPsec

## Bunu neden öğreniyoruz?

Siber güvenlikte saldırılar çoğu zaman protokol zafiyetleri, yanlış yapılandırmalar veya protokol davranışları üzerinden yapılır.

Örnek:

- ARP Spoofing
- DNS Manipulation
- TCP SYN Flood
- ICMP tunneling
- HTTP saldırıları
- SMB saldırıları

> **HATIRLA**  
> Protokol yoksa iletişim yoktur.

## KARMAŞTIRMA!

| Kavram | Görevi |
|---|---|
| IP | Adresleme ve yönlendirme |
| TCP | Güvenilir veri iletimi |
| UDP | Hızlı ama garantisiz veri iletimi |
| DNS | Alan adını IP'ye çevirir |
| ARP | IP'ye karşılık MAC adresini bulur |

## Kendini Test Et

**1. Protokol ne demektir?**  
Cihazların haberleşirken uyması gereken kurallar bütünüdür.

**2. IP'nin görevi nedir?**  
Paketi kaynaktan hedefe yönlendirmektir.

**3. DNS ne yapar?**  
Alan adını IP adresine çevirir.

---

# BÖLÜM 5 - OSI Modeli ve TCP/IP Modeli

## Bu nedir?

OSI Modeli, ağ iletişimini 7 katmana ayıran referans modeldir.

TCP/IP Modeli ise günümüzde daha pratik kullanılan 4 katmanlı modeldir.

## OSI Katmanları

1. Physical Layer
2. Data Link Layer
3. Network Layer
4. Transport Layer
5. Session Layer
6. Presentation Layer
7. Application Layer

## TCP/IP Katmanları

1. Network Access
2. Internet
3. Transport
4. Application

## Günlük hayat analojisi

Bir kargo gönderiyorsun:

- Ürün hazırlanır.
- Paketlenir.
- Adres yazılır.
- Kargo aracına verilir.
- Şubelerden geçer.
- Alıcıya ulaşır.
- Paket açılır.

OSI modeli de verinin bilgisayarda böyle katman katman hazırlanmasını anlatır.

## Bunu neden öğreniyoruz?

Çünkü saldırı analizi yaparken şu soruları sorarsın:

- Sorun kabloda mı? Physical
- MAC seviyesinde mi? Data Link
- IP yönlendirmesinde mi? Network
- TCP/UDP seviyesinde mi? Transport
- Uygulamada mı? Application

> **HATIRLA**  
> OSI öğrenmek ezber için değil, olayları katman katman analiz etmek içindir.

## KARMAŞTIRMA!

| OSI Katmanı | Ana kavram |
|---|---|
| Physical | Bit, kablo, sinyal |
| Data Link | MAC, frame, switch |
| Network | IP, router, packet |
| Transport | TCP, UDP, segment |
| Application | HTTP, DNS, SMTP |

## Kendini Test Et

**1. OSI kaç katmandır?**  
7 katmandır.

**2. TCP/IP modeli kaç katmandır?**  
4 katmandır.

**3. Router hangi katmanda çalışır?**  
Network Layer, yani 3. katmanda.

---

# BÖLÜM 6 - Encapsulation ve Decapsulation

## Bu nedir?

Encapsulation, verinin gönderilirken her katmanda yeni başlıklarla paketlenmesidir.

Decapsulation, alıcı tarafta bu başlıkların sırayla açılmasıdır.

## Sıralama

Gönderirken:

1. Data
2. Segment
3. Packet
4. Frame
5. Bits

Alırken:

1. Bits
2. Frame
3. Packet
4. Segment
5. Data

## Günlük hayat analojisi

Bir hediye gönderiyorsun:

- Hediyeyi kutuya koyarsın.
- Kutuyu paketlersin.
- Üzerine adres yazarsın.
- Kargo poşetine koyarsın.
- Kargoya verirsin.

Alıcı da ters sırayla açar.

## Bunu neden öğreniyoruz?

Wireshark, firewall logları, packet capture ve saldırı analizinde bu yapı doğrudan karşına çıkar.

> **HATIRLA**  
> Her katman sadece kendi başlığını okur.

## KARMAŞTIRMA!

| Birim | Katman |
|---|---|
| Segment | Transport |
| Packet | Network |
| Frame | Data Link |
| Bits | Physical |

## Kendini Test Et

**1. Encapsulation nedir?**  
Verinin katman katman başlık eklenerek paketlenmesidir.

**2. Frame hangi katmanda oluşur?**  
Data Link Layer'da.

**3. Packet hangi katmanda oluşur?**  
Network Layer'da.

---

# BÖLÜM 7 - Data Link Layer

## Bu nedir?

Data Link Layer, OSI modelinin 2. katmanıdır. Yerel ağdaki cihazların MAC adresleri üzerinden haberleşmesini sağlar.

## Alt bölümleri

1. LLC - Logical Link Control
2. MAC - Media Access Control

## Görevleri

- Frame oluşturur.
- MAC adreslerini kullanır.
- Fiziksel katman ile Network katmanı arasında köprü kurar.
- Frame Check Sequence ile hata kontrolü yapar.

## Günlük hayat analojisi

Apartman içindeki daire numaraları gibi düşün. Aynı apartmandaki kişiye posta gönderirken şehir/ülke bilgisine gerek yoktur; daire numarası yeterlidir.

Yerel ağda da MAC adresi bu görevi görür.

## Bunu neden öğreniyoruz?

Çünkü yerel ağ saldırılarında MAC, ARP ve switch davranışı çok önemlidir.

Örnek:

- ARP Spoofing
- MAC Flooding
- Switch hijacking
- VLAN hopping

> **HATIRLA**  
> Aynı ağdaki cihazlar MAC adresiyle haberleşir.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| MAC | Fiziksel adres |
| IP | Mantıksal/sanal adres |
| Frame | Data Link veri birimi |
| Packet | Network veri birimi |

## Kendini Test Et

**1. Data Link Layer kaçıncı katmandır?**  
2. katmandır.

**2. Bu katmanda hangi adres önemlidir?**  
MAC Address.

**3. LLC ne yapar?**  
Üst katmanla iletişim kurar.

---

# BÖLÜM 8 - MAC Address

## Bu nedir?

MAC Address, ağ kartına üretici tarafından verilen fiziksel kimlik numarasıdır.

## Teknik bilgi

- 48 bittir.
- Hexadecimal gösterilir.
- İlk 24 bit üreticiyi tanımlar.
- Son 24 bit cihazı benzersiz yapar.

Örnek format:

```text
00:2A:3F:2A:1C:00
```

## Günlük hayat analojisi

MAC adresi, cihazın fabrika çıkışlı kimlik numarası gibidir.

## Bunu neden öğreniyoruz?

Çünkü yerel ağda cihazlar MAC adresiyle bulunur. ARP, switch ve frame yapısı MAC üzerine çalışır.

## Güvenlik notu

Fiziksel MAC değişmez ama sahte MAC gösterilebilir. Buna MAC Spoofing denir.

> **HATIRLA**  
> MAC fiziksel kimliktir; IP ise ağdaki mantıksal adrestir.

## KARMAŞTIRMA!

| MAC | IP |
|---|---|
| Fiziksel adres | Mantıksal adres |
| Data Link Layer | Network Layer |
| Yerel ağda kullanılır | Ağlar arası yönlendirmede kullanılır |
| 48 bit | IPv4 32 bit, IPv6 128 bit |

## Kendini Test Et

**1. MAC adres kaç bittir?**  
48 bittir.

**2. MAC adres değiştirilebilir mi?**  
Fiziksel olarak hayır; ama spoofing yapılabilir.

**3. MAC hangi katmanda çalışır?**  
Data Link Layer.

---

# BÖLÜM 9 - ARP Protocol

## Bu nedir?

ARP, IP adresini bildiğimiz bir cihazın MAC adresini öğrenmek için kullanılır.

Açılımı:

**Address Resolution Protocol**

## Çalışma mantığı

1. Bilgisayar hedef IP'yi bilir.
2. MAC adresini bilmez.
3. ARP Request gönderir.
4. Switch bunu yayınlar.
5. Hedef cihaz cevap verir.
6. MAC adresi ARP Table'a yazılır.

## Komutlar

Windows:

```cmd
arp -a
arp /?
```

Linux:

```bash
arp -a
arp --help
```

## Günlük hayat analojisi

Bir okulda öğrencinin adını biliyorsun ama sınıfını bilmiyorsun.

Koridora çıkıp soruyorsun:

> "Ahmet burada mı?"

Ahmet cevap veriyor:

> "Ben buradayım, sınıfım 3B."

ARP de budur.

## Bunu neden öğreniyoruz?

Çünkü ARP saldırıları yerel ağlarda çok yaygındır.

Örnek:

- ARP Spoofing
- Man-in-the-Middle
- Trafik dinleme
- Sahte gateway oluşturma

> **HATIRLA**  
> ARP, IP'den MAC adresi bulur.

## KARMAŞTIRMA!

| ARP | DNS |
|---|---|
| IP -> MAC bulur | Domain -> IP bulur |
| Yerel ağda çalışır | Internet erişiminde kritiktir |
| Layer 2/3 sınırında önemlidir | Application seviyesinde kullanılır |

## Kendini Test Et

**1. ARP ne işe yarar?**  
IP adresinden MAC adresi bulur.

**2. ARP Request kime gider?**  
Broadcast olarak ağdaki cihazlara gider.

**3. ARP Table ne tutar?**  
IP ve MAC eşleşmelerini tutar.

---

# BÖLÜM 10 - Broadcast, Unicast, Multicast

## Bu nedir?

Ağda veri gönderme biçimleridir.

## Türler

| Tür | Anlam |
|---|---|
| Unicast | Tek cihaza gönderim |
| Multicast | Belirli gruba gönderim |
| Broadcast | Ağdaki herkese gönderim |

## Günlük hayat analojisi

- Unicast: Bir kişiye özel konuşmak
- Multicast: Belirli öğrenci grubuna konuşmak
- Broadcast: Tüm sınıfa seslenmek

## Bunu neden öğreniyoruz?

Çünkü ARP gibi protokoller broadcast kullanır. Fazla broadcast trafiği ağı yavaşlatır.

> **HATIRLA**  
> Broadcast herkese gider; multicast sadece ilgili gruba gider.

## Kendini Test Et

**1. Broadcast nedir?**  
Ağdaki tüm cihazlara gönderimdir.

**2. Unicast nedir?**  
Tek hedef cihaza gönderimdir.

**3. IPTV hangi modele örnek olabilir?**  
Multicast.

---

# BÖLÜM 11 - Broadcast Domain ve Collision Domain

## Bu nedir?

## Broadcast Domain

Bir broadcast mesajının ulaşabildiği ağ alanıdır.

## Collision Domain

Veri çakışmasının yaşanabileceği ağ alanıdır.

## Günlük hayat analojisi

Broadcast Domain: Bir okulda anonsun duyulduğu alan.  
Collision Domain: Dar koridorda iki kişinin çarpışabileceği alan.

## Cihazlara göre

| Cihaz | Davranış |
|---|---|
| Hub | Gelen veriyi herkese gönderir |
| Switch | MAC adresine göre yönlendirir |
| Router | Broadcast domain'i ayırır |

## Bunu neden öğreniyoruz?

Çünkü büyük ağlarda broadcast trafiği performansı düşürür, güvenlik riskini artırır.

> **HATIRLA**  
> Router'ın her portu ayrı broadcast domain kabul edilir.

## Kendini Test Et

**1. Hub akıllı cihaz mıdır?**  
Hayır. Gelen paketi herkese gönderir.

**2. Switch neye göre karar verir?**  
MAC adresine göre.

**3. Router broadcast domain'i böler mi?**  
Evet.

---

# BÖLÜM 12 - VLAN

## Bu nedir?

VLAN, fiziksel olarak aynı switch üzerinde mantıksal olarak ayrı ağlar oluşturmaktır.

Açılımı:

**Virtual Local Area Network**

## Neden kullanılır?

- Trafiği azaltır.
- Güvenliği artırır.
- Yönetimi kolaylaştırır.
- Departmanları ayırır.
- Maliyeti düşürür.

## Derste geçen örnek

Bir binada:

- Engineering
- Marketing
- Accounting
- R&D

farklı katlarda olabilir ama VLAN ile aynı departman kendi içinde mantıksal ağda tutulabilir.

## Günlük hayat analojisi

Aynı binada farklı şirketlerin ofisleri olabilir. Fiziksel bina aynı, ama giriş kartları ve yetki alanları ayrıdır.

## Siber güvenlik açısından

VLAN yoksa saldırgan bir bilgisayarı ele geçirince tüm ağa yayılabilir.

VLAN varsa saldırgan sadece bulunduğu segmentte kalabilir.

> **HATIRLA**  
> VLAN = Büyük ağı küçük ve kontrollü parçalara bölmek.

## KARMAŞTIRMA!

| LAN | VLAN |
|---|---|
| Fiziksel yerel ağ | Mantıksal/sanal yerel ağ |
| Ayrı switch gerekebilir | Aynı switch üzerinde ayrım yapılabilir |
| Daha basit | Daha güvenli ve yönetilebilir |

## Kendini Test Et

**1. VLAN ne işe yarar?**  
Ağı mantıksal parçalara böler.

**2. VLAN güvenliği nasıl artırır?**  
Bir segmentteki cihazların diğer segmentlere doğrudan erişmesini engeller.

**3. VLAN için hangi switch gerekir?**  
Layer 3 özellikli veya VLAN destekli switch gerekir.

---

# BÖLÜM 13 - Wireless LAN

## Bu nedir?

Wireless LAN, cihazların kablo olmadan radyo sinyalleriyle yerel ağa bağlanmasını sağlar.

Standardı:

**IEEE 802.11**

## Kavramlar

| Kavram | Anlam |
|---|---|
| SSID | Kablosuz ağ adı |
| BSSID | Access Point MAC adresi |
| ESSID | Genişletilmiş kablosuz ağ yapısı |

## 2.4 GHz vs 5 GHz

| Özellik | 2.4 GHz | 5 GHz |
|---|---|---|
| Menzil | Daha uzun | Daha kısa |
| Hız | Daha düşük | Daha yüksek |
| Duvar geçişi | Daha iyi | Daha zayıf |
| Parazit | Daha fazla | Daha az |

## Günlük hayat analojisi

SSID, kafenin tabelası gibidir.  
BSSID, o tabelayı taşıyan fiziksel cihazın kimliğidir.  
ESSID, zincir kafenin tüm şubelerinde aynı Wi-Fi adını kullanması gibidir.

## Bunu neden öğreniyoruz?

Kablosuz ağlar saldırıya açık yüzeylerden biridir.

## Wireless saldırı türleri

- Denial of Service
- Rogue Access Point
- Evil Twin
- Trafik dinleme
- Zayıf şifreleme saldırıları
- Yanlış yapılandırma saldırıları

> **HATIRLA**  
> Kablosuz ağ pratik ama kablolu ağ kadar stabil ve güvenli değildir.

## Kendini Test Et

**1. SSID nedir?**  
Kablosuz ağın görünen adıdır.

**2. BSSID nedir?**  
Access Point'in MAC adresidir.

**3. Rogue Access Point riski nedir?**  
Saldırgan sahte ağ kurarak kullanıcı trafiğini dinleyebilir.

---

# BÖLÜM 14 - Network Layer

## Bu nedir?

Network Layer, OSI modelinin 3. katmanıdır. IP adresleme ve yönlendirme burada gerçekleşir.

## Görevleri

- Source IP ekler.
- Destination IP ekler.
- Paketi yönlendirir.
- Router'lar bu katmanda çalışır.
- Connectionless iletişim sağlar.

## Günlük hayat analojisi

Kargo paketinde şehir, ilçe, mahalle adresi yazması gibi.

MAC apartman içindeki daire numarasıysa, IP şehirler arası adrestir.

## Bunu neden öğreniyoruz?

Çünkü internet iletişimi IP üzerinden çalışır.

> **HATIRLA**  
> Network Layer = IP ve routing katmanı.

## Kendini Test Et

**1. Network Layer kaçıncı katmandır?**  
3. katmandır.

**2. Bu katmanda hangi adres kullanılır?**  
IP adresi.

**3. Router hangi katmanda çalışır?**  
Network Layer'da.

---

# BÖLÜM 15 - IPv4

## Bu nedir?

IPv4, 32 bitlik IP adresleme sistemidir.

Örnek:

```text
192.168.1.10
```

## Yapısı

- 4 oktetten oluşur.
- Her oktet 8 bittir.
- Her oktet 0-255 arası değer alır.

## Toplam adres kapasitesi

Yaklaşık:

```text
2^32 ~= 4.3 milyar adres
```

Ama pratikte tamamı kullanılamaz.

## Günlük hayat analojisi

IPv4 eski telefon numarası sistemi gibidir. Başta yeterli görünür ama herkesin birden fazla cihazı olunca yetmez.

## Bunu neden öğreniyoruz?

Çünkü hala dünyada yaygın kullanılan IP sistemi IPv4'tür.

> **HATIRLA**  
> IPv4 = 32 bit = 4 oktet.

## Kendini Test Et

**1. IPv4 kaç bittir?**  
32 bittir.

**2. Bir oktet kaç bittir?**  
8 bittir.

**3. Bir oktet en fazla kaç olabilir?**  
255.

---

# BÖLÜM 16 - IPv6

## Bu nedir?

IPv6, IPv4 adreslerinin yetersiz kalması nedeniyle geliştirilmiş 128 bitlik adresleme sistemidir.

## Özellikleri

- 128 bittir.
- Hexadecimal gösterilir.
- Çok büyük adres alanı sağlar.
- NAT ihtiyacını azaltır.
- Public/private ayrımını büyük ölçüde gereksiz hale getirir.
- Başlığı IPv4'e göre daha sade tasarlanmıştır.
- IPsec başlangıçta zorunlu düşünülmüş, sonra opsiyonel hale gelmiştir.

## Günlük hayat analojisi

IPv4 küçük bir apartmandaki sınırlı posta kutusu gibidir. IPv6 ise her insana, her cihaza, her sensöre ayrı posta kutusu açabilecek devasa adres sistemidir.

> **HATIRLA**  
> IPv6'nın çıkış sebebi: IPv4 adresleri yetmedi.

## Kendini Test Et

**1. IPv6 kaç bittir?**  
128 bittir.

**2. IPv6 neden çıktı?**  
IPv4 adres kapasitesi yetersiz kaldığı için.

**3. IPv6'da NAT ihtiyacı neden azalır?**  
Her cihaza benzersiz global adres verilebildiği için.

---

# BÖLÜM 17 - Private IP, Public IP ve NAT

## Bu nedir?

## Private IP

İç ağda kullanılan IP adresidir.

Örnek:

```text
192.168.1.10
10.0.0.5
172.16.5.20
```

## Public IP

Dış dünyada seni temsil eden IP adresidir.

## NAT

Private IP'lerin public IP'ye çevrilmesidir.

Açılımı:

**Network Address Translation**

## Private IP aralıkları

| Aralık | Kullanım |
|---|---|
| 10.0.0.0/8 | Büyük ağlar |
| 172.16.0.0/12 | Orta ölçekli ağlar |
| 192.168.0.0/16 | Ev/küçük ofis ağları |

## Özel adresler

| IP | Anlam |
|---|---|
| 127.0.0.1 | Localhost |
| 169.254.x.x | Link-local / APIPA |

## Günlük hayat analojisi

Apartmanda herkesin iç kapı numarası vardır. Ama dışarıdan gelen kargo apartmanın ana adresine gelir.

Private IP = daire numarası  
Public IP = apartmanın dış adresi  
NAT = kapıcı/güvenlik görevlisi

## Bunu neden öğreniyoruz?

Firewall, log analizi ve saldırı takibinde NAT kritik önemdedir.

Bir logda public IP görürsün ama içeride hangi cihazın çıktığını NAT tablosundan anlarsın.

> **HATIRLA**  
> NAT, birçok private IP'yi tek public IP üzerinden internete çıkarır.

## Kendini Test Et

**1. Private IP internete doğrudan çıkar mı?**  
Hayır.

**2. NAT ne yapar?**  
Private IP'yi public IP'ye çevirir.

**3. 192.168.1.5 hangi IP türüdür?**  
Private IP.

---

# BÖLÜM 18 - CIDR

## Bu nedir?

CIDR, subnet mask bilgisini daha kısa ve esnek göstermek için kullanılan yöntemdir.

Açılımı:

**Classless Inter-Domain Routing**

Örnek:

```text
192.168.1.0/24
```

Buradaki `/24`, subnet mask içinde 24 tane 1 olduğunu gösterir.

## Günlük hayat analojisi

Eski sistemde sadece küçük, orta, büyük beden kıyafet vardı. CIDR ise tam ölçüne göre kıyafet dikmek gibidir.

## Neden çıktı?

Eski A, B, C class sistemi IP israfına neden oluyordu.

Örneğin 500 cihaz için B class almak çok büyük israftır. CIDR ile daha uygun boyutta ağ oluşturulur.

> **HATIRLA**  
> CIDR = IP adreslerini daha esnek ve verimli bölme yöntemi.

## Kendini Test Et

**1. CIDR neyi gösterir?**  
Subnet mask içindeki 1 bitlerinin sayısını gösterir.

**2. /24 neye denk gelir?**  
255.255.255.0 subnet maskesine.

**3. CIDR neden önemlidir?**  
IP israfını azaltır ve esnek subnet tasarımı sağlar.

---

# GENEL TEKRAR VE ÖZET

## Tek cümlelik genel özet

Bu ders, cihazların ağda nasıl haberleştiğini; MAC, IP, ARP, DNS, VLAN, Wireless, NAT, IPv4/IPv6 ve CIDR gibi temel kavramlarla birlikte siber güvenlik bakış açısıyla anlamayı sağlar.

## Kritik kavram özeti

| Kavram | Tek cümle |
|---|---|
| Network | Haberleşebilen cihazlar topluluğudur. |
| Internet | Ağların ağıdır. |
| Protocol | Cihazların konuşma kurallarıdır. |
| OSI | Ağ iletişimini 7 katmanda açıklar. |
| TCP/IP | Günümüzde kullanılan pratik ağ modelidir. |
| Encapsulation | Verinin katman katman paketlenmesidir. |
| MAC | Cihazın fiziksel ağ kimliğidir. |
| IP | Cihazın ağ üzerindeki mantıksal adresidir. |
| ARP | IP'den MAC bulur. |
| DNS | Domain'den IP bulur. |
| VLAN | Ağı mantıksal parçalara böler. |
| NAT | Private IP'leri public IP'ye çevirir. |
| IPv4 | 32 bitlik eski/yaygın IP sistemidir. |
| IPv6 | 128 bitlik yeni nesil IP sistemidir. |
| CIDR | IP adreslerini esnek bölme yöntemidir. |

## En kritik güvenlik bağlantısı

Network'ü anlamadan:

- Firewall kuralı doğru yazılmaz.
- EDR alarmı doğru yorumlanmaz.
- Saldırı yolu anlaşılamaz.
- Log analizi yüzeysel kalır.
- VLAN, NAT, DNS, ARP kaynaklı saldırılar doğru çözümlenemez.

**Net gerçek:** Siber güvenlikte network bilgisi "ekstra" değildir; temel zemindir.
