# Ders Kaydı İşlenmiş Notu

**Konu:** Cybersecurity'e Giriş + IT Fundamentals Başlangıcı  
**Kaynak:** Yüklenen ham ders transkripti esas alınarak hazırlanmıştır.

---

# ADIM 1 - Metnin Ana Haritası

Bu ders kaydında geçen ana konular:

1. **Eğitim Süreci ve Kullanılacak Platformlar**
   - LMS
   - Discord
   - TryHackMe
   - Quiz platformu
   - Udemy kaynakları
   - Etüt sistemi
   - Günlük tekrar ve ödev mantığı

2. **Siber Güvenlik Eğitim Yol Haritası**
   - IT Fundamentals
   - Network Fundamentals
   - Operating Systems
   - Security Module
   - Linux
   - Windows
   - Windows Server
   - Kali Linux
   - AttackBox
   - VPN
   - VMware / VirtualBox

3. **Cyber / Cyberspace / Cybersecurity Terminolojisi**
   - Cyber kavramı
   - Cybersecurity
   - Cyberspace
   - Cambridge Dictionary tanımı
   - NIST tanımı
   - Electronic information security

4. **Siber Güvenliğe Neden İhtiyaç Var?**
   - İnternetin yaygınlaşması
   - Sosyal medya
   - Finans sistemleri
   - Kritik altyapılar
   - Taşımacılık
   - Enerji
   - Savunma
   - Windows XP / eski sistem riski
   - Veri sızıntıları

5. **Gerçek Siber Güvenlik Olayları ve Örnekler**
   - Adobe veri sızıntısı
   - Akbank örneği
   - Rus hackerlar / Ukrayna savaşı
   - Deutsche Bahn
   - FireEye saldırısı
   - Lockheed Martin / F-35 verileri
   - Edward Snowden / NSA / CIA
   - PRISM, XKeyscore, Tempora
   - Estonya 2007 siber saldırıları
   - NATO CCDCOE
   - Stuxnet / Natanz / Siemens PLC / SCADA
   - Brompton Junction video analojisi
   - Brand identity copy
   - DDoS
   - Ransomware

6. **Siber Güvenliğin Temel Prensipleri**
   - Confidentiality (Gizlilik)
   - Integrity (Bütünlük)
   - Availability (Erişilebilirlik)
   - CIA Triad
   - Authentication (Kimlik doğrulama)
   - Multi-Factor Authentication
   - Identity and Access Management
   - Non-repudiation (İnkar edilemezlik)
   - Zero Trust
   - Log
   - SIEM
   - SOC Analyst

7. **Information Security ve Cybersecurity Farkı**
   - Bilgi güvenliği
   - Siber güvenlik
   - Matbu bilgi
   - Dijital bilgi
   - Sistem güvenliği

8. **Kariyer ve Sertifikalar**
   - CompTIA Security+
   - CEH
   - IBM sertifikaları
   - Cisco sertifikaları
   - Fortinet NSE
   - Splunk Enterprise Certified Admin
   - LinkedIn görünürlüğü
   - Coursera
   - Chiron

9. **IT Fundamentals Başlangıcı**
   - Bilgisayar nedir?
   - Bilgisayar çeşitleri
   - Input unit
   - Output unit
   - Storage
   - CPU

10. **Binary Sistem ve Sayı Sistemleri**
    - Decimal system
    - Binary system
    - Bit
    - Byte
    - Kilobyte
    - Megabyte
    - Gigabyte
    - Terabyte
    - ASCII
    - Hexadecimal
    - Transistor
    - Flip-flop

11. **Depolama Birimleri**
    - HDD
    - SSD
    - NVMe SSD / M.2
    - RAM
    - ROM
    - Flash memory
    - NAS
    - SAN
    - Cloud Storage
    - File System

---

# BÖLÜM 1 - Eğitim Süreci ve Kullanılacak Platformlar

## Bu bölümde ne öğreniyoruz?

Bu bölümde eğitimin nasıl ilerleyeceği, hangi platformların kullanılacağı, ödevlerin ve tekrarların nasıl yapılacağı anlatılıyor.

## LMS Nedir?

**LMS (Learning Management System)**, eğitim içeriklerinin tutulduğu dijital eğitim platformudur.

Bu derste LMS şu işler için kullanılacak:

- Ders dokümanları
- Kayıtlı ders videoları
- Etüt kayıtları
- Çözüm videoları
- Course Materials bölümü
- Platform tanıtım kayıtları

### Günlük hayat analojisi

LMS'i okulun **dijital dolabı** gibi düşün. Nasıl okulda defterlerin, kitapların, sınav kağıtların ve duyuruların belli bir yerde tutulması gerekiyorsa, burada da tüm eğitim materyalleri LMS üzerinde tutuluyor.

> **HATIRLA:** LMS = Dersin merkezi arşivi. Kaydı kaçırırsan, materyal lazımsa, çözüm videosu gerekiyorsa önce LMS'ye bakılır.

## Discord Nedir?

**Discord**, bu eğitimde anlık iletişim ve bilgi paylaşımı için kullanılacak platformdur.

Burada duyurular yapılır, Udemy kaynak linkleri paylaşılır, öğrenciler etiketlenir, çalışma ortamı kurulur ve sorular sorulabilir.

### Günlük hayat analojisi

Discord'u sınıfın **WhatsApp grubu + çalışma odası** gibi düşün. LMS arşivse, Discord canlı haberleşme alanıdır.

### KARMAŞTIRMA! LMS vs Discord

| Kavram | Ne İşe Yarar? | Benzetme |
|---|---|---|
| LMS | Ders kayıtları, dokümanlar, çözüm videoları | Okul kütüphanesi |
| Discord | Anlık mesajlaşma, duyuru, link paylaşımı | Sınıf WhatsApp grubu |

## TryHackMe Nedir?

**TryHackMe**, siber güvenlik öğrenmek için kullanılan çevrim içi uygulama/lab platformudur. Derste “TriHackMe” şeklinde geçmiş; en olası anlamı **TryHackMe** platformudur.

Burada odalar çözülür, siber güvenlik labları yapılır, Kali Linux kullanılabilir, AttackBox kullanılabilir ve öğrenci kendi bilgisayarına kurulum yapmadan uygulama yapabilir.

### Günlük hayat analojisi

TryHackMe'yi **siber güvenlik oyun parkı** gibi düşün. Gerçek sistemlere zarar vermeden, güvenli bir alanda saldırı ve savunma mantığını öğrenirsin.

> **HATIRLA:** TryHackMe = Uygulamalı siber güvenlik laboratuvarı.

## Quiz Sistemi

Eğitmen, her gün dersten sonra **20 soruluk quiz** paylaşılacağını söylüyor. Bu quizler o günkü konuyu tekrar ettirir, etüt saatinde öğretmen eşliğinde çözülür, katılamayanlar telefondan 5-10 dakikada çözebilir ve günlük tekrar için kullanılır.

### Günlük hayat analojisi

Quiz'i spor sonrası yapılan **soğuma hareketi** gibi düşün. Ders kası çalıştırır, quiz bilgiyi sabitler.

> **HATIRLA:** Günlük quiz çözmezsen konu birikir. Siber güvenlikte biriken konu, sonra duvar gibi önüne çıkar.

## Etüt Sistemi

Derslerden sonra 1 saat ara veriliyor, ardından etüt başlıyor. Etütte quizler çözülüyor, sorular cevaplanıyor, uygulamalar birlikte yapılıyor ve kaçırılan konular destekleniyor.

## Bunu Neden Öğreniyoruz?

Çünkü siber güvenlik eğitimi sadece ders dinleyerek öğrenilmez. Başarı için ders kaydını takip etmek, günlük quiz çözmek, TryHackMe lab yapmak ve etütlerde soru sormak gerekir.

## Kendini Test Et

1. **LMS ne için kullanılır?**  
   **Cevap:** Ders dokümanları, kayıtlı dersler, etüt kayıtları, çözüm videoları ve materyaller için kullanılır.

2. **Discord ile LMS arasındaki temel fark nedir?**  
   **Cevap:** LMS arşiv ve içerik platformudur; Discord anlık iletişim ve paylaşım platformudur.

3. **TryHackMe neden önemlidir?**  
   **Cevap:** Siber güvenlik konularını güvenli bir lab ortamında uygulamalı öğrenmeyi sağlar.

---

# BÖLÜM 2 - Siber Güvenlik Eğitim Yol Haritası

## Bu bölümde ne öğreniyoruz?

Siber güvenlik eğitimine doğrudan saldırı teknikleriyle başlanmadığını; önce temel IT, network ve işletim sistemi bilgisinin kurulacağını öğreniyoruz.

## Eğitim Modülleri

1. **IT Fundamentals:** Bilgisayarın temelleri, donanım, veri ve sayı sistemleri.
2. **Network Fundamentals:** Ağ temelleri, cihazların haberleşmesi, IP, bağlantı ve protokol mantığı.
3. **Operating Systems:** Windows, Windows Server ve Linux.
4. **Security Module:** Asıl siber güvenlik konuları; saldırı ve savunma, exploitation, Nmap, kriptografi, SIEM ve pentest.

## Neden Direkt Siber Güvenlikle Başlanmıyor?

Çünkü siber güvenlik, boşlukta duran bir alan değildir. Bilgisayar nasıl çalışır, ağ nasıl çalışır, işletim sistemi nasıl çalışır, dosya, kullanıcı, yetki ve servis nedir gibi temeller bilinmeden güvenlik öğrenimi ezbere dönüşür.

### Günlük hayat analojisi

Bir binanın alarm sistemini kurmadan önce binanın kapılarını, pencerelerini, elektrik hattını, odalarını ve giriş çıkış noktalarını bilmen gerekir. Siber güvenlik de aynıdır. Önce sistemi tanırsın, sonra sistemi korursun.

> **HATIRLA:** Sistemi bilmeden sistemi koruyamazsın. Network bilmeden firewall anlayamazsın. Linux bilmeden Kali Linux kullanamazsın.

## Linux Neden Önemli?

Linux, özellikle siber güvenlikte çok kullanılan bir işletim sistemidir. Öğrencilerin çoğu Windows, bazıları macOS kullanıyor. Linux çoğu öğrenci için yeni olacak. Siber güvenlikte Linux olmazsa olmazdır. Linux için öğrenciden kendi bilgisayarına kurulum istenmeyecek; TryHackMe üzerinde Kali Linux / AttackBox kullanılacak.

## Kali Linux Nedir?

**Kali Linux**, siber güvenlik araçlarıyla birlikte gelen özel bir Linux dağıtımıdır. İçinde Nmap, Metasploit, Burp Suite, Hydra, Wireshark, John the Ripper, Aircrack-ng gibi birçok araç bulunabilir.

## AttackBox Nedir?

TryHackMe içindeki hazır saldırı/analiz makinesidir. Öğrenci kendi bilgisayarına kurulum yapmadan bu makine üzerinden lab çözebilir.

## VPN Nedir?

**VPN (Virtual Private Network)**, uzaktaki bir ağa güvenli şekilde bağlanmayı sağlayan teknolojidir. Derste firewall labına bağlanma, uzak şehirdeki şirket bilgisayarına bağlanma ve farklı lokasyondaki sistemlere erişme örnekleri verilmiştir.

### Günlük hayat analojisi

VPN'i şirket binasına giden **özel güvenlik tüneli** gibi düşün. Normal internet herkesin geçtiği yolsa, VPN kimliği doğrulanmış kişilerin geçtiği özel yoldur.

## VMware ve VirtualBox Nedir?

Bunlar sanallaştırma araçlarıdır. Kendi bilgisayarında sanal bilgisayar oluşturmanı sağlar. Örneğin Windows içinde Linux çalıştırmak, Kali Linux kurmak veya lab ortamı kurmak mümkündür. Ancak ders için öğrencilerden kendi bilgisayarlarına Linux kurmaları istenmeyecek.

### KARMAŞTIRMA! Kali Linux vs Linux vs TryHackMe

| Kavram | Açıklama |
|---|---|
| Linux | Genel işletim sistemi ailesi |
| Kali Linux | Siber güvenlik araçları içeren özel Linux dağıtımı |
| TryHackMe | Lab ve eğitim platformu |
| AttackBox | TryHackMe içinde çalışan hazır saldırı makinesi |
| VMware / VirtualBox | Kendi bilgisayarında sanal makine çalıştırma yazılımları |

## Bunu Neden Öğreniyoruz?

Çünkü ileride firewall, exploit, log analizi, Linux komutları, SIEM ve pentest konularında bu temel bilgiler sürekli karşına çıkacak. Bu temeli atlamak, “komutu yazıyorum ama ne yaptığını anlamıyorum” noktasına götürür.

## Kendini Test Et

1. **Siber güvenlik eğitiminde neden önce IT Fundamentals anlatılır?**  
   **Cevap:** Bilgisayarın ve sistemlerin nasıl çalıştığını bilmeden onları korumak veya test etmek mümkün değildir.

2. **Kali Linux neden önemlidir?**  
   **Cevap:** Siber güvenlik araçlarıyla birlikte gelen, pentest ve güvenlik testlerinde sık kullanılan Linux dağıtımıdır.

3. **VPN'in temel amacı nedir?**  
   **Cevap:** Uzak bir ağa güvenli bağlantı sağlamaktır.

---

# BÖLÜM 3 - Cyber, Cyberspace ve Cybersecurity

## Önceki Konuyla Bağlantı

Bir önceki bölümde eğitimde önce IT, network ve işletim sistemi temellerinin öğrenileceğini gördük. Şimdi ise bu temellerin neden “cyber” alanına bağlandığını anlamamız gerekiyor.

## Cyber Nedir?

**Cyber**, bilgisayar, internet, ağ ve dijital sistemlerle ilişkili olan her şeyi ifade eder. Derste Cambridge Dictionary üzerinden bilgisayarla ve özellikle internetle ilişkili her şey olarak açıklanmıştır.

### Günlük hayat analojisi

“Cyber” kelimesini şehirdeki yollar gibi düşün. Evindeki tek bilgisayar internete bağlı değilse kendi başına duran bir ev gibidir. İnternete bağlandığında diğer evlere, bankalara, okullara ve mağazalara bağlanır. İşte o bağlantılı dijital dünya cyber alanıdır.

## Cyberspace Nedir?

**Cyberspace (Siber Uzay)**, bilgisayarların, ağların, cihazların ve internet üzerindeki sistemlerin oluşturduğu dijital ortamdır. Derste Facebook kullanım haritası örnek verilmiş; Amerika, Avrupa, Hindistan, Çin, okyanus adaları ve Afrika gibi bölgeler üzerinden cihazların birbirine bağlanabildiği anlatılmıştır.

### Günlük hayat analojisi

Cyberspace'i dünya çapında kurulmuş dev bir **posta ağı** gibi düşün. E-posta, WhatsApp mesajı, banka işlemi veya sosyal medya paylaşımı bu ağ üzerinden gider.

## Cybersecurity Nedir?

**Cybersecurity (Siber Güvenlik)**, dijital sistemleri, verileri, kişileri, kurumları ve ülkeleri siber saldırılara karşı koruma disiplinidir.

Derste üç tanım yaklaşımı geçiyor:

1. **Cambridge Dictionary:** Kişiyi, organizasyonu, ülkeyi ve bilgisayar bilgilerini suçlulardan koruma.
2. **NIST (National Institute of Standards and Technology):** Cyberspace'i siber saldırılardan koruma ve savunma yeteneği.
3. **Elektronik bilgi güvenliği yaklaşımı:** Elektronik bilgiyi gizli ve güvenli tutma, zarar görmesini veya çalınmasını engelleme.

## Siber Güvenlik Neyi Korur?

- Veriyi
- Elektronik bilgiyi
- IT sistemlerini
- Kişileri
- Şirketleri
- Ülkeleri
- Bilgisayar sistemlerini
- Kritik altyapıları
- Cihazları

## Siber Güvenlik Kimden Korur?

Siber suçlulardan, hackerlardan, devlet destekli saldırganlardan, zararlı yazılımlardan, veri hırsızlarından, casusluk faaliyetlerinden, DDoS saldırılarından, ransomware saldırılarından ve yetkisiz erişimlerden korur.

### KARMAŞTIRMA! Cyber vs Cyberspace vs Cybersecurity

| Kavram | Anlamı | Örnek |
|---|---|---|
| Cyber | Dijital/ağ bağlantılı olan | İnternet, bilgisayar, ağ |
| Cyberspace | Dijital sistemlerin oluşturduğu ortam | İnternet dünyası |
| Cybersecurity | Bu ortamı koruma disiplini | Firewall, şifreleme, SIEM |

> **HATIRLA:** Cyber = Dijital alan. Cyberspace = Dijital dünyanın kendisi. Cybersecurity = Bu dünyayı koruma işi.

## Bunu Neden Öğreniyoruz?

Çünkü siber güvenlik sadece “hacker yakalama” değildir. Banka hesabını, şirket sırlarını, devlet sistemlerini, sağlık verilerini, elektrik/su/ulaşım gibi kritik altyapıları ve bazen fiziksel cihazları korur.

## Kendini Test Et

1. **Cyber kelimesi neyi ifade eder?**  
   **Cevap:** Bilgisayar, internet, ağ ve dijital sistemlerle ilişkili olan her şeyi ifade eder.

2. **Cyberspace nedir?**  
   **Cevap:** Bilgisayarların, ağların ve internet bağlantılı sistemlerin oluşturduğu dijital ortamdır.

3. **Cybersecurity neyi korur?**  
   **Cevap:** Verileri, sistemleri, kişileri, şirketleri, ülkeleri ve dijital altyapıları siber saldırılardan korur.

---

# BÖLÜM 4 - Siber Güvenliğe Neden İhtiyaç Var?

## Önceki Konuyla Bağlantı

Az önce siber güvenliğin ne olduğunu tanımladık. Şimdi soru şu: Bu kadar korumaya neden ihtiyaç var? Cevap: Çünkü artık hayatın çok büyük kısmı dijital sistemlere taşındı.

## Online Yaşam

Derste “Your entire life is online.” fikri vurgulanıyor. İnsanlar sosyal medyada yaşıyor, bankacılığı telefondan yapıyor, alışverişi internetten yapıyor, yemek siparişini uygulamadan veriyor, devlet işlemlerini e-Devlet benzeri sistemlerden yapıyor ve toplantı/eğitimleri çevrim içi yürütüyor.

## Sosyal Medya Platformları

Derste Facebook, Instagram, Twitter/X ve çok sayıda başka sosyal medya platformu geçiyor. Bir isim veya takma ad arandığında 37-40 farklı sosyal medya platformunda sonuç çıkabildiği anlatılıyor.

### Günlük hayat analojisi

Eskiden kişisel bilgilerin evdeki çekmecedeydi. Şimdi adın, fotoğrafın, işin, arkadaşların, konumun, beğenilerin ve yorumların birçok platformda dağılmış durumda. Bu, evinin anahtarını farklı farklı insanlara vermeye benzer.

## Kritik Altyapılar

Derste geçen kritik altyapılar: elektrik dağıtım şebekesi, petrol iletim hatları, su dağıtım hatları, fabrika kontrol mekanizmaları, taşımacılık sistemleri, finans piyasaları, savunma sistemleri, enerji sistemleri ve iletişim sistemleri.

### Günlük hayat analojisi

Bir şehir düşün: elektrik yok, su yok, banka kartı çalışmıyor, haber siteleri açılmıyor, tren sistemi durmuş. Bu artık sadece teknik sorun değildir; toplumsal krizdir.

## Eski Sistem Riski: Windows XP

Derste CNBC kaynaklı 2018 tarihli bir haberden bahsediliyor: birçok şirketin kritik altyapılarını hâlâ Windows XP üzerinde çalıştırdığı anlatılıyor.

Sorun şudur:

- Aktif destek biter.
- Güvenlik desteği biter.
- Yeni güvenlik açıkları yamalanmaz.
- Hackerlar eski açıkları kullanabilir.
- Sistem saldırıya açık hale gelir.

### Active Support Nedir?

Yeni özellik ve uygulama desteğidir.

### Security Support Nedir?

Güvenlik açıklarının kapatılması için verilen destektir. Bir işletim sisteminin güvenlik desteği bittiyse, onu kritik sistemde kullanmak ciddi risktir.

> **HATIRLA:** Güncellenmeyen sistem, kilidi bozuk kapı gibidir. Kapı hâlâ duruyor olabilir ama güvenli değildir.

## Windows Server 2003 / 2008 / 2012 Riski

Derste firmalarda hâlâ eski Windows Server sürümlerine rastlanabileceği anlatılıyor. Windows Server 2003, 2008 ve 2012 gibi eski sistemler saldırganlar için “bulunmaz nimet” olabilir.

### KARMAŞTIRMA! Çalışıyor vs Güvenli

| Durum | Anlamı |
|---|---|
| Sistem çalışıyor | Hizmet veriyor olabilir |
| Sistem güvenli | Güncel, yamalı, izlenen ve korunan sistemdir |
| Eski ama çalışıyor | En tehlikeli yanıltıcı durumdur |

## Bunu Neden Öğreniyoruz?

Çünkü siber güvenlikte en büyük açıklar çoğu zaman gelişmiş saldırılardan değil, ihmalden doğar: eski işletim sistemi, güncellenmeyen server, destek süresi bitmiş yazılım, yanlış yapılandırılmış firewall veya kullanılmayan ama açık bırakılmış servis.

## Kendini Test Et

1. **Windows XP gibi eski sistemler neden risklidir?**  
   **Cevap:** Güvenlik desteği bittiği için yeni açıklar yamalanmaz ve saldırganlar bu açıkları kullanabilir.

2. **Kritik altyapıya örnek ver.**  
   **Cevap:** Elektrik dağıtım şebekesi, petrol hattı, su sistemi, finans sistemi, taşımacılık altyapısı.

3. **“Sistem çalışıyor” demek neden “sistem güvenli” demek değildir?**  
   **Cevap:** Sistem çalışsa bile güncel değilse, güvenlik desteği yoksa veya izlenmiyorsa saldırıya açık olabilir.

---

# BÖLÜM 5 - Gerçek Siber Güvenlik Olayları ve Hikayeler

## Önceki Konuyla Bağlantı

Önceki bölümde neden siber güvenliğe ihtiyaç olduğunu gördük. Şimdi bu ihtiyacın gerçek dünyada nasıl ortaya çıktığını örneklerle görüyoruz.

## Adobe Veri Sızıntısı

Derste Adobe örneği veriliyor. Geçen bilgiler: 2013 Ekim, Brian Krebs, 3 milyon şifrelenmiş müşteri kredi kartı kaydı, 153 milyon kişinin kaydı iddiası ve 1.1 milyon ceza.

Bu olay; şirketlerin güvenliği ihmal ederse müşteri verilerinin çalınabileceğini, hukuki süreçlerin başlayabileceğini, para cezası ödenebileceğini, marka itibarının zarar görebileceğini ve kullanıcı güveninin azalacağını gösterir.

### Günlük hayat analojisi

Bir mağazanın müşteri defterini düşün. İçinde isimler, telefonlar, adresler ve kredi kartı bilgileri var. Bu defter çalınırsa sadece mağaza değil, tüm müşteriler zarar görür.

## Akbank Örneği

Derste Türkiye'den Akbank örneği geçiyor. Eğitmen, bir saldırı sonrası siber güvenlik ekibinin yaklaşık 15 kişiden 150 kişiye çıkarıldığını tahmini olarak söylüyor. Ana fikir: Kurumlar bazen güvenliği olay yaşandıktan sonra ciddiye alır.

> **HATIRLA:** Siber güvenlikte en pahalı eğitim, saldırı yedikten sonra alınan eğitimdir.

## Rus Hackerlar, Ukrayna Savaşı ve Deutsche Bahn

Derste Microsoft duyurusu üzerinden Rus hackerların Ukrayna ve müttefiklerine yönelik siber casusluk faaliyetlerinden bahsediliyor. Almanya'nın Ukrayna'ya desteği sonrası Deutsche Bahn demiryolu sistemlerinin hedef alınması örnek veriliyor.

Kritik mantık: Bir kişinin bilgisayarına saldırırsan bir kişiyi etkilersin. Demiryolu, elektrik veya banka sistemine saldırırsan milyonları etkileyebilirsin.

## FireEye Saldırısı

FireEye bir güvenlik firmasıdır; buna rağmen saldırıya uğramıştır. Dersin mesajı nettir: “Biz güvenlik firmasıyız, bize saldırı olmaz” düşüncesi yanlıştır.

### Nation State Nedir?

**Nation State Attack**, arkasında devlet veya devlet destekli yapıların olduğu büyük çaplı saldırılardır. Daha organize, daha uzun süreli, daha gelişmiş araçlarla yapılan saldırılardır.

## Lockheed Martin ve F-35 Verileri

Derste Lockheed Martin örneği veriliyor. Geçen bilgiler: F-35 savaş uçakları, 50 TB üzeri veri, yaklaşık 600 milyar word of data, Çinli olduğu düşünülen hackerlar, 2007.

50 TB veri çalmak için sisteme sızmak, uzun süre fark edilmeden kalmak, veriyi dışarı aktarmak ve izleri gizlemek gerekir.

### SIEM ile bağlantı

**SIEM (Security Information and Event Management)** 7/24 log toplar, sistem olaylarını izler, anomali tespit eder ve şüpheli veri çıkışlarını görmeye yardım eder.

## Edward Snowden, CIA, NSA

Derste Edward Snowden örneği anlatılıyor. CIA ve NSA'de sistem admin olarak çalışması, 1.7 milyon çok gizli dokümanı çalması ve ifşa etmesi, PRISM, XKeyscore ve Tempora programlarının ortaya çıkması anlatılıyor.

Bu olay iç tehdidin ne kadar kritik olduğunu gösterir. Saldırgan her zaman dışarıdan gelmez; bazen sistemin içindeki yetkili kişi en büyük risktir.

## Estonya 2007 Siber Saldırıları

Geçen detaylar: Estonya'nın SSCB geçmişi, Kızıl Ordu Anıtı / Red Army Monument, anıtın askeri mezarlığa taşınmak istenmesi, Bronz Gece, Moskova'daki Estonya Büyükelçiliği kuşatması, 1 ölüm, 150'den fazla yaralı, 3 hafta süren siber saldırılar, parlamento/bakanlıklar/bankalar/gazeteler/yayın kuruluşlarının hedef alınması, DDoS, banka kartlarının çalışmaması, devlet iletişiminin kesilmesi, NATO'dan yardım istenmesi, NATO CCDCOE merkezinin Estonya'da kurulması ve Lüksemburg'da devlet verisi yedeği.

Bu olay, bir ülkenin konvansiyonel savaş yerine siber saldırıyla hedef alınabileceğini gösteren tarihi örneklerden biridir.

## Stuxnet, Natanz, Siemens PLC ve SCADA

Derste en önemli örneklerden biri Stuxnet saldırısıdır. Geçen bilgiler: İran'ın Natanz nükleer tesisi, yer altında ve internete açık olmayan sistem, Ahmetinejad ziyareti fotoğrafları, Windows ekranı, Siemens PLC, SCADA sistemleri, USB bellekler üzerinden bulaşma, santral civarındaki market/kırtasiye gibi yerlerde USB bellek dağıtılması, çalışanın USB'yi içerdeki bilgisayara takması, 4 adet Zero Day Exploit, Danimarka ve Malezya komuta kontrol merkezleri, İran nükleer çalışmalarının 5-10 yıl geriye gitmesi ve rootkit'in SCADA sistemine bulaşması.

### SCADA Nedir?

**SCADA (Supervisory Control and Data Acquisition)**, endüstriyel sistemleri izleme ve kontrol etme yapısıdır. Su arıtma tesisi, elektrik dağıtım şebekesi, baraj sistemi, nükleer tesis ve fabrika otomasyonu örnektir.

### PLC Nedir?

**PLC (Programmable Logic Controller)**, makineleri ve endüstriyel süreçleri kontrol eden programlanabilir cihazdır.

> **HATIRLA:** Siber saldırı sadece dosya çalmak değildir. Bazen fiziksel cihazları bozabilir.

## Brompton Junction Video Analojisi

Derste “What would a cyber attack look like in the real world?” videosu anlatılıyor. İngiltere'deki Brompton Junction adlı bisiklet satıcısının karşısına benzer sahte mağaza açılıyor. Brompton 1975'te kurulmuş; sahte tarafta 3R0AMPTON gibi taklitli yazım, benzer logo, benzer personeller, yanlış yönlendirilen teslimatlar ve kalabalık oluşturma gösteriliyor.

Bu video şu saldırıları fiziksel dünyaya çeviriyor:

- Brand Identity Copy: Markanın kimliğini kopyalamak.
- Phishing / Sahte site mantığı: isbank.com.tr yerine benzer karakterle sahte alan adı oluşturmak gibi.
- DDoS: Gerçek müşterilerin hizmet almasını engelleyecek yoğunluk oluşturmak.
- Ransomware: Sistemleri kilitleyip fidye istemek.

### KARMAŞTIRMA! DDoS vs Ransomware

| Kavram | Ne Yapar? | Günlük Hayat Benzetmesi |
|---|---|---|
| DDoS | Sisteme aşırı trafik gönderip hizmeti durdurur | Mağaza kapısına sahte kalabalık yığmak |
| Ransomware | Dosyaları şifreleyip fidye ister | Evin kapısına başkasının kilit takması |

## Kendini Test Et

1. **Stuxnet saldırısını özel yapan şey nedir?**  
   **Cevap:** Sadece veri çalmaması, endüstriyel SCADA/PLC sistemlerini etkileyerek fiziksel süreci bozmasıdır.

2. **Estonya saldırılarında hangi saldırı türü öne çıkmıştır?**  
   **Cevap:** DDoS, yani servis dışı bırakma saldırıları.

3. **Edward Snowden olayı hangi güvenlik prensibini öne çıkarır?**  
   **Cevap:** Zero Trust ve minimum yetki prensibini.

---

# BÖLÜM 6 - CIA Triad: Siber Güvenliğin Sacayağı

## Önceki Konuyla Bağlantı

Gerçek saldırı örneklerini gördük. Şimdi bu saldırıların hangi güvenlik ilkesini bozduğunu anlamamız gerekiyor.

Siber güvenliğin temel üçlüsü:

1. **Confidentiality (Gizlilik)**
2. **Integrity (Bütünlük)**
3. **Availability (Erişilebilirlik)**

Buna **CIA Triad** denir.

## Confidentiality (Gizlilik) Nedir?

**Confidentiality (Gizlilik)**, bilginin sadece yetkili kişiler tarafından görülebilmesidir. Yetkisiz kişi bilgiyi görürse gizlilik bozulur.

Örnekler: WhatsApp mesajını yanındaki kişinin okuması, metroda omuz üstünden telefon ekranına bakılması, banka bilgilerinin çalınması, kimlik bilgilerinin sızması ve müşteri verilerinin ifşa olması.

## Integrity (Bütünlük) Nedir?

**Integrity (Bütünlük)**, verinin yetkisiz şekilde değiştirilmemesidir. Veri gönderildiği haliyle karşı tarafa ulaşmalıdır.

Örnekler: mail içeriğinin yolda değiştirilmesi, web sitesindeki bilginin değiştirilmesi, indirilen ISO dosyasına zararlı kod eklenmesi, iş anlaşması yazışmalarının manipüle edilmesi.

### Kali Linux Hash Örneği

Kali Linux resmi indirme sayfasındaki **sum/hash** değeri örnek veriliyor. Hash aynıysa dosya orijinaldir ve bütünlüğü korunmuştur. Hash farklıysa dosya değiştirilmiş veya içine zararlı yazılım eklenmiş olabilir.

## Availability (Erişilebilirlik) Nedir?

**Availability (Erişilebilirlik)**, yetkili kişilerin ihtiyaç duydukları anda sisteme veya bilgiye ulaşabilmesidir.

Örnekler: banka sisteminin çalışması, e-ticaret sitesinin açık olması, devlet portalının erişilebilir olması, dosyaya yetkili kişinin ulaşabilmesi ve DDoS saldırısıyla sitenin kapanmaması.

## Alice, Bob ve Üçüncü Kişi Analojisi

- Üçüncü kişi mesajı sadece okur veya dinlerse: **Confidentiality ihlali**.
- Üçüncü kişi mesajı değiştirip gönderirse: **Integrity ihlali**.
- Üçüncü kişi mesajın ulaşmasını engellerse: **Availability ihlali**.

### KARMAŞTIRMA! CIA Üçlüsü

| İlke | Soru | İhlal Örneği |
|---|---|---|
| Confidentiality | Yetkisiz kişi gördü mü? | Mesajın okunması |
| Integrity | Veri değişti mi? | Mailin değiştirilmesi |
| Availability | Yetkili kişi erişebiliyor mu? | Sistemin çökmesi |

> **HATIRLA:** Gizlilik = sadece yetkili görür. Bütünlük = veri değişmeden kalır. Erişilebilirlik = yetkili kişi ihtiyacı olduğunda ulaşır.

## Bunu Neden Öğreniyoruz?

Çünkü her siber olayı analiz ederken şu soruyu soracağız: Gizlilik mi bozuldu? Bütünlük mü bozuldu? Erişilebilirlik mi bozuldu? Yoksa birden fazlası mı bozuldu?

## Kendini Test Et

1. **Bir saldırgan sadece e-postayı okuyup değiştirmeden bırakırsa hangi ilke bozulur?**  
   **Cevap:** Confidentiality (Gizlilik).

2. **Bir ISO dosyasının hash değeri değişmişse hangi ilke bozulmuş olabilir?**  
   **Cevap:** Integrity (Bütünlük).

3. **DDoS saldırısı en çok hangi ilkeyi hedefler?**  
   **Cevap:** Availability (Erişilebilirlik).

---

# BÖLÜM 7 - Authentication, MFA, IAM, Non-Repudiation ve Zero Trust

## Authentication (Kimlik Doğrulama) Nedir?

**Authentication**, bir kişinin gerçekten iddia ettiği kişi olup olmadığını doğrulama sürecidir. Örnekler: kullanıcı adı, parola, parmak izi, yüz tanıma, SMS kodu, Authenticator uygulaması, PIN ve güvenlik sorusu.

## Multi-Factor Authentication (MFA) Nedir?

**MFA**, giriş için birden fazla doğrulama faktörü kullanmaktır. Parolan çalınsa bile saldırgan ikinci faktöre sahip değilse sisteme giremez.

## Identity and Access Management (IAM) Nedir?

**IAM (Identity and Access Management)**, kimlerin hangi sistemlere, hangi yetkilerle erişebileceğini yöneten yapıdır. Yeni çalışan gelince yetki tanımlanmalı, çalışan ayrılınca yetkileri acilen kaldırılmalıdır.

## Geolocation ve VPN Yetkisi

Derste FortiGate Firewall ve VPN örneği veriliyor. Firma Almanya'da, kullanıcı Polonya'da olabilir; VPN ile bağlanması gerekebilir. Gürcistan'dan bağlantı ise risk sebebiyle engellenebilir. Bu coğrafi lokasyona göre erişim kuralıdır.

## Non-Repudiation (İnkar Edilemezlik) Nedir?

**Non-repudiation**, yapılan işlemin sonradan inkâr edilememesidir. EFT dekontu, mesaj gönderim kaydı ve sistem logları buna örnektir.

## Log Nedir?

**Log**, bilgisayar sistemlerinde yapılan işlemlerin kaydıdır. Kim giriş yaptı, ne zaman giriş yaptı, hangi dosyaya erişti, hangi IP'den bağlandı ve hangi komutu çalıştırdı gibi bilgileri içerir.

## Zero Trust Nedir?

**Zero Trust**, hiçbir kullanıcıya, cihaza veya bağlantıya otomatik güvenmemektir. Her erişimi doğrula, minimum yetki ver, sürekli izle, log tut ve içerden geleni de kontrol et.

### KARMAŞTIRMA! Authentication vs Authorization

| Kavram | Anlamı | Örnek |
|---|---|---|
| Authentication | Sen kimsin? | Parola, parmak izi |
| Authorization | Neye yetkin var? | Bu klasöre girebilir misin? |

## Kendini Test Et

1. **MFA neden paroladan daha güvenlidir?**  
   **Cevap:** Çünkü sadece parolayı bilmek yetmez; ikinci bir doğrulama faktörü gerekir.

2. **Non-repudiation ne demektir?**  
   **Cevap:** Bir işlemin sonradan inkâr edilememesidir.

3. **Zero Trust'ın temel mantığı nedir?**  
   **Cevap:** Hiçbir kullanıcıya veya cihaza otomatik güvenmemek; her erişimi doğrulamak.

---

# BÖLÜM 8 - Information Security ve Cybersecurity Farkı

## Information Security (Bilgi Güvenliği) Nedir?

**Information Security (Bilgi Güvenliği)**, bilginin bulunduğu ortam fark etmeksizin korunmasıdır. Bilgi kağıtta, klasörde, dolapta, bilgisayarda, sunucuda veya bulutta olabilir.

## Cybersecurity (Siber Güvenlik) Nedir?

**Cybersecurity (Siber Güvenlik)**, siber uzaydaki bilgileri ve bu bilgileri taşıyan sistemleri korur. Yani sadece bilgi değil, server, laptop, telefon, firewall, PLC, SCADA, router, switch ve cloud sistemleri de korunur.

## Fiziksel Dosya Analojisi

Bir çalışanın özlük dosyası açık dolapta durursa gizlilik bozulur. Kilitli dolapta durur ama anahtar sadece gelmeyen kişideyse erişilebilirlik bozulur. Biri dosyadaki bilgileri değiştirirse bütünlük bozulur. Aynı mantık dijital ortama taşınınca siber güvenlik devreye girer.

### KARMAŞTIRMA! Information Security vs Cybersecurity

| Kavram | Kapsam | Örnek |
|---|---|---|
| Information Security | Her ortamda bilgi güvenliği | Kağıt dosya, sözleşme, dijital dosya |
| Cybersecurity | Dijital sistem + dijital bilgi güvenliği | Server, ağ, veri tabanı, firewall |

> **HATIRLA:** Bilgi güvenliği daha geniştir. Siber güvenlik dijital sistemlere odaklanır. Ama ikisi birbirini tamamlar.

## Kendini Test Et

1. **Information Security neyi korur?**  
   **Cevap:** Bilgiyi, bulunduğu ortamdan bağımsız olarak korur.

2. **Cybersecurity bilgi dışında neyi korur?**  
   **Cevap:** Bilgiyi taşıyan bilgisayar sistemlerini, ağları ve dijital altyapıları da korur.

3. **Kilitli dolaptaki dosyaya yetkili kişi ulaşamıyorsa hangi CIA ilkesi bozulur?**  
   **Cevap:** Availability (Erişilebilirlik).

---

# BÖLÜM 9 - Kariyer, Roller ve Sertifikalar

## Derste Geçen Roller

Sistem destek yetkilisi, sistem destek uzmanı, Network Engineer, Junior System Administrator, Junior Network Administrator, Network Support Specialist, Cybersecurity Analyst, IT Security Specialist, IT Security Consultant, Cybersecurity Engineer, Junior Pentester ve SOC Analyst.

## CompTIA Security+

**CompTIA Security+**, siber güvenlik temel bilgisini ölçen ve dünya çapında bilinen bir sertifikadır. Eğitim sonunda hedef sertifikalardan biri olarak belirtilmiştir.

## CEH

**CEH (Certified Ethical Hacker)**, etik hackerlık alanında bilinen sertifikalardan biridir. Derste özellikle Amerika ve Kuzey Amerika bölgesinde bilinirliğinin yüksek olduğu söyleniyor.

## Splunk Enterprise Certified Admin

Splunk, SIEM alanında çok bilinen bir araçtır. Log toplama ve analiz için kullanılır. Güvenlik olaylarını izlemeye yardımcı olur.

## Fortinet NSE

**Fortinet NSE**, Fortinet'in güvenlik sertifikasyon yoludur. Fortinet özellikle firewall tarafında önemlidir.

## IBM, Cisco, Coursera, Chiron

Derste IBM, Cisco, Fortinet, Coursera ve Chiron platformları üzerinden ücretsiz ek sertifika ve kurslardan bahsediliyor. LinkedIn profilini güçlendirmek için kullanılmaları öneriliyor.

## LinkedIn Görünürlüğü

Teknik bilgi kadar görünürlük de kariyer için önemlidir. LinkedIn, kariyer tabelandır.

## Kendini Test Et

1. **CompTIA Security+ ne için önemlidir?**  
   **Cevap:** Siber güvenlik temel bilgisini belgeleyen, uluslararası bilinirliği olan bir sertifikadır.

2. **SOC Analyst ne yapar?**  
   **Cevap:** Sistemlerden gelen güvenlik olaylarını ve logları izler, anomali ve saldırı belirtilerini analiz eder.

3. **LinkedIn görünürlüğü neden önemlidir?**  
   **Cevap:** Alınan sertifikaları, projeleri ve teknik gelişimi görünür kılar; kariyer fırsatlarını artırır.

---

# BÖLÜM 10 - Bilgisayar Nedir?

## Bilgisayarın Temel Tanımı

Bilgisayar, veriyi alan, işleyen, depolayan ve sonucu bilgi olarak dışarı veren elektronik cihazdır.

Temel akış:

1. Veri girer.
2. Veri işlenir.
3. Veri depolanabilir.
4. Sonuç dışarı çıkar.

## Bilgisayarın Tarihsel Gelişimi

İnsanlar tarih boyunca bilgi üretmiştir. Bilgiler tabletlere, kitaplara ve kütüphanelere kaydedilmiştir. 1940'lı yıllarda bilgisayarların ataları ortaya çıkmış, 1980'lerden sonra Personal Computer (PC) yaygınlaşmıştır.

## Bilgisayar Çeşitleri

Masaüstü bilgisayar, dizüstü bilgisayar, tablet, akıllı telefon, akıllı televizyon, oyun konsolu, dijital telefon, akıllı buzdolabı, robot süpürge, akıllı ev sistemleri ve endüstriyel cihazlar.

## Input Unit (Giriş Birimi)

Bilgisayara veri girmemizi sağlayan birimdir: klavye, fare, dokunmatik ekran, parmak izi okuyucu, barkod okuyucu, retina tarayıcı, scanner, mikrofon ve kamera.

## CPU (Central Processing Unit)

CPU, bilgisayarın beynidir. Veriyi işler, hesaplama yapar, komutları yürütür, girdi/çıktıyı yönetir ve depolama birimleriyle çalışır.

## Storage (Depolama)

Verilerin tutulduğu alandır: HDD, SSD, NVMe SSD, RAM, ROM, USB bellek ve flash memory.

## Output Unit (Çıkış Birimi)

Bilgisayarın işlediği sonucu dışarı verdiği birimdir: ekran, yazıcı, hoparlör, plotter ve POS cihazı çıktısı.

### KARMAŞTIRMA! Veri vs Bilgi

| Kavram | Anlamı | Örnek |
|---|---|---|
| Veri | Ham girdi | 90, 180, “Ali”, “A” |
| Bilgi | İşlenmiş anlamlı sonuç | Ali'nin boyu 180 cm, kilosu 90 kg |

> **HATIRLA:** Bilgisayar = Girdi alır, işler, depolar, çıktı verir.

## Kendini Test Et

1. **CPU ne işe yarar?**  
   **Cevap:** Verileri işler, komutları çalıştırır ve bilgisayarın merkezi işlem görevlerini yürütür.

2. **Klavye hangi birimdir?**  
   **Cevap:** Input Unit (Giriş Birimi).

3. **Ekran hangi birimdir?**  
   **Cevap:** Output Unit (Çıkış Birimi).

---

# BÖLÜM 11 - Binary Sistem ve Sayı Sistemleri

## Decimal System (Onluk Sistem)

Günlük hayatta kullandığımız sayı sistemi decimal system yani onluk sistemdir. Rakamları 0-9 arasındadır.

## Binary System (İkilik Sistem)

**Binary System**, sadece iki rakam kullanır: 0 ve 1. Bilgisayarlar klasik olarak bu sistemle çalışır. Çünkü elektronik devrelerde temel mantık açık/kapalı, var/yok veya on/off şeklindedir.

## Transistor ve Flip-Flop

Transistor elektronik devrede anahtar gibi çalışan çok küçük parçadır. Flip-flop ise bir bitlik bilgiyi tutabilen elektronik yapıdır.

## Bit Nedir?

**Bit**, binary digit ifadesinden gelir. Bilgisayardaki en küçük veri birimidir. 0 veya 1 değerini alır.

## Byte Nedir?

**Byte**, 8 bitten oluşur. ASCII tablosunda temel karakterler genellikle 1 byte ile temsil edilir.

## ASCII Nedir?

**ASCII (American Standard Code for Information Interchange)**, karakterlerin sayısal kodlarla temsil edilmesini sağlayan standarttır. Büyük A harfi decimal sistemde 65'e, binary olarak 01000001'e karşılık gelir.

## Kilobyte, Megabyte, Gigabyte, Terabyte

- 1 byte = 8 bit
- 1024 byte = 1 kilobyte
- 1024 kilobyte = 1 megabyte
- 1024 megabyte = 1 gigabyte
- 1024 gigabyte = 1 terabyte

## Hexadecimal (Onaltılık Sistem)

Hexadecimal 16 tabanlı sayı sistemidir. Semboller: 0-9 ve A-F. A=10, B=11, C=12, D=13, E=14, F=15.

### KARMAŞTIRMA! Bit vs Byte

| Kavram | Anlamı | Örnek |
|---|---|---|
| Bit | En küçük veri birimi | 0 veya 1 |
| Byte | 8 bitten oluşur | Bir karakteri temsil edebilir |

### KARMAŞTIRMA! Decimal vs Binary vs Hexadecimal

| Sistem | Taban | Kullanılan Semboller |
|---|---:|---|
| Decimal | 10 | 0-9 |
| Binary | 2 | 0-1 |
| Hexadecimal | 16 | 0-9, A-F |

> **HATIRLA:** Bilgisayarın ana dili 0 ve 1'dir. Biz A yazarız, bilgisayar bunu binary olarak işler.

## Kendini Test Et

1. **1 byte kaç bitten oluşur?**  
   **Cevap:** 8 bit.

2. **Binary sistem hangi rakamları kullanır?**  
   **Cevap:** 0 ve 1.

3. **ASCII ne işe yarar?**  
   **Cevap:** Karakterlerin bilgisayarda sayısal/binary değerlerle temsil edilmesini sağlar.

---

# BÖLÜM 12 - Depolama Birimleri: HDD, SSD, NVMe, RAM

## HDD Nedir?

**HDD (Hard Disk Drive)**, manyetik diskler üzerinde veri depolayan kalıcı depolama birimidir. Eski teknolojidir, içinde dönen diskler vardır, kabloyla anakarta bağlanır ve 5400/7200 RPM gibi dönüş hızları olabilir.

## SSD Nedir?

**SSD (Solid State Disk)**, hareketli parçası olmayan daha hızlı depolama birimidir. HDD'ye göre yaklaşık 6-7 kat hızlı olabilir ve kabloyla bağlanan türleri vardır.

## NVMe SSD / M.2 Nedir?

**NVMe SSD**, anakarta doğrudan takılan çok hızlı SSD türüdür. M.2 olarak geçer, kablo kullanmaz ve çok daha yüksek hızlara çıkabilir.

## RAM Nedir?

**RAM (Random Access Memory)**, geçici bellektir. Elektrik olduğu sürece veri tutar, bilgisayar kapanınca içindeki veri silinir, CPU'nun hızlı erişmesi gereken verileri tutar.

## RAM İçin Mutfak Analojisi

Derste mutfak analojisi veriliyor:

- Kiler / buzdolabı = Kalıcı depolama
- Mutfak tezgahı = RAM
- Aşçı = CPU
- Yemek hazırlama = İşlem yapma

Yemek yaparken gerekli malzemeleri tezgaha koyarsın. İşin bitince tezgahı temizlersin. RAM de CPU'nun hızlı çalışması için gerekli verileri geçici olarak tutar.

## USB Bellek / Flash Memory

USB bellekler veri taşıma, dosya transferi ve kurulum medyası oluşturma için kullanılır. Ancak Stuxnet örneğinde görüldüğü gibi saldırı aracı da olabilir.

> **HATIRLA:** Tanımadığın USB belleği bilgisayara takmak, yerde bulduğun anahtarı evinin kapısında denemeye benzer.

### KARMAŞTIRMA! HDD vs SSD vs NVMe vs RAM

| Kavram | Kalıcı mı? | Hız | Ana Görev |
|---|---|---|---|
| HDD | Evet | Düşük | Uzun süreli depolama |
| SSD | Evet | Orta/Yüksek | Hızlı depolama |
| NVMe SSD | Evet | Çok yüksek | Çok hızlı depolama |
| RAM | Hayır | Çok yüksek | Geçici çalışma alanı |

## Kendini Test Et

1. **RAM neden geçici bellektir?**  
   **Cevap:** Elektrik kesildiğinde içindeki veriler silinir.

2. **NVMe SSD neden SATA SSD'den hızlıdır?**  
   **Cevap:** Anakart üzerine doğrudan takılır ve kablo üzerinden veri aktarım sınırlamasına daha az takılır.

3. **USB bellek neden güvenlik riski olabilir?**  
   **Cevap:** İçine zararlı yazılım yüklenmiş olabilir; Stuxnet gibi saldırılarda bulaşma aracı olarak kullanılabilir.

---

# GENEL TEKRAR VE ÖZET

| Konu | Tek Cümlelik Özet |
|---|---|
| LMS | Ders materyallerinin ve kayıtların tutulduğu ana eğitim platformudur. |
| Discord | Anlık duyuru, iletişim ve kaynak paylaşım alanıdır. |
| TryHackMe | Siber güvenliği uygulamalı öğrenmek için kullanılan lab platformudur. |
| IT Fundamentals | Bilgisayarın ve bilişim sistemlerinin temelini öğretir. |
| Network Fundamentals | Cihazların ağ üzerinden nasıl haberleştiğini öğretir. |
| Operating Systems | Windows, Linux ve Windows Server gibi sistemlerin mantığını öğretir. |
| Cyber | Bilgisayar, internet ve ağ bağlantılı dijital alanı ifade eder. |
| Cyberspace | Dijital sistemlerin oluşturduğu bağlantılı ortamdır. |
| Cybersecurity | Dijital sistemleri, verileri, kişileri, kurumları ve ülkeleri koruma disiplinidir. |
| CIA Triad | Gizlilik, bütünlük ve erişilebilirlik siber güvenliğin temel üçlüsüdür. |
| Confidentiality | Bilginin sadece yetkili kişilerce görülmesidir. |
| Integrity | Bilginin yetkisiz şekilde değiştirilmemesidir. |
| Availability | Yetkili kişilerin sisteme ihtiyaç anında erişebilmesidir. |
| Authentication | Kullanıcının kimliğini doğrulama işlemidir. |
| MFA | Birden fazla doğrulama faktörüyle güvenliği artırır. |
| IAM | Kimlerin hangi sistemlere erişeceğini yönetir. |
| Non-repudiation | Yapılan işlemin sonradan inkâr edilememesidir. |
| Zero Trust | Hiçbir kullanıcıya veya cihaza otomatik güvenmemektir. |
| SIEM | Güvenlik olaylarını ve logları merkezi olarak izleyen sistemdir. |
| SOC Analyst | SIEM ve loglar üzerinden güvenlik olaylarını takip eden uzmandır. |
| DDoS | Sistemi yoğun trafikle erişilemez hale getiren saldırıdır. |
| Ransomware | Dosyaları/sistemleri kilitleyip fidye isteyen zararlı yazılımdır. |
| Stuxnet | Endüstriyel sistemleri hedef alan tarihi siber saldırı örneğidir. |
| SCADA | Endüstriyel sistemleri izleme ve kontrol etme altyapısıdır. |
| PLC | Makineleri kontrol eden programlanabilir endüstriyel cihazdır. |
| Edward Snowden | İç tehdit ve aşırı yetkilendirme riskini gösteren örnektir. |
| Estonya saldırıları | Bir ülkenin dijital altyapısının siber saldırıyla felç edilebileceğini gösterir. |
| Bilgisayar | Veriyi alan, işleyen, depolayan ve çıktı veren cihazdır. |
| CPU | Bilgisayarın merkezi işlem birimidir. |
| Input Unit | Bilgisayara veri girişi sağlayan birimdir. |
| Output Unit | İşlenmiş sonucu dışarı veren birimdir. |
| Binary | Bilgisayarların 0 ve 1 ile çalıştığı ikilik sistemdir. |
| Bit | Bilgisayardaki en küçük veri birimidir. |
| Byte | 8 bitten oluşur. |
| ASCII | Karakterleri bilgisayarın anlayacağı sayısal değerlere eşler. |
| HDD | Manyetik ve daha yavaş kalıcı depolama birimidir. |
| SSD | HDD'ye göre daha hızlı kalıcı depolama birimidir. |
| NVMe SSD | Anakart üzerine takılan çok hızlı depolama birimidir. |
| RAM | İşlem sırasında kullanılan geçici ve hızlı bellektir. |

## Son Kritik Hatırlatma

Siber güvenlik, sadece saldırı aracı kullanmak değildir. Önce bilgisayarı, ağı, işletim sistemini, veriyi, erişimi ve güvenlik prensiplerini anlamaktır. Bu temel oturmazsa ileride Nmap, Metasploit, SIEM, firewall, exploitation, malware analizi veya pentest raporu ezbere dönüşür. Temel oturursa, her yeni araç mantıklı hale gelir.
