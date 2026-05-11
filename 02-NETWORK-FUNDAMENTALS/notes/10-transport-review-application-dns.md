# 🛡️ SİBER GÜVENLİK EĞİTİMİ
## Network Fundamentals – Ders 10
### Transport Layer Tekrarı & Application Layer / DNS

## 📋 İÇİNDEKİLER

1. [Bölüm 1 – Transport Katmanı Tekrarı](#bölüm-1)
   - 1.1 Transport Layer Ne Yapar?
   - 1.2 Servis Noktası Adresleme – Port Numaraları
   - 1.3 Fiziksel Port vs. Mantıksal Port
   - 1.4 Segmentation ve Reassembly
   - 1.5 Bağlantı Kontrolü – 3-Way Handshake
   - 1.6 TCP Bayrakları (Flags)
   - 1.7 Flow Control & Error Control
2. [Bölüm 2 – Application Layer / DNS](#bölüm-2)
   - 2.1 URL Yapısı
   - 2.2 DNS Nedir?
   - 2.3 DNS Çözümleme Mekanizması
   - 2.4 DNS ve İnternet Yasakları
   - 2.5 Root Server'lar
   - 2.6 AnyCast Teknolojisi
   - 2.7 DNS Kayıt Türleri
   - 2.8 Wireshark'ta DNS Trafiği
   - 2.9 NSLookup Komutu
   - 2.10 DIG Komutu
   - 2.11 Alan Adı Kayıt Hiyerarşisi (ICANN)
3. [Genel Tekrar ve Özet](#genel-özet)

---

# BÖLÜM 1
# 📦 TRANSPORT KATMANI – KISA TEKRAR

> 🎯 **BUNU NEDEN ÖĞRENİYORUZ?**
> Bir önceki derste Transport Layer'ı öğrendik. Bugün bu konuyu kısa bir tekrarla pekiştirip bir üst katman olan Application Layer'a geçiyoruz. Transport Layer'ı anlamamak, DNS'i, HTTP'yi ve diğer uygulama protokollerini anlamamayı beraberinde getirir.

> 🔗 **KONULAR ARASI BAĞLANTI**
> Physical Layer → Data Link Layer → Network Layer → **TRANSPORT LAYER** → **Application Layer**
> - OSI Modelinde: **4. katman**
> - TCP/IP Modelinde: **3. katman**

---

## 1.1 Transport Layer Ne Yapar?

Transport Layer'ın temel görevleri:

- Yukarıdan (Application Layer'dan) gelen büyük veriyi küçük parçalara böler → **Segmentlere ayırır**
- Her parçaya bir sıra numarası ekler: **Sequence Number**
- Üzerine TCP veya UDP başlığı ekleyerek Network Layer'a iletir
- Aşağıdan gelen parçaları birleştirerek (**Reassembly**) üst katmana iletir
- Verinin tamamen ve sırayla ulaştığını kontrol eder (TCP'de)

---

## 1.2 Servis Noktası Adresleme – PORT NUMARALARI

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> Bir kamu kurumuna gittiğinizi düşünün. Binanın bir **adresi** var → bu IP adresi. Ama içeride farklı hizmetler var:
> - 7. Kat, 4 No'lu Oda → Pasaport hizmetleri
> - 3. Kat, 12 No'lu Oda → Vergi işlemleri
> - Zemin kat → Danışma
>
> İşte **PORT NUMARALARI** tam olarak bu! Bilgisayarınızın IP adresi = binanın adresi, port numaraları = odaların numaraları.
>
> *Eğitmenin hastane örneği: "Hastaneye gittiğinizde göz muayenesine ayrı bölüm, dahiliyeye ayrı bölüm var. Servis noktaları böyle düşünün."*

TCP ve UDP protokollerinin her biri **0'dan 65.535'e** kadar toplam **65.536 port** numarasına sahiptir (2¹⁶ = 65.536).

| Port Aralığı | İsim | Açıklama |
|---|---|---|
| **0 – 1.023** | Well-Known (Sistem) Portları | Evrensel standartlarla belirlenmiş, değişmez. HTTP=80, HTTPS=443, DNS=53, FTP=21 |
| **1.024 – 49.151** | Registered (Kayıtlı) Portlar | Uygulama geliştiricilerine tahsis edilmiş (Skype, Apache vb.) |
| **49.152 – 65.535** | Dynamic / Private (Dinamik) Portlar | Müşteri uygulamalarının geçici kullandığı portlar |

> 🛍️ **Eğitmenin AVM Analojisi:**
> - Market zinciri kendi bölümlerini belirler → **Well-known portlar** (sabit, değişmez)
> - Kiracı mağazalar (sinema, restoran, mobilyacı) → **Registered portlar** (uygulama geliştiricileri)
> - Tuvaletler, ibadet yerleri, dinlenme alanları → **Dynamic portlar** (herkese açık, geçici)

> ⭐ **HATIRLA!**
> - Well-known portlar: **0-1023** → Sistem portları, değişmez
> - **DNS = Port 53 | HTTP = Port 80 | HTTPS = Port 443 | FTP = Port 21**
> - 65.536 port var çünkü **2¹⁶ = 65.536**

---

## 1.3 Fiziksel Port vs. Mantıksal Port

| | Fiziksel Port | Mantıksal Port |
|---|---|---|
| **Görünürlük** | Elle tutulur, gözle görülür | Sadece yazılımda var, soyut |
| **Örnekler** | USB, HDMI, RJ-45 (Ethernet) | TCP/UDP'de 80, 53, 443... |
| **Nerede?** | Kasanın/laptopun arkasında | nmap ile taranarak keşfedilir |
| **Katman** | Donanım (hardware) katmanı | Yazılım (software) katmanı |

> 📌 **GERÇEK HAYATTAN ÖRNEK**
>
> *Eğitmenin anlattığı gerçek senaryo:*
>
> "Apache Server kurdunuz, web programlamayla uğraştınız. Sonra vazgeçtiniz ama Apache'yi kaldırmadınız. Apache hâlâ arka planda çalışıyor ve bir port açık bırakıyor. Sizin kullanmamanız o portu kapatmaz!"
>
> **Sonuç:** Bir saldırgan (Attacker) o açık portu taradığında güvenlik açığından sisteminize sızabilir.
>
> **🔴 SİBER GÜVENLİKÇİ GÖREVİ:** Portları kapatmak değil, **açık portları raporlamak!** Kapatma görevi network yöneticilerinin.

> 📝 **KENDİNİ TEST ET**
>
> **1.** Well-known portlar hangi aralıktadır ve neden "değişmez" deniyor?
> > *Cevap: 0-1023 aralığıdır. Uluslararası standartlarla belirlenmiş, tüm sistemlerde aynı servislere ayrılmıştır.*
>
> **2.** Fiziksel port ile mantıksal port arasındaki temel fark nedir?
> > *Cevap: Fiziksel portlar gözle görülür donanım bağlantı noktalarıdır (USB, HDMI). Mantıksal portlar ise TCP/UDP protokollerinde tanımlı soyut hizmet noktalarıdır.*
>
> **3.** Bir program kaldırıldığında ilgili port otomatik kapanır mı?
> > *Cevap: Hayır! Program düzgün kaldırılmadıysa veya farklı bir mekanizma portu açık bırakıyorsa, port açık kalmaya devam eder.*

---

## 1.4 Segmentation ve Reassembly

Application Layer'dan büyük bir veri geliyor. Transport Layer bunu küçük parçalara böler:

- Her parçaya **Sequence Number (sıra numarası)** verir
- TCP kullanıyorsa → **TCP başlığı** eklenir; UDP kullanıyorsa → **UDP başlığı** eklenir
- Parçalara ayrılma işlemi: **Segmentation**
- Karşı tarafta tekrar birleştirme: **Reassembly**

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> 📦 Büyük bir dolabı nakliye edeceksiniz. Ama nakliye aracına sığmıyor. Ne yaparsınız?
> 1. Parçalara sökersiniz → **Segmentation**
> 2. Her parçayı numaralandırırsınız → **Sequence Number**
> 3. Karşı adreste tekrar birleştirirsiniz → **Reassembly**
>
> Eğer bir parça kaybolursa:
> - **TCP** → "Eksik parçayı tekrar gönder!" (Retransmit)
> - **UDP** → Eksik parçayı umursamadan devam eder

---

## 1.5 Bağlantı Kontrolü – 3-Way Handshake (3 Yönlü El Sıkışma)

TCP bağlantı kurmadan önce 3 adımlı bir el sıkışma gerçekleştirir:

| Adım | Kimden → Kime | Paket | Ne Anlama Gelir? |
|---|---|---|---|
| **1** | İstemci → Sunucu | `SYN` | Merhaba! Seninle bağlantı kurmak istiyorum. |
| **2** | Sunucu → İstemci | `SYN + ACK` | Tamam, buyur! Ben de sana bağlanmak istiyorum. |
| **3** | İstemci → Sunucu | `ACK` | Harika, başlayalım! |

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> 📞 *Eğitmenin ev ziyareti analojisi:*
> - **SYN:** "Bu akşam size oturmaya gelmek istiyoruz."
> - **SYN+ACK:** "Tabii, buyurun! Çok seviniriz."
> - **ACK:** "Tamam, akşam sizdeyiz!"
>
> Bağlantı biterken de **FIN** paketleriyle kibarca kapatılır (4 paket), ya da **RST** ile aniden kesilir.

**Toplam paket sayısı:**
- Bağlantı kurulumu: **3 paket** (SYN → SYN-ACK → ACK)
- Bağlantı kapatma: **4 paket** (FIN+ACK → ACK → FIN+ACK → ACK)
- **Toplam: 7 paket** (data transferi hariç)

> ⭐ **HATIRLA!**
> - UDP'de bu 3+4 = 7 paket **yoktur**. Doğrudan veri gönderimi başlar.
> - Bu yüzden video izlerken, online oyun oynarken **UDP** kullanılır.

---

## 1.6 TCP Bayrakları (Flags)

TCP paketlerinde **6 temel bayrak** bulunur:

| Bayrak | İngilizce | Türkçe | Ne İşe Yarar? |
|---|---|---|---|
| **SYN** | Synchronize | Senkronize | Bağlantı kurma isteği. 3-way handshake'in ilk adımı. |
| **ACK** | Acknowledgement | Onay | "Şu numaralı paketini aldım." Alındı paketi. |
| **FIN** | Finish | Bitir | Kibarca bağlantı kapatma. "Artık bitse iyi olur." |
| **RST** | Reset | Sıfırla | Acil/zorla bağlantı kesme. Saldırı veya hata tespitinde. |
| **PSH** | Push | İt | Veriyi tamponda beklettirmeden hemen ilet! |
| **URG** | Urgent | Acil | Bu pakette öncelikli/acil veri var, önce işle! |

> ⚠️ **KARIŞTIRMA UYARISI!**
>
> **FIN vs RST — İKİSİ DE BAĞLANTIYI KESİYOR AMA FARKI BÜYÜK:**
> - **FIN** = Kibar sonlandırma. "Artık bitirmek istiyorum, müsait misin?" → Normal durum
> - **RST** = Zorla kesme. "Dur, anında kes!" → Hata veya saldırı durumu
>
> *Eğitmenin sözü: "FIN kibarca sonlandırma, RST kabaca sonlandırma."*
>
> *Örnek: Firewall binlerce SYN paketi görürse bunu saldırı olarak algılar ve RST ile keser.*

> ⭐ **HATIRLA!**
> - `SYN` = Bağlan | `ACK` = Onayladım | `FIN` = Kibarca kapat | `RST` = Acil kes
> - `PSH` = Hemen ilet | `URG` = Acil veri içeriyor
> - Bilmemiz gereken toplam bayrak sayısı: **6**

---

## 1.7 Akış Kontrolü (Flow Control) ve Hata Kontrolü (Error Control)

### Flow Control – Akış Kontrolü

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> 🚗 *Eğitmenin yol analojisi:*
>
> Bir otoyolda 4 şeritli yol var, saatte 120 km arabalar geliyor. Ama sizin bağlandığınız noktada yol çalışması var, 4 şeritten 1 şeride düşüyor.
>
> Ne yapılır? Karşı tarafa **"Yavaşla!"** mesajı gönderilir.
>
> TCP'de bu mesaj → **WINDOW SIZE (Pencere Boyutu)** ile yapılır.
> - Window Size = "Şu an bu kadar veriyi alabilirim" mesajı
> - Alıcının kapasitesi dolunca window size küçülür, gönderici yavaşlar

### Error Control – Hata Kontrolü

| Protokol | Hata Tespit Edilirse Ne Olur? |
|---|---|
| **TCP** | Eksik/hatalı segment istenir, tekrar gönderilir (**Retransmit**). Uygulama beklemeye alınır. |
| **UDP** | Hatalı paket düşürülür (**Drop**). Geri kalanlar yollanmaya devam eder. Retransmit yok. |

> 📝 **KENDİNİ TEST ET**
>
> **1.** 3-Way Handshake'in 3 adımını sırasıyla söyleyin.
> > *Cevap: 1) SYN (istemci→sunucu), 2) SYN+ACK (sunucu→istemci), 3) ACK (istemci→sunucu)*
>
> **2.** TCP ile UDP arasındaki temel fark nedir?
> > *Cevap: TCP bağlantı tabanlıdır, hata kontrolü yapar, yavaştır. UDP bağlantısızdır, hata kontrolü yapmaz, hızlıdır.*
>
> **3.** YouTube videosu izlerken TCP mi UDP mi kullanılır? Neden?
> > *Cevap: UDP. Çünkü anlık akış önemlidir, bir-iki karenin kaybolması sorun yaratmaz, ama TCP'nin el sıkışmaları ve retransmit mekanizması videoyu sürekli duraksatırdı.*

---

---

# BÖLÜM 2
# 🌐 APPLICATION LAYER – DNS

> 🔗 **KONULAR ARASI BAĞLANTI**
>
> Bir önceki bölümde Transport Layer'ı tekrar ettik. Şimdi en üst katmana, **Application Layer'a** geçiyoruz. Bu katmanda uygulamalar çalışır: DNS, HTTP, HTTPS, FTP, SMTP gibi protokoller burada yaşar.
>
> *Eğitmenin sözü: "OSI 7. katman, TCP/IP 4. katman olarak geçen Application Layer. Artık uygulama katmanındayız!"*

---

## 2.1 URL Yapısı – İnternet Adresi Nasıl Okunur?

Eğitmen HubSpot örneğini verdi:

```
https://marketing.hubspot.com/marketing
```

| Parça | Örnek | İsim | Açıklama |
|---|---|---|---|
| `https://` | `https://` | Protokol | İletişim protokolü |
| `.com` | `.com` | **Top Level Domain (TLD)** | En üst seviye alan adı. `.net`, `.org`, `.edu`, `.gov`... |
| `hubspot` | `hubspot` | **Second Level Domain** | Asıl şirket / marka adı |
| `marketing` | `marketing` | **Sub-Domain (Alt Alan)** | Ana domainin alt bölümü |

---

## 2.2 DNS Nedir? – İnternetin Telefon Rehberi

> 🎯 **BUNU NEDEN ÖĞRENİYORUZ?**
> İnternette milyarlarca web sitesi var. Hepsinin IP adresini ezberlemek imkânsız. DNS bu sorunu çözer. Siber güvenlikçiler için DNS; hem savunma hem de keşif (reconnaissance) aracıdır.

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> 📱 *Eğitmenin telefon rehberi analojisi:*
>
> Telefonunuzda 400-500 kişi kayıtlı. Ama siz onları numarayla değil, **isimle** kaydettiniz: "Mehmet İş", "Ayşe Bakkal", "Frankfurt'tan Metin"...
>
> Metin'i aramak istediğinizde onun adına basarsınız. Telefon **otomatik onun numarasını çevirir**. Siz numarayı hiç bilmiyorsunuzdur!
>
> İnternette de aynı şey:
> - `google.com` → Siz bunu yazarsınız (isim)
> - `142.250.185.46` → Aslında gidilmesi gereken adres (numara = IP adresi)
> - **DNS** → Bu dönüşümü yapan sistem
>
> *Eğitmenin tam sözü: "DNS, internetin telefon defteri. Biz hiçbir zaman IP adresi yazarak web sitesine gitmiyoruz."*

**DNS = Domain Name System (Alan Adı Sistemi)**

- Alan adlarını IP adreslerine çeviren sistem
- DNS sunucuları; alan adı ↔ IP adresi eşleştirmelerini tutan veritabanı içerir
- **Forward DNS:** `google.com` → `142.250.x.x` (isimden IP'ye)
- **Reverse DNS:** `142.250.x.x` → `google.com` (IP'den isme)

En bilinen DNS sunucuları:
- **8.8.8.8 / 8.8.4.4** → Google'ın DNS'i
- **1.1.1.1 / 1.0.0.1** → Cloudflare'ın DNS'i

---

## 2.3 DNS Çözümleme Mekanizması – Adım Adım

Siz tarayıcıya `mail.google.com` yazdınız. Ne oluyor?

**1️⃣ BİLGİSAYARINIZIN KENDİ CACHE'İ**
Daha önce bu siteye gittiniz mi? Eğer gittiyseniz IP adresi bilgisayarınızda zaten vardır → **Direkt gidilir!**

**2️⃣ LOCAL DNS SERVER (ISP'nin DNS'i)**
Bilgisayarınızda bulunamadı. En yakın DNS sunucusu olan ISP'nizinkine (Turk Telekom, Deutsche Telekom...) sorulur:
*"mail.google.com'un IP'si ne?"*

**3️⃣ ROOT SERVER**
Local DNS server da bilmiyorsa, kök sunuculara gidilir. Root server şöyle der:
*"Ben tam adresini bilmem ama .com'ların nerede olduğunu bilirim. Şu TLD sunucusuna git!"*

**4️⃣ TLD SERVER (Top Level Domain Sunucusu)**
`.com` uzantılı adresleri yöneten sunucu. Der ki:
*"google.com'un tüm bilgileri şu Authoritative sunucuda."*

**5️⃣ AUTHORITATIVE (YETKİLİ) DNS SERVER**
google.com ile ilgili tüm alt alanlar, tüm kayıtlar burada. Cevap:
*"mail.google.com'un IP adresi 74.125.x.x"* ✅

**6️⃣ GERİ DÖN**
Bu IP adresi Local DNS'e, Local DNS bize iletir. Tarayıcı bu IP'ye gider. Site açılır!

> ⭐ **HATIRLA!**
> - Bu tüm süreç **milisaniyeler** içinde gerçekleşir!
> - Siz Local DNS'e bir mesaj gönderirsiniz, o halleder ve size bir mesaj gönderir.
> - **DNS portu: UDP 53** (bilgisayar ↔ Local DNS arası)
> - **DNS sunucuları arası:** TCP 53 de kullanılabilir

> ⚠️ **KARIŞTIRMA UYARISI!**
>
> **LOCAL DNS SERVER = DNS RESOLVER = ISP DNS — ÜÇÜ AYNI ŞEY!**
> - **Local DNS Server** → Bulunduğunuz yere en yakın DNS sunucusu
> - **DNS Resolver** → Bu sunucunun görevi: sorunu çözmek (resolve etmek)
> - **ISP DNS** → Bu sunucuyu size atayan kişi: İnternet Servis Sağlayıcınız
>
> `ipconfig` (Windows) veya `ifconfig` (Linux) yazınca çıkan DNS Server adresi = bu sunucunun adresi!

---

## 2.4 DNS ve İnternet Yasakları

> 📌 **GERÇEK HAYATTAN ÖRNEK**
>
> *Eğitmenin anlattığı gerçek örnek:*
>
> "Türkiye'de bir dönem Twitter yasaklıydı, Wikipedia yasaklıydı. Bu yasaklama işlemi Local DNS Server seviyesinde yapılıyordu!"
>
> **Nasıl çalışır?**
> 1. Siz `wikipedia.org` yazarsınız
> 2. Local DNS Server'da (Türk Telekom, Vodafone...) bir kural vardır
> 3. Bu kural der ki: "Wikipedia sorgularını şu uyarı sayfasına yönlendir"
> 4. Siz IP adresini bile öğrenemeden yasaklama gerçekleşmiştir!
>
> **İnsanlar bunu nasıl aştı?**
> - DNS Server'ı değiştirdiler: `8.8.8.8` (Google) veya `1.1.1.1` (Cloudflare)
> - Ama ISP bunu da fark etti ve farklı engelleme mekanizmaları koydu
>
> *Eğitmenin sözü: "Saldırganlar beyaz şapkalı hackerlardan her zaman bir adım önde olacak. Savunma tarafı hep geride kalır."*

---

## 2.5 Root Server'lar – Dünyanın Kök Sunucuları

Root Server'lar; `.com`, `.net`, `.org` gibi TLD'lerin hangi sunucularda bulunduğunu bilen **en üst düzey DNS sunucularıdır.**

| Harf | Yöneten Kuruluş | Ülke |
|---|---|---|
| **A** | VeriSign | ABD |
| **B** | USC Information Sciences Institute | ABD |
| **C** | Cogent Communications | ABD |
| **D** | University of Maryland | ABD |
| **E** | NASA | ABD |
| **F** | Internet Systems Consortium | ABD |
| **G** | US Savunma Bakanlığı (DoD) | ABD |
| **H** | US Ordusu | ABD |
| **I** | Netnod | İsveç |
| **J** | VeriSign | ABD |
| **K** | RIPE NCC | Hollanda |
| **L** | ICANN | ABD |
| **M** | WIDE Project | Japonya |

*Eğitmen rootservers.org sitesini canlı olarak gösterdi.*

> ⭐ **HATIRLA!**
> - Root Server **çeşidi:** Sadece **13** (A'dan M'ye)
> - Root Server **fiziksel sayısı:** ~**1.958** (Ocak 2026 verisi — eğitmenin rootservers.org'dan gösterdiği rakam)
> - Bu çoğaltma **AnyCast** teknolojisiyle yapılır
> - **ICANN** bu tüm sistemi organize eden en üst kuruluştur
> - **Türkiye'de:** İstanbul'da 4 (2×E, 1×F, 1×D), İzmir'de 2 (F, K), Ankara'da 1 (R)

---

## 2.6 AnyCast Teknolojisi – Aynı IP, Farklı Yerler

13 Root Server nasıl binlerce makineye dönüşüyor? **AnyCast** ile!

> 🏠 **GÜNLÜK HAYAT ANALOJİSİ**
>
> 🍔 McDonald's analojisini düşünün:
>
> Dünyada binlerce McDonald's var ama hepsinde aynı menü var. Siz açken **en yakın** McDonald's'a gidersiniz. "En yakın" otomatik seçilir.
>
> AnyCast de böyle: Aynı IP adresi dünyanın farklı yerlerindeki onlarca sunucuda tanımlı. Siz sorgu gönderdiğinizde **en yakın sunucu** cevap verir.

| Yayın Türü | Hedef | Örnek |
|---|---|---|
| **Unicast** | 1 cihazdan 1 cihaza | Özel telefon konuşması |
| **Broadcast** | 1 cihazdan HERKESe | Radyo yayını |
| **Multicast** | 1 cihazdan belirli gruba | Abonelere canlı yayın |
| **AnyCast** | 1 cihazdan **EN YAKIN** cihaza | Root Server sorguları |

> ⭐ **HATIRLA!**
> - Hollanda'daki Root Server J kapandı → **Otomatik** en yakın diğer J'ye yönlendirilirsiniz
> - A sunucularının tümü kendi aralarında AnyCast yapar; **B sunucularıyla değil!**
> - **BGP (Border Gateway Protocol)** bu yönlendirme kararlarını verir
> - Aynı harf altındaki sunucular sürekli senkronize çalışır; biri güncellendi mi, diğerleri de anında güncellenir

---

## 2.7 DNS Kayıt Türleri

DNS sunucuları sadece IP adresi tutmaz. Farklı amaçlar için farklı kayıt türleri vardır:

| Kayıt Türü | Ne İşe Yarar? | Örnek |
|---|---|---|
| **A** | Alan adını **IPv4** adresine çevirir | `google.com` → `142.250.185.46` |
| **AAAA** (4×A) | Alan adını **IPv6** adresine çevirir | `google.com` → `2607:f8b0:...` |
| **CNAME** | Takma isim – bir domain'i başka domain'e yönlendirir | `twitter.com` → `x.com` |
| **MX** | Mail Exchange – e-posta hangi sunucuya gidecek? | Priority 10: `mailhost1.example.com` |
| **NS** | Bu alan adının yetkili DNS sunucusu hangisi? | `ns1.googledomains.com` |
| **TXT** | Metin tabanlı notlar, alan adı doğrulama | Alan adı sahipliği kanıtı |
| **SOA** | Start of Authority – Zone hakkında yönetici bilgisi | Hangi NS yetkili, seri no, yenileme süresi |

> ⚠️ **KARIŞTIRMA UYARISI!**
>
> **A KAYDI vs AAAA (4×A) KAYDI:**
> - **A kaydı** → IPv4 adresi → örn: `192.168.1.1` → 4 sayı grubu, nokta ile ayrılmış
> - **AAAA kaydı** → IPv6 adresi → örn: `2607:f8b0:4004::...` → çok daha uzun, `:` ile ayrılmış
>
> *Wireshark'ta gördüğünüz "A" sorgusu IPv4, "4A" sorgusu IPv6 içindir.*

> 📌 **GERÇEK HAYATTAN ÖRNEKLER**
>
> **CNAME için — Eğitmenin Twitter/X örneği:**
> Elon Musk Twitter'ı X olarak yeniden markalaştırdı. Ama siz hâlâ `twitter.com` yazıyorsunuz ve X'e gidiyorsunuz. Bu bir **CNAME** kaydı! `twitter.com → x.com` yönlendirmesi.
>
> **MX için — Eğitmenin mail analojisi:**
> Siz Gmail'den bir arkadaşınızın Hotmail adresine mail gönderdiniz. Direkt gitmiyor!
> **Gmail Server → Hotmail Server → Arkadaşınız**
> MX kayıtları bu yönlendirmeyi sağlar.
>
> **Güvenlik notu — ProtonMail:**
> Eğitmen ProtonMail'den bahsetti: *"Secure email that protects your privacy."*
> Ancak her iki taraf da Proton kullanmıyorsa, e-postanız bir noktadan sonra açık metin (clear text) olarak gidebilir. E-postalar varsayılan olarak şifresiz iletilir!
>
> **Brave Browser:**
> Eğitmenin notu: "Brave browser, siber güvenlik perspektifinden diğer tarayıcılara göre daha güvenli kabul edilir."

---

## 2.8 Wireshark'ta DNS Trafiği

Eğitmen Attack Box üzerinde canlı demonstrasyon yaptı. Öğrendiklerimiz:

- Wireshark'ta filtre olarak `dns` yazdığınızda sadece DNS paketleri görünür
- Her DNS sorgusunda **iki** paket gider: Biri IPv4 için (A), biri IPv6 için (AAAA)
- `Standard Query` → Siz sordunuz | `Standard Query Response` → Cevap geldi
- Her DNS paketi **UDP** protokolü kullanır (bilgisayar ↔ Local DNS arası)
- Kaynak port: Dinamik aralık (49152-65535) | Hedef port: Her zaman **53**

> 📌 **GERÇEK HAYATTAN ÖRNEK — UDP vs TCP Karşılaştırması**
>
> *Eğitmenin mükemmel hesabı:*
>
> `oakacademy.de`'nin A kaydını öğrenmek için:
>
> **UDP ile:** 1 Query + 1 Response = **2 paket** ✅
>
> **TCP ile:**
> ```
> SYN → SYN-ACK → ACK          (3 paket — bağlantı kurma)
> Query → Response               (2 paket — asıl iş)
> FIN+ACK → ACK → FIN+ACK → ACK (4 paket — kapanış)
> TOPLAM: 9 paket ❌
> ```
>
> **4,5 kat daha fazla trafik!** Milyarlarca DNS sorgusunda bu fark devasa olur. İşte bu yüzden DNS **UDP** kullanır.

---

## 2.9 NSLookup Komutu – DNS Sorgu Aracı

**NSLookup (Name Server Lookup):** Windows, Linux ve MacOS'ta çalışan evrensel bir DNS sorgulama aracıdır.

| Komut | Ne Yapar? |
|---|---|
| `nslookup` | NSLookup modunu başlatır |
| `nslookup google.com` | Google'ın IP adresini bulur |
| `set query=a` | Sadece IPv4 (A) kayıtlarını getir |
| `set query=aaaa` | Sadece IPv6 (AAAA) kayıtlarını getir |
| `set query=mx` | Mail sunucusu (MX) kayıtlarını getir |
| `set query=ns` | Name Server kayıtlarını getir |
| `server 8.8.8.8` | Sorgu yapılan DNS sunucusunu Google'a değiştir |
| `server 1.1.1.1` | Sorgu yapılan DNS sunucusunu Cloudflare'a değiştir |

> 📌 **GERÇEK HAYATTAN ÖRNEKLER**
>
> Eğitmenin canlı olarak gösterdiği örnekler:
>
> - `meta.com` sorgulandığında: Facebook, Instagram, WhatsApp'ın bulunduğu en yakın sunucu IP'si gelir
> - **CNN'in MX kaydı:** `senomx.mailprotection.outlook.com` → CNN, Microsoft'un mail altyapısını kullanıyor!
> - **oakacademy.de MX kaydı:** `exchange.aspmx.google.com` → 5 farklı Google mail sunucusu
>
> *Eğitmenin extra tüyo (off the record):*
>
> "Erişilemeyen bir siteye gitmek için: NSLookup ile farklı bir DNS sunucusundan IP adresini öğrenin. Sonra o IP'yi direkt tarayıcıya yazın. (WAF yoksa çalışır)"

---

## 2.10 DIG Komutu – Gelişmiş DNS Sorgulama

**DIG (Domain Information Groper):** Yalnızca **Linux'ta** çalışan, NSLookup'tan daha güçlü bir DNS aracıdır.

| Komut | Ne Yapar? |
|---|---|
| `dig google.com` | Google'ın A kayıtlarını getirir |
| `dig oakacademy.de +short` | Kısa, sadece sonuç formatında gösterir |
| `dig oakacademy.de mx` | MX kayıtlarını getirir |
| `dig oakacademy.de any` | Tüm kayıt türlerini birden getirir |
| `dig @8.8.8.8 oakacademy.de mx` | Google DNS'e sorarak MX kaydını getirir |
| `dig -x [IP adresi]` | IP'den alan adını bulur (Reverse DNS) |

> ⭐ **HATIRLA!**
> - **DIG** → Sadece Linux | **NSLookup** → Windows, Linux, MacOS (hepsi)
> - DIG çıktısında **TTL** değeri: O IP'nin cache'de kaç saniye tutulacağı
>   - `google.com` → 4 saniye | `oakacademy.de` → 300 saniye
> - NSLookup ve DIG, siber güvenlikçilerin ve network yöneticilerinin en sık kullandığı araçlar arasında

> 📝 **KENDİNİ TEST ET**
>
> **1.** DNS çözümleme sürecini 5 adımda sıralayın.
> > *Cevap: 1) Kendi cache → 2) Local DNS (ISP) → 3) Root Server → 4) TLD Server → 5) Authoritative DNS → IP adresi döner*
>
> **2.** Neden DNS UDP kullanır, TCP değil?
> > *Cevap: UDP ile 2 paket yeterli (sorgu + cevap). TCP ile 9 paket gerekir. Milyarlarca DNS sorgusunda bu fark çok büyük.*
>
> **3.** Elon Musk Twitter'ı X olarak değiştirdi. `twitter.com` yazan kullanıcılar `x.com`'a gidiyor. Bu hangi DNS kayıt türü sayesinde?
> > *Cevap: CNAME (Canonical Name – Takma İsim) kaydı. `twitter.com → x.com` yönlendirmesi CNAME ile yapılır.*

---

## 2.11 Alan Adı Kayıt Hiyerarşisi – ICANN

Bir domain adı satın aldığınızda arka planda şu yapı çalışır:

| Seviye | Kim? | Görev |
|---|---|---|
| **1 — En Üst** | **ICANN** | Kâr amacı gütmeyen, tüm sistemi yöneten üst kurum |
| **2** | **Registry Operators** | `.com`, `.net`, `.org` gibi TLD'lerin merkezi veritabanını yöneten kuruluşlar |
| **3** | **Registrar'lar** | ICANN tarafından akredite edilmiş, domain satma yetkisi olan firmalar |
| **4** | **Reseller'lar (Bayiler)** | Registrar'lardan toplu alan, son kullanıcıya satan bayiler |
| **5 — En Altta** | **Registrant (Siz!)** | Domain'i satın alan gerçek kişi veya kuruluş |

> 📌 **GERÇEK HAYATTAN HİKAYELER**
>
> **Hikaye 1 – Domain Squatting (Alan Adı Ele Geçirme):**
>
> *Eğitmenin anlattığı:* "40 yıldır faaliyet gösteren bir firma web sitesi almak istedi. Ama o alan adını bir şahıs çoktan almış! Şahıs 25.000–50.000 dolar istedi."
>
> Bu bir iş kolu haline gelmiştir. İnsanlar ünlü markaların, yeni kurulacak partilerin isimlerini önceden satın alır.
>
> ---
>
> **Hikaye 2 – Siyasi Parti:**
>
> *Eğitmenin anlattığı:* "Bir siyasi parti kurulmadan önce isim spekülasyonları başladı. Bazı kişiler bu isimlerle domain aldı. Parti kurulduğunda resmi web sayfasını o domain ile açamadılar!"
>
> ---
>
> **Hikaye 3 – Şirket E-posta Yönetimi:**
>
> *Eğitmenin iş yerinden:* "15 kişilik şirkette mail sistemi vardı. Biz şirket domain'indeki e-postaları Google Workspace'e bağladık. Her mail için aylık 1 dolar ödedik. Böylece Google'ın güvenli altyapısını şirket domaini için kullandık."

> ⭐ **HATIRLA!**
> - **ICANN** = İnternetin anayasasını yazan, kâr amacı gütmeyen kuruluş
> - **Registrar** = ICANN'dan domain satma yetkisi almış firma (GoDaddy, Namecheap gibi)
> - **Reseller** = Registrar'dan bayi olmuş firma (birçok hosting şirketi)
> - `com.tr` almak için eskiden ticaret sicil belgesi gerekiyordu, artık serbestleşti
> - Herhangi bir ülkedeki domain'i başka bir ülkedeki kişi alabilir — **sınır yok**
> - **WHOIS** verileri bile saldırganlar için değerli istihbarat kaynağıdır!

### Country Code TLD'ler (Ülke Uzantıları)

| Uzantı | Ülke | Kayıt Yılı |
|---|---|---|
| `.tr` | Türkiye ve Kuzey Kıbrıs | 1990 |
| `.de` | Almanya | 1986 |
| `.uk` | İngiltere | 1985 |
| `.us` | Amerika Birleşik Devletleri | 1985 |
| `.jp` | Japonya | 1986 |

---

---

# GENEL ÖZET
# 📚 GENEL TEKRAR VE ÖZET

## Bu Derste İşlenen Tüm Konular — Tek Cümlelik Özet

| Konu | Tek Cümlelik Özet |
|---|---|
| **Transport Layer** | Veriyi segmentlere böler, hata kontrolü yapar ve port numaraları aracılığıyla doğru uygulamaya iletir. |
| **Port Numaraları** | 0-1023 sistem portları, 1024-49151 uygulama portları, 49152-65535 dinamik portlardır. |
| **3-Way Handshake** | TCP bağlantısı SYN→SYN-ACK→ACK ile kurulur, FIN paketleriyle kibarca kapatılır. |
| **TCP Flags** | SYN bağlan, ACK onayla, FIN kibarca kapat, RST zorla kes, PSH hemen ilet, URG acil. |
| **TCP vs UDP** | TCP güvenilir ama yavaş; UDP hızlı ama güvensiz; hangisini kullanacağınız amaca göre değişir. |
| **DNS** | Alan adlarını IP adreslerine çeviren, internetin telefon defteri işlevi gören sistemdir. |
| **DNS Çözümleme** | Kendi cache → ISP DNS → Root Server → TLD Server → Authoritative DNS → IP adresi. |
| **Root Servers** | 13 çeşit (A-M), ~1.958 fiziksel kopya, AnyCast teknolojisiyle dünyaya dağıtılmış. |
| **AnyCast** | Tek IP adresi birden fazla fiziksel sunucuda tanımlı; en yakın sunucu cevap verir. |
| **DNS Kayıtları** | A (IPv4), AAAA (IPv6), CNAME (takma isim), MX (mail), NS (yetkili sunucu), SOA (yönetici bilgisi). |
| **NSLookup / DIG** | DNS sorgularını manuel yapmaya yarayan; NSLookup her işletim sisteminde, DIG yalnızca Linux'ta. |
| **ICANN Hiyerarşisi** | ICANN → Registrar → Reseller → Registrant şeklinde alan adı kayıt hiyerarşisi. |

---

## 🔢 Önemli Sayı ve Bilgiler

| Sayı / Değer | Ne Anlama Gelir? |
|---|---|
| **65.536** | Toplam TCP veya UDP port sayısı (2¹⁶) |
| **0 – 1.023** | Well-Known (Sistem) portlar |
| **53** | DNS port numarası (UDP 53: bilgisayar↔DNS \| TCP 53: sunucular arası) |
| **3** | TCP bağlantısı kurulurken gönderilen paket sayısı |
| **4** | TCP bağlantısı kapatılırken gönderilen paket sayısı |
| **9** | Aynı DNS sorgusu TCP ile yapılsaydı gereken paket sayısı |
| **13** | Root Server çeşidi (A'dan M'ye) |
| **1.958** | Dünya genelinde fiziksel Root Server sayısı (Ocak 2026) |
| **8.8.8.8 / 8.8.4.4** | Google'ın DNS sunucuları |
| **1.1.1.1 / 1.0.0.1** | Cloudflare'ın DNS sunucuları |

---

## ✅ Son Hatırlatmalar

> ⭐ **HATIRLA!**
> - Siber güvenlikçi olarak port kapatmak değil, **açık portları RAPORLAMAK** sizin göreviniz
> - DNS yasakları **Local DNS seviyesinde** yapılır; DNS değiştirerek aşılabilir (ama ek engeller gelebilir)
> - E-postalar varsayılan olarak **açık metin (clear text)** gider — ProtonMail gibi çözümler şifreleme sağlar
> - **Brave Browser**, siber güvenlik perspektifinden daha güvenli kabul edilen bir tarayıcıdır
> - **WHOIS verileri** bile saldırganlar için değerli istihbarat kaynağıdır
> - Önümüzdeki derslerde: **Network Topolojileri** ve **CTF sınavı** hazırlığı
> - nmap dersleri geçtikten sonra açık port taraması uygulamalı olarak yapılacak



