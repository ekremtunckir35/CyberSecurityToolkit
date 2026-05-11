# Network Fundamentals – Ders 9

<div align="center">

![Ders İnfografiği](../assets/09-transport-layer-tcp-udp-ports.png)

</div>

---

## Transport Layer · TCP · UDP · Port Kavramı

> **Hedef:** Hiçbir teknik bilgisi olmayan biri bile anlasın diye hazırlandı. Sıfırdan, adım adım, analogilerle.

**Kapsam:** OSI Modeli 4. Katman | Three-Way Handshake | Port Kategorileri | Wireshark Uygulaması

---

## İçindekiler

1. [OSI Modeli – Neredeyiz? Bağlantı Kuralım](#bolum-1)
2. [Transport Layer – Taşıma Katmanı](#bolum-2)
3. [Port Kavramı – Fiziksel mi, Mantıksal mı?](#bolum-3)
4. [TCP – Transmission Control Protocol](#bolum-4)
5. [Three-Way Handshake – Üç Yollu El Sıkışma](#bolum-5)
6. [TCP Bayrakları (Flags)](#bolum-6)
7. [TCP Başlığı (Header)](#bolum-7)
8. [UDP – User Datagram Protocol](#bolum-8)
9. [Port Numarası Kategorileri](#bolum-9)
10. [Yaygın Kullanılan Port Numaraları](#bolum-10)
11. [Wireshark ile Uygulamalı İnceleme](#bolum-11)
12. [Siber Güvenlik Perspektifi: Açık Portlar](#bolum-12)
13. [Genel Tekrar ve Özet](#ozet)

---

## Bölüm 1 · OSI Modeli – Neredeyiz? Bağlantı Kuralım {#bolum-1}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Siber güvenlikte bir saldırıyı ya da savunmayı anlamak için paketin hangi katmandan geçtiğini bilmek zorundayız. Katmanları bilmeden Wireshark'ta gördüğün şeyleri yorumlayamazsın, güvenlik duvarı (firewall) kurallarını yazamazsın.

Bu ders, daha önceki derslerle birebir bağlantılı. Önceki derslerde OSI Modelinin ilk dört katmanını incelemiştik. Hepsini bir tablo olarak görelim ve bugün nerede çalıştığımızı işaretleyelim:

| Katman | Ad | Önemli Protokoller |
|--------|----|--------------------|
| 7 | Application (Uygulama) | HTTP, SMTP, DNS… |
| 6 | Presentation (Sunum) | Şifreleme, kodlama |
| 5 | Session (Oturum) | Oturum yönetimi |
| **4** | **▶ Transport (Taşıma) ← BUGÜNKÜ DERSIMIZ** | **TCP, UDP · Port** |
| 3 | Network (Ağ) | IP, ARP, ICMP |
| 2 | Data Link (Veri Bağlantı) | MAC adresi, Ethernet |
| 1 | Physical (Fiziksel) | Kablo, sinyal |

> 🔗 **BAĞLANTI:** Önceki derslerde 2. katmanda **MAC adresi**, 3. katmanda **IP adresi** öğrendik. Bugün 4. katmanda **Port numarası** kavramını öğreneceğiz. Her katman bir öncekinin üstüne bilgi ekler.

### 🏠 Günlük Hayat Analojisi – Kargo Gönderme

Bir kargo gönderdiğinde üstüne ne yazarsın?

- **Gönderenin adı-soyadı** → Data Link katmanı → *MAC adresi* (kim gönderdi?)
- **Adres bilgisi (şehir, mahalle, sokak)** → Network katmanı → *IP adresi* (nereye gidecek?)
- **Daire numarası (içerideki ilgili birim)** → Transport katmanı → *Port numarası* (hangi servise gidecek?)

### ✏️ Kendini Test Et – Bölüm 1

**S-01:** OSI modelinde Transport Layer kaçıncı katmandır?
> ✅ **Cevap:** 4. katmandır.

**S-02:** MAC adresi OSI'nin hangi katmanında eklenir?
> ✅ **Cevap:** 2. katmanda, Data Link (Veri Bağlantı) katmanında eklenir.

**S-03:** Kargo analojisinde "daire numarası" neye karşılık gelir?
> ✅ **Cevap:** Port numarasına karşılık gelir. Aynı IP adresindeki (aynı bina) farklı servislere (farklı daireler) ulaştırmayı sağlar.

---

## Bölüm 2 · Transport Layer – Taşıma Katmanı {#bolum-2}

> 🎯 **Bunu Neden Öğreniyoruz?**
> İnternette gönderip aldığın her şey — e-posta, video, web sayfası, oyun verisi — Transport Layer üzerinden geçer. Bu katmanın ne iş yaptığını anlamak, bir iletişimin neden yavaş, hatalı veya güvensiz olduğunu anlamana yardımcı olur.

Transport Layer'ın temel görevi: **Gönderici ile alıcı arasındaki veri akışını yönetmek, verinin hatasız ve doğru sırayla ulaştığından emin olmak.**

### Segmentation (Bölümleme)

Büyük bir veriyi internette tek parça olarak göndermek mümkün değil.

> 🍕 **Analoji – Pizza Dilimleme:** Büyük bir pizzayı tek seferde ısırabilir misin? Tabii ki hayır. Önce dilimlerine ayırırsın, sonra tek tek yersin. Transport Layer da büyük veriyi **segment** adı verilen küçük parçalara böler. Her segmente bir *sıra numarası (Sequence Number)* verir. Karşı taraf bu numaraları kullanarak segmentleri doğru sırayla birleştirir.

Transport Layer hem böler **(segmentation)** hem de birleştirir **(reassembling)**. Yukarıdan (Application katmanından) gelirken böler, aşağıdan (Network katmanından) gelirken birleştirir.

### Akış Kontrolü (Flow Control)

Hoca şöyle bir örnek verdi: Berko Hocam aynı anda internette birçok iş yapıyor ve sistemi yavaşlamış. Bu durumda Transport Layer, gönderene şunu söyler: *"Bana şu an bu kadarlık veri gönderebilirsin, fazlasını kaldıramam."*

Bunu TCP Header'daki **Window Size (Pencere Boyutu)** alanı ile yapar.

### Hata Kontrolü (Error Control)

20 segment gönderdik. 4 numaralı segment hasarlı geldi. İki farklı tepki:

- **TCP kullanılıyorsa:** "4 numaralı segmenti tekrar gönder!" der ve eksiksiz birleştirir.
- **UDP kullanılıyorsa:** Hasarlı segmenti düşürür ve ilerler, beklemez.

### Servis Adresleme (Service Point Addressing)

IP adresi bizi doğru binaya götürür. Ama binanın içindeki hangi bölüme gideceğiz?

> 🏥 **Analoji – Hastane:** Şehir Hastanesinin adresi = **IP Adresi** (binaya ulaştırır). Ortopedi servisi / Dahiliye / Göz polikliniği = **Port Numarası** (içerideki doğru birime ulaştırır).

> 💡 **HATIRLA:** **Routing (Yönlendirme)** → IP Protokolünün görevi (3. katman). **Akış / Hata / Servis yönetimi** → Transport Layer'ın görevi (4. katman). Transport Layer paketi nereye göndereceğine karar vermez. Ama paketin nasıl, ne kadar hızlı ve ne kadar güvenli gideceğine karar verir.

### ✏️ Kendini Test Et – Bölüm 2

**S-01:** Segmentation ne demektir?
> ✅ **Cevap:** Büyük veriyi daha küçük parçalara (segment) bölmek demektir. Her parçaya sıra numarası verilir.

**S-02:** Window Size ne işe yarar?
> ✅ **Cevap:** Alıcının o anda ne kadar veri alabileceğini gönderene bildiren akış kontrol mekanizmasıdır.

**S-03:** Yönlendirme (Routing) hangi katmanın görevidir?
> ✅ **Cevap:** 3. katmanın (Network Layer) görevidir. IP protokolü bu işi yapar.

---

## Bölüm 3 · Port Kavramı – Fiziksel mi, Mantıksal mı? {#bolum-3}

> 🎯 **Bunu Neden Öğreniyoruz?**
> "Port" kelimesi siber güvenlikte çok kritik. Port taraması (port scanning) saldırıların temel adımıdır. NMAP gibi araçlarla açık portları tespit etmek, hem savunma hem saldırı perspektifinden zorunlu bir beceridir.

### Fiziksel Portlar (Port Parts)

Bunları gözle görebilir, elle tutabilirsin:

| Port Adı | Ne İçin? |
|----------|----------|
| USB 1.0, 2.0, 3.0 | Klavye, mouse, flash bellek bağlantısı |
| HDMI / Display Port / DVI | Monitör / projeksiyon görüntüsü aktarımı |
| Ethernet (RJ-45) | İnternet kablosu bağlantısı |
| SATA | Hard diskleri kasaya bağlamak için |
| FireWire | Eski nesil hızlı veri aktarımı |
| Optical Audio | Gelişmiş ses sistemleri |
| PS/2 | Eski klavye ve mouse bağlantısı |

Switch'teki numaralı bağlantı noktaları da fiziksel port olarak adlandırılır.

### Soket (Socket) Nedir? Port ile Farkı?

> 🔌 **Soket:** Fizikte bir şeyi takabileceğin delik/yuva. Duvardan elektrik prizi soketi gibi. "Sokete taktınız mı?" derken bağlantıyı kurdunuz mu diye soruyoruz.
> 
> **Port:** Veri iletimi için kullanılan bağlantı noktası. Tüm soketler veri iletiminden sorumlu değil, ama portlar mutlaka veri transferiyle ilgili.
> 
> Kısaca: *İkisi benzer anlam taşır, ağ dünyasında sıkça birbirinin yerine kullanılır.*

### Mantıksal Portlar (Logical Ports) – Asıl Konumuz

Bunlar fiziksel değil, yazılım düzeyinde var olan **sanal kapılar**.

Hoca soruyor: "Ben aynı anda 6 tane farklı web sayfasını açtım. Benim tek bir IP adresim var. Bu nasıl mümkün?"

> 🏬 **Analoji – Alışveriş Merkezi:** AVM'ye girdiniz. IP adresiniz AVM'nin adresi. Ama içeride:
> - Ayakkabı almak istiyorsanız → Ayakkabı mağazasına gidiyorsunuz *(Belirli bir porta)*
> - Sinema istiyorsanız → Sinema salonuna gidiyorsunuz *(Başka bir porta)*
> - Kahve istiyorsanız → Kahveciye gidiyorsunuz *(Yine başka bir porta)*

TCP'de **0 ile 65.535** arasında (toplam **65.536 tane**) mantıksal port var.

```
# Port sayısının matematiksel açıklaması
TCP başlığında port alanı = 16 bit
2 üzeri 16 = 65.536
Port aralığı = 0 ile 65.535 arası
# UDP'nin de aynı şekilde 0-65535 arası kendi portları var
```

> ⚠️ **KARIŞTIRMA!**
> - **Fiziksel Port** ≠ **Mantıksal Port**
> - "Switch'in 5 numaralı portuna takıldım" → FİZİKSEL port (elle tutulur, gözle görülür)
> - "HTTP 80 numaralı portta çalışır" → MANTIKSAL port (yazılım düzeyinde, gözle görülmez)

### ✏️ Kendini Test Et – Bölüm 3

**S-01:** TCP ve UDP protokolleri kaçar tane mantıksal porta sahiptir?
> ✅ **Cevap:** Her biri 0'dan 65.535'e kadar, yani 65.536 tane porta sahiptir. Bu sayı 16 bit'ten gelir (2¹⁶ = 65.536).

**S-02:** Neden tek bir IP adresinden aynı anda birden fazla web sitesine bağlanabilirsiniz?
> ✅ **Cevap:** Çünkü her bağlantı farklı bir port numarası kullanır. IP adresi binayı, port numarası ise o binanın içindeki farklı servisleri (daireleri) temsil eder.

**S-03:** Port numarası 16 bit uzunluğunda olduğunda kaç farklı değer alabilir?
> ✅ **Cevap:** 2¹⁶ = 65.536 farklı değer alabilir (0 ile 65.535 arasında).

---

## Bölüm 4 · TCP – Transmission Control Protocol {#bolum-4}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Siber güvenlikte Wireshark ile paket analizi yaparken gördüğünüz SYN, ACK, FIN paketleri TCP'ye ait. TCP bağlantılarını anlamak, bir saldırıyı (örneğin SYN flood saldırısı) tespit etmek için temeldir.

**TCP (Transmission Control Protocol)** = Türkçe'de *İletim Kontrol Protokolü*. Güvenilir iletişim için kullanılan bir protokoldür.

| Özellik | TCP |
|---------|-----|
| Bağlantı tipi | Connection Oriented (Bağlantı Odaklı) |
| Güvenilirlik | ✅ Yüksek – Her paket kontrol edilir |
| Hata kontrolü | ✅ Var – Kayıp paketler tekrar istenir |
| Hız | ⚠️ Göreceli yavaş (güvenlik bedeli) |
| Kullanıldığı yerler | Web (HTTP/HTTPS), E-posta (SMTP), Dosya transferi (FTP) |

> 📦 **Analoji – İadeli Taahhütlü Kargo:** Bir arkadaşına güzel bir paket gönderiyorsun: çiçek, çikolata ve el yazısıyla not. Kurye seni önce arıyor: *"Ben şu adresim, kargoyu teslim edeceğim, onay var mı?"* Sen onaylıyorsun. Teslim ettikten sonra da sana mesaj geliyor: *"Paketiniz saat 14:35'te teslim edildi."* İşte bu TCP. Her adımda onay var, geri bildirim var, güvenli.

> 💡 **HATIRLA:** TCP yavaş mı? Evet. Neden? Çünkü her gönderilen segment için onay (ACK) bekler. Kaybolan segmenti tekrar ister. Bu güvenlik mekanizması hızı biraz düşürür ama verinin eksiksiz gitmesini garantiler.

---

## Bölüm 5 · Three-Way Handshake – Üç Yollu El Sıkışma {#bolum-5}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Mülakatlarda TCP'nin nasıl çalıştığı sorusu mutlaka gelir. Ayrıca Wireshark'ta bir SYN flood saldırısını tanımak için Three-Way Handshake'i çok iyi bilmek gerekir. SYN paketlerinin sayısı anormal şekilde artıyorsa saldırı var demektir.

TCP'de veri transferi başlamadan önce **mutlaka** bir ön anlaşma gerekir. Bu anlaşma 3 paket ile gerçekleşir. Adı: **Three-Way Handshake (Üç Yollu El Sıkışma).**

> 📞 **Analoji – Komşuya Misafirliğe Gitmek:** Muazzeze Hanım komşusunu aramak istiyor:
> 1. Muazzeze Hanım: *"Bu akşam size gelebilir miyiz?"* → **SYN paketi**
> 2. Komşu: *"Evet, buyurun gelin!"* → **SYN-ACK paketi**
> 3. Muazzeze Hanım: *"Tamam, bu akşam geliyoruz."* → **ACK paketi**
>
> Sonuç: Akşam kapıyı çaldığında komşu hazır, bekliyor. Çat kapı gitseydin kimse olmayabilirdi!

### Three-Way Handshake Akış Diyagramı

```
CLIENT                          SERVER
  |                               |
  |-------- ① SYN (seq=0) ------->|
  |                               |
  |<-- ② SYN-ACK (seq=0, ack=1) --|
  |                               |
  |-------- ③ ACK (ack=1) ------->|
  |                               |
  ✅ Handshake tamamlandı → Veri transferi başlayabilir
```

### Sequence Number Mantığı

```
# Örnek: seq=9001 ile başlayan bir handshake

Adım 1 – CLIENT → SERVER:
  SYN = 1, ACK = 0
  Sequence Number = 9001

Adım 2 – SERVER → CLIENT:
  SYN = 1, ACK = 1
  Sequence Number = 5001   (sunucunun kendi numarası)
  Ack Number = 9002        (9001 + 1 = "bir sonrakini istiyorum")

Adım 3 – CLIENT → SERVER:
  SYN = 0, ACK = 1
  Sequence Number = 9002   (server 9002 istemişti)
  Ack Number = 5002        (sunucunun 5001'inin bir sonrakisi)
```

**Kural:** Acknowledgement Number = Karşı tarafın Sequence Number'ı + 1 (ya da paketin uzunluğu kadar artış).

### Bağlantıyı Kapatmak – FIN-ACK Dörtlüsü

```
Açılış:  SYN → SYN-ACK → ACK           (3 paket)
Kapanış: FIN-ACK → ACK → FIN-ACK → ACK (4 paket)
```

FIN = nazikçe bitirme isteği. İki taraf da birbirinden onay alarak kapanışı gerçekleştirir.

> ⚠️ **KARIŞTIRMA! – FIN vs RST:**
> - **FIN:** Kibarca bağlantıyı kapatmak. "Görüşürüz, hoşçakal" demek gibi. Karşılıklı onay beklenir.
> - **RST:** Acil durum. Bir sunucu aniden kapandığında, bağlantıda beklenmeyen bir paket geldiğinde anlık "bağlantı kesildi" denir. Onay beklenmez.

### ✏️ Kendini Test Et – Bölüm 5

**S-01:** Three-Way Handshake'deki 3 paket hangileridir ve sırası nedir?
> ✅ **Cevap:** SYN → SYN-ACK → ACK. Önce istemci SYN gönderir, sunucu SYN-ACK ile yanıtlar, istemci de ACK ile onaylar.

**S-02:** TCP bağlantısını kapatmak kaç paket gerektirir?
> ✅ **Cevap:** 4 paket: FIN-ACK → ACK → FIN-ACK → ACK. Açılıştan (3 paket) bir fazla.

**S-03:** Sunucu aniden çöktüğünde hangisi gelir: FIN mi, RST mi?
> ✅ **Cevap:** RST (Reset) gelir. FIN kibarca kapanıştır; RST ise olağanüstü, acil durum kapanışıdır.

---

## Bölüm 6 · TCP Bayrakları (Flags) – 6 Kritik Bayrak {#bolum-6}

TCP başlığındaki bayraklar (flags), paketin ne tür bir paket olduğunu sisteme söyler. Bayrak **"1" ise set edilmiş (aktif)**, **"0" ise set edilmemiş (pasif)** demektir.

| Bayrak | Tam Adı | Görevi | Ne Zaman? |
|--------|---------|--------|-----------|
| **SYN** | Synchronize | Bağlantı kurma isteği | Three-Way Handshake'in ilk paketi |
| **ACK** | Acknowledge | Onay – "Senden X aldım, Y'yi istiyorum" | SYN hariç hemen her pakette |
| **FIN** | Finish | Kibarca bağlantı kapatma isteği | Normal bağlantı sonlandırma |
| **RST** | Reset | Acil bağlantı sıfırlama | Hata veya beklenmedik paket |
| **PSH** | Push | Veriyi hemen üst katmana ilet | Arabelleğe almadan anlık iletim |
| **URG** | Urgent | Bu paket acil, öncelikli işle | Acil veri gönderiminde |

> 🏥 **Analoji:**
> - 🚨 **URG (Urgent)** → Acil servis gibi. Normal sırayı beklemez, hemen işlem görür.
> - 🤝 **SYN** → "Merhaba, bağlantı kurmak istiyorum" demek.
> - ✅ **ACK** → "Aldım, anladım, devam et" demek.
> - 👋 **FIN** → "Konuşmamızı bitiriyorum, görüşürüz" demek.

> 💡 **HATIRLA:** Wireshark'ta bir pakete tıkladığında aşağıda bayraklar kısmını görürsün. Eğer bir bayrakta **"Set"** yazıyorsa o bayrak aktif demektir. **"Not Set"** yazıyorsa pasif. SYN-ACK paketinde hem SYN hem ACK → iki bayrak birden "Set" durumunda.

### ✏️ Kendini Test Et – Bölüm 6

**S-01:** Hangi paket türünde SYN bayrağı SET, ACK bayrağı NOT SET olur?
> ✅ **Cevap:** Three-Way Handshake'in ilk paketi olan SYN paketinde. Sadece SYN bayrağı set edilmiştir.

**S-02:** PSH bayrağının görevi nedir?
> ✅ **Cevap:** Gelen segmenti arabelleğe (buffer) almadan anlık olarak bir üst katmana (Application Layer) iletmektir.

**S-03:** Bir sunucu aniden kapandığında hangi bayrak gönderilir?
> ✅ **Cevap:** RST (Reset) bayrağı. Acil ve olağanüstü durumlar için kullanılır.

---

## Bölüm 7 · TCP Başlığı (Header) – Temel Alanlar {#bolum-7}

Her TCP segmentinin başına bir **header (başlık)** eklenir.

| Alan | Boyut | Görevi |
|------|-------|--------|
| **Source Port** | 16 bit | Paketin çıktığı port (0-65535) |
| **Destination Port** | 16 bit | Paketin gideceği port (0-65535) |
| **Sequence Number** | 32 bit | Bu segmentin sıra numarası – doğru sıralamayı sağlar |
| **Acknowledgement Number** | 32 bit | "Şunu aldım, şimdi şunu gönder" mesajı |
| **Flags (Bayraklar)** | 6 bit | SYN, ACK, FIN, RST, PSH, URG |
| **Window Size** | 16 bit | Akış kontrolü – "Şu an bu kadar veri alabilirim" |
| **Checksum** | 16 bit | Hata kontrolü – matematiksel doğrulama değeri |
| **Urgent Pointer** | 16 bit | URG bayrağı aktifse acil veriyi işaret eder |

> ⚠️ **KARIŞTIRMA! – Window Size vs Segment Boyutu:**
> - **Window Size** = "Benim buffer'ımda (geçici belleğimde) şu an şu kadar yer var, bana bu kadarlık veri gönder." Her paket gidip geldikçe bu değer değişebilir.
> - **Segment boyutu** = Gönderilen tek bir segmentin büyüklüğü (örneğin 1460 byte).

> 🏦 **Checksum Analojisi – Banka Çeki:** Bir banka çeki yazarken tutarı hem rakamla hem yazıyla yazarsın. Alıcı ikisini karşılaştırır; tutuyorsa geçerli. TCP de segmenti gönderirken matematiksel bir değer hesaplar (Checksum). Karşı taraf aynı hesabı yapar. Sonuçlar eşleşirse segment bozulmamış demektir.

### ✏️ Kendini Test Et – Bölüm 7

**S-01:** Sequence Number'ın amacı nedir?
> ✅ **Cevap:** Gönderilen segmentlerin sırasını takip etmek için kullanılır. Karşı taraf bu numarayı kullanarak segmentleri doğru sırayla birleştirir.

**S-02:** Checksum değeri eşleşmezse ne olur?
> ✅ **Cevap:** TCP'de eşleşmezse o segment istenerek tekrar gönderilir. UDP'de ise o segment düşürülür (drop), tekrar istenmez.

**S-03:** Window Size değeri sabit midir?
> ✅ **Cevap:** Hayır. Her iletişim döngüsünde değişebilir. Alıcının o anki buffer kapasitesine göre dinamik olarak ayarlanır.

---

## Bölüm 8 · UDP – User Datagram Protocol {#bolum-8}

> 🎯 **Bunu Neden Öğreniyoruz?**
> DNS, DHCP ve video akışı gibi kritik servisler UDP kullanır. UDP'de doğrulama olmadığı için IP sahteciliği (spoofing) saldırıları daha kolay yapılabilir.

**UDP (User Datagram Protocol)** = Hızlı ama güvenilirliği ikinci planda tutan bir protokol. Handshake yok, onay yok, tekrar gönderme yok.

> 📬 **Analoji – Posta Kutusu:** Kargo bekliyorsun. Kurye kapıyı çalmıyor, aşağıdaki ortak posta kutusuna bırakıyor ve gidiyor. Elinize geçti mi geçmedi mi, içindekiler tam mı eksik mi — hiç önemli değil. UDP tam olarak bu.

| Özellik | UDP |
|---------|-----|
| Bağlantı tipi | Connectionless (Bağlantısız) |
| Güvenilirlik | ⚠️ Düşük – paket kayıpları tespit edilebilir ama telafi edilmez |
| Hata kontrolü | ⚠️ Kısmi – hata tespit var, ama tekrar gönderme yok |
| Hız | ✅ Çok hızlı |
| Kullanıldığı yerler | DNS (port 53), DHCP (port 67-68), Video/Ses akışı, Oyunlar |

### UDP Header – Çok Daha Sade

```
UDP Header Alanları:
  1. Source Port        (16 bit)
  2. Destination Port   (16 bit)
  3. Length             (16 bit)
  4. Checksum           (16 bit)
```

TCP header 8+ alan içerirken UDP header sadece 4 alan içerir.

> 📺 **Analoji – Canlı Yayın:** YouTube'dan canlı futbol maçı izliyorsun. Bir saniye atladı, ekran dondu, sonra devam etti. UDP işte bu. O kaybolan kareyi geri istemez, anlık devam eder. Çünkü canlı yayında geri almak zaten anlamsız.

### TCP vs UDP Karşılaştırması

> ⚠️ **KARIŞTIRMA! – TCP ne zaman, UDP ne zaman?**

**TCP kullan:**
- Web sayfası (HTTP/HTTPS)
- E-posta (SMTP)
- Dosya transferi (FTP)
- SSH bağlantısı

**UDP kullan:**
- Video/müzik akışı (YouTube, Spotify)
- DNS sorgusu
- DHCP (IP ataması)
- Çevrimiçi oyunlar
- VoIP (sesli görüşme)

**Kural:** Güvenlik öncelikli → TCP. Hız öncelikli → UDP.

### ✏️ Kendini Test Et – Bölüm 8

**S-01:** UDP'de Three-Way Handshake var mı?
> ✅ **Cevap:** Hayır. UDP "connectionless" (bağlantısız) protokoldür. Önceden bağlantı kurma aşaması yoktur, direkt gönderir.

**S-02:** DNS hangi protokolü kullanır ve neden?
> ✅ **Cevap:** UDP kullanır (Port 53). DNS sorguları genellikle çok küçük ve hızlı olduğu için TCP'nin ek yükü gereksizdir.

**S-03:** UDP'de kayıp paketler ne olur?
> ✅ **Cevap:** Tespit edilebilir ama tekrar gönderilmez. Hatalı ya da eksik paketler "drop" edilir (atılır) ve sistem ilerler.

---

## Bölüm 9 · Port Numarası Kategorileri – IANA Tanımlaması {#bolum-9}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Penetrasyon testinde, bir sistemde 49.500 numaralı portu gördüğünde bunun dinamik/özel bir port olduğunu bilmen gerekir. 80 numaralı portu gördüğünde bunun web servisi olduğunu anlamalısın.

Hoca derste **IANA (Internet Assigned Numbers Authority)**'dan bahsetti. Bu kurum port numaralarını düzenler. Portları üç kategoriye ayırmıştır:

### Kategori 1: Well-Known Ports (0 – 1023)

- **İyi bilinen sistem servisleri** için ayrılmış
- Web (80, 443), DNS (53), SSH (22), FTP (21) gibi evrensel servisler burada
- Bu portları kullanmak için genellikle sistem yetkisi gerekir

### Kategori 2: Registered / Kayıtlı Portlar (1024 – 49151)

- **Firmalar ve uygulamalar** IANA'ya kayıt yaptırarak kullanır
- Örnekler: MS SQL Server (1433), Oracle (1527), Adobe (1102), Novel (1416)
- Bu portları kullanmak için kayıt gerekir

### Kategori 3: Dynamic / Private Portlar (49152 – 65535)

- **Kullanıcı bilgisayarlarının** oturum başlatırken kendine atadığı portlar
- Sen bir web sitesine bağlandığında senin bilgisayarın bu aralıktan bir port seçer
- Geçici, dinamik olarak atanır

> 🏢 **Analoji – Site / Apartman:**
> - **Sistem portları (0-1023):** Sitenin ortak alanları – güvenlik, yönetim, çöp toplama gibi hizmetler. Herkese açık, evrensel.
> - **Kayıtlı portlar (1024-49151):** Dairelerin numaraları – her firmaya atanmış odalar.
> - **Dinamik portlar (49152-65535):** Misafir odaları – sen bir web sitesine bağlandığında sana geçici olarak verilen oda.

> 🔬 **Wireshark Bağlantısı:** Hoca derste Wireshark'ta gösterdi: Kaynak port olarak **50.294** veya **54.181** gibi yüksek numaralar gördüğünde, bu senin bilgisayarının oturum için seçtiği dinamik portlardır. Hedef port **443** ise sunucunun HTTPS servisidir.

### ✏️ Kendini Test Et – Bölüm 9

**S-01:** IANA port kategorileri nelerdir ve sınırları?
> ✅ **Cevap:** Sistem/Well-Known Portlar (0-1023), Kayıtlı Portlar (1024-49151), Dinamik/Private Portlar (49152-65535).

**S-02:** Microsoft SQL Server hangi port aralığında ve neden?
> ✅ **Cevap:** 1433 numaralı portu kullanır. 1024-49151 arasında olduğu için "Kayıtlı Port" kategorisindedir. Microsoft, IANA'ya bu portu kayıt ettirmiştir.

**S-03:** Sen bir web sitesine bağlandığında senin bilgisayarın hangi aralıktan port seçer?
> ✅ **Cevap:** 49152-65535 aralığından, yani dinamik/private portlardan. Bu portlar geçici olarak oturum için atanır.

---

## Bölüm 10 · Yaygın Kullanılan Port Numaraları {#bolum-10}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Penetrasyon testinde, güvenlik duvarı (firewall) kuralı yazarken veya ağ analizi yaparken bu portları hızla tanımak gerekir.

Hoca derste dedi ki: *"65.000 portun hepsini bilmem gerekmiyor. Ama belirli başlı portları bilmek zorundasın."*

| Port | Protokol | Servis | Açıklama |
|------|----------|--------|----------|
| **21** | TCP | FTP | File Transfer Protocol – güvensiz dosya transferi |
| **22** | TCP | SSH | Güvenli uzak bağlantı |
| **25** | TCP | SMTP | E-posta gönderimi |
| **53** | UDP | DNS | Domain Name System – alan adı çözümleme |
| **67-68** | UDP | DHCP | IP adresi otomatik atama (DORA süreci) |
| **80** | TCP | HTTP | Web – şifresiz, açık metin |
| **110** | TCP | POP3 | E-posta alma (eski protokol) |
| **143** | TCP | IMAP | E-posta alma (modern protokol) |
| **443** | TCP | HTTPS | Güvenli web – şifreli (TLS ile) |
| **1433** | TCP | MS SQL Server | Microsoft veritabanı servisi |
| **3389** | TCP | RDP | Remote Desktop Protocol – uzak masaüstü |

### HTTP (80) vs HTTPS (443)

> ✉️ **Analoji – Posta Kartı vs Zarflı Mektup:**
> - **HTTP (Port 80):** Posta kartı gibi. Herkes okuyabilir. Araya giren (Man-in-the-Middle saldırısı) tüm veriyi düz metin olarak görür.
> - **HTTPS (Port 443):** Mühürlü zarflı mektup gibi. Şifrelenmiş. Araya giren karakter karmaşasından başka bir şey göremez. TLS sertifikaları ile güvenlik sağlanır.

Hoca derste Wireshark'ta HTTP trafiğini "Follow TCP Stream" ile incelediğinde sunucu bilgileri, içerikler açıkça okunabiliyordu. HTTPS'de ise şifreli olduğu için okunamıyor.

### DNS Nasıl Çalışır?

```
# DNS Çalışma Mantığı
Sen tarayıcıya "hackeracademy.uk" yazıyorsun
  ↓
Bilgisayar DNS sunucusuna soruyor (UDP Port 53): "hackeracademy.uk'nin IP'si ne?"
  ↓
DNS sunucusu cevap veriyor: 203.0.113.42
  ↓
Tarayıcı o IP adresine gidiyor (TCP Port 80 ya da 443)
# Sen "hackeracademy.uk"a değil, onun IP adresine gidiyorsun
```

### DHCP – DORA Süreci

```
D → Discover  "Ağda DHCP sunucusu var mı?"
O → Offer     "Sana şu IP'yi verebilirim"
R → Request   "Tamam, o IP'yi istiyorum"
A → ACK       "Peki, IP senin. Gateway ve DNS de şunlar."
```

DHCP, UDP Port **67** (sunucu) ve Port **68** (istemci) üzerinde çalışır.

### ✏️ Kendini Test Et – Bölüm 10

**S-01:** HTTP ve HTTPS arasındaki temel fark nedir?
> ✅ **Cevap:** HTTP (Port 80) şifresizdir, açık metin (clear text) olarak iletilir. HTTPS (Port 443) TLS şifrelemesi kullanır, araya giren biri veriyi okuyamaz.

**S-02:** RDP hangi porttur ve ne işe yarar?
> ✅ **Cevap:** RDP (Remote Desktop Protocol) port 3389'da çalışır. Uzak masaüstü bağlantısı için kullanılır.

**S-03:** DNS çözümlemesi hangi protokolü ve portu kullanır?
> ✅ **Cevap:** UDP protokolünü, Port 53'ü kullanır.

---

## Bölüm 11 · Wireshark ile Uygulamalı İnceleme {#bolum-11}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Wireshark, siber güvenliğin en önemli araçlarından biri. Network trafiğini "görünür" kılar. Saldırıları, şüpheli paketleri ve güvenlik açıklarını Wireshark ile fark edersin.

Hoca derste TryHackMe'deki Attack Box üzerinde Wireshark kullandı.

### Adım 1: Hangi Interface'i Dinleyeceğiz?

```bash
# Linux'ta ağ arayüzlerini görmek için
$ ifconfig

# Windows'ta eşdeğeri
$ ipconfig
```

Hoca bu adımda **ENS5** interface'ini buldu ve Wireshark'ta onu seçti.

### Adım 2: Paket Yakalama ve Filtreleme

| Filtre | Ne Gösterir? |
|--------|-------------|
| `http` | Sadece HTTP trafiği |
| `tcp` | Tüm TCP trafiği |
| `udp` | Tüm UDP trafiği |
| `dns` | Sadece DNS sorguları |
| `tcp.flags.syn == 1` | Sadece SYN paketleri |
| `tcp.flags.syn == 1 and tcp.flags.ack == 0` | Sadece SYN (SYN-ACK hariç) |

### Adım 3: Three-Way Handshake'i Wireshark'ta Görmek

```
# Wireshark'ta Three-Way Handshake incelemesi

Paket 1: SYN
  Source Port: 7875
  Destination Port: 2000
  Sequence Number: 0
  Window Size: 64240
  Uzunluk: 0

Paket 2: SYN-ACK
  Source Port: 2000
  Destination Port: 7875
  Sequence Number: 0
  Ack Number: 1     (karşının 0'ını + 1 yaptı)

Paket 3: ACK
  Sequence Number: 1
  Ack Number: 1
```

Handshake bittikten sonra data transfer başlıyor. 1460 byte'lık segmentler gitmeye başlıyor. Sequence number 1461, 2921, 4381... şeklinde 1460'ar 1460'ar artıyor.

### Adım 4: Follow TCP Stream

Bir pakete sağ tıklayıp "Follow → TCP Stream" dendi. Bu seçenek o bağlantıya ait tüm paketleri gruplayarak gösteriyor.

- HTTP trafiğinde: Server bilgileri, içerik açıkça okunabilir (clear text)
- HTTPS trafiğinde: TLS sayesinde şifreli, okunabilir değil

### Adım 5: Netstat Komutu

```bash
# Hangi portlar açık, hangi bağlantılar aktif?
$ netstat -an

# Örnek çıktı:
0.0.0.0:80  →  LISTENING        (HTTP servisi dinliyor)
192.168.x.x:63510 → xx.xx.xx.xx:80  ESTABLISHED
# Yani biz 63510 portumuzdan karşının 80 nolu portuna bağlandık
```

> 💡 **HATIRLA:** Wireshark'ta her pakette şu katmanlar görünür:
> - **Frame** → Wireshark'ın kendi verdiği başlık
> - **Ethernet** → Data Link katmanı (MAC adres)
> - **Internet Protocol** → Network katmanı (IP adres)
> - **Transmission Control Protocol** → Transport katmanı (Port, Flag, Sequence Number)
> - **HTTP/DNS/vb.** → Application katmanı (asıl veri)

### ✏️ Kendini Test Et – Bölüm 11

**S-01:** Wireshark'ta sadece SYN paketlerini görmek için hangi filtre kullanılır?
> ✅ **Cevap:** `tcp.flags.syn == 1` filtresi kullanılır.

**S-02:** HTTP trafiğinde "Follow TCP Stream" neden tehlikeli olabilir?
> ✅ **Cevap:** HTTP şifresiz (clear text) olduğu için Follow TCP Stream ile tüm içerik okunabilir. Giriş bilgileri, içerik, sunucu bilgisi gibi hassas veriler görünür.

**S-03:** Yeni bir siteye gidildiğinde Wireshark'ta neden önce DNS paketi görünür?
> ✅ **Cevap:** Tarayıcı sitenin IP adresini bilmediği için önce DNS sunucusuna sorar. Bu DNS sorgusu UDP/53 üzerinden yapılır ve Wireshark'ta önce görünür.

---

## Bölüm 12 · Siber Güvenlik Perspektifi: Açık Portlar {#bolum-12}

> 🎯 **Bunu Neden Öğreniyoruz?**
> Bu, bugünkü dersin siber güvenlik özüdür. Port kavramını teorik olarak öğrenmek yetmez; açık portların tehlikesini anlamak, gerçek dünyada saldırı ve savunma perspektifini kazandırır.

Hoca şöyle dedi: *"Gerçek hayatta hırsızlar kapıyı çalar, içeriden ses gelmezse gider. Ama siber alemde kapıyı çalar, ses varsa girer."*

> 🔴 **GÜVENLİK UYARISI:** Bir bilgisayarda açık olan port = potansiyel giriş noktası. Saldırganlar NMAP gibi araçlarla hedef sistemdeki açık portları tarar ve orada çalışan servislerdeki zafiyetleri araştırır.
>
> **Hoca'nın gerçek hayat örneği:** Ahmet Mert Hoca 7-8 yıl önce bir web tasarımı projesi için **Apache Web Server** kurdu. İşi bitince server'ı kaldırdı ama port açık kaldı. Bu süre zarfında Apache'de zafiyetler keşfedildi. Saldırganlar o açık porttan girerek sistemi ele geçirebilirdi.

### Siber Güvenlikçinin Yaklaşımı

1. **Hangi portlar açık?** → NMAP ile tarama yap
2. **Bu portlar gerekli mi?** → Analiz et
3. **Gereksizse kapat!** → Servis durdur, firewall kuralı yaz
4. **Açık portlarda zafiyetler var mı?** → Vulnerability Scanner kullan

```bash
# Port taraması için NMAP kullanımı (temel)
$ nmap -sV <hedef_ip>
# -sV: Servislerin versiyonlarını da gösterir

# Örnek çıktı:
PORT     STATE  SERVICE  VERSION
22/tcp   open   ssh      OpenSSH 8.2
80/tcp   open   http     Apache httpd 2.4.41
3306/tcp open   mysql    MySQL 8.0.x
# → MySQL dışarıya açık mı? Bu tehlikeli olabilir!
```

> 🔒 **SİBER GÜVENLİK KURALI – Minimum Yetki İlkesi (Least Privilege):** Sadece ihtiyaç duyulan portlar açık olmalı. Gerisi kapalı. Bir servis kaldırıldığında mutlaka o servise ait port da kapatılmalı.

### ✏️ Kendini Test Et – Bölüm 12

**S-01:** Bir servis kaldırıldıktan sonra portu neden kapatmak gerekir?
> ✅ **Cevap:** Çünkü port açık kaldığında, o servise ait zafiyetler hâlâ istismar edilebilir (Hoca'nın Apache örneğindeki gibi).

**S-02:** Gerçek hayat ile siber güvenlik arasındaki "kapı çalmak" analojisini açıkla.
> ✅ **Cevap:** Gerçek hayatta hırsız kapıyı çalar, ses yoksa gider. Siber alemde ise saldırgan portu tarar, servis açıksa (ses varsa) girer. Kapalı port = ses yok = giriş yok.

**S-03:** NMAP ne işe yarar?
> ✅ **Cevap:** Hedef sistemdeki açık portları, o portlarda çalışan servisleri ve servis versiyonlarını taramak için kullanılan bir ağ tarayıcısıdır.

---

## Genel Tekrar ve Özet {#ozet}

Bugün öğrendiklerimizi tek cümleyle özetleyelim:

- **OSI Modeli bağlantısı:** 2. katmanda MAC, 3. katmanda IP, 4. katmanda PORT ekleniyor; kargo analojisinde bu sırasıyla ad-soyad, adres ve daire numarasına karşılık gelir.

- **Transport Layer:** Segmentation (bölme), Reassembling (birleştirme), Akış Kontrolü, Hata Kontrolü ve Servis Adresleme (port) işlemlerini yapan 4. katmandır.

- **Port kavramı:** 0-65535 arası mantıksal bağlantı noktaları; bir IP adresindeki farklı servislere (hastane analojisinde farklı servislere) ulaştırmayı sağlar.

- **TCP:** Güvenilir, bağlantı odaklı protokol. Three-Way Handshake (SYN→SYN-ACK→ACK) ile başlar, FIN-ACK dörtlüsüyle kapanır. Web, e-posta, dosya transferi için kullanılır.

- **Three-Way Handshake:** TCP'de veri transferinden önce zorunlu 3 paketlik (SYN, SYN-ACK, ACK) el sıkışma protokolüdür; misafirliğe gitmeden önce arama yapmak gibi.

- **TCP Bayrakları:** SYN (bağlan), ACK (onayla), FIN (kibarca bitir), RST (acil bitir), PSH (hemen ilet), URG (öncelikli işle) — 6 kritik bayrak.

- **UDP:** Hızlı, bağlantısız protokol. DNS (53), DHCP (67/68), video akışı ve oyunlar için kullanılır. Paket kaybı tolere edilir, geri gönderim yoktur.

- **Port kategorileri:** 0-1023 (sistem/well-known), 1024-49151 (kayıtlı/firmalar), 49152-65535 (dinamik/kullanıcı). IANA bu dağılımı yönetir.

- **Kritik portlar:** 21 (FTP), 22 (SSH), 25 (SMTP), 53 (DNS-UDP), 67-68 (DHCP-UDP), 80 (HTTP), 443 (HTTPS), 3389 (RDP).

- **Siber güvenlik:** Açık port = potansiyel giriş noktası. NMAP ile port taraması yapılır, gereksiz portlar kapatılır, servis kaldırıldığında port da kapatılmalıdır.

---

> 💪 *Bu ders zor değil. Her şey hayatımızdaki analojilerle açıklanabilir. Tekrar et, pekiştir, Wireshark'ta uygula!*
