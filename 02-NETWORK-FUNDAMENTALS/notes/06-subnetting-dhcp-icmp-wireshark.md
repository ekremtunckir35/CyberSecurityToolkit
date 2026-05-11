## Konu

<div align="center">

![Ders İnfografiği](../assets/06-ipv4-ipv6-nat-subnetting-dhcp.png)

</div>

---

IPv4, IPv6, NAT, Default Gateway, Subnetting, DHCP ve ICMP'ye giris

# ADIM 1 - Dersin Ana Haritasi

Bu derste su konular islendi:

1. Network Layer (Ag Katmani)
2. IP Protocol (Internet Protocol)
3. IPv4
4. IPv6
5. IPv4 Header ve IPv6 Header
6. Private IP / Public IP
7. NAT (Network Address Translation)
8. Default Gateway
9. Subnet Mask
10. CIDR Notation
11. Subnetting
12. VLAN ve Subnetting farki
13. DHCP
14. DHCP DORA sureci
15. DHCP guvenlik riski
16. ICMP ve Ping'e giris

---

# 1. Network Layer Nedir?

## Bu nedir?

Network Layer, OSI modelinin 3. katmanidir. Temel gorevi, verinin bir agdan baska bir aga yonlendirilmesini saglamaktir.

Bu katmanda en onemli protokol IP Protocol (Internet Protocol)'dur.

## Gunluk hayat analojisi

Network Layer'i sehirler arasi kargo sistemi gibi dusun.

- Evindeki cihaz = gonderici
- Hedef cihaz = alici
- IP adresi = acik adres
- Router = kargo aktarma merkezi
- Paket = kargo kutusu

Kargo sirketi paketi yola cikarir ama her zaman teslim garantisi vermez. IP protokolu de buna benzer.

## Bunu neden ogreniyoruz?

Cunku siber guvenlikte ag trafigini anlamadan saldiri analizi, log inceleme, firewall kurali, subnet tasarimi, port analizi ve zafiyet taramasi saglam yapilamaz.

## HATIRLA

Network Layer = IP adresleme + yonlendirme.

## KARMASHTIRMA!

| Kavram | Anlami |
|---|---|
| MAC Address | Fiziksel ag adresi, Layer 2 |
| IP Address | Mantiksal ag adresi, Layer 3 |
| Switch | Genelde MAC adresine bakar |
| Router | IP adresine bakar |

## Kendini Test Et

**Soru 1:** Network Layer hangi OSI katmanidir?  
**Cevap:** 3. katmandir.

**Soru 2:** Bu katmandaki en onemli protokol nedir?  
**Cevap:** IP Protocol.

**Soru 3:** Router hangi adres turune gore yonlendirme yapar?  
**Cevap:** IP adresine gore.

---

# 2. IP Protocol Nedir?

## Bu nedir?

IP Protocol, cihazlarin ag uzerinde adreslenmesini ve verilerin bir kaynaktan hedefe yonlendirilmesini saglar.

Ders icinde ozellikle su nokta vurgulandi: IP protokolu connectionless calisir. Yani IP, paketin hedefe ulasip ulasmadigini garanti etmez. Sadece paketi gonderir.

## Gunluk hayat analojisi

Bir mektubu posta kutusuna attigini dusun. Posta sistemi mektubu yola cikarir ama sen takip sistemi kullanmiyorsan gercekten ulasti mi bilmiyorsun.

IP de buna benzer: paketi gonderir; hedefe ulasti mi, kayboldu mu, sirayla mi gitti, bunun garantisini tek basina vermez.

## Bunu neden ogreniyoruz?

Agda veri kaybi, gecikme, paket dusmesi ve TTL bitmesi gibi olaylari anlamak icin IP'nin garanti vermeyen yapisini bilmek gerekir.

## HATIRLA

IP gonderir, garanti etmez.

## KARMASHTIRMA!

| Kavram | Gorevi |
|---|---|
| IP | Adresleme ve yonlendirme |
| TCP | Guvenilir veri iletimi |
| UDP | Hizli ama garantisiz veri iletimi |

## Kendini Test Et

**Soru 1:** IP connectionless ne demektir?  
**Cevap:** Baglanti kurmadan paket gonderir, teslim garantisi vermez.

**Soru 2:** IP'nin ana gorevi nedir?  
**Cevap:** Adresleme ve yonlendirme.

**Soru 3:** Teslim garantisini IP mi TCP mi saglar?  
**Cevap:** TCP saglar.

---

# 3. IPv4 Nedir?

## Bu nedir?

IPv4, IP protokolunun eski ve hala cok kullanilan surumudur.

Ozellikleri:

- 32 bit uzunlugundadir.
- 4 oktetten olusur.
- Her oktet 0-255 arasi deger alir.
- Ornek: `192.168.1.10`

IPv4 teorik olarak yaklasik 2^32 = 4.294.967.296 adres uretebilir.

## Gunluk hayat analojisi

IPv4'u eski telefon numarasi sistemi gibi dusun. Basta herkese yeter sanildi ama telefon, tablet, kamera, sunucu ve IoT cihazlari artinca numaralar yetmemeye basladi.

## Ders icindeki ozel vurgu

Egitmen, IPv4 ciktiginda bu kadar cihaz olacaginin hesaplanmadigini soyledi. Bu yuzden IPv4 adresleri zamanla yetersiz kaldi.

Cozum olarak iki yol anlatildi:

1. Gecici cozum: Private IP + NAT
2. Kalici cozum: IPv6

## Bunu neden ogreniyoruz?

Bugunku aglarin cogunda hala IPv4 kullaniliyor. Firewall, NAT, subnetting ve DHCP gibi konular IPv4 bilgisi olmadan oturmaz.

## HATIRLA

IPv4 = 32 bit = 4 oktet = yaklasik 4.3 milyar adres.

## KARMASHTIRMA!

| Kavram | Aciklama |
|---|---|
| Oktet | 8 bitlik grup |
| IPv4 | 4 oktetten olusur |
| 255 | Bir oktetin alabilecegi en yuksek deger |
| 256 | Deger sayisidir ama IP'de yazilmaz |

## Kendini Test Et

**Soru 1:** IPv4 kac bittir?  
**Cevap:** 32 bit.

**Soru 2:** IPv4 kac oktetten olusur?  
**Cevap:** 4 oktet.

**Soru 3:** Bir oktet hangi degerleri alabilir?  
**Cevap:** 0 ile 255 arasinda.

---

# 4. IPv6 Nedir?

## Bu nedir?

IPv6, IPv4 adres yetersizligine kalici cozum olarak gelistirilen IP surumudur.

Ozellikleri:

- 128 bit uzunlugundadir.
- Hexadecimal gosterim kullanir.
- `:` ile ayrilmis 8 bloktan olusur.
- Cok daha buyuk adres alani saglar.

Ornek IPv6 yapisi:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

## Gunluk hayat analojisi

IPv4 kucuk bir apartman posta kutusu sistemi gibidir. IPv6 ise tum dunyadaki herkese ayri ayri devasa posta kutusu verebilecek kadar buyuk bir sistemdir.

## Ders icindeki ozel bilgiler

Egitmen su noktalari anlatti:

- IPv6'ya gecis hizli olmuyor.
- ISP altyapisi hazir olmayabilir.
- Eski cihazlar IPv6 desteklemeyebilir.
- Kurum altyapilari hazir olmayabilir.
- 2025 itibariyle bazi ulkeler IPv6'da cok ileride, bazilari geride.
- Turkiye'nin IPv6 adaptasyonu dusuk seviyede gosterildi.
- Google IPv6 adoption istatistiklerinden ornek verildi.

## Bunu neden ogreniyoruz?

IPv6 gelecegin ana adresleme modelidir. Modern aglarda, cloud sistemlerde ve guvenlik politikalarinda IPv6 trafigini yok saymak ciddi kor nokta olusturur.

## HATIRLA

IPv6 = 128 bit = devasa adres alani = NAT ihtiyacini azaltir.

## KARMASHTIRMA!

| IPv4 | IPv6 |
|---|---|
| 32 bit | 128 bit |
| Decimal gosterim | Hexadecimal gosterim |
| Nokta ile ayrilir | Iki nokta ile ayrilir |
| NAT yaygin | Uctan uca baglanti daha dogal |
| Broadcast var | Broadcast yok, multicast var |

## Kendini Test Et

**Soru 1:** IPv6 kac bittir?  
**Cevap:** 128 bit.

**Soru 2:** IPv6 hangi sayi sistemini kullanir?  
**Cevap:** Hexadecimal.

**Soru 3:** IPv6'da broadcast var mi?  
**Cevap:** Yoktur; multicast kullanilir.

---

# 5. IPv4 Header Nedir?

## Bu nedir?

IPv4 Header, IPv4 paketinin baslik bilgisidir. Paketle ilgili teknik kontrol bilgilerini tasir.

Ders icinde gecen onemli alanlar:

| Alan | Gorevi |
|---|---|
| Version | IPv4 mu IPv6 mi belirtir |
| Internet Header Length | Baslik uzunlugu |
| Total Length | Paket toplam uzunlugu |
| Identification | Parcalanan paketleri tanimlar |
| Flags | Paket parcalandi mi bilgisini verir |
| TTL | Paketin yasam suresi |
| Protocol | TCP mi UDP mi bilgisini tasir |
| Header Checksum | Baslik hata kontrolu |
| Source IP | Kaynak IP adresi |
| Destination IP | Hedef IP adresi |

## Gunluk hayat analojisi

Bir kargo kutusunun ustundeki etiket gibi dusun:

- Kimden geldi?
- Kime gidecek?
- Icinde kac parca var?
- Acil mi?
- Kac aktarma hakki kaldi?

IPv4 Header da paketin etiketidir.

## TTL Nedir?

TTL (Time To Live), paketin agda sonsuza kadar dolasmasini engeller. Her router'dan gecerken TTL 1 azalir. TTL 0 olursa paket dusurulur.

Ders icinde verilen degerler:

| Sistem | Varsayilan TTL |
|---|---|
| Windows | 128 |
| Linux | 64 |
| macOS | 64 |
| Router | 256 olarak anlatildi |

## Bunu neden ogreniyoruz?

TTL; traceroute, ping analizi, OS fingerprinting ve ag sorun giderme icin onemlidir.

## HATIRLA

TTL sifirlanirsa paket drop edilir.

## KARMASHTIRMA!

| Kavram | Anlami |
|---|---|
| TTL | Paketin kac hop yasayacagini belirler |
| Hop | Router gecis noktasi |
| Drop | Paketin dusurulmesi |
| Fragmentation | Buyuk paketin parcalara ayrilmasi |

## Kendini Test Et

**Soru 1:** TTL ne ise yarar?  
**Cevap:** Paketin agda sonsuza kadar dolasmasini engeller.

**Soru 2:** Her router gecisinde TTL ne olur?  
**Cevap:** 1 azalir.

**Soru 3:** IPv4 header'da kaynak ve hedef bilgisi hangi alanlarda tutulur?  
**Cevap:** Source IP ve Destination IP.

---

# 6. Private IP ve Public IP Nedir?

## Bu nedir?

Public IP, internette dogrudan kullanilan IP adresidir. Private IP, ic aglarda kullanilan ve internete dogrudan cikamayan IP adresidir.

Private IP bloklari:

| Blok | Kullanim |
|---|---|
| 10.0.0.0/8 | Buyuk aglar |
| 172.16.0.0/12 | Orta olcekli aglar |
| 192.168.0.0/16 | Ev ve kucuk isletmeler |

## Gunluk hayat analojisi

Private IP, apartman icindeki daire numarasi gibidir. Public IP ise apartmanin sokaktaki resmi adresidir.

Disaridan biri sana ulasacaksa apartman adresini bilir. Iceride hangi daireye gidecegini bina gorevlisi yonlendirir. Bu gorev NAT'a benzer.

## Bunu neden ogreniyoruz?

Ev, sirket, okul ve lab ortamlarinda cihazlarin cogu private IP kullanir. Internete cikarken NAT gerekir.

## HATIRLA

Private IP internette dogrudan yonlendirilmez.

## KARMASHTIRMA!

| Private IP | Public IP |
|---|---|
| Ic agda kullanilir | Internette kullanilir |
| NAT gerekir | Dogrudan yonlendirilebilir |
| Ayni private IP baska evde de olabilir | Benzersiz olmalidir |

## Kendini Test Et

**Soru 1:** 192.168.1.10 private mi public mi?  
**Cevap:** Private IP.

**Soru 2:** Private IP internete dogrudan cikabilir mi?  
**Cevap:** Hayir, NAT gerekir.

**Soru 3:** Ev modeminin dis IP'si genellikle private mi public mi olur?  
**Cevap:** Genellikle public IP veya ISP tarafinda CGNAT olabilir.

---

# 7. NAT Nedir?

## Bu nedir?

NAT (Network Address Translation), private IP adreslerinin public IP'ye cevrilmesidir.

Ders cumlesiyle: private adreslerin public adreslere donusturulmesi olayidir.

## Gunluk hayat analojisi

Bir ofiste 100 calisan var ama dis dunyaya sirket santral numarasiyla cikiyorlar.

- Calisan dahili numarasi = private IP
- Sirket ana numarasi = public IP
- Santral = NAT yapan router

## NAT nasil calisir?

Ornek:

```text
192.168.1.5 -> Router -> Public IP -> Internet
```

Router NAT tablosu tutar:

| Ic IP | Ic Port | Dis IP/Port |
|---|---|---|
| 192.168.1.5 | 27386 | PublicIP:43314 |
| 192.168.1.4 | 27386 | PublicIP:43315 |

Ayni hedefe birden fazla cihaz gitse bile port numarasi sayesinde ayristirilir.

## Ders icindeki ozel ornek

Egitmen, ayni anda birden fazla kisinin YouTube'dan ayni videoyu izlemesi ornegini verdi. Hepsi ayni hedefe gitse bile router port numaralarini degistirerek baglantilari ayirir.

## Bunu neden ogreniyoruz?

NAT bilmeden firewall loglari, port forwarding, VPN, ev agi, lab agi ve public/private ayrimi dogru anlasilamaz.

## HATIRLA

NAT, icerideki cok sayida cihazi disarida tek IP gibi gosterebilir.

## KARMASHTIRMA!

| Kavram | Aciklama |
|---|---|
| NAT | IP adres cevirimi |
| PAT | Port numarasiyla coklu ceviri |
| Port Forwarding | Disaridan ic cihaza yonlendirme |
| Private IP | NAT oncesi ic adres |

## Kendini Test Et

**Soru 1:** NAT ne yapar?  
**Cevap:** Private IP'yi public IP'ye cevirir.

**Soru 2:** Router ayni hedefe giden iki cihazi nasil ayirir?  
**Cevap:** Port numaralariyla.

**Soru 3:** IPv6'da NAT ihtiyaci neden azalir?  
**Cevap:** Cunku her cihaza benzersiz global adres verilebilir.

---

# 8. Default Gateway Nedir?

## Bu nedir?

Default Gateway, bir cihazin kendi agi disina cikmak icin kullandigi gecis kapisidir.

Genellikle modem, router, firewall veya Layer 3 switch default gateway olabilir.

## Gunluk hayat analojisi

Bir ulkeden baska ulkeye gecmek istiyorsun. Her yerden gecemezsin. Sinir kapisini kullanman gerekir. Default Gateway = agin sinir kapisi.

## Ayni ag / farkli ag farki

Ayni agdaki cihazlar dogrudan haberlesebilir.

Ornek:

```text
192.168.1.10
192.168.1.20
Subnet Mask: 255.255.255.0
```

Bunlar ayni agdadir.

Farkli ag:

```text
192.168.1.10
192.168.2.20
Subnet Mask: 255.255.255.0
```

Bu durumda default gateway gerekir.

## Ders icindeki ozel cumle

Default Gateway sadece internete cikmak icin degil, baska bir network'e gecmek icin de kullanilir.

## Bunu neden ogreniyoruz?

Default Gateway yanlissa cihaz internete cikamaz veya baska network'e erisemez.

## HATIRLA

Ayni agda gateway gerekmez. Farkli aga gecerken gateway gerekir.

## KARMASHTIRMA!

| Durum | Gateway gerekir mi? |
|---|---|
| Ayni LAN ici iletisim | Hayir |
| Internete cikis | Evet |
| Baska subnet'e gecis | Evet |
| Ayni switch ici ayni subnet | Hayir |

## Kendini Test Et

**Soru 1:** Default Gateway nedir?  
**Cevap:** Farkli aga cikis kapisidir.

**Soru 2:** Ev aginda default gateway genelde hangi cihazdir?  
**Cevap:** Modem/router.

**Soru 3:** Ayni agdaki iki cihaz iletisim icin gateway kullanir mi?  
**Cevap:** Hayir.

---

# 9. Subnet Mask Nedir?

## Bu nedir?

Subnet Mask, IP adresinin hangi kisminin network, hangi kisminin host oldugunu belirler.

Ornek:

```text
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
```

Burada:

- `192.168.1` = network kismi
- `.10` = host kismi

## Gunluk hayat analojisi

Bir okul dusun:

- Okul adi = network
- Sinif icindeki ogrenci numarasi = host

Subnet Mask, adresin hangi kisminin okul, hangi kisminin ogrenci oldugunu gosterir.

## 255 ve 0 mantigi

Subnet mask icinde:

- 1 olan bitler network kismini gosterir.
- 0 olan bitler host kismini gosterir.

```text
255.255.255.0 = /24
```

Yani ilk 24 bit network, son 8 bit host.

## Bunu neden ogreniyoruz?

Iki cihaz ayni agda mi degil mi sorusunun cevabi subnet mask ile bulunur.

## HATIRLA

Subnet Mask olmadan IP adresinin hangi aga ait oldugunu net bilemezsin.

## KARMASHTIRMA!

| Kavram | Aciklama |
|---|---|
| IP Address | Cihazin adresi |
| Subnet Mask | Ag/host ayrimini yapar |
| Network Address | Agin kimligi |
| Broadcast Address | Agdaki herkese yayin adresi |

## Kendini Test Et

**Soru 1:** Subnet Mask ne ise yarar?  
**Cevap:** IP'nin network ve host kismini ayirir.

**Soru 2:** 255.255.255.0 kac CIDR'dir?  
**Cevap:** /24.

**Soru 3:** /24 agda toplam kac IP vardir?  
**Cevap:** 256 toplam, 254 kullanilabilir.

---

# 10. CIDR Notation Nedir?

## Bu nedir?

CIDR (Classless Inter-Domain Routing), IP aglarini esnek sekilde gostermeye yarayan notasyondur.

Ornek:

```text
192.168.1.0/24
```

Buradaki `/24`, subnet mask icinde 24 tane 1 oldugunu gosterir.

## Gunluk hayat analojisi

Eski sistemde sadece S, M, L beden kiyafet vardi. CIDR gelince aradaki tum olculer mumkun oldu. Yani A, B, C siniflari kaba olcuydu; CIDR daha esnek olcudur.

## Ders icindeki ozel bilgi

Egitmen, classful addressing'in 1980'lerde, CIDR'in ise 1993'te ortaya ciktigini anlatti.

## Bunu neden ogreniyoruz?

Firewall kurali, subnet hesabi, route tanimi, cloud network ayari ve VPN yapilandirmasi CIDR ile yapilir.

## HATIRLA

- /24 = 255.255.255.0
- /16 = 255.255.0.0
- /8 = 255.0.0.0
- /32 = tek IP adresi

## KARMASHTIRMA!

| CIDR | Anlam |
|---|---|
| /24 | 256 toplam IP |
| /25 | 128 toplam IP |
| /26 | 64 toplam IP |
| /30 | 4 toplam IP, 2 kullanilabilir |
| /32 | Tek cihaz/IP |

## Kendini Test Et

**Soru 1:** CIDR ne saglar?  
**Cevap:** IP aglarini esnek sekilde bolmeyi saglar.

**Soru 2:** /32 neyi ifade eder?  
**Cevap:** Tek bir IP adresini.

**Soru 3:** /24 kac kullanilabilir host saglar?  
**Cevap:** 254.

---

# 11. Subnetting Nedir?

## Bu nedir?

Subnetting, buyuk bir agi daha kucuk alt aglara bolme islemidir.

Amac:

- agi yonetilebilir yapmak,
- broadcast trafigini azaltmak,
- departmanlari ayirmak,
- guvenlik politikalarini kolaylastirmak,
- IP kullanimini verimli hale getirmek.

## Gunluk hayat analojisi

Buyuk bir sirket binasini dusun. Herkes ayni salonda calisirsa kaos olur. Bunun yerine IT departmani, satis, muhasebe ve AR-GE ayri odalara ayrilir. Subnetting de agi boyle bolumlere ayirir.

## Ders icindeki ornekler

Egitmen su departman orneklerini verdi:

- IT Department
- Sales and Marketing
- Research and Development

Bu departmanlar ayri subnet'lere ayrilabilir.

## Bunu neden ogreniyoruz?

Siber guvenlikte segmentasyon kritik bir savunma teknigidir. Kamera agi, sunucu agi, misafir Wi-Fi ve yonetici cihazlari ayri olmalidir. Aksi halde tek cihaz ele gecirilirse tum ag etkilenebilir.

## HATIRLA

Subnetting = agi kucuk ve yonetilebilir parcalara bolmek.

## KARMASHTIRMA!

| Kavram | Ana amac |
|---|---|
| Subnetting | IP duzeyinde agi bolmek |
| VLAN | Layer 2 duzeyinde sanal ag ayirmak |
| Firewall Rule | Aglar arasi gecisi kontrol etmek |

## Kendini Test Et

**Soru 1:** Subnetting neden yapilir?  
**Cevap:** Agi kucuk, guvenli ve yonetilebilir parcalara bolmek icin.

**Soru 2:** /26 toplam kac IP verir?  
**Cevap:** 64 toplam IP, 62 kullanilabilir.

**Soru 3:** Network ve broadcast adresi kullanilabilir mi?  
**Cevap:** Hayir.

---

# 12. VLAN ve Subnetting Farki

## Bu nedir?

Dersin onemli soru-cevap kisimlarindan biri buydu.

Subnetting, IP adresleme tarafindaki bolmedir. VLAN, switch uzerinde sanal ag ayrimidir.

## Kisa fark

| Ozellik | VLAN | Subnetting |
|---|---|---|
| Katman | Layer 2 agirlikli | Layer 3 |
| Temel amac | Broadcast domain ayirmak | IP aglarini bolmek |
| Cihaz | Switch | Router/L3 switch/firewall |
| Guvenlik etkisi | Trafik izolasyonu saglar | Routing ve IP yonetimi saglar |

## Gunluk hayat analojisi

Subnetting = mahalleyi sokaklara bolmek. VLAN = ayni binadaki insanlari kartli gecisle ayri katlara ayirmak.

## Bunu neden ogreniyoruz?

Gercek sirket aglarinda VLAN ve subnet genellikle birlikte kullanilir.

| Departman | VLAN | Subnet |
|---|---|---|
| IT | VLAN 10 | 192.168.10.0/24 |
| Muhasebe | VLAN 20 | 192.168.20.0/24 |
| Misafir | VLAN 30 | 192.168.30.0/24 |

## HATIRLA

VLAN teknolojinin adi, subnet IP planlamasinin adidir.

## KARMASHTIRMA!

| Yanlis dusunce | Dogrusu |
|---|---|
| VLAN ve subnet ayni seydir | Hayir, farkli katmanlarda calisirlar |
| VLAN varsa subnet gerekmez | Genellikle ikisi birlikte kullanilir |
| Subnet guvenlik saglar | Tek basina yetmez, firewall kurali gerekir |

## Kendini Test Et

**Soru 1:** VLAN hangi katmanda daha cok iliskilidir?  
**Cevap:** Layer 2.

**Soru 2:** Subnetting hangi katmandadir?  
**Cevap:** Layer 3.

**Soru 3:** VLAN'lar arasi iletisim icin ne gerekir?  
**Cevap:** Router, Layer 3 switch veya firewall uzerinde routing/kural gerekir.

---

# 13. DHCP Nedir?

## Bu nedir?

DHCP (Dynamic Host Configuration Protocol), cihazlara otomatik IP yapilandirmasi veren protokoldur.

DHCP sunlari verir:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server

## Gunluk hayat analojisi

Bir otele giris yaptigini dusun. Resepsiyon sana oda numarasi, Wi-Fi bilgisi, kahvalti saati ve cikis bilgisi verir. DHCP de aga baglanan cihaza gerekli ag bilgilerini verir.

## Statik IP vs Dinamik IP

| Statik IP | Dinamik IP |
|---|---|
| Elle girilir | DHCP verir |
| Sabittir | Degisebilir |
| Sunucu/yazici/kamera icin uygundur | Kullanici cihazlari icin uygundur |
| Yonetimi zordur | Yonetimi kolaydir |

## Bunu neden ogreniyoruz?

DHCP olmazsa buyuk aglarda her cihaza elle IP vermek gerekir. Bu hem zaman kaybi hem de hata riskidir.

## HATIRLA

DHCP = otomatik IP dagitimi.

## KARMASHTIRMA!

| Kavram | Anlam |
|---|---|
| DHCP Server | IP dagitan sistem |
| DHCP Client | IP isteyen cihaz |
| Scope | Dagitilacak IP araligi |
| Lease | IP kiralama suresi |
| Reservation | MAC adresine sabit IP ayirma |

## Kendini Test Et

**Soru 1:** DHCP ne ise yarar?  
**Cevap:** Cihazlara otomatik IP yapilandirmasi verir.

**Soru 2:** DHCP hangi bilgileri verebilir?  
**Cevap:** IP, subnet mask, default gateway, DNS.

**Soru 3:** IP cakismasini DHCP nasil azaltir?  
**Cevap:** Merkezi IP havuzu yoneterek.

---

# 14. DHCP DORA Sureci

## Bu nedir?

DHCP IP alma sureci 4 adimdan olusur: DORA.

| Adim | Acilim | Anlami |
|---|---|---|
| D | Discover | Client DHCP server arar |
| O | Offer | Server IP teklif eder |
| R | Request | Client IP'yi ister |
| A | Acknowledge | Server onaylar |

## Gunluk hayat analojisi

Bir restoranda masa istemek gibi:

1. Discover: Bos masa var mi?
2. Offer: Su masa uygun.
3. Request: Tamam, o masayi istiyorum.
4. Ack: Masa sana ayrildi.

## Ders icindeki teknik detay

Client baslangicta IP bilmez. Bu yuzden:

```text
Source IP: 0.0.0.0
Destination IP: 255.255.255.255
Destination MAC: FF:FF:FF:FF:FF:FF
```

Broadcast yapar.

## Bunu neden ogreniyoruz?

DHCP sorunlarinda hangi asamada hata oldugunu anlamak icin DORA bilinmelidir.

## HATIRLA

Discover -> Offer -> Request -> Acknowledge

## KARMASHTIRMA!

| Paket | Kim gonderir? |
|---|---|
| Discover | Client |
| Offer | DHCP Server |
| Request | Client |
| Ack | DHCP Server |

## Kendini Test Et

**Soru 1:** DORA'nin ilk adimi nedir?  
**Cevap:** Discover.

**Soru 2:** DHCP Offer kimden gelir?  
**Cevap:** DHCP Server'dan.

**Soru 3:** DHCP Ack ne demektir?  
**Cevap:** IP atamasinin onaylanmasidir.

---

# 15. DHCP Guvenlik Riski

## Bu nedir?

DHCP'de kimlik dogrulama varsayilan olarak guclu degildir. Bu yuzden sahte DHCP server riski vardir.

## Saldiri senaryosu

Bir saldirgan aga sahte DHCP server koyarsa:

- client IP'yi saldirgandan alabilir,
- default gateway saldirgan cihaz olabilir,
- DNS saldirganin belirledigi sunucu olabilir,
- trafik saldirgan uzerinden gecebilir.

Bu, Rogue DHCP Server riskidir.

## Gunluk hayat analojisi

Gercek resepsiyon yerine sahte bir gorevli sana yanlis oda ve yanlis anahtar verirse, tum hareketin kontrol edilir.

## Bunu neden ogreniyoruz?

Blue Team tarafinda DHCP guvenligi onemlidir.

Alinabilecek onlemler:

- DHCP Snooping
- Switch port security
- Rogue DHCP tespiti
- NAC kullanimi
- Yetkisiz cihaz engelleme
- Log takibi

## HATIRLA

DHCP kolaylik saglar ama kontrolsuz birakilirsa saldiri yuzeyi olusturur.

## KARMASHTIRMA!

| Risk | Aciklama |
|---|---|
| Rogue DHCP | Sahte DHCP server |
| IP Conflict | Ayni IP'nin iki cihaza verilmesi |
| DHCP Starvation | IP havuzunu tüketme saldirisi |
| DNS Hijacking | Yanlis DNS ile trafigi yonlendirme |

## Kendini Test Et

**Soru 1:** Rogue DHCP nedir?  
**Cevap:** Yetkisiz/sahte DHCP server'dir.

**Soru 2:** DHCP saldirgan icin neden degerlidir?  
**Cevap:** Gateway ve DNS bilgilerini manipule edebilir.

**Soru 3:** DHCP guvenligi icin hangi ozellik kullanilabilir?  
**Cevap:** DHCP Snooping.

---

# 16. ICMP ve Ping'e Giris

## Bu nedir?

ICMP (Internet Control Message Protocol), agdaki hata ve kontrol mesajlari icin kullanilan protokoldur.

Ping, ICMP kullanan bir komuttur.

Dersin kritik cumlesi: Ping bir protokol degildir, komuttur. ICMP paketlerini kullanir.

## Gunluk hayat analojisi

Birine "Orada misin?" diye seslenmek gibi.

- Sen seslenirsin: Echo Request
- Karsi taraf cevap verir: Echo Reply

## Bunu neden ogreniyoruz?

ICMP ve Ping hedef ayakta mi, agda gecikme var mi, paket gidip geliyor mu ve firewall ICMP engelliyor mu gibi sorulari test eder.

## HATIRLA

Ping komuttur, ICMP protokoldur.

## KARMASHTIRMA!

| Kavram | Anlam |
|---|---|
| ICMP | Kontrol mesaj protokolu |
| Ping | ICMP kullanan test komutu |
| Echo Request | Gonderilen test mesaji |
| Echo Reply | Gelen cevap |

## Kendini Test Et

**Soru 1:** Ping protokol mudur?  
**Cevap:** Hayir, komuttur.

**Soru 2:** Ping hangi protokolu kullanir?  
**Cevap:** ICMP.

**Soru 3:** Ping neyi test eder?  
**Cevap:** Hedefe erisilebilirligi.

---

# GENEL TEKRAR VE OZET

## Tüm dersi tek cumleyle ozet

Bu ders, cihazlarin IP ile nasil adreslendigini, router/gateway uzerinden nasil yonlendirildigini, private-public IP donusumunun NAT ile nasil yapildigini, aglarin subnet/VLAN ile nasil bolundugunu ve DHCP ile IP yapilandirmasinin nasil otomatik verildigini anlatir.

## En kritik 10 bilgi

1. Network Layer, IP adresleme ve yonlendirme katmanidir.
2. IP connectionless calisir; teslim garantisi vermez.
3. IPv4 32 bit, IPv6 128 bittir.
4. IPv4 adresleri yetersiz kaldigi icin NAT ve IPv6 gelistirilmistir.
5. NAT, private IP'leri public IP'ye cevirir.
6. Default Gateway, baska aga cikis kapisidir.
7. Subnet Mask, IP'nin network ve host kismini ayirir.
8. CIDR, subnet mask'in kisa gosterimidir.
9. VLAN Layer 2, subnetting Layer 3 odaklidir.
10. DHCP cihazlara otomatik IP, gateway, subnet mask ve DNS verir.

## Siber guvenlik acisindan cikarim

Bu konular ezberlik degil, savunma ve saldiri analizinin temelidir. Bir saldirganin agda nasil hareket ettigini anlamak istiyorsan sunlari net bilmelisin:

- Hangi cihaz hangi subnet'te?
- Gateway neresi?
- NAT arkasinda mi?
- DHCP'den mi IP aliyor?
- VLAN izolasyonu var mi?
- ICMP/ping cevap veriyor mu?
- Firewall hangi aglar arasi gecise izin veriyor?

Burada bosluk varsa ag guvenligi tarafinda kör uçarsın.
