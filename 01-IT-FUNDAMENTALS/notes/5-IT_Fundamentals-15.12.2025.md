# IT Fundamentals-6 Ders Kaydı İşlenmiş Ders Notu

**Kaynak transkript:** `5-15.12.2025_-_IT_Fundamentals-6.docx`

Bu dersin ana ekseni şudur:

> **Bilgisayar donanımı + işletim sistemi + ağ bileşenleri + uygulamalar + sanallaştırma + konteyner mantığı = siber güvenliğin teknik zemini.**

---

# ADIM 1 — Metnin Ana Başlıkları

## 1. Ders ve Eğitim Süreci Bilgilendirmesi

Burada eğitmen; Almanca dersleri, Soft Skills, kariyer çalışmaları, Job Center, Almanya’dan katılan öğrenciler, etüt ve sanallaştırma kurulumu hakkında bilgi veriyor.

## 2. Siber Güvenlik Temeli ve CIA Triad

Siber güvenliğin üç temel direği anlatılıyor:

- Confidentiality (Gizlilik)
- Integrity (Bütünlük)
- Availability (Erişilebilirlik)

## 3. Gerçek Siber Saldırı Hikâyesi

Bir firmanın saldırı tehdidi alması, para istenmesi, ödeme yapılmayınca sistemlerinin çökertilmesi anlatılıyor.

## 4. Güvenlik Politikası, Firewall, EDR, SIEM, Pentest

Bir kurumun siber saldırıya karşı nasıl hazırlanması gerektiği açıklanıyor.

## 5. Bilgisayar Donanımı

Anakart, işlemci, RAM, ROM, BIOS, POST, power supply, UPS, ekran kartı, ses kartı, DVD sürücü, giriş/çıkış birimleri anlatılıyor.

## 6. Network Bileşenleri

NIC, MAC adresi, Switch, Hub, Router, Firewall, WAP, DSL modem, kablo modem gibi ağ cihazları anlatılıyor.

## 7. Network Güvenliği ve Ürün Güveni

Trump-Huawei örneği, Palo Alto, Cisco, CVE, Gartner gibi kavramlar üzerinden ağ cihazlarının da güvenlik riski oluşturabileceği açıklanıyor.

## 8. İşletim Sistemleri

Windows, Linux, macOS, Android, iOS; GUI, CLI, açık kaynak, kapalı kaynak kavramları anlatılıyor.

## 9. Application, Service, Process, Interface

Uygulama, servis, proses, arayüz, Task Manager, PowerShell ve saldırı yüzeyi ilişkisi açıklanıyor.

## 10. Client-Server Modeli

İstemci, sunucu, request-response modeli; YouTube, Instagram, Yahoo, Gmail örnekleriyle anlatılıyor.

## 11. Database, SQL ve SQL Injection

Veri tabanı, ilişkisel veri tabanı, SQL dili, SQL Injection saldırıları ve sağlık sistemi örnekleri anlatılıyor.

## 12. API

API’nin garson benzetmesiyle iki sistem arasında veri taşıyan arayüz olduğu açıklanıyor.

## 13. Virtualization

Sanal makine, host, guest, hypervisor, VMware, VirtualBox, snapshot, backup, Type 1/Type 2 hypervisor anlatılıyor.

## 14. Containerization

Docker, Kubernetes, container engine, cloud, ölçeklenebilirlik, Black Friday, ÖSYM örneğiyle konteyner mantığı anlatılıyor.

## 15. Library ve Programming Language

Kütüphane dosyaları, DLL, LIB, statik/dinamik kütüphaneler ve programların bunları nasıl kullandığı açıklanıyor.

---

# BÖLÜM 1 — Eğitim Süreci ve Ders Akışı

## Bu nedir?

Bu bölüm teknik konudan önce eğitim programının nasıl ilerleyeceğini anlatır. Eğitmen; IT Fundamentals’ın son kısmına gelindiğini, ardından Network Fundamentals’a başlanacağını söylüyor.

Geçen özel isimler ve kavramlar:

- Job Center
- Almanya
- Almanca dersleri
- Beruf Deutsch / Berufliche Deutsch dersi olarak yorumlanabilir
- Soft Skills
- Sibel Hanım
- Ümit Bey
- Elif Hanım
- TryHackMe
- Etüt
- Sanallaştırma kurulumu

## Bunu neden öğreniyoruz?

Çünkü siber güvenlik eğitimi sadece teknik araç kullanmak değildir. İş hayatı, kariyer platformları, iletişim becerileri ve ekip çalışması da mesleğin parçasıdır.

## Günlük hayat analojisi

Bir futbolcu sadece top sürmeyi bilirse yeterli olmaz. Takım oyunu, kondisyon, maç stratejisi ve iletişim de gerekir. Siber güvenlikte de Linux, ağ, saldırı araçları kadar iletişim ve kariyer yönetimi önemlidir.

> **HATIRLA**  
> Teknik bilgi seni kapıdan içeri sokar. İletişim, raporlama ve iş disiplini seni içeride tutar.

## Kendini Test Et

**1. Soft Skills neden önemlidir?**  
Cevap: Çünkü siber güvenlik uzmanı sadece teknik işlem yapmaz; rapor yazar, ekiplerle iletişim kurar, riskleri yönetime anlatır.

**2. Etütte yapılacak teknik çalışma neydi?**  
Cevap: Sanallaştırma kurulumu.

**3. IT Fundamentals’tan sonra hangi konuya geçilecekti?**  
Cevap: Network Fundamentals.

---

# BÖLÜM 2 — Siber Güvenlik ve CIA Triad

## Bu nedir?

CIA Triad, siber güvenliğin üç temel hedefidir.

## Confidentiality (Gizlilik)

Verinin sadece yetkili kişiler tarafından görülmesidir.

**Örnek:** Bir hastane sistemindeki hasta kayıtlarını sadece doktor ve yetkili personel görmelidir.

**Günlük hayat analojisi:** Evindeki kasaya sadece senin anahtarın varsa, kasadaki para gizlidir.

## Integrity (Bütünlük)

Verinin izinsiz değiştirilmemesidir.

**Örnek:** Bir banka hesabında 10.000 TL varsa, saldırgan bunu 100.000 TL yapamamalıdır.

**Günlük hayat analojisi:** Öğretmenin not defterindeki notların öğrenciler tarafından değiştirilememesi gerekir.

## Availability (Erişilebilirlik)

Sistemin ihtiyaç duyulduğunda çalışır durumda olmasıdır.

**Örnek:** E-devlet sistemine ihtiyacın olduğunda erişebilmen gerekir.

**Günlük hayat analojisi:** Bir hastanenin acil servisi kapalıysa, sağlık hizmeti var gibi görünür ama erişilebilir değildir.

## KARMAŞTIRMA!

| Kavram | Ne demek? | Örnek |
|---|---|---|
| Confidentiality (Gizlilik) | Yetkisiz kişi görmesin | Parola koruması |
| Integrity (Bütünlük) | Veri değiştirilmesin | Banka bakiyesi bozulmasın |
| Availability (Erişilebilirlik) | Sistem çalışsın | Web sitesi çökmesin |

> **HATIRLA**  
> Siber güvenlik sadece “veri çalınmasın” değildir. Veri doğru kalsın ve sistem çalışmaya devam etsin.

## Bunu neden öğreniyoruz?

Çünkü her saldırıyı bu üç başlıktan biriyle analiz edebilirsin:

- Veri mi çalındı? → Gizlilik ihlali
- Veri mi değiştirildi? → Bütünlük ihlali
- Sistem mi çöktü? → Erişilebilirlik ihlali

## Kendini Test Et

**1. Bir web sitesinin çökertilmesi CIA Triad’ın hangi ayağıyla ilgilidir?**  
Cevap: Availability (Erişilebilirlik).

**2. Hasta bilgilerinin internete sızması hangi ayağı ihlal eder?**  
Cevap: Confidentiality (Gizlilik).

**3. Bir faturanın tutarının izinsiz değiştirilmesi hangi ayağı ihlal eder?**  
Cevap: Integrity (Bütünlük).

---

# BÖLÜM 3 — Gerçek Siber Saldırı Hikâyesi

## Bu nedir?

Eğitmen, tanıdığı birinin çalıştığı firmanın siber saldırıya uğradığını anlatıyor. Saldırganlar firmadan para istiyor. Firma ödeme yapmayınca web sitesi ve uygulamaları çökertiliyor.

## Olayın özeti

1. Saldırganlar firmayı önceden tehdit ediyor.
2. “Para vermezseniz sistemi çökertiriz” diyorlar.
3. Firma ödeme yapmıyor.
4. Bir gün sonra sistemler çöküyor.
5. Kurumsal kaynak yönetimi sistemi çalışamaz hale geliyor.
6. Üretim süreçleri manuel ilerlemek zorunda kalıyor.

## Bunu neden öğreniyoruz?

Çünkü siber saldırı sadece bilgisayar problemi değildir. Üretimi, finansı, müşteri hizmetini, itibarı ve operasyonu durdurur.

## Günlük hayat analojisi

Bir fabrikanın elektrik panosu bozulursa sadece ışıklar sönmez. Üretim bandı, güvenlik sistemi, stok yönetimi ve sevkiyat da durur.

## KARMAŞTIRMA!

| Kavram | Yanlış düşünce | Doğru düşünce |
|---|---|---|
| Siber saldırı | Sadece web sitesi bozulur | Tüm iş süreçleri durabilir |
| Firewall | Tek başına yeter | Güvenlik katmanlarından sadece biridir |
| Pentest | Bir kere yapılır biter | Sürekli tekrar edilmelidir |
| Güvenlik politikası | Gereksiz belge | Kurumun savunma stratejisidir |

> **HATIRLA**  
> Saldırıdan sonra güvenlik kurmak pahalıdır. Saldırıdan önce güvenlik kurmak stratejidir.

## Kendini Test Et

**1. Firma saldırıdan sonra hangi problemi yaşadı?**  
Cevap: Sistemleri çöktü ve üretim süreçleri manuel ilerlemek zorunda kaldı.

**2. Sadece firewall almak neden yeterli değildir?**  
Cevap: Çünkü saldırılar çok katmanlıdır; EDR, SIEM, zafiyet taraması, farkındalık eğitimi ve pentest de gerekir.

**3. Bu olay CIA Triad’ın en çok hangi ayağını etkiler?**  
Cevap: Availability (Erişilebilirlik).

---

# BÖLÜM 4 — Güvenlik Politikası, Firewall, EDR, SIEM ve Pentest

## Bu nedir?

Bir kurumu korumak için kullanılan savunma yapılarıdır.

## Security Policy (Güvenlik Politikası)

Kurumun güvenliği nasıl sağlayacağını belirleyen kurallar bütünüdür.

**Analojisi:** Bir apartmanda yangın çıkarsa kim ne yapacak, hangi kapıdan çıkılacak, yangın tüpü nerede olacak? Bunların önceden belirlenmesi gerekir.

## Firewall (Güvenlik Duvarı)

Ağa giren ve ağdan çıkan trafiği filtreleyen güvenlik cihazı/yazılımıdır.

**Analojisi:** Site girişindeki güvenlik görevlisi gibi çalışır. Her geleni içeri almaz.

## EDR (Endpoint Detection and Response)

Bilgisayar, sunucu gibi uç cihazlarda şüpheli davranışları tespit eder ve müdahale eder.

**Analojisi:** Evdeki hareket sensörü gibidir. İçeri biri girdiyse fark eder.

## SIEM (Security Information and Event Management)

Sistemlerden log toplar, analiz eder, olayları ilişkilendirir.

**Analojisi:** Bir AVM’nin tüm kameralarını izleyen güvenlik merkezi gibidir.

## Pentest (Sızma Testi)

Yetkili güvenlik uzmanlarının sistemi saldırgan gibi test etmesidir.

**Analojisi:** Bir binanın hırsıza karşı dayanıklı olup olmadığını anlamak için kontrollü güvenlik testi yapmak gibidir.

## Zero Day (Sıfır Gün Açığı)

Henüz üretici tarafından bilinmeyen veya yaması olmayan güvenlik açığıdır.

**Analojisi:** Evin kapısında kimsenin fark etmediği gizli bir kilit kusuru olması gibi.

## Bunu neden öğreniyoruz?

Çünkü kurumsal güvenlik tek ürünle sağlanmaz. Güvenlik bir döngüdür:

1. Önlem al
2. İzle
3. Test et
4. Açıkları kapat
5. Tekrar izle

> **HATIRLA**  
> Siber güvenlik ürün değil, süreçtir.

## Kendini Test Et

**1. SIEM ne yapar?**  
Cevap: Log toplar, analiz eder ve güvenlik olaylarını ilişkilendirir.

**2. EDR hangi noktayı korur?**  
Cevap: Endpoint yani uç cihazları.

**3. Zero Day neden tehlikelidir?**  
Cevap: Çünkü henüz bilinen bir yaması veya savunması olmayabilir.

---

# BÖLÜM 5 — Estonya ve Louvre Müzesi Örnekleri

## Bu nedir?

Eğitmen, siber güvenlikte güçlü görünen yapıların bile saldırıya uğrayabileceğini anlatıyor.

## Estonya örneği

Estonya teknolojik altyapısı güçlü bir ülke olarak anlatılıyor. Ancak Kızıl Ordu anıtı ile ilgili olaydan sonra büyük bir siber saldırıya uğradığı ve yaklaşık üç hafta teknik altyapısının felç olduğu belirtiliyor.

## Louvre Müzesi analojisi

Çok değerli sanat eserlerini fiziksel olarak korumak yetmez. Kamera sistemleri, internet bağlantılı güvenlik sistemleri ve dijital altyapılar da korunmalıdır.

## Bunu neden öğreniyoruz?

Çünkü modern sistemlerde fiziksel güvenlik ve siber güvenlik iç içedir.

## Günlük hayat analojisi

Evinin kapısını çelik kapı yaptırdın ama akıllı kilidin internete bağlı ve parolası “123456”. Fiziksel olarak güçlü görünürsün ama dijital olarak zayıfsındır.

## KARMAŞTIRMA!

| Güvenlik türü | Koruduğu alan | Örnek |
|---|---|---|
| Fiziksel güvenlik | Bina, oda, cihaz | Kamera, kapı, güvenlik görevlisi |
| Siber güvenlik | Sistem, veri, ağ | Firewall, EDR, SIEM |
| Operasyonel güvenlik | Süreç | Kim neye erişebilir? |

> **HATIRLA**  
> İnternete bağlanan her kolaylık, saldırgan için de potansiyel bir giriş noktasıdır.

## Kendini Test Et

**1. Estonya örneği neyi gösterir?**  
Cevap: Teknolojik olarak güçlü sistemlerin bile siber saldırılarla felç edilebileceğini.

**2. Kamera sistemlerinin internete bağlı olması ne doğurur?**  
Cevap: Uzaktan erişim kolaylığı sağlar ama saldırı yüzeyi oluşturur.

**3. Fiziksel güvenlik tek başına yeterli midir?**  
Cevap: Hayır, dijital sistemler de korunmalıdır.

---

# BÖLÜM 6 — Bilgisayar Donanımı

## Bu nedir?

Bilgisayarın fiziksel parçalarıdır. Bunlara hardware (donanım) denir.

## Ana bileşenler

- Motherboard (Anakart)
- CPU / Processor (İşlemci)
- RAM (Geçici Bellek)
- ROM (Salt Okunur Bellek)
- BIOS
- Power Supply (Güç Kaynağı)
- SSD / HDD
- GPU (Ekran Kartı)
- Sound Card (Ses Kartı)
- DVD Drive
- Keyboard (Klavye)
- Mouse (Fare)
- Monitor (Monitör)
- Printer (Yazıcı)
- Microphone (Mikrofon)
- Speaker (Hoparlör)
- UPS (Kesintisiz Güç Kaynağı)

## Motherboard (Anakart)

Bilgisayardaki tüm parçaların bağlandığı ana devre kartıdır.

**Analojisi:** Bir şehirdeki yollar, kavşaklar ve elektrik hatları gibi düşün. Her şey anakart üzerinden haberleşir.

## CPU (İşlemci)

Bilgisayarın beynidir. Komutları işler.

**Analojisi:** Bir fabrikadaki karar veren yönetici gibidir.

## RAM

Bilgisayarın geçici çalışma alanıdır. Elektrik kesilirse içindeki veri gider.

**Analojisi:** Ders çalışırken masanın üstüne koyduğun kitaplar gibidir. İşin bitince kaldırılır.

## ROM

Üzerine kalıcı bilgi yazılan bellek türüdür.

**Analojisi:** Bir cihazın fabrika ayarlarını taşıyan küçük not defteri gibidir.

## BIOS

Bilgisayar açılırken donanımları kontrol eden temel sistemdir.

## POST (Power On Self Test)

Bilgisayar açılırken yapılan ilk donanım kontrolüdür.

**Analojisi:** Arabayı çalıştırmadan önce yağ, yakıt, fren kontrolü yapmak gibidir.

## UPS

Elektrik kesildiğinde bilgisayara kısa süre enerji sağlayan cihazdır.

**Analojisi:** Elektrik kesilince devreye giren yedek batarya gibidir.

## Input / Output Birimleri

| Tür | Örnek |
|---|---|
| Input (Giriş) | Klavye, fare, mikrofon |
| Output (Çıkış) | Monitör, hoparlör, yazıcı |

## KARMAŞTIRMA!

| Kavram | Ne işe yarar? | Karıştırılan nokta |
|---|---|---|
| RAM | Geçici veri tutar | Depolama değildir |
| SSD/HDD | Kalıcı veri tutar | RAM kadar hızlı değildir |
| ROM | Kalıcı sistem bilgisi | Kullanıcının normal dosyaları burada tutulmaz |
| BIOS | Açılış kontrolü yapar | İşletim sistemi değildir |

> **HATIRLA**  
> Anakart, işlemci ve RAM bir bilgisayarın temel merkezini oluşturur. Ama bilgisayarı kullanılabilir yapan şey işletim sistemidir.

## Kendini Test Et

**1. RAM elektrik kesilince veriyi korur mu?**  
Cevap: Hayır.

**2. POST ne zaman çalışır?**  
Cevap: Bilgisayar açılırken.

**3. UPS’in iki temel faydası nedir?**  
Cevap: Elektrik kesilince süre kazandırır ve elektrik dalgalanmalarına karşı koruma sağlar.

---

# BÖLÜM 7 — Network Bileşenleri

## Bu nedir?

Bilgisayarların birbirleriyle haberleşmesini sağlayan cihaz ve yapılardır.

## NIC (Network Interface Card)

Bilgisayarı ağa bağlayan ağ kartıdır.

İki türü vardır:

- Kablolu NIC
- Kablosuz NIC

## MAC Address

Ağ kartına fabrikada verilen fiziksel adrestir.

**Analojisi:** Bir kişinin kimlik numarası gibi düşünülebilir.

## Switch

Yerel ağdaki cihazları birbirine bağlar.

**Analojisi:** Bir apartmandaki daireler arası dahili telefon santrali gibidir.

## Hub

Eski ve daha ilkel ağ cihazıdır. Gelen veriyi herkese gönderir.

## Router

Farklı ağları birbirine bağlar. İnternete çıkışı sağlar.

**Analojisi:** Şehirler arası yolları birbirine bağlayan kavşak gibidir.

## Firewall

Ağ trafiğini filtreleyen güvenlik duvarıdır.

## WAP (Wireless Access Point)

Kablolu ağı kablosuz hale getirir.

**Analojisi:** Kablolu interneti Wi-Fi sinyaline çeviren dağıtıcı gibidir.

## KARMAŞTIRMA!

| Cihaz | Temel görev | Çalışma mantığı |
|---|---|---|
| Hub | Veriyi herkese yollar | Akılsız dağıtım |
| Switch | Yerel ağda doğru cihaza yollar | MAC adresi |
| Router | Farklı ağları bağlar | IP adresi |
| WAP | Kablosuzu sağlar | Kablolu sinyali Wi-Fi’ye çevirir |
| Firewall | Trafiği filtreler | Kurallara göre izin/verme |

> **HATIRLA**  
> Switch evin içindeki odaları bağlar. Router evi dış dünyaya bağlar.

## Kendini Test Et

**1. Switch hangi adres türüyle çalışır?**  
Cevap: MAC adresi.

**2. Router’ın temel görevi nedir?**  
Cevap: Farklı ağları birbirine bağlamak.

**3. WAP ne yapar?**  
Cevap: Kablolu ağı kablosuz erişime dönüştürür.

---

# BÖLÜM 8 — Network Güvenliği: Huawei, Trump, Palo Alto, Cisco, CVE

## Bu nedir?

Eğitmen, ağ cihazlarının da güvenlik riski oluşturabileceğini anlatıyor.

## Trump-Huawei örneği

ABD’de büyük ağ yönlendirme altyapısında Huawei ürünlerinin kullanılması tartışılıyor. Trump, Çinli bir firmanın ülkenin kritik yönlendirme altyapısında yer almasını güvenlik riski olarak görüyor.

## Ana fikir

Router, firewall, switch gibi cihazlar sadece donanım değildir. İçlerinde yazılım vardır. Yazılım varsa zafiyet olabilir.

## Palo Alto ve Cisco örneği

Palo Alto ve Cisco gibi kaliteli güvenlik ürünlerinde bile CVE kodlarıyla takip edilen güvenlik açıkları çıkabilir.

## CVE (Common Vulnerabilities and Exposures)

Bilinen güvenlik açıklarının standart kimliklendirme sistemidir.

**Analojisi:** Her güvenlik açığının plaka numarası gibidir.

## Gartner

Teknoloji ürünlerini değerlendiren analiz şirketidir. Liderler, vizyonerler, challenger gibi sınıflandırmalar yapar.

## Bunu neden öğreniyoruz?

Çünkü “pahalı ürün = mutlak güvenlik” değildir.

> **HATIRLA**  
> Güvenlik cihazının kendisi de saldırı yüzeyi olabilir.

## Kendini Test Et

**1. CVE ne işe yarar?**  
Cevap: Güvenlik açıklarını standart bir kodla takip etmeye yarar.

**2. Palo Alto gibi kaliteli ürünlerde açık çıkabilir mi?**  
Cevap: Evet.

**3. Router neden kritik güvenlik cihazıdır?**  
Cevap: Çünkü ağlar arası trafik onun üzerinden geçer.

---

# BÖLÜM 9 — İşletim Sistemleri

## Bu nedir?

Operating System (İşletim Sistemi), donanım ile kullanıcı/uygulama arasında tercümanlık yapan temel yazılımdır.

## Örnek işletim sistemleri

- Microsoft Windows
- Linux
- macOS
- Android
- iOS

## İşletim sistemi ne yapar?

- Donanımı yönetir
- Uygulamaları çalıştırır
- Dosya sistemini yönetir
- Giriş/çıkış işlemlerini yönetir
- Güncellemelerle güvenlik açıklarını kapatır

## Günlük hayat analojisi

Bir otelde resepsiyon görevlisi gibi düşün. Sen doğrudan mutfağa, temizlik ekibine veya teknik servise gitmezsin. Resepsiyona söylersin, o yönlendirir.

## GUI (Graphical User Interface)

Grafiksel kullanıcı arayüzüdür. Mouse ile tıklayarak işlem yaparsın.

## CLI (Command Line Interface)

Komut satırı arayüzüdür. Komut yazarak işlem yaparsın.

## KARMAŞTIRMA!

| Kavram | Kolaylık | Güç |
|---|---|---|
| GUI | Kullanımı kolay | Sınırlı |
| CLI | Öğrenmesi zor | Daha güçlü |
| Windows | Kullanıcı dostu | Kapalı kaynak |
| Linux | Daha teknik | Açık kaynak |
| macOS | Stabil | Kapalı kaynak |

> **HATIRLA**  
> GUI’de yaptığın çoğu şeyi CLI’da yaparsın. Ama CLI’da yapabileceğin her şeyi GUI’de yapamayabilirsin.

## Kendini Test Et

**1. İşletim sistemi neden gereklidir?**  
Cevap: Donanım ile uygulamalar/kullanıcı arasında iletişim sağlar.

**2. Linux neden siber güvenlikte önemlidir?**  
Cevap: Açık kaynaklıdır, özelleştirilebilir ve birçok güvenlik aracı Linux üzerinde çalışır.

**3. GUI neyi kolaylaştırmıştır?**  
Cevap: Bilgisayar kullanımını yaygınlaştırmıştır.

---

# BÖLÜM 10 — Application, Service, Process, Interface

## Application (Uygulama) nedir?

Kullanıcının belirli bir ihtiyacını karşılayan yazılımdır.

Örnekler:

- Microsoft Word
- PowerPoint
- Google Chrome
- VLC Player
- WhatsApp Desktop
- Instagram mobil uygulaması
- Pac-Man oyunu

## Service (Servis) nedir?

Arka planda çalışan, genellikle kullanıcıyla doğrudan etkileşime girmeyen yazılımdır.

Örnek:

- Yazdırma biriktiricisi
- Google Update Service
- Adobe Update Service
- Windows Search

## Process (Proses) nedir?

Çalışmakta olan bir uygulamanın aktif örneğidir.

Örnek: Chrome’da 10 sekme açıksa, birden fazla Chrome prosesi çalışabilir.

## Interface (Arayüz) nedir?

İki sistemin iletişim kurduğu ortak sınırdır.

Örnekler:

- NIC → Network Interface Card
- GUI → Graphical User Interface
- CLI → Command Line Interface
- API → Application Programming Interface

## KARMAŞTIRMA!

| Kavram | Ne demek? | Örnek |
|---|---|---|
| Application | Kullanıcının açtığı program | Chrome |
| Process | Çalışan program örneği | chrome.exe süreci |
| Service | Arka plan hizmeti | Windows Update |
| Interface | İletişim noktası | GUI, CLI, API |

> **HATIRLA**  
> Her servis bir tür proses olabilir; ama her proses servis değildir.

## Siber güvenlik açısından önemi

Servisler ve prosesler saldırganlar için gizlenme alanı olabilir. Örneğin saldırgan zararlı yazılımını normal görünen bir servis gibi çalıştırabilir.

## PowerShell uyarısı

PowerShell güçlü bir yönetim aracıdır. Kullanılmıyorsa kurumlarda kısıtlanması veya kontrol altına alınması önerilir. Çünkü saldırganlar uzaktan komut çalıştırmak için PowerShell’i kötüye kullanabilir.

## Kendini Test Et

**1. Servisler genelde nerede çalışır?**  
Cevap: Arka planda.

**2. Process nedir?**  
Cevap: Çalışmakta olan uygulama örneğidir.

**3. PowerShell neden güvenlik açısından dikkat gerektirir?**  
Cevap: Saldırganlar komut çalıştırmak için kullanabilir.

---

# BÖLÜM 11 — Client-Server Modeli

## Bu nedir?

Client-Server modeli, istemci ile sunucu arasındaki istek-cevap ilişkisidir.

## Client (İstemci)

İstek gönderen taraftır.

Örnek:

- Chrome
- Firefox
- Safari
- Opera
- FileZilla
- Mobil uygulama

## Server (Sunucu)

İsteğe cevap veren taraftır.

Örnek:

- YouTube sunucusu
- Instagram sunucusu
- Gmail sunucusu
- Yahoo sunucusu
- FTP sunucusu

## Request (İstek)

Client’ın server’a gönderdiği taleptir.

## Response (Cevap)

Server’ın client’a döndürdüğü yanıttır.

## Günlük hayat analojisi

Restoranda müşteri client’tır. Garson üzerinden sipariş verir. Mutfak server’dır. Sipariş hazırlanır ve cevap olarak yemek gelir.

## Bunu neden öğreniyoruz?

Çünkü web güvenliği, API güvenliği, SQL Injection, kimlik doğrulama ve ağ güvenliği hep client-server mantığı üzerine kuruludur.

> **HATIRLA**  
> İnternette yaptığın neredeyse her işlem bir request-response döngüsüdür.

## Kendini Test Et

**1. Chrome client mıdır server mıdır?**  
Cevap: Client.

**2. YouTube video sunduğunda hangi rolü üstlenir?**  
Cevap: Server.

**3. Request ne demektir?**  
Cevap: İstemcinin sunucuya gönderdiği istek.

---

# BÖLÜM 12 — Database, SQL ve SQL Injection

## Database (Veri Tabanı) nedir?

Verilerin sistemli şekilde tutulduğu depodur.

Örnek bilgiler:

- Ad
- Soyad
- Doğum tarihi
- Telefon
- Adres
- Sipariş bilgisi
- Sağlık kaydı
- Ürün bilgisi

## Günlük hayat analojisi

Bir okulun öğrenci kayıt defteri gibi düşün. Her satır bir öğrenci, her sütun bir bilgidir.

## Record (Kayıt)

Veri tabanındaki bir satırdır.

## Column (Sütun)

Aynı türde bilgilerin tutulduğu alandır.

## Relational Database (İlişkisel Veri Tabanı)

Tablolar arasında ilişki kuran veri tabanıdır.

Örnek: Müşteri tablosundaki `customer_id`, sipariş tablosundaki `customer_id` ile eşleşebilir.

## SQL (Structured Query Language)

Veri tabanından veri çekmek, eklemek, silmek veya güncellemek için kullanılan dildir.

## SQL Injection

Saldırganın veri tabanına zararlı SQL komutu enjekte etmesidir.

## Eğitmenin verdiği örnek

Hindistan ve Endonezya sağlık sistemlerine saldırı örnekleri veriliyor. Amaç sistemleri sadece kapatmak değil, sağlık verilerini ele geçirmek olabilir.

## KARMAŞTIRMA!

| Kavram | Ne demek? |
|---|---|
| Database | Verinin depolandığı sistem |
| SQL | Veri tabanıyla konuşma dili |
| SQL Injection | SQL komutlarını kötüye kullanma saldırısı |
| Record | Veri tabanındaki satır |
| Table | Verilerin tutulduğu tablo |

> **HATIRLA**  
> Veri tabanı kurumun hafızasıdır. SQL Injection bu hafızaya izinsiz müdahaledir.

## Kendini Test Et

**1. SQL ne işe yarar?**  
Cevap: Veri tabanında sorgu, ekleme, silme ve güncelleme işlemleri yapmaya yarar.

**2. SQL Injection ne tür bir saldırıdır?**  
Cevap: Veri tabanına zararlı SQL komutu enjekte etme saldırısıdır.

**3. Sağlık sistemleri neden saldırganlar için değerlidir?**  
Cevap: İçlerinde hassas kişisel ve tıbbi veriler bulunur.

---

# BÖLÜM 13 — API

## API nedir?

API (Application Programming Interface), iki yazılımın birbiriyle konuşmasını sağlayan arayüzdür.

## Eğitmenin garson analojisi

Sen restoranda masaya oturursun. Garson menüyü getirir, siparişi mutfağa iletir, yemeği sana getirir.

Burada:

- Sen: Kullanıcı
- Garson: API
- Mutfak: Server / uygulama
- Yemek: Veri

## Hava durumu örneği

Telefonunda hava durumu uygulamasına tıklarsın. Uygulama API üzerinden meteoroloji sunucusuna gider, veriyi alır ve sana gösterir.

## Endüstriyel otomat örneği

Bir içecek otomatından hangi lokasyonda ne kadar satış yapıldığını merkezi sisteme iletmek için API kullanılabilir.

## Bunu neden öğreniyoruz?

Çünkü modern uygulamalar API’ler üzerinden konuşur. API güvenliği siber güvenliğin kritik alanlarından biridir.

> **HATIRLA**  
> API veri üretmez; veriyi doğru yere götürür ve getirir.

## Kendini Test Et

**1. API’nin temel görevi nedir?**  
Cevap: İki yazılım sistemi arasında iletişim kurmak.

**2. API garson benzetmesinde hangi roldedir?**  
Cevap: Siparişi taşıyan aracı.

**3. API güvenliği neden önemlidir?**  
Cevap: Çünkü API üzerinden hassas verilere erişilebilir.

---

# BÖLÜM 14 — Virtualization (Sanallaştırma)

## Bu nedir?

Sanallaştırma, bir fiziksel bilgisayar üzerinde birden fazla sanal bilgisayar çalıştırma teknolojisidir.

## Örnek

Windows 11 bilgisayarının içine sanal olarak şunları kurabilirsin:

- Kali Linux
- Ubuntu
- Windows XP
- Windows Server 2012
- Windows Server 2003
- Red Hat
- OpenSUSE

## Host nedir?

Fiziksel ana bilgisayardır.

## Guest / Virtual Machine nedir?

Host üzerinde çalışan sanal bilgisayardır.

## Hypervisor nedir?

Sanal makineleri yöneten yazılımdır.

**Analojisi:** Bir orkestra şefi gibi düşün. Hangi sanal makine ne kadar RAM, CPU, disk kullanacak, bunu yönetir.

## Type 2 Hypervisor

Mevcut işletim sistemi üzerine kurulur.

Örnek:

- VMware Workstation
- Oracle VirtualBox
- Parallels
- QEMU
- Virtual PC

## Type 1 Hypervisor / Bare Metal

Doğrudan donanım üzerine kurulur.

Örnek:

- VMware ESXi
- KVM
- Xen
- Citrix Hypervisor

## Snapshot nedir?

Sanal makinenin belirli bir andaki görüntüsünü almaktır. Sorun olursa saniyeler içinde eski hale dönebilirsin.

## Backup ile Snapshot farkı

| Kavram | Ne yapar? | Hız |
|---|---|---|
| Backup | Yedek alır | Daha yavaş |
| Snapshot | Anlık durum kaydı alır | Çok hızlı |

## Siber güvenlikte kullanımı

- Zararlı dosya analizi
- Lab ortamı kurma
- Kali Linux kullanma
- TryHackMe çalışmaları
- Test ortamı oluşturma
- Sistemi bozup geri döndürme

> **HATIRLA**  
> Sanal makine, hata yapma lüksü sağlar. Bu yüzden siber güvenlik eğitiminde kritiktir.

## Kendini Test Et

**1. Hypervisor ne yapar?**  
Cevap: Sanal makineleri ve kaynak paylaşımını yönetir.

**2. Type 2 hypervisor örneği ver.**  
Cevap: VMware Workstation veya VirtualBox.

**3. Snapshot neden önemlidir?**  
Cevap: Sistemi hızlıca eski sağlam haline döndürmeye yarar.

---

# BÖLÜM 15 — Containerization

## Bu nedir?

Containerization, uygulamaları küçük, taşınabilir ve hızlı çalıştırılabilir paketler halinde yönetme yöntemidir.

## Günlük hayat analojisi

Kargo konteyneri düşün. İçine farklı ürünleri koyarsın, gemiye yüklersin, başka ülkeye taşırsın. Konteynerin içinde ne olduğu önemli değildir; taşıma standardı aynıdır.

## Virtual Machine ile Container farkı

| Özellik | Virtual Machine | Container |
|---|---|---|
| İşletim sistemi | Her VM kendi OS’ine sahip olabilir | Host OS kernelini paylaşır |
| Kaynak kullanımı | Daha ağır | Daha hafif |
| Başlama süresi | Daha yavaş | Daha hızlı |
| İzolasyon | Daha güçlü | Daha hafif izolasyon |
| Kullanım alanı | Lab, farklı OS testleri | Mikroservis, cloud, ölçeklenebilir uygulamalar |

## Docker nedir?

Container oluşturmak ve çalıştırmak için kullanılan popüler platformdur.

## Kubernetes nedir?

Container’ları merkezi olarak yöneten orkestrasyon sistemidir.

**Analojisi:** Docker konteynerleri taşır. Kubernetes limandaki trafik kontrol merkezidir.

## Eğitmenin e-ticaret örneği

Başta 1000 müşteri ve 10 ürün için bir sistem yeterlidir. Sonra müşteri 5000’e, ürün 50’ye çıkınca sistem yetmez. Yeni sunucular almak yerine container yapısı ile ihtiyaç arttıkça yeni container ayağa kaldırılır.

## Black Friday örneği

Alışveriş yoğunluğu artınca sistem otomatik olarak daha fazla container çalıştırabilir. Yoğunluk bitince container sayısı azaltılır.

## ÖSYM örneği

Sınav sonuçları açıklandığında yüz binlerce kişi aynı anda sisteme girer. Sadece o an için yüksek kapasite gerekir. Container/cloud mantığı burada işe yarar.

## KARMAŞTIRMA!

| Kavram | Ne işe yarar? |
|---|---|
| Docker | Container oluşturur/çalıştırır |
| Kubernetes | Container’ları yönetir |
| Cloud | Kaynakları kiralama mantığıyla sağlar |
| Load Balancing | Yükü sistemler arasında dağıtır |
| Scaling | İhtiyaca göre kapasite artırma/azaltma |

> **HATIRLA**  
> Container mantığı: “İhtiyaç artarsa çoğalt, ihtiyaç azalırsa kapat.”

## Kendini Test Et

**1. Docker ve Kubernetes aynı şey midir?**  
Cevap: Hayır. Docker container çalıştırır, Kubernetes container yönetir.

**2. Container neden cloud ortamında avantajlıdır?**  
Cevap: İhtiyaca göre hızlı ölçeklenebilir ve kullanılan kadar ödeme yapılabilir.

**3. Black Friday örneği hangi kavramı anlatır?**  
Cevap: Ölçeklenebilirlik ve otomatik kaynak artırımı.

---

# BÖLÜM 16 — Library ve Programming Language

## Library (Kütüphane) nedir?

Programların tekrar tekrar kullanabileceği hazır fonksiyon ve kod parçalarını barındıran dosyalardır.

## Örnek dosya türleri

- `.lib`
- `.dll`
- `.obj`
- `.exe`

## DLL nedir?

Dynamic Link Library yani dinamik bağlantı kütüphanesidir. Program çalışırken ihtiyaç duyduğu fonksiyonu DLL dosyasından çağırabilir.

## LIB nedir?

Statik kütüphane dosyasıdır. Genellikle program derlenirken kullanılır.

## Günlük hayat analojisi

Bir yemek kitabı düşün. Her yemek için “soğan nasıl doğranır?” kısmını tekrar yazmazsın. Ortak tarif tek yerde durur, herkes onu kullanır.

## Eğitmenin muhasebe örneği

Bir muhasebe programında `5525,50 TL` tutarını yazıyla “beş bin beş yüz yirmi beş lira elli kuruş” şeklinde yazdırmak istiyorsan, bunu yapan hazır bir kütüphane kullanılabilir.

## Siber güvenlik açısından önemi

Eksik veya bozulmuş DLL dosyaları sistem hatasına neden olabilir. Zararlı yazılımlar bazen sahte DLL dosyalarıyla sisteme sızabilir. Buna DLL hijacking gibi saldırılar örnek verilebilir.

> **HATIRLA**  
> Kütüphaneler yazılımcıya hız kazandırır; saldırgana da kötüye kullanılırsa fırsat verir.

## Kendini Test Et

**1. Library ne işe yarar?**  
Cevap: Hazır fonksiyonları ve kodları tekrar kullanılabilir hale getirir.

**2. DLL hangi tür kütüphanedir?**  
Cevap: Dinamik kütüphane.

**3. Kütüphane dosyalarının silinmesi neye yol açabilir?**  
Cevap: Programların veya işletim sisteminin hata vermesine.

---

# GENEL TEKRAR ve ÖZET

## Tüm konuların tek cümlelik özeti

1. **CIA Triad:** Siber güvenlik gizlilik, bütünlük ve erişilebilirlik üzerine kurulur.
2. **Gerçek saldırı hikâyesi:** Siber saldırılar şirketlerin üretim süreçlerini durdurabilir.
3. **Güvenlik politikası:** Kurum güvenliği ürün değil, sürekli iyileştirilen bir süreçtir.
4. **Firewall/EDR/SIEM/Pentest:** Savunma çok katmanlı kurulmalıdır.
5. **Estonya örneği:** Güçlü altyapılar bile saldırıyla felç olabilir.
6. **Donanım:** Bilgisayar fiziksel parçaların sistemli birleşimidir.
7. **Anakart:** Tüm bileşenlerin bağlandığı ana platformdur.
8. **BIOS/POST:** Bilgisayar açılırken temel donanım kontrolü yapar.
9. **UPS:** Elektrik kesintisi ve dalgalanmalara karşı koruma sağlar.
10. **Network bileşenleri:** Cihazlar ağ üzerinden haberleşmek için switch, router, NIC, WAP gibi yapılara ihtiyaç duyar.
11. **CVE:** Güvenlik açıklarının standart takip numarasıdır.
12. **İşletim sistemi:** Donanım ile kullanıcı/uygulama arasında tercümandır.
13. **CLI/GUI:** Komut satırı güçlü, grafik arayüz kullanımı kolaydır.
14. **Application:** Kullanıcı ihtiyacını karşılayan yazılımdır.
15. **Service:** Arka planda çalışan otomatik hizmettir.
16. **Process:** Çalışan uygulamanın aktif örneğidir.
17. **Interface:** İki sistemin iletişim noktasıdır.
18. **Client-Server:** İnternetteki temel istek-cevap modelidir.
19. **Database:** Verilerin sistemli şekilde saklandığı yapıdır.
20. **SQL Injection:** Veri tabanına zararlı sorgu enjekte etme saldırısıdır.
21. **API:** Yazılımlar arasında veri taşıyan arayüzdür.
22. **Virtualization:** Bir bilgisayarda birden fazla sanal sistem çalıştırmayı sağlar.
23. **Snapshot:** Sanal makineyi hızlıca eski haline döndürür.
24. **Containerization:** Uygulamaları hafif ve ölçeklenebilir paketler halinde çalıştırır.
25. **Docker/Kubernetes:** Container çalıştırma ve yönetme araçlarıdır.
26. **Library:** Programların ortak fonksiyonları tekrar kullanmasını sağlar.

---

# En Kritik 10 Hatırlatma

> **1.** Siber güvenlik sadece saldırı aracı öğrenmek değildir; sistemin nasıl çalıştığını anlamaktır.  
> **2.** CIA Triad her olay analizinde temel çerçevedir.  
> **3.** Firewall tek başına güvenlik değildir.  
> **4.** Güncelleme almayan sistem zafiyet üretir.  
> **5.** Ağ cihazları da saldırıya uğrayabilir.  
> **6.** CLI öğrenmeden siber güvenlikte ileri seviye olmak zorlaşır.  
> **7.** Servisler ve prosesler saldırganların gizlenebileceği alanlardır.  
> **8.** SQL Injection veri tabanı güvenliğinin temel saldırı tiplerinden biridir.  
> **9.** Sanal makineler güvenli lab ortamı sağlar.  
> **10.** Container ve cloud mantığı modern sistem mimarisinin temelidir.
