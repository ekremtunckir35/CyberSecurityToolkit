## Ana Ders Haritası

Bu ders tek bir konu değil; **Subnetting -> DHCP -> NAT -> ICMP/Ping/Traceroute -> Wireshark** hattında ilerleyen bütünlüklü bir Network Fundamentals dersidir.

Ana konular:

1. Subnetting tekrar ve IP hesaplama araçları
2. Network Layer / Layer 3
3. IPv4 ve IPv6
4. Private IP / Public IP
5. NAT (Network Address Translation)
6. DHCP ve DORA süreci
7. Default Gateway, DNS, Subnet Mask
8. ICMP, Ping, Traceroute / Tracert
9. Wireshark ile paket analizi
10. Güvenlik perspektifi: Public Wi-Fi, ICMP saldırıları, Firewall

---

# 1. Subnetting Nedir?

## Bu nedir?

**Subnetting**, büyük bir ağı daha küçük alt ağlara bölme işlemidir.

Örnek:

```text
192.168.1.0/24
```

Bu ağ normalde yaklaşık **254 kullanılabilir host IP** verir. Ama bunu departmanlara göre bölebilirsin:

```text
İnsan Kaynakları
Muhasebe
IT
Yönetim
```

## Günlük hayat analojisi

Bir apartmanı düşün.

Apartmanın tamamı büyük ağdır. Daireler ise subnet'tir.

```text
Apartman = Ana Network
Daire 1 = Subnet 1
Daire 2 = Subnet 2
Daire 3 = Subnet 3
```

Herkes aynı apartmanda olabilir ama her daire kendi içinde ayrıdır.

## Bunu neden öğreniyoruz?

Çünkü gerçek şirket ağlarında tüm cihazlar tek bir düz ağda bırakılmaz. Ağlar bölünür:

- Yönetim kolaylaşır.
- Broadcast trafiği azalır.
- Güvenlik artar.
- Departmanlar ayrılır.
- Firewall ve ACL kuralları daha kontrollü yazılır.

## Önemli örnek

Eğitmen derste şunu anlattı: **4 bilgisayarlık bir ağ istiyorsan sadece 4 IP yetmez.**

Çünkü ayrıca:

```text
1 Network Address
1 Broadcast Address
4 Host IP
= En az 6 IP gerekir
```

Ama IP blokları 2'nin kuvvetleriyle gider:

```text
2, 4, 8, 16, 32...
```

Bu yüzden **6 IP ihtiyacı için /29 yani 8 IP'lik blok** gerekir.

> **HATIRLA:** Kullanılabilir Host Sayısı = Toplam IP - 2. Çünkü 1 IP network address, 1 IP broadcast address için ayrılır.

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Network Address | Ağın kimliği |
| Broadcast Address | Ağdaki herkese gönderim adresi |
| Host Address | Cihaza verilebilen IP |
| Subnet Mask | Ağ ve host kısmını ayıran yapı |

## Kendini Test Et

**Soru 1:** 4 cihaz için neden 4 IP yetmez?  
**Cevap:** Çünkü network ve broadcast adresleri de gerekir.

**Soru 2:** 6 IP ihtiyacı için neden 8 IP'lik blok gerekir?  
**Cevap:** IP blokları 2'nin kuvvetleriyle ayrılır.

**Soru 3:** Subnetting neden yapılır?  
**Cevap:** Ağı daha yönetilebilir, güvenli ve düzenli hale getirmek için.

---

# 2. Network Layer / Layer 3 Nedir?

## Bu nedir?

**Network Layer**, OSI modelinin **3. katmanıdır**.

Temel görevi:

```text
Paketleri kaynaktan hedefe yönlendirmek
```

Bu katmanda en önemli yapı **IP Address** bilgisidir.

## Günlük hayat analojisi

Bir kargo düşün. Kargo paketinin üzerinde gönderen adresi ve alıcı adresi yazar. Network Layer da veri paketlerine şu bilgileri ekler:

```text
Source IP Address
Destination IP Address
```

## Ne iş yapar?

Network Layer:

- IP adresleme yapar.
- Paketleri yönlendirir.
- Router'lar üzerinden hedefe taşır.
- Transport Layer ile Data Link Layer arasında çalışır.
- Segmentleri paket haline getirir.
- Paketleri alt katmanda frame'e dönüşmek üzere gönderir.

## Connectionless Communication Nedir?

IP protokolü **connectionless** çalışır. Yani IP şunu garanti etmez:

```text
Paket hedefe ulaştı mı?
Sıralı gitti mi?
Eksiksiz gitti mi?
```

IP sadece gönderir.

## Günlük hayat analojisi

Postacı mektubu kutuya bırakır. Ama mektubu alıcı okudu mu, cevap verdi mi, eksik mi geldi, bununla ilgilenmez. IP de böyledir.

> **HATIRLA:** IP umursamaz. TCP kontrol eder. IP paketi gönderir; teslim garantisi Transport Layer'daki TCP gibi protokollerin işidir.

## KARMAŞTIRMA!

| Layer | Adresleme |
|---|---|
| Data Link Layer | MAC Address |
| Network Layer | IP Address |

## Kendini Test Et

**Soru 1:** Network Layer kaçıncı katmandır?  
**Cevap:** 3. katman.

**Soru 2:** Network Layer'ın temel adresleme yapısı nedir?  
**Cevap:** IP Address.

**Soru 3:** IP paketin ulaşıp ulaşmadığını garanti eder mi?  
**Cevap:** Hayır.

---

# 3. IPv4 Nedir?

## Bu nedir?

**IPv4**, 32 bitlik IP adresleme sistemidir.

Örnek:

```text
192.168.1.10
```

IPv4 dört parçadan oluşur. Her parçaya **octet** denir.

```text
192 . 168 . 1 . 10
```

Her octet 8 bittir.

## IPv4 adres sayısı

IPv4 teorik olarak yaklaşık **4.3 milyar adres** sağlar. Ama bu sayı günümüz için yetersiz kalmıştır.

## Neden yetersiz?

Çünkü artık internete sadece bilgisayarlar bağlanmıyor:

- Telefonlar
- Tabletler
- Akıllı TV'ler
- Kameralar
- IoT cihazları
- Sunucular
- Arabalar
- Endüstriyel sistemler

## Günlük hayat analojisi

Bir şehirde 4.3 milyon telefon numarası olduğunu düşün. Başta yeterli gelir. Ama herkesin 5 cihazı olunca numaralar yetmez. IPv4 de aynı problemi yaşadı.

## IPv4 Header'da önemli alanlar

| Alan | Açıklama |
|---|---|
| Version | IPv4 mü IPv6 mı? |
| IHL | Header uzunluğu |
| Total Length | Paketin toplam boyutu |
| Identification | Parçalanmış paketleri ilişkilendirir |
| Flags | Fragmentation bilgisi |
| TTL | Paketin yaşam süresi |
| Protocol | TCP mi UDP mi? |
| Header Checksum | Header hata kontrolü |
| Source IP | Kaynak IP |
| Destination IP | Hedef IP |

## TTL Nedir?

**TTL (Time To Live)** paketin kaç router geçebileceğini belirler. Her router'dan geçince TTL değeri 1 azalır. TTL sıfır olursa paket düşürülür.

## İşletim sistemi ipucu

Derste şu bilgi verildi:

```text
Windows genelde TTL 128 ile başlar.
Linux/macOS genelde TTL 64 ile başlar.
```

Bu yüzden Wireshark'ta TTL değerinden sistem hakkında tahmin yapılabilir.

## Bunu neden öğreniyoruz?

TTL; routing sorunlarını anlamada, traceroute analizinde, paket yaşam süresini takipte ve işletim sistemi tahmininde kullanılır.

## KARMAŞTIRMA!

| Kavram | Görev |
|---|---|
| TTL | Paketin yaşam süresi |
| Hop | Paketin geçtiği router/adım |
| Traceroute | Hop'ları gösteren araç |

## Kendini Test Et

**Soru 1:** IPv4 kaç bittir?  
**Cevap:** 32 bit.

**Soru 2:** TTL sıfır olursa ne olur?  
**Cevap:** Paket düşürülür.

**Soru 3:** Windows genelde hangi TTL ile başlar?  
**Cevap:** 128.

---

# 4. IPv6 Nedir?

## Bu nedir?

**IPv6**, IPv4 adres yetersizliğine kalıcı çözüm olarak geliştirilmiş yeni IP adresleme sistemidir. IPv6 **128 bit** uzunluğundadır.

Örnek format:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

## IPv6'nın avantajları

- Çok daha fazla IP adresi sağlar.
- NAT ihtiyacını azaltır.
- Uçtan uca bağlantıyı destekler.
- Otomatik yapılandırmayı destekler.
- Broadcast yerine daha verimli iletişim yöntemleri kullanır.
- Header yapısı daha sadeleştirilmiştir.

## Günlük hayat analojisi

IPv4 küçük bir mahalledeki ev numaraları gibidir. IPv6 ise tüm dünyadaki her nesneye özel adres verebilecek kadar geniş bir sistemdir.

## IPv6'da kısaltma

Şu adres:

```text
2001:0db8:0000:0000:0000:0000:0000:0001
```

şöyle yazılabilir:

```text
2001:db8::1
```

Sıfır blokları kısaltılır.

## IPv6 Header'da önemli alanlar

| IPv6 Alanı | IPv4'teki Karşılığı |
|---|---|
| Version | Version |
| Payload Length | Total Length |
| Next Header | Protocol |
| Hop Limit | TTL |
| Source Address | Source IP |
| Destination Address | Destination IP |

> **HATIRLA:** IPv4 = 32 bit. IPv6 = 128 bit.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| IPv4 | Eski ama hâlâ çok yaygın |
| IPv6 | Yeni nesil, geniş adresleme |
| NAT | IPv4 yetersizliğine geçici çözüm |
| IPv6 | IPv4 yetersizliğine kalıcı çözüm |

## Kendini Test Et

**Soru 1:** IPv6 kaç bittir?  
**Cevap:** 128 bit.

**Soru 2:** IPv6 neden geliştirildi?  
**Cevap:** IPv4 adres yetersizliğini çözmek için.

**Soru 3:** IPv6'da TTL yerine hangi alan vardır?  
**Cevap:** Hop Limit.

---

# 5. Private IP ve Public IP

## Bu nedir?

**Private IP**, yerel ağ içinde kullanılan IP adresidir.

Örnek:

```text
192.168.1.10
10.10.0.21
172.16.1.15
```

**Public IP**, internete çıkarken dış dünyanın gördüğü IP adresidir.

## Private IP blokları

| Aralık | Kullanım |
|---|---|
| 10.0.0.0/8 | Büyük ağlar |
| 172.16.0.0/12 | Orta/büyük ağlar |
| 192.168.0.0/16 | Ev ve küçük ofis ağları |

## Günlük hayat analojisi

Bir apartmanda herkesin oda numarası olabilir ama dışarıdan gelen kargo sadece apartman adresini bilir.

```text
Public IP = Apartman adresi
Private IP = Daire/oda içi adres
```

## Eğitmenin örneği

Evde telefonun Wi-Fi'ye bağlandığında modemden private IP alır. Örneğin:

```text
192.168.0.102
```

Ama internete çıkarken modem/router'ın public IP'si kullanılır.

Kafeye gidersen:

```text
Kafenin router'ından private IP alırsın.
Dışarıya kafenin public IP'siyle çıkarsın.
```

## Güvenlik uyarısı

Public Wi-Fi risklidir. Çünkü saldırgan:

- Sahte Access Point kurabilir.
- Kafe Wi-Fi adını taklit edebilir.
- Trafiği kendi cihazından geçirebilir.
- Şifrelenmemiş verileri okuyabilir.

> **HATIRLA:** Bankacılık gibi kritik işlemler için public Wi-Fi yerine hücresel veri kullanmak daha güvenlidir.

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Private IP | Yerel ağ içi IP |
| Public IP | İnternette görünen IP |
| Default Gateway | Yerel ağdan çıkış kapısı |
| NAT | Private/Public dönüşümü |

## Kendini Test Et

**Soru 1:** 192.168.1.20 private mı public mi?  
**Cevap:** Private IP.

**Soru 2:** Kafede internete bağlanınca dışarıya hangi IP ile çıkarsın?  
**Cevap:** Kafenin public IP'siyle.

**Soru 3:** Public Wi-Fi neden risklidir?  
**Cevap:** Sahte access point ve trafik dinleme riski vardır.

---

# 6. NAT Nedir?

## Bu nedir?

**NAT (Network Address Translation)**, private IP adreslerini public IP adresine çeviren işlemdir.

Evdeki cihazın:

```text
192.168.1.5
```

IP'si internete doğrudan çıkamaz. Router bunu public IP'ye çevirir.

## Günlük hayat analojisi

Bir şirket düşün. Çalışanların iç dahili numaraları vardır:

```text
101
102
103
```

Ama dışarı arama yapıldığında şirketin ana numarası görünür.

```text
Private IP = Dahili numara
Public IP = Şirket ana numarası
NAT = Santral
```

## NAT nasıl çalışır?

1. Cihaz internete istek gönderir.
2. İstek router'a gider.
3. Router private IP'yi public IP'ye çevirir.
4. NAT tablosuna kayıt açar.
5. Cevap geldiğinde NAT tablosuna bakar.
6. Paketi doğru iç cihaza gönderir.

## Örnek

```text
İç cihaz: 192.168.1.5
Router Public IP: 52.209.219.109
Hedef: google.com
```

Google dışarıdan sadece şunu görür:

```text
52.209.219.109
```

Ama router içeride bunun hangi cihaza ait olduğunu NAT tablosundan bilir.

> **HATIRLA:** NAT, IPv4 yetersizliğine geçici ama pratik çözümdür.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| NAT | IP adresini çevirir |
| DHCP | IP adresi dağıtır |
| DNS | Alan adını IP'ye çevirir |
| Firewall | Trafiği izin/engel kurallarına göre denetler |

## Kendini Test Et

**Soru 1:** NAT ne yapar?  
**Cevap:** Private IP ile public IP arasında dönüşüm yapar.

**Soru 2:** NAT tablosu ne işe yarar?  
**Cevap:** Gelen cevabın içeride hangi cihaza döneceğini belirler.

**Soru 3:** NAT en çok hangi IP sürümünde gereklidir?  
**Cevap:** IPv4.

---

# 7. DHCP Nedir?

## Bu nedir?

**DHCP (Dynamic Host Configuration Protocol)**, cihazlara otomatik IP bilgisi veren protokoldür.

DHCP şunları dağıtabilir:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server
- Lease Time

## Günlük hayat analojisi

Bir otelde resepsiyon sana oda verir. Sen odayı seçmezsin. Resepsiyon uygun olanı verir. DHCP de cihaza uygun IP verir.

## Static IP vs DHCP

| Yöntem | Açıklama |
|---|---|
| Static IP | Elle verilen sabit IP |
| DHCP | Otomatik verilen IP |

## DHCP neden kullanılır?

Elle IP vermek büyük ağlarda zahmetlidir. Örneğin 300 bilgisayarlı bir şirkette her bilgisayara manuel IP vermek:

- Zaman kaybettirir.
- Hata riskini artırır.
- IP çakışmasına neden olabilir.
- Yönetimi zorlaştırır.

DHCP bunu otomatikleştirir.

## DORA Süreci

DHCP'nin 4 adımı vardır:

```text
DORA
```

| Harf | Açılım | Anlam |
|---|---|---|
| D | Discover | IP verecek DHCP var mı? |
| O | Offer | Sana şu IP'yi teklif ediyorum |
| R | Request | Bu IP'yi istiyorum |
| A | Acknowledge | Tamam, bu IP senin |

> **HATIRLA:** DHCP = Otomatik IP dağıtımı. DORA = DHCP'nin çalışma süreci.

## 169.254.x.x Nedir?

Cihaz DHCP'den IP alamazsa kendine geçici bir IP verir. Bu genelde şu aralıkla başlar:

```text
169.254.x.x
```

Buna **Link-Local Address** denir.

## Bunu neden öğreniyoruz?

Çünkü bir cihazda 169.254 ile başlayan IP görüyorsan büyük ihtimalle:

```text
DHCP çalışmıyor
Cihaz DHCP server'a ulaşamıyor
Ağda IP dağıtım problemi var
```

## KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| DHCP | IP dağıtır |
| Static IP | Elle verilir |
| Lease Time | IP'nin kiralama süresi |
| Link-Local | DHCP alınamazsa geçici IP |

## Kendini Test Et

**Soru 1:** DHCP ne yapar?  
**Cevap:** Cihazlara otomatik IP yapılandırması verir.

**Soru 2:** DORA'daki O ne demektir?  
**Cevap:** Offer.

**Soru 3:** 169.254 ile başlayan IP neyi gösterir?  
**Cevap:** Cihaz DHCP'den IP alamamıştır.

---

# 8. Default Gateway Nedir?

## Bu nedir?

**Default Gateway**, yerel ağdan dış dünyaya çıkış kapısıdır. Genellikle router'ın iç IP adresidir.

Örnek:

```text
192.168.1.1
```

## Günlük hayat analojisi

Bir binadan dışarı çıkmak için ana kapıyı kullanırsın.

```text
Default Gateway = Ana kapı
```

Cihaz internete çıkacaksa önce default gateway'e gider.

## Eğitmenin örneği

Evde modem/router:

```text
192.168.0.1
```

olabilir. Telefonun:

```text
192.168.0.102
```

IP'sini alır. Telefon dışarı çıkarken önce:

```text
192.168.0.1
```

adresine gider.

## Firewall varsa?

Kurumsal ağlarda default gateway router değil, firewall olabilir.

Örnek:

```text
Client -> Firewall -> Router -> Internet
```

Bu durumda iç cihazların default gateway'i firewall'un iç bacağıdır.

## KARMAŞTIRMA!

| Cihaz | Görev |
|---|---|
| Router | Ağlar arası yönlendirme |
| Firewall | Trafiği güvenlik kurallarına göre denetleme |
| Default Gateway | Yerel ağdan çıkış kapısı |

## Kendini Test Et

**Soru 1:** Default Gateway nedir?  
**Cevap:** Yerel ağdan dış dünyaya çıkış kapısıdır.

**Soru 2:** Ev ağında default gateway genelde hangi cihazdır?  
**Cevap:** Modem/router.

**Soru 3:** Kurumsal ağda default gateway firewall olabilir mi?  
**Cevap:** Evet.

---

# 9. DNS Nedir?

## Bu nedir?

**DNS (Domain Name System)** alan adlarını IP adreslerine çevirir.

Örnek:

```text
google.com -> 142.250.x.x
```

## Günlük hayat analojisi

Telefon rehberinde kişinin adı vardır ama arama yapmak için numara gerekir. DNS, internetin telefon rehberidir.

```text
Alan adı = Kişi adı
IP adresi = Telefon numarası
DNS = Rehber
```

## Bunu neden öğreniyoruz?

Çünkü web sitelerine isimle gideriz ama bilgisayarlar IP ile konuşur. Sen:

```text
google.com
```

yazarsın. Cihaz önce DNS'e sorar:

```text
google.com'un IP'si nedir?
```

## Wireshark'ta DNS

Wireshark ile DNS sorguları görülebilir.

Örnek filtre:

```text
dns
```

veya:

```text
dns.qry.name == "sahibinden.com"
```

## Kendini Test Et

**Soru 1:** DNS ne yapar?  
**Cevap:** Alan adını IP adresine çevirir.

**Soru 2:** google.com yazınca cihaz ilk ne yapar?  
**Cevap:** DNS sorgusu yapar.

**Soru 3:** DNS trafiği Wireshark'ta görülebilir mi?  
**Cevap:** Evet.

---

# 10. ICMP Nedir?

## Bu nedir?

**ICMP (Internet Control Message Protocol)** hata raporlama ve ağ teşhis protokolüdür.

Temel görevleri:

- Hedef erişilebilir mi?
- Ağda hata var mı?
- Paket hedefe ulaşabiliyor mu?
- Hangi noktada sorun var?

## Günlük hayat analojisi

Birine sesleniyorsun:

```text
Orada mısın?
```

Karşıdan cevap geliyor:

```text
Buradayım.
```

Bu ping mantığıdır.

```text
Echo Request = Orada mısın?
Echo Reply = Buradayım.
```

## ICMP Type ve Code

ICMP mesajlarında iki önemli alan vardır:

```text
Type
Code
```

Örnekler:

| Type | Anlam |
|---|---|
| 0 | Echo Reply |
| 3 | Destination Unreachable |
| 8 | Echo Request |
| 11 | Time Exceeded |

## Ping Nedir?

**Ping**, ICMP kullanarak bir hedefe erişilip erişilemediğini test eder.

Windows örneği:

```bash
ping google.com
```

Linux örneği:

```bash
ping google.com
```

## Windows ve Linux Ping farkı

| Sistem | Davranış |
|---|---|
| Windows | 4 paket gönderir ve durur |
| Linux | Sen durdurana kadar devam eder |

Windows'ta sürekli ping:

```bash
ping -t google.com
```

Linux'ta belirli sayıda ping:

```bash
ping -c 5 google.com
```

## Güvenlik perspektifi

ICMP faydalıdır ama saldırganlar tarafından da kullanılır.

Örnek saldırılar:

- Ping of Death
- ICMP Flood
- Host discovery
- Network reconnaissance

Bu yüzden birçok kurum firewall'da ICMP trafiğini sınırlar veya engeller.

> **HATIRLA:** ICMP hem teşhis aracıdır hem keşif aracı olarak kötüye kullanılabilir.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| Ping | Hedef erişilebilir mi test eder |
| ICMP | Ping'in kullandığı protokol |
| Echo Request | Soru paketi |
| Echo Reply | Cevap paketi |
| Destination Unreachable | Hedefe ulaşılamıyor |

## Kendini Test Et

**Soru 1:** Ping hangi protokolü kullanır?  
**Cevap:** ICMP.

**Soru 2:** Echo Request ne demektir?  
**Cevap:** Hedefe gönderilen "orada mısın?" isteğidir.

**Soru 3:** ICMP neden firewall'da engellenebilir?  
**Cevap:** Saldırganlar ağ keşfi ve saldırı için kullanabilir.

---

# 11. Traceroute / Tracert Nedir?

## Bu nedir?

**Traceroute**, bir hedefe giderken geçilen router/hop noktalarını gösterir.

Windows'ta:

```bash
tracert google.com
```

Linux'ta:

```bash
traceroute google.com
```

## Günlük hayat analojisi

Bir şehirden başka bir şehre gidiyorsun.

```text
Niğde -> Ankara -> İstanbul -> Frankfurt -> Google Server
```

Traceroute bu durakları gösterir.

## Hop Nedir?

Her router geçişi bir **hop** olarak sayılır.

## TTL ile ilişkisi

Traceroute TTL değerlerini kullanarak her adımı tespit eder. TTL her router'da azalır. Bu sayede paket hangi router'dan geçti, görülebilir.

## Örnek kullanım

```bash
tracert cnn.com
```

Maksimum hop sınırlama:

```bash
tracert -h 5 cnn.com
```

DNS çözümlemesini kapatarak daha hızlı çalışma:

```bash
tracert -d cnn.com
```

## KARMAŞTIRMA!

| Komut | Sistem |
|---|---|
| tracert | Windows |
| traceroute | Linux/macOS |

## Kendini Test Et

**Soru 1:** Traceroute neyi gösterir?  
**Cevap:** Hedefe giderken geçilen router/hop noktalarını.

**Soru 2:** Windows'ta hangi komut kullanılır?  
**Cevap:** tracert.

**Soru 3:** Hop ne demektir?  
**Cevap:** Paketin geçtiği her router/adım.

---

# 12. ipconfig ve ifconfig

## Windows tarafı

Temel komut:

```bash
ipconfig
```

Detaylı bilgi:

```bash
ipconfig /all
```

Görebileceğin bilgiler:

- IPv4 Address
- IPv6 Address
- Subnet Mask
- Default Gateway
- DHCP Server
- DNS Server
- MAC Address
- Lease Time

## Linux tarafı

Eski ama hâlâ kullanılan komut:

```bash
ifconfig
```

Modern Linux alternatifi:

```bash
ip addr
```

## Günlük hayat analojisi

Kimlik kartını düşün. Cihazın ağ kimliği de bu komutlarla görülür.

```text
IP Address = Adres
MAC Address = Kimlik numarası
Default Gateway = Çıkış kapısı
DNS = Rehber
```

## Kendini Test Et

**Soru 1:** Windows'ta detaylı ağ bilgisi için hangi komut kullanılır?  
**Cevap:** ipconfig /all.

**Soru 2:** Linux'ta ağ arayüz bilgisi için hangi komut kullanılabilir?  
**Cevap:** ifconfig veya ip addr.

**Soru 3:** DHCP açık mı kapalı mı nereden anlaşılır?  
**Cevap:** ipconfig /all çıktısındaki DHCP Enabled alanından.

---

# 13. ARP Nedir?

## Bu nedir?

**ARP (Address Resolution Protocol)** IP adresinden MAC adresini bulmak için kullanılır.

## Günlük hayat analojisi

Bir apartmanda daire numarasını biliyorsun ama kişinin kim olduğunu bilmiyorsun. ARP şunu sorar:

```text
Bu IP kimde?
```

Cevap:

```text
Bu IP şu MAC adresinde.
```

## Komutlar

Windows:

```bash
arp -a
```

Linux:

```bash
arp -a
```

veya:

```bash
ip neigh
```

## Bunu neden öğreniyoruz?

Çünkü aynı yerel ağdaki iletişimde cihazlar IP ile düşünür ama Ethernet seviyesinde MAC adresi gerekir.

## Kendini Test Et

**Soru 1:** ARP ne yapar?  
**Cevap:** IP adresine karşılık gelen MAC adresini bulur.

**Soru 2:** ARP hangi ağ ortamında önemlidir?  
**Cevap:** Yerel ağda.

**Soru 3:** Windows'ta ARP tablosu nasıl görüntülenir?  
**Cevap:** arp -a.

---

# 14. Wireshark Nedir?

## Bu nedir?

**Wireshark**, ağ trafiğini paket seviyesinde yakalayıp analiz eden bir protokol analiz aracıdır.

## Ne için kullanılır?

- Paket yakalama
- Protokol analizi
- Şüpheli trafik inceleme
- DNS/HTTP/TCP/UDP/ICMP analizi
- Malware C2 iletişimi araştırma
- Incident Response
- Forensic analiz
- Port scan / DoS belirtileri inceleme
- Plaintext parola yakalama testi

## Günlük hayat analojisi

Bir güvenlik kamerası düşün. Wireshark ağdaki paketleri kaydeder ve sana gösterir.

```text
Ağ trafiği = Yoldan geçen araçlar
Wireshark = Trafik kamerası
Paket = Her bir araç
```

## Wireshark ekran bölümleri

| Bölüm | Açıklama |
|---|---|
| Packet List | Yakalanan paketlerin listesi |
| Packet Details | Seçili paketin detayları |
| Packet Bytes | Paketin ham hexadecimal verisi |

## Wireshark'ta görülen katmanlar

Örnek bir paket açıldığında:

```text
Frame
Ethernet II
Internet Protocol Version 4
User Datagram Protocol
Domain Name System
```

Bu aslında OSI/TCP-IP katmanlarının paket içinde nasıl kapsüllendiğini gösterir.

## Filtre örnekleri

Sadece ICMP:

```text
icmp
```

Sadece DNS:

```text
dns
```

Sadece UDP:

```text
udp
```

Belirli IP:

```text
ip.addr == 10.80.67.219
```

Kaynak IP:

```text
ip.src == 10.80.67.219
```

Hedef IP:

```text
ip.dst == 8.8.8.8
```

DNS sorgu adı:

```text
dns.qry.name == "sahibinden.com"
```

## Güvenlik açısından önemi

Wireshark ile şunlar tespit edilebilir:

- Şüpheli bağlantılar
- C2 sunucu iletişimi
- Anormal DNS sorguları
- Şifrelenmemiş HTTP/FTP/Telnet parolaları
- ICMP flood
- Port scan belirtileri
- Gereksiz broadcast trafiği

> **HATIRLA:** Wireshark sana ağı gösterir. Ama yorumlamayı sen öğrenmelisin. Araç tek başına çözüm değildir. Paketleri okuyabilmek gerekir.

## KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| Capture Filter | Paket yakalamadan önce filtre |
| Display Filter | Yakalanmış paketleri ekranda filtreleme |
| Packet List | Paket listesi |
| Packet Details | Paket içeriği |

## Kendini Test Et

**Soru 1:** Wireshark ne işe yarar?  
**Cevap:** Ağ paketlerini yakalayıp analiz etmeye yarar.

**Soru 2:** Sadece ICMP paketleri için hangi filtre yazılır?  
**Cevap:** icmp.

**Soru 3:** Packet Details bölümü ne gösterir?  
**Cevap:** Seçili paketin protokol ve alan detaylarını gösterir.

---

# 15. Ders İçindeki Gerçek Dünya Güvenlik Dersleri

## 1. Public Wi-Fi tehlikelidir

Kafe, havaalanı, otel gibi yerlerde bağlandığın Wi-Fi gerçek olmayabilir. Saldırgan aynı SSID ile sahte ağ kurabilir.

Örnek:

```text
Cafe_WiFi
```

Saldırgan da aynı isimle sahte ağ açar. Sen bağlanırsan trafiğin onun üzerinden geçebilir.

## 2. ICMP keşif için kullanılabilir

Saldırgan önce şunu anlamak ister:

```text
Ağda kimler açık?
```

Ping ve ICMP burada kullanılabilir.

## 3. Firewall ICMP'yi kısıtlayabilir

Kurumsal yapılarda ICMP tamamen açık bırakılmaz. Ama tamamen kapatmak da bazen troubleshooting'i zorlaştırır.

En doğru yaklaşım:

```text
Gerektiği kadar izin ver, fazlasını engelle.
```

## 4. Wireshark güçlüdür ama dikkat ister

Wireshark ile hassas bilgiler görülebilir. Özellikle şifrelenmemiş protokoller risklidir:

- HTTP
- FTP
- Telnet

## 5. NAT güvenlik değildir

NAT dışarıdan iç IP'leri gizler ama firewall yerine geçmez.

```text
NAT ≠ Firewall
```

---

# Genel Tekrar ve Özet

| Konu | Tek Cümlelik Özet |
|---|---|
| Subnetting | Büyük ağı küçük yönetilebilir ağlara böler. |
| Network Layer | IP ile paketleri kaynaktan hedefe yönlendirir. |
| IPv4 | 32 bitlik eski ama yaygın IP sistemidir. |
| IPv6 | 128 bitlik yeni nesil IP sistemidir. |
| Private IP | Yerel ağ içinde kullanılan IP'dir. |
| Public IP | İnternette görünen IP'dir. |
| NAT | Private IP ile public IP arasında dönüşüm yapar. |
| DHCP | Cihazlara otomatik IP bilgisi verir. |
| DORA | DHCP'nin dört adımlı çalışma sürecidir. |
| Default Gateway | Ağdan dışarı çıkış kapısıdır. |
| DNS | Alan adlarını IP'ye çevirir. |
| ICMP | Ağ hatalarını ve erişilebilirliği test eder. |
| Ping | ICMP ile hedefe ulaşılıp ulaşılmadığını test eder. |
| Traceroute | Hedefe giderken geçilen router'ları gösterir. |
| Wireshark | Ağ paketlerini yakalayıp analiz eder. |

---

# En Kritik 10 Bilgi

1. IP, paketin ulaşıp ulaşmadığını garanti etmez.
2. TCP güvenilirlik sağlar; IP sadece yönlendirir.
3. Private IP internete doğrudan çıkamaz.
4. NAT private IP'yi public IP'ye çevirir.
5. DHCP otomatik IP verir.
6. DORA = Discover, Offer, Request, Acknowledge.
7. 169.254.x.x görüyorsan DHCP problemi olabilir.
8. Ping ICMP kullanır.
9. Traceroute hop/router yolunu gösterir.
10. Wireshark paketleri gösterir; güvenlik analizi için temel araçtır.
