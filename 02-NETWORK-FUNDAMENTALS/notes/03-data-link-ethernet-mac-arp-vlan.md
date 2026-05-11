


## 1. Dersin Ana Haritasi
Ana odak: Data Link Layer, Ethernet, MAC Address, ARP, Broadcast/Collision Domain, VLAN ve Wireless LAN.

Bu derste islenen ana konular:

1. Network ogrenme sureci ve TryHackMe yaklasimi
2. OSI tekrar mantigi
3. Data Link Layer (Veri Baglanti Katmani)
4. LLC ve MAC alt katmanlari
5. Frame, Header, Trailer, FCS ve CRC
6. Ethernet teknolojisi
7. Koaksiyel, Ethernet ve fiber kablolar
8. MAC Address yapisi
9. Hexadecimal, binary ve 48-bit MAC mantigi
10. Ethernet Frame yapisi
11. Broadcast, Unicast, Multicast
12. Broadcast Domain
13. Collision Domain
14. Hub, Switch, Router farki
15. ARP (Address Resolution Protocol)
16. ARP Request / ARP Reply
17. ARP Table komutlari
18. Wireshark ile paket inceleme
19. VLAN
20. Wireless LAN / 802.11

---

## 2. Network Ogrenme Sureci

### Bu nedir?

Egitmen dersin basinda ogrencilerin "cok fazla kavram karisti" hissini normal karsiliyor. Cunku Network Fundamentals icinde kisa surede cok fazla yeni kavram geliyor:

- OSI
- TCP/IP
- Layer 2
- Layer 3
- MAC
- Frame
- Header
- Trailer
- CRC
- Ethernet
- ARP
- Broadcast
- Collision

Bu yuzden amac bir anda network admin olmak degil; **siber guvenlik icin gerekli network temelini oturtmak**.

### Gunluk hayat analojisi

Network ogrenmek, yeni bir sehri ogrenmek gibidir.

Ilk gun sokak isimleri karisir, hangi yolun nereye gittigi belirsiz olur. Bir sure sonra ana yollari, mahalleleri ve trafik mantigini ayirirsin. Network de aynidir: tekrar ve uygulama ile oturur.

### Bunu neden ogreniyoruz?

Cunku siber guvenlikte su terimler surekli karsina cikar:

- Layer 2 attack
- ARP spoofing
- MAC flooding
- VLAN hopping
- Packet capture
- Broadcast traffic
- Wireshark analysis

Bunlari anlamadan saldiriyi da savunmayi da dogru okuyamazsin.

> **HATIRLA:** Network'u ezberlemeye calisma. Katmanlarin ne ise yaradigini anla.

### KARMASTIRMA!

| Kavram | Dogru anlam |
|---|---|
| Network ogrenmek | Network admin olmak degildir |
| OSI bilmek | Her protokolu ezberlemek degildir |
| Layer 2 bilmek | Switch, MAC, Frame ve ARP mantigini anlamaktir |
| Siber guvenlik | Network temeli olmadan eksik kalir |

### Kendini test et

**1. Bu egitimde amac network admin yetistirmek mi?**  
Cevap: Hayir. Amac siber guvenlik icin temel network bilgisini vermektir.

**2. OSI katmanlarini bir gunde tamamen ogrenmek gercekci mi?**  
Cevap: Hayir. Tekrar ve uygulamayla oturur.

**3. Network bilgisi siber guvenlikte neden gereklidir?**  
Cevap: Cunku saldirilarin ve loglarin buyuk kismi ag trafigi uzerinden anlasilir.

---

## 3. Data Link Layer Nedir?

### Bu nedir?

**Data Link Layer (Veri Baglanti Katmani)**, OSI modelinin 2. katmanidir.

Gorevi:

- Fiziksel katmandan gelen sinyalleri anlamli dijital verilere cevirmek
- Network Layer'dan gelen paketleri fiziksel ortama gonderilebilir hale getirmek
- MAC adreslerini kullanmak
- Frame olusturmak
- Hata kontrolu yapmak

### Gunluk hayat analojisi

Data Link Layer'i apartman gorevlisi gibi dusun.

Kargo sehre kadar geldi. Ama apartmanda hangi daireye gidecek?

- IP adresi = apartmanin adresi
- MAC adresi = daire numarasi
- Data Link Layer = kargoyu dogru daireye goturen gorevli

### Konular arasi baglanti

Bir onceki konuda OSI modelini gorduk. Simdi o modelin ozellikle **Layer 2** kismina odaklaniyoruz. Cunku Layer 2, yerel agdaki cihazlarin nasil haberlesitigini aciklar.

### Bunu neden ogreniyoruz?

Cunku yerel ag saldirilari genellikle Layer 2'de gerceklesir:

- ARP spoofing
- MAC flooding
- VLAN hopping
- Broadcast storm
- Rogue device baglantisi

> **HATIRLA:** Data Link Layer = MAC + Frame + Ethernet + yerel ag iletisimi.

### KARMASTIRMA!

| Layer | Gorev |
|---|---|
| Layer 1 Physical | Sinyal tasir |
| Layer 2 Data Link | Frame olusturur, MAC kullanir |
| Layer 3 Network | IP kullanir, routing yapar |

### Kendini test et

**1. Data Link Layer OSI'nin kacinci katmanidir?**  
Cevap: 2. katmandir.

**2. Data Link Layer hangi adresi kullanir?**  
Cevap: MAC Address.

**3. Data Link Layer'daki veri birimi nedir?**  
Cevap: Frame.

---

## 4. LLC ve MAC Alt Katmanlari

### Bu nedir?

Data Link Layer iki alt bolume ayrilir:

1. **LLC (Logical Link Control)**
2. **MAC (Media Access Control)**

### LLC ne yapar?

LLC, ust katmandan gelen paketlerle Data Link Layer arasindaki mantiksal baglantiyi yonetir.

### MAC ne yapar?

MAC, fiziksel ortama erisimi ve donanimsal adreslemeyi yonetir.

Yani:

- Hangi cihaz gonderecek?
- Hangi cihaza gidecek?
- MAC adresi nedir?
- Frame icine hangi MAC bilgisi yazilacak?

### Gunluk hayat analojisi

Bir okul dusun:

- LLC = ogretmenin sinif ici duzeni saglamasi
- MAC = kapidaki guvenligin kimlik kontrolu yapmasi

LLC mantiksal duzeni saglar. MAC fiziksel erisimi kontrol eder.

### Bunu neden ogreniyoruz?

Cunku Ethernet frame icinde bizi en cok ilgilendiren bilgi MAC adresidir. Siber guvenlikte Layer 2 analiz yaparken MAC bilgisi kritik hale gelir.

> **HATIRLA:** Data Link Layer icinde guvenlik acisindan en cok MAC tarafi onemlidir.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| LLC | Mantiksal baglanti kontrolu |
| MAC | Fiziksel ortama erisim kontrolu |
| MAC Address | Cihazin Layer 2 kimligi |
| Ethernet Frame | Layer 2 veri paketi |

### Kendini test et

**1. LLC neyin kisaltmasidir?**  
Cevap: Logical Link Control.

**2. MAC neyin kisaltmasidir?**  
Cevap: Media Access Control.

**3. Ethernet frame icinde hangi adres bilgisi onemlidir?**  
Cevap: Source MAC ve Destination MAC.

---

## 5. Frame, Header, Trailer, FCS ve CRC

### Bu nedir?

Data Link Layer'da veri **Frame** haline gelir.

Frame icinde sunlar bulunur:

- Header
- Payload / Data
- Trailer

### Header nedir?

**Header**, paketin basina eklenen yonlendirme ve kontrol bilgisidir.

Ethernet header icinde genellikle:

- Destination MAC
- Source MAC
- EtherType

bulunur.

### Trailer nedir?

**Trailer**, frame'in sonuna eklenen kontrol bilgisidir.

### FCS nedir?

**FCS (Frame Check Sequence)**, frame'in bozulup bozulmadigini anlamak icin kullanilan kontrol alanidir.

### CRC nedir?

**CRC (Cyclic Redundancy Check)**, hata kontrolunde kullanilan matematiksel hesaplama yontemidir.

### Gunluk hayat analojisi

Bir kargo paketi dusun:

- Header = kargonun uzerindeki alici/gonderici etiketi
- Payload = kutunun icindeki urun
- Trailer/FCS = kargonun hasarli olup olmadigini gosteren kontrol bandi

### Bunu neden ogreniyoruz?

Cunku agda veri tasinirken bozulabilir. Sistem, gelen frame'in dogru gelip gelmedigini kontrol etmelidir.

Eger hata varsa:

- TCP tekrar isteyebilir.
- Bazi durumlarda frame dusurulur.
- Bazi durumlarda uygulama/isletim sistemi eksikligi tolere edebilir.

> **HATIRLA:** FCS hatayi duzeltmez; hatayi tespit etmeye yarar.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| Header | Baslik bilgisi |
| Payload | Tasinan gercek veri |
| Trailer | Sondaki kontrol bilgisi |
| FCS | Frame hata kontrol alani |
| CRC | Hata kontrol hesaplama yontemi |

### Kendini test et

**1. Frame hangi katmanda olusur?**  
Cevap: Data Link Layer.

**2. FCS ne ise yarar?**  
Cevap: Frame'in bozulup bozulmadigini kontrol eder.

**3. Header ile Trailer farki nedir?**  
Cevap: Header basta, Trailer sonda bulunur.

---

## 6. Ethernet Teknolojisi

### Bu nedir?

**Ethernet**, kablolu yerel aglarda kullanilan temel iletisim teknolojisidir.

Ders icinde Ethernet'in:

- 1980'lerde yayginlastigi
- 1983'te IEEE tarafindan 802.3 standardiyla standartlastirildigi
- Kablolu aglarda temel protokol oldugu

anlatiliyor.

### Gunluk hayat analojisi

Ethernet'i binadaki kablolu telefon hatti gibi dusun.

Herkes ayni binada ama iletisim belirli kablolar ve kurallar uzerinden yapilir.

### Ethernet neden ortaya cikti?

Amac, birden fazla bilgisayarin ayni ag ortaminda veri gonderebilmesini saglamakti.

Eski teknolojilerde veri cakismasi olabiliyordu. Bu yuzden **CSMA/CD** gibi yontemler gelistirildi.

### CSMA/CD nedir?

**CSMA/CD (Carrier Sense Multiple Access / Collision Detection)**, eski Ethernet ortamlarinda cakismayi algilamak icin kullanilan yontemdir.

Basitce:

1. Hat bos mu diye bak.
2. Bossa gonder.
3. Cakisma olursa dur.
4. Sonra tekrar dene.

### Bunu neden ogreniyoruz?

Cunku Ethernet, Layer 2'nin pratikteki en onemli protokoludur. Switch, MAC, frame ve LAN guvenligi Ethernet mantigina dayanir.

> **HATIRLA:** Ethernet = kablolu LAN dunyasinin temelidir.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| Ethernet | Kablolu ag teknolojisi |
| Wi-Fi | Kablosuz ag teknolojisi |
| IEEE 802.3 | Ethernet standardi |
| IEEE 802.11 | Kablosuz ag standardi |

### Kendini test et

**1. Ethernet hangi baglanti turudur?**  
Cevap: Kablolu baglantidir.

**2. Ethernet'in IEEE standardi nedir?**  
Cevap: 802.3.

**3. CSMA/CD ne ise yarar?**  
Cevap: Eski Ethernet ortamlarinda cakismayi algilamak icin kullanilir.

---

## 7. Kablo Turleri: Koaksiyel, Ethernet, Fiber

### Bu nedir?

Ders icinde uc ana kablo tipi geciyor:

1. **Koaksiyel Kablo**
2. **Ethernet Kablosu / Twisted Pair**
3. **Fiber Optik Kablo**

### Koaksiyel kablo nedir?

Eski TV, uydu, kamera ve kablo internet altyapilarinda kullanilan kablo turudur.

Ders ornekleri:

- Kamera tesisati
- Kablo TV
- Kablonet
- Eski baglantilar

### Ethernet kablosu nedir?

Icinde 8 tel bulunan, bukumlu ciftlerden olusan kablodur.

Ders icinde su detay veriliyor:

- 4 cift kablo vardir.
- Toplam 8 tel bulunur.
- Bazi baglantilarda 1, 2, 3 ve 6 numarali teller kullanilir.
- A ve B baglanti standartlari vardir.
- Genellikle B standardi tercih edilebilir.

### Fiber optik nedir?

Veriyi isik sinyalleriyle tasiyan kablodur.

### Gunluk hayat analojisi

- Koaksiyel = eski tek seritli yol
- Ethernet = cok seritli mahalle yolu
- Fiber = yuksek hizli tren hatti

### Bunu neden ogreniyoruz?

Cunku fiziksel ortam baglanti kalitesini, hizi, guvenilirligi ve guvenlik risklerini etkiler.

> **HATIRLA:** Kablo sadece tasiyici degildir; hiz, parazit ve guvenilirlik uzerinde dogrudan etkilidir.

### KARMASTIRMA!

| Kablo | Ozellik |
|---|---|
| Koaksiyel | Eski TV/kamera/kablonet altyapisi |
| Ethernet | Guncel kablolu LAN baglantisi |
| Fiber | Isikla yuksek hizli veri tasima |

### Kendini test et

**1. Ethernet kablosunda kac tel bulunur?**  
Cevap: Genellikle 8 tel bulunur.

**2. Fiber veri tasimak icin ne kullanir?**  
Cevap: Isik sinyalleri.

**3. Koaksiyel kabloya ornek kullanim nedir?**  
Cevap: Kablo TV, kamera sistemi, eski modem baglantilari.

---

## 8. MAC Address Nedir?

### Bu nedir?

**MAC Address (Media Access Control Address)**, ag kartinin fiziksel adresidir.

Ders icinde MAC adresi su sekilde anlatiliyor:

- Kisinin kimlik numarasi gibi dusunulebilir.
- Cihazi / ag kartini tanimlar.
- 48 bitten olusur.
- 6 bolum halinde yazilir.
- Hexadecimal gosterim kullanilir.
- Ilk 24 bit ureticiye aittir.
- Son 24 bit cihazin benzersiz kismidir.

### Gunluk hayat analojisi

MAC adresi = TC kimlik numarasi gibi.

IP adresi tasindigin yere gore degisebilir. MAC adresi ise cihazin ag kartina bagli kimlik gibidir.

### MAC adresi ornek yapisi

```text
80:00:20:7A:3F:3E
```

Bu yapi:

- 6 bolumden olusur.
- Her bolum hexadecimal yazilir.
- Toplam 48 bittir.

### Vendor ve Unique kismi

| Bolum | Anlam |
|---|---|
| Ilk 24 bit | Vendor / uretici bilgisi |
| Son 24 bit | Cihaza ozgu benzersiz bilgi |

Ornek ureticiler:

- Realtek
- Apple
- Cisco
- Fortinet

### Bunu neden ogreniyoruz?

Cunku Layer 2 analizinde MAC adresi cihazi tanimak icin kullanilir.

Siber guvenlikte MAC bilgisi su alanlarda onemlidir:

- ARP analizi
- MAC spoofing
- MAC flooding
- Switch guvenligi
- Wireshark paket inceleme
- Network access control

> **HATIRLA:** IP adresi agdaki konumu, MAC adresi cihazin fiziksel ag kimligini temsil eder.

### KARMASTIRMA!

| IP Address | MAC Address |
|---|---|
| Layer 3 | Layer 2 |
| Degisebilir | Genelde cihaza baglidir |
| Routing icin kullanilir | Yerel agda teslim icin kullanilir |
| Ornek: 192.168.1.10 | Ornek: 80:00:20:7A:3F:3E |

### Kendini test et

**1. MAC adresi kac bittir?**  
Cevap: 48 bittir.

**2. MAC adresinin ilk 24 biti neyi gosterir?**  
Cevap: Uretici/vendor bilgisini.

**3. MAC adresi hangi katmanda kullanilir?**  
Cevap: Data Link Layer / Layer 2.

---

## 9. Binary, Decimal ve Hexadecimal

### Bu nedir?

Ders icinde MAC adresi anlatilirken sayi sistemlerinden bahsediliyor:

- **Binary:** 0 ve 1'den olusur.
- **Decimal:** Gunluk kullandigimiz 10'luk sistemdir.
- **Hexadecimal:** 0-9 ve A-F karakterlerini kullanir.

### Hexadecimal neden kullanilir?

Cunku binary cok uzundur. Hexadecimal, binary veriyi daha kisa gostermeyi saglar.

Ornek:

```text
F = 1111
A = 1010
8 = 1000
0 = 0000
```

### Gunluk hayat analojisi

Binary uzun bir telefon numarasini tek tek okumak gibidir. Hexadecimal ise ayni bilgiyi daha kisa kodla yazmak gibidir.

### Bunu neden ogreniyoruz?

MAC adresleri hexadecimal yazilir. Wireshark, firewall loglari, packet capture ciktilari ve exploit analizlerinde hexadecimal veriler sik gorulur.

> **HATIRLA:** Hexadecimal, binary verinin kisa yazilmis halidir.

### KARMASTIRMA!

| Sistem | Karakterler |
|---|---|
| Binary | 0 ve 1 |
| Decimal | 0-9 |
| Hexadecimal | 0-9, A-F |

### Kendini test et

**1. Binary sistem hangi karakterlerden olusur?**  
Cevap: 0 ve 1.

**2. Hexadecimal sistemde F neyi temsil eder?**  
Cevap: Decimal 15 degerini.

**3. MAC adresleri hangi sistemle yazilir?**  
Cevap: Hexadecimal.

---

## 10. Ethernet Frame Yapisi

### Bu nedir?

Ethernet Frame, Data Link Layer'da olusturulan veri yapisidir.

Genel alanlar:

- Preamble / oncu alan
- Destination MAC
- Source MAC
- EtherType
- Payload
- FCS

### Alanlarin anlami

| Alan | Gorev |
|---|---|
| Preamble | Aliciyi veri gelecegine hazirlar |
| Destination MAC | Hedef cihazin MAC adresi |
| Source MAC | Gonderen cihazin MAC adresi |
| EtherType | Ust katmandaki protokol tipini belirtir |
| Payload | Tasinan veri |
| FCS | Hata kontrolu |

### Gunluk hayat analojisi

Bir kargo etiketi dusun:

- Alici adresi = Destination MAC
- Gonderen adresi = Source MAC
- Paket turu = EtherType
- Icindeki urun = Payload
- Hasar kontrol etiketi = FCS

### Bunu neden ogreniyoruz?

Cunku Wireshark'ta paket incelerken bu alanlari goreceksin. MAC spoofing ve ARP saldirilari da bu alanlarin manipule edilmesiyle ilgilidir.

> **HATIRLA:** Ethernet Frame icinde MAC bilgileri gorunur; IP bilgisi daha ust katmandadir.

### Kendini test et

**1. Destination MAC neyi gosterir?**  
Cevap: Frame'in gidecegi hedef cihazin MAC adresini.

**2. Source MAC neyi gosterir?**  
Cevap: Frame'i gonderen cihazin MAC adresini.

**3. EtherType ne ise yarar?**  
Cevap: Ust katmandaki protokol tipini belirtir.

---

## 11. Unicast, Multicast ve Broadcast

### Bu nedir?

Agda uc temel yayin tipi vardir:

### Unicast

Bir cihazdan bir cihaza iletisimdir.

Ornek: Senin bilgisayarindan bir server'a istek gitmesi.

### Multicast

Bir cihazdan secili bir gruba iletisimdir.

Ders icindeki analoji:

- IPTV
- Netflix benzeri uyelikli yayin mantigi

Herkes aga bagli olabilir ama sadece secili grup yayini alir.

### Broadcast

Bir cihazdan agdaki herkese gonderilen yayindir.

Ornek: "Bu IP kime ait?" diye ARP sorgusu.

### Gunluk hayat analojisi

| Yayin tipi | Gunluk hayat |
|---|---|
| Unicast | Bir kisiye ozel mesaj |
| Multicast | Sadece siniftaki belirli gruba mesaj |
| Broadcast | Okul hoparlorunden herkese duyuru |

### Bunu neden ogreniyoruz?

Cunku ARP, DHCP gibi bazi ag islemleri broadcast kullanir. Fazla broadcast trafik ag performansini bozabilir.

> **HATIRLA:** Broadcast herkese gider; Unicast tek kisiye gider; Multicast secili gruba gider.

### KARMASTIRMA!

| Kavram | Kime gider? |
|---|---|
| Unicast | Tek hedefe |
| Multicast | Secili gruba |
| Broadcast | Herkese |

### Kendini test et

**1. Unicast nedir?**  
Cevap: Bir kaynaktan tek hedefe iletisimdir.

**2. Multicast'e ornek nedir?**  
Cevap: IPTV uyelerine yapilan yayin.

**3. Broadcast ne demektir?**  
Cevap: Agdaki herkese yapilan yayindir.

---

## 12. Broadcast Domain

### Bu nedir?

**Broadcast Domain**, bir broadcast mesajinin ulasabildigi ag alanidir.

Bir cihaz broadcast gonderdiginde, mesajin ulastigi tum cihazlar ayni broadcast domain icindedir.

### Router ne yapar?

Router broadcast domain'i boler.

Yani broadcast mesaji router'in otesine normalde gecmez.

### Gunluk hayat analojisi

Bir sinifta ogretmen "herkes dinlesin" dediginde sadece o siniftakiler duyar. Koridordaki baska sinif duymaz.

Sinif = Broadcast Domain  
Kapi/duvar = Router siniri

### Bunu neden ogreniyoruz?

Cunku buyuk broadcast domain performans ve guvenlik riski olusturabilir.

Riskler:

- Broadcast storm
- Gereksiz trafik
- Ag yavaslamasi
- Saldirganin daha fazla cihazi kesfetmesi

> **HATIRLA:** Router broadcast trafigini sinirlar.

### KARMASTIRMA!

| Cihaz | Broadcast davranisi |
|---|---|
| Hub | Geleni herkese yayar |
| Switch | Ayni VLAN icinde broadcast yayar |
| Router | Broadcast domain'i boler |

### Kendini test et

**1. Broadcast Domain nedir?**  
Cevap: Broadcast mesajinin ulasabildigi ag alanidir.

**2. Router broadcast domain'i boler mi?**  
Cevap: Evet.

**3. Broadcast Storm nedir?**  
Cevap: Broadcast trafiginin asiri artarak agi zorlamasidir.

---

## 13. Collision Domain

### Bu nedir?

**Collision Domain**, veri cakismasinin yasanabilecegi ag alanidir.

Eski aglarda ayni ortami kullanan cihazlar ayni anda veri gonderirse cakisma olusabilirdi.

### Hub neden risklidir?

Hub, gelen veriyi kime gidecegine bakmadan herkese gonderir. Bu yuzden cakisma ihtimali yuksektir.

### Switch neden daha iyidir?

Switch, hangi cihazin hangi portta oldugunu ogrenir. Boylece veriyi daha hedefli gonderir ve cakisma ihtimalini azaltir.

### Gunluk hayat analojisi

Tek seritli kopru dusun.

- Ayni anda iki arac girerse carpisir.
- Bu Half Duplex gibidir.

Cift yonlu yol dusun.

- Araclar ayni anda gidip gelebilir.
- Bu Full Duplex gibidir.

### Bunu neden ogreniyoruz?

Cunku ag performansi ve tasariminda collision domain mantigi onemlidir. Ayrica eski cihazlar, hub yapilari ve hatali network tasarimlari guvenlik ve performans sorunlari dogurabilir.

> **HATIRLA:** Hub cakisma uretir; switch cakismayi azaltir.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| Broadcast Domain | Yayinin ulastigi alan |
| Collision Domain | Cakismanin yasanabilecegi alan |
| Hub | Buyuk collision domain olusturur |
| Switch | Her portu ayri collision domain gibi yonetebilir |

### Kendini test et

**1. Collision Domain nedir?**  
Cevap: Veri cakismasinin yasanabilecegi ag alanidir.

**2. Hub neden sorunludur?**  
Cevap: Gelen veriyi herkese gonderdigi icin cakisma ihtimali yuksektir.

**3. Full Duplex ne saglar?**  
Cevap: Ayni anda veri gonderme ve alma imkani saglar.

---

## 14. Hub, Switch ve Router Farki

### Bu nedir?

Ag cihazlarinin gorevleri farklidir.

### Hub

- Eski teknolojidir.
- Gelen veriyi herkese gonderir.
- Akilli degildir.
- Collision riski yuksektir.

### Switch

- Ayni yerel agdaki cihazlari baglar.
- MAC tablosu tutar.
- Veriyi dogru porta gondermeye calisir.
- Hub'a gore daha akillidir.

### Router

- Farkli aglari birbirine baglar.
- IP ve routing mantigiyla calisir.
- Broadcast domain'i boler.

### Gunluk hayat analojisi

| Cihaz | Analoji |
|---|---|
| Hub | Herkese bagiran kisi |
| Switch | Kimin nerede oturdugunu bilen sekreter |
| Router | Sehirlerarasi yonlendirme yapan navigasyon |

### Bunu neden ogreniyoruz?

Cunku saldiri ve savunma stratejileri cihaza gore degisir:

- Hub ortaminda sniffing kolaydir.
- Switch ortaminda MAC flooding denenebilir.
- Router seviyesinde ACL/firewall/routing analizi yapilir.

> **HATIRLA:** Hub aptal dagiticidir, switch MAC'e bakar, router IP'ye bakar.

### Kendini test et

**1. Hub gelen veriyi kime gonderir?**  
Cevap: Herkese.

**2. Switch hangi tabloyu kullanir?**  
Cevap: MAC table.

**3. Router hangi katmanda calisir?**  
Cevap: Genellikle Layer 3 / Network Layer.

---

## 15. ARP Nedir?

### Bu nedir?

**ARP (Address Resolution Protocol)**, IP adresinden MAC adresini bulmaya yarayan protokoldur.

Soru sudur:

> "Bu IP adresi kime ait? Bana MAC adresini soyle."

### ARP neden gerekir?

Bilgisayar bir IP'ye veri gondermek ister. Ama yerel agda fiziksel teslim icin MAC adresi gerekir.

Bu yuzden ARP devreye girer.

### ARP Request

Bilgisayar agdaki herkese sorar:

```text
Who has 192.168.1.10?
```

Bu broadcast'tir.

### ARP Reply

Ilgili cihaz cevap verir:

```text
192.168.1.10 benim. MAC adresim sudur.
```

Bu genellikle unicast olarak doner.

### Gunluk hayat analojisi

Bir apartmana girdin ve "Ahmet hangi dairede?" diye herkese sordun. Bu ARP Request'tir.

Ahmet cevap verdi: "Ben 5 numaradayim." Bu ARP Reply'dir.

### Bunu neden ogreniyoruz?

Cunku ARP yerel ag saldirilarinin merkezindedir.

Ozellikle:

- ARP spoofing
- ARP poisoning
- Man-in-the-Middle
- Yerel ag trafigi dinleme
- Gateway taklidi

ARP mantigini bilmeden Layer 2 saldirilarini anlamak mumkun degildir.

> **HATIRLA:** ARP, IP'yi MAC'e cevirir.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| ARP Request | MAC adresini ogrenmek icin broadcast soru |
| ARP Reply | MAC adresiyle verilen cevap |
| ARP Table | IP-MAC eslesme tablosu |
| ARP Spoofing | Sahte IP-MAC eslesmesi gonderme saldirisi |

### Kendini test et

**1. ARP ne ise yarar?**  
Cevap: IP adresinden MAC adresini bulur.

**2. ARP Request broadcast midir?**  
Cevap: Evet.

**3. ARP Reply ne icerir?**  
Cevap: Ilgili IP'nin MAC adresini.

---

## 16. ARP Table ve Komutlar

### Bu nedir?

**ARP Table**, bilgisayarin ogrendigi IP-MAC eslesmelerini tuttugu tablodur.

Ders icinde su komutlardan bahsediliyor:

```bash
arp -a
```

ARP tablosunu gosterir.

```bash
arp -s
```

Statik ARP kaydi eklemek icin kullanilir.

```bash
arp -d
```

ARP kaydi silmek icin kullanilir.

### Gunluk hayat analojisi

ARP Table = telefon rehberi.

Telefon rehberinde:

- Isim = IP adresi
- Telefon numarasi = MAC adresi

Birini aramak icin her seferinde herkese sormazsin. Rehbere bakarsin.

### Bunu neden ogreniyoruz?

Cunku saldirgan ARP tablosunu manipule ederse trafik yanlis cihaza gidebilir.

Ornegin saldirgan kendini gateway gibi gosterebilir.

> **HATIRLA:** ARP Table RAM'de tutulur; sistem yeniden basladiginda dinamik kayitlar kaybolabilir.

### Kendini test et

**1. `arp -a` ne yapar?**  
Cevap: ARP tablosunu gosterir.

**2. ARP tablosu ne tutar?**  
Cevap: IP-MAC eslesmelerini.

**3. ARP tablosu neden guvenlik acisindan onemlidir?**  
Cevap: Sahte kayitlar trafigi saldirgana yonlendirebilir.

---

## 17. Wireshark ile Paket Inceleme

### Bu nedir?

**Wireshark**, ag paketlerini yakalamaya ve incelemeye yarayan aractir.

Ders icinde Wireshark ile:

- ARP paketleri
- Request / Reply yapisi
- Broadcast MAC
- Hedef MAC bilinmediginde 00:00:00:00:00:00 kullanimi
- FF:FF:FF:FF:FF:FF broadcast adresi

gibi yapilarin gorulebilecegi anlatiliyor.

### Gunluk hayat analojisi

Wireshark = guvenlik kamerasi.

Normalde agda paketler gorunmez. Wireshark, bu paketleri yakalayip "kim kime ne gonderdi?" diye gosterir.

### Bunu neden ogreniyoruz?

Cunku gercek analiz araclarla yapilir.

Siber guvenlikte Wireshark sunlar icin kullanilir:

- Trafik analizi
- ARP spoofing tespiti
- DNS sorgusu inceleme
- TCP handshake inceleme
- Supheli baglanti analizi
- Malware trafik analizi

> **HATIRLA:** Wireshark sana teoriyi gercek paket uzerinde gosterir.

### Kendini test et

**1. Wireshark ne ise yarar?**  
Cevap: Ag paketlerini yakalar ve analiz eder.

**2. ARP Request'te hedef MAC bilinmiyorsa ne olur?**  
Cevap: Target MAC alani bos/0 olarak gorulebilir.

**3. Broadcast MAC adresi nasil gosterilir?**  
Cevap: FF:FF:FF:FF:FF:FF.

---

## 18. VLAN Nedir?

### Bu nedir?

**VLAN (Virtual Local Area Network)**, fiziksel olarak ayni switch uzerinde bulunan cihazlari mantiksal olarak farkli aglara ayirma yontemidir.

Ornek:

- Muhasebe VLAN
- Insan Kaynaklari VLAN
- AR-GE VLAN
- Satis VLAN

### Gunluk hayat analojisi

Ayni binada farkli departmanlar dusun.

- Muhasebe ayri odada
- Insan kaynaklari ayri odada
- AR-GE ayri odada

Ayni binadalar ama herkes her yere giremiyor.

### Bunu neden ogreniyoruz?

Cunku VLAN guvenligi artirir.

Saldirgan bir departmana girse bile diger departmanlara kolayca gecememelidir.

### Siber guvenlik baglantisi

VLAN su amaclarla kullanilir:

- Segmentasyon
- Yetki sinirlandirma
- Broadcast domain kucultme
- Kritik sistemleri ayirma
- Misafir agini ic agdan ayirma

> **HATIRLA:** VLAN, agi mantiksal parcalara boler.

### KARMASTIRMA!

| Kavram | Aciklama |
|---|---|
| LAN | Fiziksel/yerel ag |
| VLAN | Mantiksal bolunmus yerel ag |
| Subnet | IP adresleme bolumu |
| Broadcast Domain | Yayinin ulastigi alan |

### Kendini test et

**1. VLAN ne ise yarar?**  
Cevap: Ayni fiziksel agdaki cihazlari mantiksal olarak ayirir.

**2. VLAN guvenligi artirir mi?**  
Cevap: Evet, segmentasyon saglar.

**3. VLAN sadece kablosuz aglarda mi kullanilir?**  
Cevap: Hayir, switch tabanli kablolu aglarda da kullanilir.

---

## 19. Wireless LAN ve IEEE 802.11

### Bu nedir?

**Wireless LAN**, kablosuz yerel agdir.

IEEE standardi:

```text
802.11
```

Ders icinde Ethernet icin **802.3**, kablosuz aglar icin **802.11** standardi anlatiliyor.

### Wi-Fi nasil calisir?

Kablo yerine radyo frekansi kullanir.

Ornek frekanslar:

- 2.4 GHz
- 5 GHz

### Gunluk hayat analojisi

Ethernet = kablolu telefon  
Wi-Fi = telsiz konusmasi

Kabloda hat daha kontrolludur. Kablosuzda ortam paylasimlidir ve parazit/cakisma daha olasidir.

### Bunu neden ogreniyoruz?

Cunku kablosuz aglar saldiriya daha aciktir:

- Evil Twin
- Deauthentication attack
- WPA/WPA2 cracking
- Rogue Access Point
- Wi-Fi sniffing
- Signal jamming

> **HATIRLA:** 802.3 kablolu Ethernet, 802.11 kablosuz Wi-Fi standardidir.

### KARMASTIRMA!

| Standart | Anlam |
|---|---|
| IEEE 802.3 | Ethernet |
| IEEE 802.11 | Wireless LAN / Wi-Fi |
| 2.4 GHz | Daha genis kapsama, daha fazla kalabalik |
| 5 GHz | Daha hizli, daha kisa kapsama |

### Kendini test et

**1. Wi-Fi hangi IEEE standardiyla iliskilidir?**  
Cevap: 802.11.

**2. Ethernet hangi IEEE standardiyla iliskilidir?**  
Cevap: 802.3.

**3. Kablosuz aglarda neden cakisma/parazit daha sik olabilir?**  
Cevap: Ayni ortamda bircok cihaz radyo sinyali yaydigi icin.

---

## 20. Genel Tekrar ve Ozet

| Konu | Tek cumlelik ozet |
|---|---|
| Data Link Layer | Yerel agda frame ve MAC adresleriyle veri iletimini saglar. |
| LLC | Ust katmanlarla mantiksal baglantiyi yonetir. |
| MAC | Fiziksel ortama erisimi ve MAC adreslemeyi yonetir. |
| Frame | Layer 2'deki veri birimidir. |
| Header | Frame'in baslik bilgisidir. |
| Trailer | Frame'in son kontrol bilgisidir. |
| FCS | Frame'in bozulup bozulmadigini kontrol eder. |
| CRC | Hata kontrol algoritmasidir. |
| Ethernet | Kablolu LAN teknolojisidir. |
| 802.3 | Ethernet standardidir. |
| 802.11 | Wireless LAN standardidir. |
| MAC Address | Ag kartinin fiziksel kimligidir. |
| Broadcast | Herkese yapilan yayindir. |
| Unicast | Tek hedefe yapilan iletisimdir. |
| Multicast | Secili gruba yapilan yayindir. |
| Broadcast Domain | Broadcast'in ulasabildigi alandir. |
| Collision Domain | Veri cakismasinin yasanabilecegi alandir. |
| Hub | Gelen veriyi herkese gonderir. |
| Switch | MAC adresine gore yonlendirir. |
| Router | IP'ye gore aglar arasi yonlendirme yapar. |
| ARP | IP adresinden MAC adresi bulur. |
| ARP Table | IP-MAC eslesmelerini tutar. |
| VLAN | Agi mantiksal olarak boler. |
| Wireshark | Paket yakalama ve analiz aracidir. |

## En kritik sonuc

**Layer 2 dunyasini anlamadan yerel ag guvenligini anlayamazsin. MAC, Ethernet, ARP, Broadcast, Collision ve VLAN konulari; hem network troubleshooting hem de siber guvenlik saldiri analizi icin temel yapi taslaridir.**
