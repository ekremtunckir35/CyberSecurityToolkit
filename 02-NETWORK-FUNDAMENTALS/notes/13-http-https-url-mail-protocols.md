# Ağ Temelleri — Ders 13

<div align="center">

![Ders İnfografiği](../assets/13-topologies-devices-http-mail-protocols.png)

</div>

---

## Network Topolojileri · Switch · Router · HTTP/HTTPS · URL · SMTP/POP3/IMAP

# 🛡️ AĞ TEMELLERİ
## DERS 13 — UZMAN SİBER GÜVENLİK EĞİTİM NOTU

**Topoloji | Switch | Router | HTTP | HTTPS | SSL/TLS | URL | SMTP | POP3 | IMAP**  
---

# 📌 Bu Derste Ne Öğreniyoruz?

| Konu | Ne Yapar? | Neden Önemli? |
|---|---|---|
| Network Topolojileri | Ağ cihazlarının nasıl bağlandığını açıklar | Ağ tasarımı ve hata analizi için temel bilgidir |
| Switch | Aynı ağdaki cihazları MAC adresleriyle bağlar | LAN güvenliği ve VLAN mantığı için kritiktir |
| Router | Farklı ağları birbirine bağlar | İnternete çıkış, routing, NAT ve güvenlik için gereklidir |
| HTTP | Web sayfalarının taşınmasını sağlar | Web trafiğini anlamanın temelidir |
| HTTPS | HTTP trafiğini şifreler | Kimlik bilgisi ve veri güvenliği sağlar |
| SSL/TLS | Güvenli bağlantı kurar | HTTPS’in arkasındaki şifreleme sistemidir |
| URL | Web adresinin yapısını açıklar | Web isteklerini analiz etmek için gerekir |
| SMTP | E-posta gönderir | Mail güvenliği için bilinmelidir |
| POP3 | Mail indirir | Eski e-posta alma modelidir |
| IMAP | Mail senkronize eder | Modern e-posta kullanımının temelidir |

---

# 📚 BÖLÜM 1 — Network Derslerinde Zorlanmak Normaldir

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Eğitmen dersin başında önemli bir noktayı vurguluyor: Network konuları ilk başta karmaşık gelebilir. Çünkü her derste yeni kavram, yeni protokol, yeni cihaz ve yeni çalışma mantığı öğreniliyor.

Bu normaldir. Ama bu bilgiler ilerleyen derslerde tekrar tekrar kullanılacağı için zamanla oturacaktır.

## 🏠 Günlük Hayat Analojisi

İlk defa araba kullanmayı öğrenen biri gibi düşün.

İlk gün:

- Direksiyon zor gelir.
- Debriyaj zor gelir.
- Trafik işaretleri karışır.
- Vites geçişleri kafa yorar.

Ama birkaç hafta sonra birçok şeyi düşünmeden yaparsın.

Network de böyledir.

## ✅ HATIRLA!

> Network ezberlenmez.  
> Network tekrar ettikçe oturur.

## ⚠️ KARMAŞTIRMA!

| Yanlış Düşünce | Doğru Yaklaşım |
|---|---|
| “Her şeyi hemen anlamalıyım.” | Hayır, tekrar ettikçe oturur. |
| “Portları ezberleyemiyorum, yapamam.” | Önce mantığını öğren, portlar pratikte oturur. |
| “Topoloji gereksiz teori.” | Hayır, gerçek ağ tasarımı topolojiyle başlar. |

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Network konularında ilk başta zorlanmak normal midir?

**CEVAP:** Evet. Çünkü çok sayıda yeni kavram ve protokol öğrenilir.

### ❓ Soru 2
Network bilgileri ileride nerelerde kullanılır?

**CEVAP:** Security, firewall, CTF, operating systems, pentest ve blue team çalışmalarında.

### ❓ Soru 3
En doğru öğrenme yöntemi nedir?

**CEVAP:** Kavramları tekrar ederek, laboratuvarlarda uygulayarak ve notlara dönerek öğrenmek.

---

# 📚 BÖLÜM 2 — Network Topolojileri

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Network topolojisi, ağdaki cihazların nasıl yerleştirildiğini ve birbirine nasıl bağlandığını gösterir. Bir ağ kurmadan önce topoloji bilinmezse, cihaz yerleşimi, kablolama, maliyet ve güvenlik yanlış planlanır.

## 2.1 — Network Topology Nedir?

Network Topology, ağ cihazlarının geometrik veya mantıksal bağlantı düzenidir.

Eğitmenin ifadesiyle:

> Cihazların birbirine nasıl bağlanacağının geometrik gösterimidir.

## 🏠 Günlük Hayat Analojisi

Bir şehir haritası düşün.

- Yollar nereden geçiyor?
- Hangi mahalle hangi yola bağlı?
- Ana kavşak nerede?
- Alternatif yollar var mı?

Network topolojisi de ağın yol haritasıdır.

## 2.2 — Point-to-Point Topoloji

### Bu nedir?

İki cihazın doğrudan birbirine bağlanmasıdır.

Örnek:

- Bilgisayar ↔ Bilgisayar
- Bilgisayar ↔ Yazıcı
- İki şube arasında özel bağlantı

Derste eğitmen 1999–2000 yıllarında iki bilgisayarı kabloyla bağlama örneği verdi. O dönemde Line Printer tarzı kalın ve yavaş kablolardan bahsetti.

## 2.3 — Bus Topoloji

Tek ana hat üzerine cihazların bağlandığı eski yapıdır.

Özellikleri:

- Ana hat vardır.
- T-Connector kullanılır.
- Koaksiyel/anten kablosu benzeri kablo kullanılır.
- Başta ve sonda terminator bulunur.
- Ana hat koparsa ağ bozulur.

## 2.4 — Ring Topoloji

Cihazların halka şeklinde bağlanmasıdır.

Özellikleri:

- Her cihaz sıradaki cihaza bağlıdır.
- Token Ring mantığı vardır.
- Sırası gelen cihaz veri gönderir.
- Bağlantılardan biri koparsa iletişim bozulabilir.

## 2.5 — Star Topoloji

Günümüzde en yaygın kullanılan yapıdır.

Özellikleri:

- Ortada switch bulunur.
- Tüm cihazlar switch’e bağlanır.
- Cihaz eklemek kolaydır.
- Arıza tespiti kolaydır.
- Switch bozulursa tüm ağ etkilenir.

## 2.6 — Tree Topoloji

Birden fazla star topolojinin birleşmesidir.

Örnek:

3 katlı bir işletme:

- Her katta bir switch
- Her switch kendi katındaki cihazlara bağlı
- Switch’ler birbirine bağlı
- Böylece tüm bina tek ağ yapısına kavuşur

## 2.7 — Mesh Topoloji

Her cihazın diğer cihazlara alternatif yollarla bağlandığı yapıdır.

Avantajları:

- Yüksek yedeklilik
- Alternatif yollar
- Kesintiye dayanıklı yapı

Dezavantajları:

- Pahalı
- Kurulumu zor
- Çok kablo ve port gerekir

Routerların ve büyük internet omurgasının mantığı mesh yapısına benzer.

## 2.8 — Hybrid Topoloji

Birden fazla topolojinin birlikte kullanılmasıdır.

Örnek:

- Bir bölüm Star
- Bir bölüm Bus
- Bir toplantı odası Ring

## ⚠️ KARMAŞTIRMA!

| Topoloji | En Temel Farkı |
|---|---|
| Point-to-Point | İki cihaz doğrudan bağlıdır |
| Bus | Tek ana hat vardır |
| Ring | Halka şeklinde bağlantı vardır |
| Star | Merkezde switch vardır |
| Tree | Birden fazla star birleşir |
| Mesh | Alternatif yollar çoktur |
| Hybrid | Birden fazla yapı birlikte kullanılır |

## ✅ HATIRLA!

> Günümüzde en gerçekçi ve yaygın çözüm Star Topology’dir.  
> Mesh güçlüdür ama pahalıdır.  
> Tree, büyük bina ve kampüslerde mantıklıdır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Günümüzde en yaygın kullanılan topoloji hangisidir?

**CEVAP:** Star Topology.

### ❓ Soru 2
Bus topolojide ana hat koparsa ne olur?

**CEVAP:** Ağ iletişimi ciddi şekilde bozulur veya tamamen kesilir.

### ❓ Soru 3
Mesh topolojinin en büyük avantajı nedir?

**CEVAP:** Alternatif yollar sayesinde yüksek yedeklilik sağlamasıdır.

---

# 📚 BÖLÜM 3 — Switch Mantığı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Switch, yerel ağın merkezindeki cihazdır. Switch mantığını bilmeden VLAN, port security, MAC flooding, LAN güvenliği ve ağ segmentasyonu anlaşılamaz.

## 3.1 — Switch Nedir?

Switch, aynı yerel ağdaki cihazları birbirine bağlayan cihazdır.

Layer 2 yani Data Link katmanında çalışır.

MAC adresleri üzerinden iletişim sağlar.

## 3.2 — Switch Portları

Switch üzerinde fiziksel portlar vardır.

Örnek:

- 4 port
- 8 port
- 16 port
- 24 port
- 48 port
- 96 port

Bu portlar Transport Layer’daki TCP/UDP portlarıyla karıştırılmamalıdır.

## ⚠️ KARMAŞTIRMA!

| Kavram | Anlamı |
|---|---|
| Fiziksel Switch Portu | Ethernet kablosunun takıldığı fiziksel giriş |
| TCP/UDP Portu | Uygulama/protokol iletişimi için kullanılan mantıksal numara |

## 3.3 — Switch Türleri

| Switch Türü | Açıklama | Kullanım |
|---|---|---|
| Unmanaged Switch | Tak-çalıştır switch | Ev/küçük ofis |
| Smart / Hybrid Switch | Kısmen yönetilebilir | KOBİ |
| Managed Switch | Tam yönetilebilir | Kurumsal ağlar |

## 3.4 — Managed Switch

Yönetilebilir switch’tir.

Özellikleri:

- VLAN oluşturabilir.
- Port bazlı güvenlik sağlayabilir.
- Layer 3 seviyesinde bazı kontroller yapabilir.
- Gelişmiş yapılandırma sunar.
- Pahalıdır.
- Uzmanlık ister.

## 3.5 — Unmanaged Switch

Tak-çalıştır cihazdır.

Özellikleri:

- Ayar gerekmez.
- Elektriği ve kabloları takarsın, çalışır.
- Ucuzdur.
- Güvenlik kabiliyeti düşüktür.

## 3.6 — Smart / Hybrid Switch

İki modelin ortasıdır.

Özellikleri:

- Temel VLAN desteği olabilir.
- Basit arayüzü vardır.
- Managed kadar güçlü değildir.
- Unmanaged kadar basit değildir.

## 🏠 Günlük Hayat Analojisi

| Switch Türü | Analojisi |
|---|---|
| Unmanaged | Basit priz çoklayıcı |
| Smart | Ayarlanabilir priz grubu |
| Managed | Akıllı bina kontrol paneli |

## ✅ HATIRLA!

> Büyük kurum = Managed Switch  
> Küçük ortam = Unmanaged veya Smart Switch  
> Güvenlik ihtiyacı arttıkça yönetilebilirlik ihtiyacı da artar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Switch hangi katmanda çalışır?

**CEVAP:** Genellikle Layer 2, yani Data Link katmanında çalışır.

### ❓ Soru 2
Managed switch neden pahalıdır?

**CEVAP:** VLAN, güvenlik, yönetim ve gelişmiş konfigürasyon özellikleri sunduğu için.

### ❓ Soru 3
Switch portu ile TCP portu aynı şey midir?

**CEVAP:** Hayır. Switch portu fiziksel giriştir; TCP/UDP portu mantıksal iletişim numarasıdır.

---

# 📚 BÖLÜM 4 — MAC Address Table ve Switch Öğrenme Mantığı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Switch’in hangi cihazın hangi portta olduğunu nasıl bildiğini anlamak LAN güvenliği için zorunludur.

## 4.1 — MAC Address Table Nedir?

Switch şu eşleşmeyi tutar:

```text
Switch Portu ↔ Cihaz MAC Adresi
```

Örnek:

| Switch Portu | MAC Address |
|---|---|
| Port 1 | AA:AA:AA |
| Port 2 | BB:BB:BB |
| Port 4 | DD:DD:DD |

## 4.2 — Switch Nasıl Öğrenir?

1. Cihaz switch’e paket gönderir.
2. Switch gelen paketin kaynak MAC adresine bakar.
3. Paketin geldiği portu öğrenir.
4. MAC tablosuna işler.
5. Hedefi bilmiyorsa broadcast yapar.
6. Cevap gelen cihazın MAC adresini tabloya ekler.

## 4.3 — Switch Portlarının MAC Adresi Var mı?

Eğitmen burada kritik bir düzeltme yapıyor:

> Layer 2 switch’te her portun kendi MAC adresi yoktur. Switch sadece port-MAC eşleşmesini tablo olarak tutar.

## 4.4 — Aging Time

Switch’in MAC tablosundaki kayıtlar belirli süre sonra yenilenir.

Derste verilen değer:

```text
300 saniye = 5 dakika
```

## 4.5 — Full Duplex

Modern switch altyapısında iletişim full duplex olabilir.

Yani aynı anda hem veri gönderilir hem veri alınır.

## 🏠 Günlük Hayat Analojisi

Switch apartman görevlisi gibidir.

İlk başta kimin hangi dairede olduğunu bilmez. Gelenleri gördükçe liste tutar:

- Ahmet → 1. daire
- Ayşe → 4. daire
- Yazıcı → 7. daire

Sonra paketleri doğru yere yollar.

## ⚠️ KARMAŞTIRMA!

| Kavram | Ne Demek? |
|---|---|
| MAC Address Table | Switch’in tuttuğu port-MAC eşleşmesi |
| ARP Table | IP-MAC eşleşmesini tutar |
| Aging Time | Eski kayıtların silinme süresi |
| Full Duplex | Aynı anda gönderme ve alma |

## ✅ HATIRLA!

> Layer 2 switch ARP tablosu tutmaz.  
> MAC Address Table tutar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Switch hangi tabloyu tutar?

**CEVAP:** MAC Address Table.

### ❓ Soru 2
Aging Time ne işe yarar?

**CEVAP:** Kullanılmayan MAC kayıtlarını belirli süre sonra temizler.

### ❓ Soru 3
Full Duplex ne demektir?

**CEVAP:** Aynı anda hem veri gönderip hem veri alabilmektir.

---

# 📚 BÖLÜM 5 — Router

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Router farklı ağları birbirine bağlar. İnternete çıkış, NAT, routing, VPN ve WAN bağlantıları router mantığıyla anlaşılır.

## 5.1 — Router Nedir?

Router, farklı ağları birbirine bağlayan cihazdır.

Örnek:

- LAN ↔ WAN
- Şube ↔ Merkez
- Ev ağı ↔ İnternet
- 192.168.x.x ağı ↔ 10.x.x.x ağı

## 5.2 — ADSL Router Örneği

Evdeki modem aslında birkaç iş yapar:

| Parça | Görev |
|---|---|
| ADSL Modem | Telefon hattından gelen sinyali internet verisine çevirir |
| Router | İç ağı dış dünyaya bağlar |
| Access Point | Kablolu interneti Wi-Fi olarak yayar |
| Switch Portları | Kablolu cihazları bağlar |

## 5.3 — Router’ın Görevleri

- Farklı ağları bağlar.
- IP adreslerine göre yönlendirme yapar.
- Routing Table tutar.
- En iyi rotayı seçer.
- Trafiği güvenli ve hızlı yoldan iletmeye çalışır.
- Edge Router ve Core Router olarak farklı türleri vardır.

## 5.4 — Edge Router ve Core Router

| Router Türü | Görevi |
|---|---|
| Edge Router | Ev/kurum ağını dış dünyaya bağlar |
| Core Router | İnternet omurgasında çalışır |
| Wireless Router | Kablosuz yönlendirme sağlar |
| Virtual Router | Sanal/cloud ortamda çalışır |

## 🏠 Günlük Hayat Analojisi

Router şehirlerarası yol kavşağıdır.

Bir paket Ankara’dan İstanbul’a gidecekse, router hangi yolu kullanacağını seçer.

## ✅ HATIRLA!

> Switch aynı ağdaki cihazları bağlar.  
> Router farklı ağları bağlar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Router hangi katmanda çalışır?

**CEVAP:** Layer 3, Network katmanı.

### ❓ Soru 2
Router neye göre yönlendirme yapar?

**CEVAP:** IP adreslerine göre.

### ❓ Soru 3
Edge Router nedir?

**CEVAP:** Yerel ağı dış dünyaya bağlayan router’dır.

---

# 📚 BÖLÜM 6 — Routing Table, Metric ve Next Hop

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Bir paketin hedefe nasıl gittiğini anlamak için routing table mantığını bilmek gerekir.

## 6.1 — Routing Table Nedir?

Router’ın yol haritasıdır.

İçerdiği temel bilgiler:

- Network Identifier
- Destination Network
- Gateway
- Interface
- Metric
- Next Hop

## 6.2 — Metric Nedir?

Metric, bir yolun maliyet değeridir.

Düşük metric genellikle daha iyi yol anlamına gelir.

## 6.3 — Next Hop Nedir?

Paketin gideceği bir sonraki router’dır.

## 6.4 — Routing Algoritmaları

Derste şu kavramlardan bahsedildi:

- Distance Vector
- Link State
- Path Vector
- RIP
- EIGRP
- OSPF
- BGP

## ⚠️ Loop Problemi

Routing’de bir paket yanlış yönlendirilirse döngüye girebilir. Buna loop denir.

Path Vector yaklaşımı loop prevention açısından daha güçlüdür.

## 🏠 Günlük Hayat Analojisi

Navigasyon uygulaması gibi düşün.

- Hedef: İstanbul
- En kısa yol: düşük metric
- Alternatif yol: trafik varsa kullanılır
- Next hop: bir sonraki kavşak

## ✅ HATIRLA!

> Router en iyi yolu bulmak için routing table ve metric kullanır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Metric nedir?

**CEVAP:** Bir yolun maliyet/tercih değeridir.

### ❓ Soru 2
Next Hop nedir?

**CEVAP:** Paketin gideceği bir sonraki router’dır.

### ❓ Soru 3
Loop ne demektir?

**CEVAP:** Paketin hedefe ulaşmadan sürekli döngüye girmesidir.

---

# 📚 BÖLÜM 7 — HTTP: Web’in Temel Protokolü

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Web sitelerine girdiğimizde arka planda HTTP veya HTTPS çalışır. Web güvenliği, header analizi, web pentest ve trafik analizi için HTTP mantığı bilinmelidir.

## 7.1 — HTTP Nedir?

HTTP = Hypertext Transfer Protocol.

Web sayfalarının istemci ve sunucu arasında taşınmasını sağlar.

Application Layer’da çalışır.

## 7.2 — Stateless Nedir?

HTTP stateless bir protokoldür.

Yani her istek bağımsızdır. Sunucu önceki isteği doğal olarak hatırlamaz.

## 🏠 Günlük Hayat Analojisi

Bir gişeye gidiyorsun:

Sen: “Merhaba ben Şükrü.”  
Gişe: “Tamam, ne istiyorsunuz?”  
Sen tekrar gidiyorsun.  
Gişe seni hatırlamıyor.

HTTP de her isteği yeniymiş gibi değerlendirir.

## 7.3 — Peki Siteler Bizi Nasıl Hatırlıyor?

Cookie (Çerez) kullanarak.

Cookie, tarayıcıda tutulan küçük bilgi parçalarıdır.

Örnek:

- Oturum bilgisi
- Login durumu
- Kullanıcı tercihleri
- Sepet bilgisi

## ✅ HATIRLA!

> HTTP stateless’tir.  
> Kullanıcıyı hatırlama işi cookie ile yapılır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
HTTP hangi katmanda çalışır?

**CEVAP:** Application Layer.

### ❓ Soru 2
Stateless ne demektir?

**CEVAP:** Önceki isteklerin durum bilgisinin tutulmaması demektir.

### ❓ Soru 3
HTTP’de kullanıcı nasıl hatırlanır?

**CEVAP:** Cookie kullanılarak.

---

# 📚 BÖLÜM 8 — HTTP Request Yapısı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Web güvenlik analizinde request yapısını okumak gerekir. Burp Suite, Wireshark ve browser developer tools bu yapıyı gösterir.

## 8.1 — HTTP Request Bölümleri

Bir HTTP isteği şu bölümlerden oluşur:

1. Request Line
2. Headers
3. Blank Line
4. Message Body

## 8.2 — Request Line

Request Line içinde:

- HTTP Method
- Resource Path
- HTTP Version

bulunur.

Örnek:

```http
POST /account/login.php HTTP/1.1
```

## 8.3 — HTTP Methods

| Method | Ne Yapar? |
|---|---|
| GET | Veri çeker |
| POST | Yeni veri gönderir |
| PUT | Tüm veriyi günceller |
| PATCH | Verinin bir kısmını günceller |
| DELETE | Veri siler |
| HEAD | Sadece başlık bilgisi ister |
| OPTIONS | Desteklenen seçenekleri sorar |

## 8.4 — POST, PUT, PATCH Farkı

| Method | Anlamı |
|---|---|
| POST | İlk defa veri oluşturur |
| PUT | Tüm veriyi değiştirir |
| PATCH | Sadece belirli alanı değiştirir |

## 🏠 Günlük Hayat Analojisi

Bir form düşün:

- POST: Yeni kayıt oluşturmak
- PUT: Tüm formu baştan değiştirmek
- PATCH: Sadece telefon numarasını düzeltmek
- DELETE: Kaydı silmek

## ⚠️ KARMAŞTIRMA!

| Kavram | Fark |
|---|---|
| GET | Veri ister |
| POST | Veri gönderir |
| PUT | Tam günceller |
| PATCH | Kısmi günceller |
| DELETE | Siler |

## ✅ HATIRLA!

> Web pentest yapacaksan GET, POST, PUT, PATCH ve DELETE farkını bilmek zorundasın.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
GET ne işe yarar?

**CEVAP:** Sunucudan veri almak için kullanılır.

### ❓ Soru 2
POST ne işe yarar?

**CEVAP:** Sunucuya yeni veri göndermek için kullanılır.

### ❓ Soru 3
PATCH ile PUT farkı nedir?

**CEVAP:** PUT tüm veriyi günceller, PATCH sadece belirli kısmı günceller.

---

# 📚 BÖLÜM 9 — HTTP Response ve Status Code

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Web sunucusunun verdiği cevap kodları, bağlantının başarılı mı hatalı mı olduğunu gösterir. Pentest ve hata analizi için kritiktir.

## 9.1 — HTTP Response Yapısı

Bir HTTP cevabı şunlardan oluşur:

1. HTTP Version
2. Status Code
3. Reason Phrase
4. Response Headers
5. Blank Line
6. Message Body

Örnek:

```http
HTTP/1.1 200 OK
```

## 9.2 — Status Code Grupları

| Kod Grubu | Anlamı |
|---|---|
| 1xx | Bilgi |
| 2xx | Başarılı |
| 3xx | Yönlendirme |
| 4xx | İstemci hatası |
| 5xx | Sunucu hatası |

## 9.3 — Derste Geçen Örnekler

| Kod | Anlamı |
|---|---|
| 200 OK | Başarılı |
| 204 No Content | İçerik yok |
| 302 Found | Geçici yönlendirme |
| 307 Internal Redirect | İç yönlendirme |
| 401 Unauthorized | Yetkisiz |
| 404 Not Found | Sayfa bulunamadı |

## ⚠️ Güvenlik Uyarısı

Hata sayfaları saldırgan için bilgi kaynağı olabilir.

Örneğin:

- Server tipi
- Framework bilgisi
- Dosya yolu
- Yetkilendirme hatası
- Eksik kaynak

Bu bilgiler keşif aşamasında kullanılabilir.

## ✅ HATIRLA!

> 2xx iyidir.  
> 3xx yönlendirmedir.  
> 4xx istemci hatasıdır.  
> 5xx sunucu hatasıdır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
404 ne demektir?

**CEVAP:** Sayfa bulunamadı.

### ❓ Soru 2
200 OK ne demektir?

**CEVAP:** İstek başarıyla tamamlandı.

### ❓ Soru 3
500’lü hatalar neyi gösterir?

**CEVAP:** Sunucu taraflı hataları gösterir.

---

# 📚 BÖLÜM 10 — Browser Developer Tools ile HTTP İnceleme

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Tarayıcı geliştirici araçları ile HTTP request, response, method, status code ve protocol bilgileri görülebilir.

## 10.1 — Nasıl Açılır?

- F12 tuşu
- Sağ tık → İncele
- Menü → Diğer Araçlar → Geliştirici Araçları

## 10.2 — Network Sekmesi

Network sekmesinde şunlar görülür:

- Request URL
- Method
- Status Code
- Protocol
- Response Headers
- Request Headers
- Cookies
- Content Type
- User-Agent

## 10.3 — Derste Geçen Örnekler

Eğitmen şu sitelerde inceleme yaptı:

- google.com
- youtube.com
- oaccademy.d
- hackeracademy.uk
- developer.mozilla.org

Örnek gözlemler:

- Google için HTTP/3 görüldü.
- OAK Academy’de 307 redirect görüldü.
- Yanlış URL’de 404 Not Found görüldü.
- Request/Response Header alanları incelendi.

## ✅ HATIRLA!

> F12 → Network sekmesi, HTTP analizinin en hızlı başlangıç noktasıdır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Tarayıcıda geliştirici araçları hangi tuşla açılır?

**CEVAP:** F12.

### ❓ Soru 2
HTTP status code nerede görülür?

**CEVAP:** Network sekmesinde.

### ❓ Soru 3
Protocol sütunu neyi gösterir?

**CEVAP:** HTTP/1.1, HTTP/2, HTTP/3 gibi kullanılan protokol versiyonunu gösterir.

---

# 📚 BÖLÜM 11 — HTTP vs HTTPS

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

HTTP açık metin taşır. HTTPS ise şifreli iletişim sağlar. Kimlik bilgileri, kredi kartı bilgileri ve kişisel veriler için HTTPS zorunludur.

## 11.1 — HTTP Problemi

HTTP clear text yani açık metin çalışır.

Bu yüzden saldırgan trafiği dinlerse:

- Kullanıcı adı
- Parola
- Adres
- Telefon
- Kredi kartı

gibi bilgileri okuyabilir.

## 11.2 — HTTPS Nedir?

HTTPS = Hypertext Transfer Protocol Secure.

HTTP’nin güvenli halidir.

TLS/SSL ile şifreleme sağlar.

## 11.3 — HTTPS Ne Sağlar?

- Confidentiality (Gizlilik)
- Integrity (Bütünlük)
- Authentication (Kimlik Doğrulama)

## 🏠 Günlük Hayat Analojisi

HTTP açık kartpostal gibidir.  
Postacı dahil herkes okuyabilir.

HTTPS ise kilitli zarf gibidir.  
Yolda biri ele geçirse bile içeriği okuyamaz.

## ✅ HATIRLA!

> HTTP açık metindir.  
> HTTPS şifreli iletişim sağlar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
HTTP neden risklidir?

**CEVAP:** Verileri açık metin olarak taşıdığı için.

### ❓ Soru 2
HTTPS hangi güvenlik özelliklerini sağlar?

**CEVAP:** Gizlilik, bütünlük ve kimlik doğrulama.

### ❓ Soru 3
Kilit simgesi neyi gösterir?

**CEVAP:** Bağlantının HTTPS/TLS ile güvenli olduğunu gösterir.

---

# 📚 BÖLÜM 12 — SSL/TLS ve Sertifika Mantığı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

HTTPS’in güvenliği SSL/TLS ve sertifikalar üzerinden sağlanır. Web güvenliğini anlamak için sertifika mantığı bilinmelidir.

## 12.1 — SSL Nedir?

SSL = Secure Sockets Layer.

Eski güvenli iletişim protokolüdür.

## 12.2 — TLS Nedir?

TLS = Transport Layer Security.

SSL’in daha modern ve güvenli devamıdır.

Bugün teknik olarak TLS kullanılır, ama halk arasında hâlâ “SSL sertifikası” denir.

## 12.3 — Sertifika Ne İşe Yarar?

Sertifika, web sitesinin gerçekten iddia ettiği site olduğunu doğrulamaya yardım eder.

Tarayıcı şunu kontrol eder:

> “Bu site güvenilir bir sertifika otoritesi tarafından doğrulanmış mı?”

## 12.4 — Public Key / Private Key

| Anahtar | Açıklama |
|---|---|
| Public Key | Herkesle paylaşılabilir |
| Private Key | Sadece sunucuda kalır |

Public key ile şifrelenen veri, private key ile çözülür.

## 12.5 — Derste Geçen Kurumlar

- Google Trust Services
- Amazon CA
- TÜBİTAK
- Mozilla Certificate Store
- Windows Certificate Manager

## ✅ HATIRLA!

> SSL eski isimdir.  
> TLS güncel yapıdır.  
> Sertifika güven ilişkisinin temelidir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
TLS ne işe yarar?

**CEVAP:** İstemci ve sunucu arasında güvenli, şifreli iletişim sağlar.

### ❓ Soru 2
Public key herkesle paylaşılabilir mi?

**CEVAP:** Evet.

### ❓ Soru 3
Private key kimde kalmalıdır?

**CEVAP:** Sadece sunucuda/gizli tarafta kalmalıdır.

---

# 📚 BÖLÜM 13 — URL Yapısı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Web isteklerini analiz etmek için URL yapısını anlamak gerekir. Web pentest, log analizi ve HTTP trafiği incelemede URL temel bilgidir.

## 13.1 — URL Nedir?

URL = Uniform Resource Locator.

Web üzerindeki bir kaynağın adresidir.

## 13.2 — URL Parçaları

Örnek:

```text
https://www.example.com:443/path/to/file.html?key1=value1&key2=value2#section
```

| Parça | Anlamı |
|---|---|
| `https` | Scheme / Protokol |
| `www.example.com` | Domain |
| `443` | Port |
| `/path/to/file.html` | Resource Path |
| `?key=value` | Query Parameter |
| `#section` | Anchor / Sayfa içi konum |

## 🏠 Günlük Hayat Analojisi

URL bir posta adresi gibidir.

- Ülke
- Şehir
- Sokak
- Apartman
- Daire
- Kime teslim edileceği

Hepsi farklı parçaları temsil eder.

## ✅ HATIRLA!

> URL sadece domain değildir.  
> Protokol, path, parametre ve anchor gibi parçalar içerir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
URL ne demektir?

**CEVAP:** Uniform Resource Locator, yani web kaynağının adresidir.

### ❓ Soru 2
`?key=value` kısmı neyi ifade eder?

**CEVAP:** Query parameter yani sorgu parametresidir.

### ❓ Soru 3
`#section` ne işe yarar?

**CEVAP:** Sayfa içindeki belirli bir bölüme yönlendirir.

---

# 📚 BÖLÜM 14 — SMTP: E-posta Gönderme Protokolü

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

E-posta güvenliği siber güvenliğin temel alanlarından biridir. Phishing, spoofing, mail relay ve credential saldırılarını anlamak için SMTP bilinmelidir.

## 14.1 — SMTP Nedir?

SMTP = Simple Mail Transfer Protocol.

E-posta göndermek için kullanılır.

## 14.2 — SMTP Nerede Çalışır?

Mail gönderirken:

```text
Kullanıcı → Kendi Mail Sunucusu → Karşı Taraf Mail Sunucusu
```

bu süreçte SMTP kullanılır.

## 14.3 — SMTP Portları

| Port | Açıklama |
|---|---|
| 25 | Eski/standart SMTP, çoğu yerde kapalıdır |
| 465 | Güvenli SMTP |
| 587 | Modern ve önerilen güvenli SMTP portu |

Derste Türkiye’de ISP’lerin 25 numaralı portu kapatabildiği belirtildi.

## 🏠 Günlük Hayat Analojisi

SMTP posta gönderen kargo görevlisidir.

Sen mektubu verirsin.  
O, mektubu alıcının posta merkezine taşır.

## ✅ HATIRLA!

> SMTP mail gönderir.  
> Mail almak için POP3 veya IMAP kullanılır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
SMTP ne işe yarar?

**CEVAP:** E-posta göndermek için kullanılır.

### ❓ Soru 2
SMTP’nin önerilen modern portu hangisidir?

**CEVAP:** 587.

### ❓ Soru 3
SMTP mail almak için kullanılır mı?

**CEVAP:** Hayır. Mail almak için POP3 veya IMAP kullanılır.

---

# 📚 BÖLÜM 15 — POP3 ve IMAP

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

E-posta istemcilerinde mail alma yöntemlerini bilmek güvenlik, yedekleme ve senkronizasyon açısından önemlidir.

## 15.1 — POP3 Nedir?

POP3 = Post Office Protocol Version 3.

Mail sunucusundan e-postayı indirir.

Eski modeldir.

## POP3 Mantığı

- Mail sunucudan indirilir.
- Genellikle yerel bilgisayara kaydedilir.
- Başka cihazdan erişim zorlaşabilir.
- Sunucuda kopya bırakma opsiyonu olabilir ama sınırlıdır.

## 15.2 — IMAP Nedir?

IMAP = Internet Message Access Protocol.

Mail sunucusuyla cihazlar arasında senkronizasyon sağlar.

## IMAP Mantığı

- Mail sunucuda kalır.
- Bilgisayar, telefon, tablet aynı mailbox’ı görür.
- Silme, okundu bilgisi, klasör yapısı senkronize olur.
- Modern kullanımda daha yaygındır.

## 15.3 — POP3 vs IMAP

| Özellik | POP3 | IMAP |
|---|---|---|
| Mail nerede tutulur? | Genelde yerel cihazda | Sunucuda |
| Senkronizasyon | Zayıf | Güçlü |
| Çoklu cihaz kullanımı | Zor | Kolay |
| Eski mail erişimi | Cihaza bağlı | Sunucudan erişilebilir |
| Modern kullanım | Daha az | Daha yaygın |

## 🏠 Günlük Hayat Analojisi

POP3: Postacı mektubu getirir, sen alırsın, postanede kopya kalmaz.  
IMAP: Mektuplar postanede durur, sen her cihazdan aynı kutuya bakarsın.

## ✅ HATIRLA!

> SMTP gönderir.  
> POP3 indirir.  
> IMAP senkronize eder.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
POP3 ne işe yarar?

**CEVAP:** Mail sunucusundan e-postaları yerel cihaza indirmek için kullanılır.

### ❓ Soru 2
IMAP’in POP3’e göre avantajı nedir?

**CEVAP:** Mail, klasör ve okundu bilgisini cihazlar arasında senkronize eder.

### ❓ Soru 3
SMTP, POP3 ve IMAP arasındaki temel fark nedir?

**CEVAP:** SMTP mail gönderir; POP3 ve IMAP mail almak için kullanılır.

---

# 🗺️ GENEL TEKRAR VE ÖZET

## Tek Cümlelik Özet — Her Konu

| Konu | Tek Cümle Özet |
|---|---|
| Network Topolojisi | Ağ cihazlarının nasıl bağlandığını gösteren yerleşim modelidir. |
| Point-to-Point | İki cihazın doğrudan bağlandığı yapıdır. |
| Bus | Tek ana hat üzerinden çalışan eski topolojidir. |
| Ring | Cihazların halka şeklinde bağlandığı yapıdır. |
| Star | Merkezde switch bulunan en yaygın topolojidir. |
| Tree | Birden fazla star yapının birleşmesidir. |
| Mesh | Alternatif yolları çok olan dayanıklı ama pahalı yapıdır. |
| Switch | Aynı ağdaki cihazları MAC adresleriyle bağlar. |
| Managed Switch | VLAN ve güvenlik yönetimi sağlayan gelişmiş switch’tir. |
| MAC Address Table | Switch’in port-MAC eşleşmesini tuttuğu tablodur. |
| Router | Farklı ağları IP adreslerine göre birbirine bağlar. |
| Routing Table | Router’ın hedef ağlara giden yolları tuttuğu tablodur. |
| Metric | Router’ın en iyi yolu seçerken kullandığı maliyet değeridir. |
| HTTP | Web sayfalarının istemci-sunucu arasında taşınmasını sağlar. |
| Stateless | HTTP’nin önceki isteği doğal olarak hatırlamaması demektir. |
| Cookie | HTTP’de kullanıcıyı hatırlamak için kullanılan küçük veri parçasıdır. |
| HTTP Method | GET, POST, PUT, PATCH, DELETE gibi işlem türleridir. |
| HTTP Status Code | Sunucunun isteğe verdiği sonucu gösterir. |
| HTTPS | HTTP trafiğini TLS ile şifreleyen güvenli yapıdır. |
| SSL/TLS | Güvenli iletişim ve sertifika doğrulaması sağlar. |
| URL | Web kaynağının tam adresidir. |
| SMTP | E-posta göndermek için kullanılır. |
| POP3 | E-postayı sunucudan yerel cihaza indirir. |
| IMAP | E-postaları cihazlar arasında senkronize eder. |

---

# Kritik Port Listesi

| Port | Protokol | Açıklama |
|---|---|---|
| 25 | SMTP | Eski mail gönderme portu |
| 465 | SMTPS | Güvenli SMTP |
| 587 | SMTP Submission | Modern önerilen SMTP portu |
| 110 | POP3 | Eski mail alma portu |
| 143 | IMAP | Standart IMAP |
| 993 | IMAPS | Güvenli IMAP |
| 80 | HTTP | Şifresiz web trafiği |
| 443 | HTTPS | Şifreli web trafiği |

---

# Eğitmenin Önemli Uyarıları

1. Network konularını hemen ezberlemeye çalışma; tekrar ettikçe oturur.
2. Topoloji ağ tasarımının temelidir.
3. Star topoloji günümüzde en pratik çözümdür.
4. Mesh güçlüdür ama maliyetlidir.
5. Managed switch pahalıdır ama güvenlik için değerlidir.
6. Altyapı kablolaması kötüyse pahalı switch almak işe yaramaz.
7. HTTP açık metin taşır; hassas veri için risklidir.
8. HTTPS, TLS/SSL ile güvenli iletişim sağlar.
9. Developer Tools → Network sekmesi HTTP analizinde çok değerlidir.
10. SMTP mail gönderir; POP3/IMAP mail alır.
11. POP3 eski ve cihaz bağımlı çalışır.
12. IMAP modern ve senkronize çalışır.

---



**Network Temelleri Ders 13 · 19 Ocak 2026 · Topoloji / Switch / Router / HTTP / HTTPS / URL / SMTP / POP3 / IMAP**
