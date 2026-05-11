# 🛡️ AĞ TEMELLERİ – DERS 8

<div align="center">

![Ders İnfografiği](../assets/08-packet-analysis-wireshark-network-tools.png)

</div>

---

## Kapsamlı Eğitim Notu
### Konu: ICMP, PING, Traceroute, Wireshark & Transport Katmanı

> **Eğitmenin Notu:** Bu ders, gerçek bir ağ analizinin nasıl yapıldığını, paketlerin nasıl yakalandığını ve protokollerin gerçek hayatta nasıl çalıştığını görmek için Wireshark programını merkeze alıyor. Anlattığımız her protokolü buradan gözlerimizle göreceğiz!

---

## 📌 ÖNCEKİ DERSLERİN KISA ÖZETI (Bağlantı Kuruyoruz)

Şimdiye kadar şunları öğrendik:
- **MAC adresi** → Datalink katmanında kullanılır (fiziksel kimlik)
- **IP adresi** → Network katmanında kullanılır (mantıksal kimlik)
- **ARP protokolü** → "Bu IP kimin?" diye soran protokol
- **DHCP** → IP dağıtan protokol (Discover → Offer → Request → Acknowledge)
- **DNS** → Alan adını IP'ye çeviren sistem

**Şimdi bu dersteki bağlantı:**
> "Peki tüm bu protokoller gerçekte nasıl çalışıyor? Bunları gözle görebilir miyiz?" → **EVET! Wireshark ile görebiliriz.**

---

# BÖLÜM 1: ICMP Protokolü (Hatırlama + Derinleştirme)

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
ICMP olmadan ağda sorun giderme yapamayız. Ping ve Traceroute gibi temel araçlar ICMP'ye dayanır. Bir sistem çalışıyor mu, erişilebilir mi? Ağda neler oluyor? ICMP bize bunları söyler.

---

## ICMP Nedir? (En Temelden Başlıyoruz)

**Açılımı:** Internet Control Message Protocol (İnternet Kontrol Mesaj Protokolü)

**Günlük Hayat Analogisi:** 🏠
> Bir arkadaşına mektup gönderdin. Posta servisi o adrese ulaşamadı. Ne yapar posta servisi? Sana "Bu adrese teslim edilemedi" diye bir bildirim yollar. İşte ICMP tam olarak bu bildirim servisi! Ağda bir şeyler ters gittiğinde veya test edildiğinde bu mesajları taşır.

**Teknik Tanım:** IP protokolü haberleşmesinde karşılaşılan problemleri kullanıcıya bildirmek için kullanılan bir protokoldür.

---

## ICMP Mesaj Tipleri ve Kodları

ICMP'nin iki temel bileşeni var: **Tip (Type)** ve **Kod (Code)**

**Günlük Hayat Analogisi:** 📬
> Düşün: Bir paketin geri döndüğünde üzerinde yazılar var:
> - **Tip = Ana kategori** → "Teslim edilemedi" (genel kategori)
> - **Kod = Detay** → "Alıcı o adrese taşınmış" (özel detay)

### Önemli ICMP Tipleri:

| Tip Numarası | Anlamı | Kullanıldığı Yer |
|---|---|---|
| **Tip 0** | Echo Reply (Yankı Cevabı) | PING cevabı |
| **Tip 3** | Destination Unreachable (Hedefe Ulaşılamıyor) | Erişim hatası |
| **Tip 5** | Redirect (Yönlendirme) | Route değişikliği |
| **Tip 8** | Echo Request (Yankı İsteği) | PING isteği |
| **Tip 11** | Time Exceeded (Zaman Aşımı) | TTL sıfırlandı |

### Tip 3'ün Kodları (Örnek):
Tip 3 "Hedefe ulaşılamıyor" diyorken Kod, sebebi açıklar:
- **Kod 0** → Ağa ulaşılamıyor (Network Unreachable)
- **Kod 1** → Hosta ulaşılamıyor (Host Unreachable)
- **Kod 3** → Porta ulaşılamıyor (Port Unreachable)

> 🎯 **Mantık:** Tip = "Ne var?" Kod = "Neden?"

---

## 📦 HATIRLA!
> ICMP bir **taşıma protokolü değildir**. Veri taşımaz. Sadece kontrol mesajları ve hata bildirimleri taşır. Ambulans servisi gibi düşün – kargo taşımaz, acil durumlarda bildirim yapar!

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 1a

**Soru 1:** ICMP'nin açılımı nedir?
> **Cevap:** Internet Control Message Protocol – İnternet Kontrol Mesaj Protokolü

**Soru 2:** ICMP Tip 8 ne anlama gelir?
> **Cevap:** Echo Request – PING isteği gönderimi

**Soru 3:** Bir hedefe ulaşılamadığında hangi ICMP tipi döner?
> **Cevap:** Tip 3 – Destination Unreachable (ve kodlar detay verir: hosta mı, porta mı, ağa mı ulaşılamıyor)

---

# BÖLÜM 2: PING Komutu

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
Ping, bir ağ cihazının "hayatta" olup olmadığını test etmenin en hızlı yoludur. Her bilgisayarcı, ağcı ve siber güvenlikçi günde onlarca kez ping kullanır.

---

## PING Nedir?

**Önemli Ayrım:** PING bir **protokol değil**, bir **komuttur!**

**Günlük Hayat Analogisi:** 📞
> Birinin evinde olup olmadığını öğrenmek istiyorsun. Kapıyı çalıyorsun. İçeriden ses gelirse "evde var", gelmezse "evde yok veya meşgul". PING tam olarak bu kapı çalma işlemidir!

**Ne İşe Yarar?**
Karşımızdaki IP adresini bildiğimiz bir cihazın, hostun veya domain'in (google.com, CNN, Fox News, UAK Akademi gibi) **"up"** (ayakta) olup olmadığını, çalışıp çalışmadığını test eder.

**Nasıl Çalışır?**
PING, ICMP protokolünün **2 özelliğini** kullanır:
1. **Echo Request (Tip 8, Kod 0)** → "Merhaba, orada mısın?" mesajı gönderir
2. **Echo Reply (Tip 0, Kod 0)** → "Evet, buradayım!" cevabı alır

---

## ⚠️ DİKKAT! Ping Her Zaman Çalışmaz

**Neden?** Bazı sistemlerde **Firewall (Güvenlik Duvarı)** ICMP paketlerini engeller.

**Eğitmenin Gösterdiği Örnek:**
> Windows işletim sisteminde Güvenlik Duvarı'nın **"Advanced Settings → Inbound Rules"** kısmında PING'e özel engelleme kuralı yazılabilir. "Deny" (reddet) dersen, dışarıdan gelen ping istekleri sisteme ulaşmaz.

**Sonuç:** Ping'e cevap gelmiyorsa, sistem kapalı OLMAYABILIR. Sadece ping'i engelliyor olabilir!

---

## KARMAŞTIRMA! ⚠️

| PING | ICMP |
|---|---|
| Bir **komut** (araç) | Bir **protokol** |
| Terminal'den çalıştırılır | Arka planda otomatik çalışır |
| ICMP'ye ihtiyaç duyar | Bağımsız çalışır |
| **PING protokol DEĞİLDİR** | **ICMP komut DEĞİLDİR** |

---

## Özel Durum: Lokal Ağ vs. Dış Dünya

**Eğitmenin sınıfta verdiği örnek:**
> Sınıftaki bir öğrencinin cihazı: 192.168.0.75
> Dışarıdan o cihaza ping atmak mümkün mü?

**Cevap:** Hayır! Çünkü 192.168.0.75 **özel (private) bir IP adresidir**. Dış dünyadan erişilemez. Lokal ağın içinde, router'ın arkasında gizlidir.

**Peki Çözüm?** → **VPN (Virtual Private Network)**!
> Uzaktan o ağa bağlanmak için önce VPN ile kendini o ağın içindeymiş gibi tanıtırsın. Sonra ping, traceroute gibi komutları sanki o ağın içindeymiş gibi kullanabilirsin.

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 2

**Soru 1:** Ping komutu hangi iki ICMP tipini kullanır?
> **Cevap:** Tip 8 (Echo Request) ve Tip 0 (Echo Reply)

**Soru 2:** Ping bir protokol müdür komut mudur?
> **Cevap:** Komuttur. ICMP protokolünü kullanır ama kendisi bir protokol değildir.

**Soru 3:** Ping'e cevap gelmiyorsa ne anlama gelir?
> **Cevap:** Sistem kapalı OLABİLİR veya Firewall ICMP paketlerini engelliyor olabilir – kesin kapalı demek değildir!

---

# BÖLÜM 3: Traceroute / Tracert Komutu

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
Bazen bir siteye ulaşamıyoruz ama nerede takıldığımızı bilmiyoruz. Traceroute bize "yolculuğun haritasını" çıkarır – hangi router'lardan geçtik, nerede durdu?

---

## Traceroute Nedir?

**İşletim Sistemine Göre İsim Farkı:**
- **Windows'ta:** `tracert`
- **Linux/Mac'te:** `traceroute`
- İkisi aynı işi yapar!

**Günlük Hayat Analogisi:** ✈️
> İstanbul'dan New York'a gidiyorsun. Uçağın rotası: İstanbul → Londra → İzlanda → New York. Traceroute tam olarak bu ara durma noktalarını (mola noktalarını) listeler! Her mola noktasına ağ dilinde **HOP** diyoruz.

**Ne Yapar?**
Bir kaynaktan bir hedefe giderken uğranılan **tüm router'ların bilgilerini** toplayıp getirir.

**Önemli Not:** Bazen `* * *` (yıldız) görürsünüz. Bu ne demek?
> O ara nokta kendisini gizliyordur veya o yolu kullanamamıştır. Ama devam eder ve hedefe ulaşmayı dener.

---

## TTL (Time to Live) – Yaşam Süresi

**Bu kavram çok önemli!** Traceroute'un çalışmasının sırrı burada.

**Açılımı:** Time to Live – "Yaşam Süresi" veya "Ömür"

**Günlük Hayat Analogisi:** 🔋
> Düşün: Bir paketin elinde belirli sayıda "enerji" var. Her router'dan geçtiğinde 1 enerji harcar. Enerjisi bittiğinde "Ben buraya kadar gelebildim!" diye rapor verir ve ölür (drop edilir). Traceroute bu "raporları" toplayarak yolu haritalandırır.

**Teknik Detaylar:**
- Her router'dan geçişte TTL **1 azalır**
- TTL = 0 olduğunda paket **drop edilir** (atılır)
- **Başlangıç Değerleri:**
  - Windows: **128'den** başlar, aşağı sayar
  - Linux ve macOS: **64'ten** başlar, aşağı sayar
  - Genel maksimum: **255**

**Eğitmenin ifadesi:** "Kaç solukta ulaşacağını" gösteren bir değer.

---

## Traceroute ve Cloudflare Örneği

**Eğitmen sınıfta şunu anlattı:**
> Eğer bir web sitesi Cloudflare'ın arkasına gizlenmişse, traceroute o sitenin gerçek sunucusuna değil, en önde duran Cloudflare sunucusuna kadar ulaşabilir. İç sistemler gizli kalır.

---

## 📦 HATIRLA!
> - Traceroute ICMP paketlerini kullanır
> - Genel hedef: **30 adımda (hop'ta) hedefe ulaşmak**
> - TTL: Windows'ta 128, Linux/Mac'te 64'ten başlar
> - `* * *` görüyorsan: o nokta gizleniyor veya yanıt vermiyor

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 3

**Soru 1:** TTL nedir ve ne işe yarar?
> **Cevap:** Time to Live – Her router'dan geçişte 1 azalan sayaç. 0'a ulaşınca paket atılır. Ağda paketlerin sonsuza dek dolaşmasını önler.

**Soru 2:** Linux'ta traceroute komutunun TTL başlangıç değeri nedir?
> **Cevap:** 64

**Soru 3:** Traceroute çıktısında `* * *` görürsek ne anlama gelir?
> **Cevap:** O ara nokta (router) kendini gizliyor veya o yolu kullanamadı. Yolculuk devam eder.

---

# BÖLÜM 4: Wireshark – Giriş ve Temel Kavramlar

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
Eğitmenin sözleriyle: *"Veri asla yalan söylemez."* Wireshark, ağda gerçekte neler olduğunu ham verisiyle gösterir. Slaytlarda anlattığımız her protokolü gerçekten gözlerimizle görmek için Wireshark kullanıyoruz.

---

## Wireshark Nedir?

**Günlük Hayat Analogisi:** 🏥 X-Ray Cihazı
> Doktor hastanın içini görmek için röntgen çeker. Wireshark da ağın "röntgenini" çeker. Ağda hangi paketler gidip geliyor, hangi protokoller çalışıyor, kim kiminle konuşuyor – hepsini gösterir.

**Teknik Tanım:** Ağ trafiğini yakalayan (capture eden), kaydeden ve analiz etmeyi sağlayan ücretsiz ve açık kaynaklı bir program.

**Resmi Sitesi:** wireshark.org (buradan ücretsiz indirilebilir)

**Önemli Özellikler:**
- ✅ **Ücretsiz** (Free)
- ✅ **Açık kaynak** (Open Source)
- ✅ Windows, Linux, Mac'te çalışır
- ✅ Portable kullanılabilir (kurulum gerekmez)

---

## Wireshark'ın Siber Güvenlikteki Kullanım Alanları

Eğitmen şu alanları anlattı:

### 1. 🎯 Saldırı Tespiti (Threat Hunting)
Hangi portlara bağlantı kurulduğunu, anomali (normalden sapma) olan davranışları, DDoS saldırısı varsa bununla ilgili bilgileri tespit edebilirsin.

### 2. 🦠 Zararlı Yazılım Tespiti
Zararlı yazılımlar **"Command and Control" (C&C)** sistemiyle sürekli dış dünyayla iletişim kurar. Bu iletişimi Wireshark ile yakalayabilir ve analiz edebilirsin.

**Günlük Hayat Analogisi:** 🕵️
> Bir casus, üssüyle sürekli mesaj gönderip alıyor. Wireshark bu mesajların geçtiği kanalı dinleyerek casusun varlığını tespit etmemize yardım eder.

### 3. 📤 Veri Sızıntısı Tespiti
Çok büyük boyutlu dosyaların sürekli dışarıya transfer edildiğini görürsen, veri sızıntısı olduğunu tespit edebilirsin. **(Eğitmen dünkü derste "length" (uzunluk) konusundan bahsetmişti – bağlantı burada!)**

### 4. 🔒 Güvenli Protokol Testi
Zayıf protokolleri tespit edip bunları SSH gibi daha güçlü sürümlere değiştirmeyi önerebilirsin.

### 5. 🔍 Adli Bilişim (Digital Forensics)
Olay incelemelerinde kullanılır. Birileri bir sisteme saldırmışsa, Wireshark o andaki paket trafiği kaydı üzerinden soruşturma yapılmasını sağlar.

### 6. 🔥 Güvenlik Duvarı Doğrulama
Yeni bir firewall kurduğunda, kuralların doğru çalışıp çalışmadığını test etmek için kullanabilirsin.

---

## ⚠️ Wireshark'ın Sınırları

Eğitmen bunu özellikle vurguladı:
> Wireshark **tek başına** bir analiz aracıdır. Bir saldırıyı **durduramaz**! Ama saldırının nasıl yapıldığını anlamamızı ve kalıcı çözümler üretmemizi sağlar.

---

## "Başkasının Trafiğini Dinleyebilir miyim?" Sorusu

Sınıfta çok önemli bir soru soruldu:
> "Ağda 20 bilgisayar var. Ben Wireshark açtığımda diğer 19 bilgisayarın trafiğini de dinleyebilir miyim?"

**Cevap: Hayır!**

**Neden?**
Wireshark açıldığında **hangi ağ kartı (network interface)** üzerinden dinleyeceğini seçiyoruz. Biz sadece **kendi ağ kartımızdan** geçen trafiği görebiliriz.

**Günlük Hayat Analogisi:** 📻
> Radyoda sadece kendi anteniyle gelen frekansı yakalayabilirsin. Komşunun evindeki radyonun yakaladığı sinyali kendi anteninle yakalayamazsın.

**İstisna Durum:**
Eğer gateway (geçiş noktası) cihazında **mirroring (aynalama)** yapılırsa, yani "bu cihazdan geçen trafiğin bir kopyasını benim bilgisayarıma gönder" denirse, o zaman dinleme mümkün olabilir. Ama bu özel bir kurulum gerektirir.

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 4

**Soru 1:** Wireshark'ı "ağın röntgeni" olarak neden tanımlıyoruz?
> **Cevap:** Ağda gidip gelen tüm paketleri, protokolleri ve iletişimleri ham veri olarak gösterdiği için – tıpkı röntgenin vücudun içini göstermesi gibi.

**Soru 2:** Wireshark bir saldırıyı durdurabileceğimi mi?
> **Cevap:** Hayır! Saldırıyı tespit edip analiz etmemize yardımcı olur ama durdurmak için başka güvenlik araçları (IPS, Firewall vb.) gereklidir.

**Soru 3:** Wireshark'ı açtığımda ağdaki diğer bilgisayarların trafiğini görebilir miyim?
> **Cevap:** Normal şartlarda hayır. Sadece kendi ağ kartımızdan geçen trafiği görebiliriz.

---

# BÖLÜM 5: Wireshark Arayüzü – Ekranı Tanıyalım

## Wireshark'ı Açtığımızda Ne Görürüz?

Wireshark açıldığında iki ana alan karşımıza çıkar:

### 1. Capture (Yakalama) Alanı
Hangi ağ kartından trafik yakalayacağımızı seçtiğimiz alan.
- En az bir **network interface (ağ arayüzü)** seçmemiz gerekir
- Üzerine çift tıklayarak veya "Köpekbalığı kuyruğu" simgesine tıklayarak başlatılır

### 2. Filter (Filtre) Alanı
Hangi paketleri görmek istediğimizi belirttiğimiz alan.

---

## Wireshark'taki "Any" Seçeneği

**Linux'taki AttackBox'ta şöyle bir liste görülür:**
- ns5, loopback, any, docker, vb.

**"Any" ne demek?**
> Herhangi bir ağ kartı → Cihazdaki **tüm** ağ bağlantılarını aynı anda dinle!

**Eğitmenin Notu:** Birden fazla ağ kartın varsa (Wi-Fi + Ethernet gibi), "Any" seçerek ikisini birden dinleyebilirsin.

---

## Wireshark Ekran Yapısı – 3 Ana Bölge

Bir paket yakalamaya başladığımızda ekran 3 bölgeye ayrılır:

### 📋 Bölge 1: Packet List (Paket Listesi)
En üstteki liste. Yakalanan her paket bir satırda gösterilir.
- **No:** Sıra numarası (Wireshark'ın verdiği)
- **Time:** Milisaniye cinsinden zaman
- **Source:** Kaynak IP adresi
- **Destination:** Hedef IP adresi
- **Protocol:** Hangi protokol
- **Length:** Boyut (byte)
- **Info:** Kısa açıklama

### 🔍 Bölge 2: Packet Details (Paket Detayları)
Ortadaki alan. Seçilen paketin katmanlara göre açılımı.
- Frame → Ethernet → Internet Protocol → TCP/UDP → Application

### 💻 Bölge 3: Packet Bytes (Paket Byte'ları)
En alttaki alan. Paketin **hexadecimal** (onaltılık) ve **ASCII** formatında ham görünümü.

---

## KARMAŞTIRMA! ⚠️

| Packet **List** | Packet **Details** | Packet **Bytes** |
|---|---|---|
| Paketlerin genel listesi | Seçili paketin katman detayı | Ham hexadecimal veri |
| Üst bölge | Orta bölge | Alt bölge |
| Hızlı genel bakış | Protokol detayları | Düz veri görünümü |

---

## Frame Kavramı (Wireshark'ın Kendi Verdiği!)

**⚠️ Dikkat!** Wireshark'taki "Frame" kavramı, OSI modelindeki 2. Katman (Datalink) "Frame"i ile **aynı şey DEĞİLDİR!**

**Wireshark'ın Frame'i:**
- Wireshark her yakaladığı pakete kendi sıra numarasını verir
- "Frame 140" demek: "Bu yakalamada 140. paket"
- Içinde: section numarası, interface, encapsulation tipi, zaman, boyut bilgileri var

**Eğitmenin notu:** "Frame kısmı OSI ya da TCP/IP referans modelleriyle alakası yok. Bunu kendisi veriyor."

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 5

**Soru 1:** Wireshark'taki 3 ana ekran bölgesi nelerdir?
> **Cevap:** Packet List (üst), Packet Details (orta), Packet Bytes (alt)

**Soru 2:** Wireshark'ta "Any" ne demek?
> **Cevap:** Cihazdaki tüm ağ kartlarını aynı anda dinle

**Soru 3:** Wireshark'taki "Frame" kavramı OSI'nin hangi katmanıyla aynıdır?
> **Cevap:** HİÇBİRİYLE! Wireshark'ın kendi numaralandırma sistemidir.

---

# BÖLÜM 6: Capture Filter vs. Display Filter

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
Büyük ağlarda saniyede binlerce paket geçer. Hepsini kaydetmek ve analiz etmek imkânsız. Filtreler sayesinde sadece istediğimiz paketlere odaklanabiliriz.

---

## İki Farklı Filtre Var – Ve Çok Farklılar!

### 🔴 Capture Filter (Yakalama Filtresi)

**Ne zaman ayarlanır?** Yakalamaya **BAŞLAMADAN ÖNCE**

**Ne yapar?** Sadece bu filtreye uyan paketleri yakalar, diğerlerini hiç kaydetmez.

**Günlük Hayat Analogisi:** 🚪 Kapı Görevlisi
> Bir klübe giriş için "Sadece davetli misafirler girebilir" kuralı koyarsın. Davetli olmayanlar içeri hiç girmez, var bile olmaz. Capture Filter böyle çalışır – filtreye uymayan paketler diske hiç yazılmaz, kalıcı olarak atılır!

**Avantajı:** 
- CPU (işlemci) ve Disk kullanımını azaltır
- RAM'i korur
- Çok yoğun trafikli ortamlarda şart!

**Kullandığı Dil:** **Berkeley Packet Filter (BPF)** sözdizimi
- Örnek: `host 192.168.1.1` (Bu IP'ye ait paketler)
- Örnek: `port 80` (80 numaralı porta ait paketler)
- Örnek: `udp` (Sadece UDP paketleri)

**Önemli Kural:** Yakalama sırasında değiştirilemez! Değiştirmek için yakalamayı durdurman gerekir.

---

### 🟢 Display Filter (Görüntüleme Filtresi)

**Ne zaman ayarlanır?** Yakalama sırasında VEYA sonrasında, istediğin zaman

**Ne yapar?** Zaten yakalanmış paketler arasında istediğini gösterir/gizler

**Günlük Hayat Analogisi:** 🔍 Arama Motoru
> Elinizde dev bir arşiv var (tüm yakalanan paketler). Arama kutusuna "DNS" yazarsın ve sadece DNS paketleri önüne gelir. Diğerleri silinmedi, sadece gizlendi.

**Kullandığı Dil:** Wireshark'ın **kendi özel sözdizimi**
- Örnek: `ip.addr == 192.168.1.1`
- Örnek: `tcp.port == 80`
- Örnek: `icmp`
- Örnek: `dns`

**Renk Geri Bildirimi:**
- 🔴 **Kırmızı** → Hatalı filtre, düzeltmeden devam edemezsin!
- 🟢 **Yeşil** → Filtre doğru, kullanılabilir!

---

## KARMAŞTIRMA! ⚠️ Capture Filter vs. Display Filter

| | **Capture Filter** | **Display Filter** |
|---|---|---|
| **Ne zaman?** | Başlamadan önce | Her zaman |
| **Etki** | Filtresiz paketler kaydedilmez | Filtresiz paketler gizlenir (silinmez) |
| **Dil** | Berkeley Packet Filter (BPF) | Wireshark'ın kendi dili |
| **Yazım örneği** | `host 192.168.1.1` | `ip.addr == 192.168.1.1` |
| **Değiştirilebilir mi?** | Hayır (durdurman lazım) | Evet (çalışırken) |
| **Disk kullanımı** | Azaltır | Etkilemez |

---

## Eğitmenin Gösterdiği Örnek:

**Eğitmen şunu yaptı:** 5294 paket yakalandıktan sonra Display Filter'a şunu yazdı:
```
ip.addr == 10.80.86.182
```
**Sonuç:** 5294 paketten sadece 8 tanesi gösterildi – Emine Hocam'ın bilgisayarıyla ilgili paketler!

---

## Display Filter – Gelişmiş Kullanım

### AND (Ve) Operatörü:
```
ip.addr == 10.80.86.182 && icmp
```
> "Bu IP ile olan VE ICMP protokolüne ait paketleri göster"
> Her iki koşulun da doğru olması gerekir!

### OR (Veya) Operatörü:
```
ip.addr == 10.80.86.182 || icmp
```
> "Bu IP ile olan VEYA ICMP paketi olan – birisi doğruysa göster"

### Subnet (Alt Ağ) Filtresi:
```
ip.addr == 10.80.0.0/16
```
> "10.80 ile başlayan tüm IP'lere ait paketler"

### Eşit Değil Operatörü:
```
ip.addr != 192.168.1.1
```
(`!=` = eşit değildir, `==` = eşittir)

### Kaynak (Source) ve Hedef (Destination) Ayrımı:
```
ip.src == 10.80.87.205    (sadece kaynak)
ip.dst == 10.80.86.182    (sadece hedef)
```

---

## Yaygın Filtre Karşılaştırması (Eğitmenin Tablosu)

| Amaç | Capture Filter | Display Filter |
|---|---|---|
| Belirli IP | `host 192.168.1.1` | `ip.addr == 192.168.1.1` |
| Sadece kaynak | `src host 192.168.1.1` | `ip.src == 192.168.1.1` |
| TCP protokolü | `tcp` | `tcp` |
| UDP protokolü | `udp` | `udp` |
| Belirli port | `port 80` | `tcp.port == 80` |

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 6

**Soru 1:** Disk doluyorsa ve yalnızca HTTP trafiği kaydedilmeli – hangi filtreyi kullanırsın?
> **Cevap:** Capture Filter! Yakalamadan önce ayarlanır ve filtreye uymayan paketler diske hiç yazılmaz.

**Soru 2:** `ip.addr == 10.0.0.1 && tcp` ne anlama gelir?
> **Cevap:** Kaynak ya da hedef IP'si 10.0.0.1 olan VE TCP protokolü kullanan paketleri göster.

**Soru 3:** Wireshark'ta filtre kutusunun rengi kırmızıya dönerse ne yapmalısın?
> **Cevap:** Filtreyi düzeltmelisin! Kırmızı = hatalı filtre, filtreyi uygulayana kadar devam edemezsin.

---

# BÖLÜM 7: Wireshark Menüleri – Detaylı İnceleme

## File Menüsü

**Ne İçerir?**
- **Open:** Önceden kaydedilmiş paket dosyasını aç
- **Recent:** En son açılan dosyalar
- **Merge:** Birden fazla yakalama dosyasını birleştir
- **Close:** Mevcut yakalamayı kapat
- **Save / Save As:** Kaydet / Farklı kaydet
- **Export Specified Packets:** Seçili paketleri farklı formatta dışa aktar

### Dosya Formatları:

**En yaygın Wireshark formatları:**
- **.pcap** → Klasik paket yakalama formatı
- **.pcapng** → Gelişmiş versiyon, daha küçük boyut, daha fazla özellik

**Eğitmenin not ettiği:** pcap ve pcapng arasındaki fark? İkisi de benzer ama pcapng daha gelişmiş. Hangi programın kabul ettiğine bağlı.

### Dışa Aktarma Formatları:
- **Plain Text (.txt)** → Düz metin, insan okuyabilir
- **CSV** → Excel ve LibreOffice'te tablolama
- **C Arrays** → C programlama dili için
- **JSON** → Python ve modern araçlar için

**Pratik Kullanım:**
> Kınar Hocam şunu yapabilir: Bir firmada 3 saatlik paket yakalama yaptı. Dosyayı kaydetti. Eve geldi, kendi bilgisayarında açıp analiz etti!

---

## Edit Menüsü

**Önemli Özellikler:**

### Copy (Kopyala):
- Plain Text olarak kopyala
- CSV olarak kopyala
- YAML olarak kopyala
- Başka ortamlara yapıştırmak için kullanılır

### Find Packet (Paket Bul):
**Çok Kullanışlı!** Edit → Find Packet

- **Packet List'te** arama yap (üst bölge)
- **Packet Details'te** arama yap (orta bölge)
- **Packet Bytes'ta** arama yap (alt bölge, hex veri)
- **Regular Expression** ile arama

**Eğitmenin Gösterdiği İtalyan Telekom Örneği:**
> Şifreli gönderilmeyen (açık metin) eski bir bağlantıdan "password" kelimesini aradı. Sonuç: "Alice ADSL" kullanıcı adı ve şifresi düz metin olarak yakalandı!

**Bu ne anlama geliyor?** Eğer veriler şifrelenmeden (encrypt edilmeden) gönderiliyorsa, Wireshark bunları okuyabilir! **Bu yüzden HTTPS, SSH gibi şifreli protokoller bu kadar önemli!**

### Mark / Unmark (İşaretle):
- Önemli paketleri siyah renkle işaretle
- **Sağ tıkla → Mark** veya **Edit → Mark All Display**
- Büyük bir yakalamada ilgini çeken paketleri hızlıca işaretlemek için

### Time Reference (Zaman Referansı):
- Belirli bir paketi **referans noktası** olarak işaretle
- O paketten sonraki zaman farkları sıfırdan başlar
- "Bu noktadan sonrasını ayrıca inceleyelim" durumları için

### Packet Comment (Paket Yorumu):
- Bir pakete not ekle: "Bu paket şüpheli görünüyor!"
- Edit → Packet Comment → Add New Comment
- Yorumlar istatistiklerde görünür

### Preferences (Tercihler):
- **Dil seçimi:** Almanya'daysan Almanca, Türkiye'deysen Türkçe
- **Columns (Sütunlar):** Yeni sütun ekle veya mevcut sütunları düzenle
- **Font and Colors:** Yazı boyutu ve tipi (görme sorunu varsa büyütebilirsin)
- **Layout:** Ekran düzeni değiştirme
- **Name Resolution:** IP adreslerini bilgisayar adlarına çözümleme

---

## View Menüsü

**Önemli Özellikler:**
- **Toolbar'ları** aç/kapat (Packet List, ana toolbar, filtre, status)
- **Time Display Format:** Zamanı nasıl göster (UTC, local, vb.)
- **Zoom In/Out:** Yaklaştır/uzaklaştır
- **Collapse/Expand All:** Tüm detayları topla veya aç

### Name Resolution (İsim Çözümleme):
> Wireshark, IP adresleri yerine bilgisayar adlarını gösterebilir. Şirkette bir tarama yapıyorsun ve "10.80.87.205" yerine "bilgisayar-muhasebe-3" gibi anlamlı isimler görmek istiyorsun → Name Resolution!

### Colorize Packet List (Renklendirme):
Farklı protokoller farklı renklerle gösterilir:

| Renk | Anlam |
|---|---|
| Siyah arka plan | Kritik hata, bozuk paket |
| Kırmızı | Ciddi hata, bağlantı kesilmesi |
| Sarı | Dosya paylaşımı, ağ yazıcısı trafiği |
| Yeşil | Web içerikleri |
| Açık mavi | UDP trafiği, DNS, video akışı |
| Koyu mavi | Farklı anlam |
| Koyu gri | Sistem olayları |

**Profesyoneller için not:** Renklendirme işlemciyi (CPU) ve belleği (RAM) yorar! Uzun yakalamalarda renksiz kullanım tercih edilir.

### Coloring Rules (Renklendirme Kuralları):
View → Coloring Rules ile hangi paketin hangi renkte görüneceğini özelleştirebilirsin.

### Follow TCP/UDP Stream (Akışı Takip Et):
Bir paketin üzerine sağ tıkla → Follow → TCP Stream

**Çok güçlü bir özellik!** O paket bir konuşmanın parçasıysa, tüm konuşmayı gösterir:
- 🔴 Kırmızı: Bir tarafın gönderdiği
- 🔵 Mavi/Mor: Diğer tarafın gönderdiği

**Eğitmenin notu:** Eğer şifrelenmiş değilse, konuşmanın tam içeriğini okuyabilirsin!

---

## Analyze Menüsü

**En Önemli Özellikler:**

### Display Filter:
- Örnek listesini görmek için buraya tıklayabilirsin

### Apply as Filter (Filtre Olarak Uygula):
**Süper Pratik!** Bir paketin herhangi bir alanına sağ tıkla → Apply as Filter → Selected

**Örnek Kullanımlar Eğitmenin Gösterdiği:**
```
TCP protokolü → Sağ tık → Apply as Filter → TCP olanları getir
IP Length = 52 → Sağ tık → Apply as Filter → 52 byte'lık paketler
TTL = 64 → Sağ tık → Apply as Filter → TTL'si 64 olanlar
Source Port = 80 → Sağ tık → Apply as Filter → Port 80'den gelenler
```

### Apply as Column (Sütun Olarak Ekle):
Herhangi bir alan değerini → Sütun olarak ekle

**Eğitmenin örneği:** "Total Length" değerini sütun olarak ekleyince paket boyutlarına göre filtreleme yapabildi.

### Prepare as Filter:
Apply as Filter'dan farkı: Uygulamadan önce filtreyi hazırlar, "Enter" beklenir. Birden fazla koşul eklemek için kullanışlı.

### Conversation Filter (Konuşma Filtresi):
- İki IP arasındaki karşılıklı trafiği göster
- TCP konuşmalarını filtrele
- IPv4 konuşmalarını filtrele

---

## Statistics (İstatistik) Menüsü

### Capture File Properties (Yakalama Dosyası Özellikleri):
Çok bilgi içerir:
- Dosya adı, boyutu, **SHA1 ve SHA2** hash değerleri (kriptografi dersinde bu önem kazanacak!)
- Hangi donanımla (AMD işlemci, Linux OS)
- Hangi uygulama ile yakalandı
- Kaç paket yakalandı, kaç tanesi gösteriliyor
- Ortalama paket boyutu, ortalama bit hızı
- **Packet Comments:** Yazılan tüm yorumları gösterir!

### Conversations (Konuşmalar):
Kim kiminle konuşmuş?
- Ethernet düzeyinde
- IPv4 düzeyinde
- IPv6 düzeyinde

### Endpoints (Uç Noktalar):
Ağdaki tüm cihazların MAC ve IP adreslerini listeler.

### I/O Graphs:
Trafik grafiği – nerede artıyor, nerede azalıyor?

### DNS İstatistikleri:
Hangi DNS sorguları yapılmış, ne zaman?

### TCP Time Sequence Graph:
TCP trafiğinin zaman akış grafiği.

---

## Help Menüsü – Sample Captures (Örnek Yakalamalar)

**Eğitmenin Gösterdiği Çok Faydalı Özellik!**

Help → Sample Captures → Wireshark'ın resmi wiki'si açılır.

Buradan gerçek yakalama dosyaları indirebilirsin!

**Eğitmen "DHCP" araması yaparak DHCP örneği indirdi:**
> İndirilen dosyayı açınca şunu gördük:
> - **Discover** → Broadcast ile DHCP sunucusu aranıyor
> - **Offer** → DHCP sunucusu IP teklif ediyor
> - **Request** → IP isteniyor
> - **Acknowledge** → IP onaylanıyor

Anlattığımız DHCP teorisi gerçek bir yakalamada böyle görünüyor!

---

## Expert Information (Uzman Bilgisi)

Analyze → Expert Information veya altta sağ köşe ikonu.

**Renk Kodlaması:**
- **Kırmızı (Error):** Ciddi hata
- **Sarı (Warning):** Uyarı
- **Mavi (Note):** Not
- **Yeşil (Comment):** Yorum

**Eğitmenin Örneği:**
"UDP Lite Illegal" dosyasında checksum kontrolü yapıldığında normalden farklı bir değer bulunmuş → Wireshark bunu "Bad Checksum" olarak işaretlemiş ve Expert Information'da göstermiş.

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 7

**Soru 1:** Şifreli olmayan bir bağlantıda "password" kelimesini nasıl ararım?
> **Cevap:** Edit → Find Packet → arama alanına "password" yaz, hangi bölgede arayacağını seç (Packet Details veya Packet List)

**Soru 2:** Bir pakete not eklemek için ne kullanırsın?
> **Cevap:** Edit → Packet Comment → Add New Comment

**Soru 3:** Statistics → Capture File Properties'te "SHA1" ve "SHA2" değerleri ne için kullanılır?
> **Cevap:** Dosyanın doğruluğunu kriptografik olarak doğrulamak için (bütünlük kontrolü)

---

# BÖLÜM 8: Gerçek Hayat Uygulama – Wireshark'ta Protokoller

## ARP Trafiği Yakalama

**Eğitmenin Yaptığı:**
1. Wireshark açtı, Windows'ta Ethernet kartını seçti
2. Capture Filter'a: `host 10.80.70.0` yazdı (belirli bir hosta ait paketler)
3. Terminal'den ping attı: `ping 10.80.70.0`
4. Display Filter'a: `arp` yazarak ARP paketlerini izoledi

**Sonuç – ARP Paket Analizi:**

**Frame 1 – ARP Request (İstek):**
- Destination: `FF:FF:FF:FF:FF:FF` (Broadcast – herkese bağırıyor)
- Source: Kendi MAC adresi
- Soru: "10.80.70.0 IP'si kimin? Bana MAC adresini söyle!"

**Frame 2 – ARP Reply (Cevap):**
- Kaynak ve hedef yer değiştiriyor
- Cevap: "10.80.70.0 benim! İşte MAC adresim!"

**BUNU NEDEN GÖRDÜK?**
Ping atmadan önce lokal ağda önce ARP yapılıyor. Çünkü MAC adresi bilinmeden iletişim kurulamaz!

---

## ICMP/PING Trafiği Yakalama

**Eğitmenin Yaptığı:**
1. ARP filtresini kaldırdı, `icmp` yazdı
2. Sonuçlar:
   - **Echo Request** (Tip 8, Kod 0) – "PING" notu ile birlikte
   - **Echo Reply** (Tip 0, Kod 0) – "PONG" cevabı
3. 4 ping gönderilmişti → 4 istek + 4 cevap = 8 paket

---

## ICMP Tip 11 – Time to Live Exceeded (TTL Bitti)

**Traceroute sırasında yakalanan:**
- **Tip 11, Kod 0:** "Time to Live Exceeded" – TTL değeri sona erdi
- Bu mesaj traceroute komutunun çalışma mekanizmasının görünür hali!

---

## DNS Trafiği Yakalama

**Eğitmenin Yaptığı:**
1. Wireshark başlattı, yeni bir siteye (hackeracademyuk) bağlandı
2. Display Filter'a `dns` yazdı

**Sonuç:**
- Bilgisayarın DNS sunucusuna (10.80.02) sorgu gönderdiği görüldü
- DNS sorgu türü: **"Standard Query"** – "hackeracademyuk'un IP adresi nedir?"
- DNS cevabı: **172.67.73.157** (Cloudflare IP)

**Follow UDP Stream:**
> Sağ tık → Follow → UDP Stream deyince DNS konuşmasının tam içeriği görüldü!

---

## SoC Analisti Sorusu – Gerçek Hayat Senaryosu

**Öğrencinin sorusu:** "İş yerinde SIEM veya XDR var. Önüme otomatik alarm düşüyor. Bu durumda Wireshark'ı ne zaman kullanacağım?"

**Eğitmenin cevabı:**
1. Alarm düştüğünde → SIEM/Splunk üzerinden log'lara bakarsın
2. Alarm True Positive (gerçek tehdit) ise → Daha derinlemesine araştırma için Wireshark
3. O bilgisayara gidip paket yakalarsın veya daha önceden kaydedilmiş .pcap dosyasını açarsın
4. Sorunun kaynağını bulursun, rapor yazarsın

**Bir diğer soru:** "Geçmişte başlamış bir alarmı Wireshark'ta geriye dönük görebilir miyim?"

**Eğitmenin cevabı:** 
> Sadece Wireshark **7/24 çalışıyorsa** ve o andan itibaren kayıt yapıyorsa. Öncesi için Wireshark'ta geçmişe bakamazsın. Bu yüzden kurumsal ortamlarda sürekli trafik kaydı yapan sistemler bulunur.

---

# BÖLÜM 9: Transport Katmanı (Giriş)

## 🔵 BUNU NEDEN ÖĞRENİYORUZ?
Şimdiye kadar Datalink (MAC) ve Network (IP) katmanlarını öğrendik. Bir üstü Transport katmanı – burada TCP ve UDP var. İnternetteki neredeyse her şey bu iki protokolden birine dayanır.

---

## Katmanlar Arası Bağlantı Hatırlatması

```
Application Layer     ← DNS, HTTP, DHCP burada
Transport Layer       ← TCP ve UDP burada (YENİ!)
Network/Internet Layer ← IP adresi burada
Data Link Layer       ← MAC adresi, Frame burada
Physical Layer        ← Fiziksel bağlantı
```

**Her katmanın kendi veri birimi:**
- Application → Data (Veri)
- Transport → **Segment**
- Network → Paket
- Data Link → Frame
- Physical → Bit

---

## Transport Katmanı Ne Yapar?

1. **Segmentation (Parçalama):** Yukarıdan gelen büyük veriyi ağda taşınabilecek küçük parçalara böler
2. **Reassembly (Birleştirme):** Aşağıdan gelen parçaları birleştirir ve üst katmana iletir
3. **Port tabanlı adresleme:** Hangi uygulama, hangi port? (Bunu ilerleyen derslerde göreceğiz)
4. **Akış kontrolü (Flow Control):** Veriyi doğru hızda göndermek
5. **Hata kontrolü:** Paketin karşıya doğru gittiğini kontrol etmek

---

## TCP – Transmission Control Protocol

**Çalıştığı Katman:** Transport (Katman 4)

**Karakteri:** Güvenilir, dikkatli, yavaş ama emin

**Günlük Hayat Analogisi:** 📦 Garantili Kargo
> Kargo şirketine paketini veriyorsun. Şirket "Teslim edildiğini imzayla onaylıyorum" diyor. Kaybolursa tekrar gönderiyor. Yavaş ama güvenilir!

**TCP'nin Özellikleri:**
- ✅ **Bağlantı tabanlı** (Connection-based) – önce bağlantı kurulur
- ✅ **Veri parçalama** (Fragmentation) yapar
- ✅ **Hatasız iletim** – kayıp paketleri tekrar gönderir
- ✅ **Sıra numarası** (Sequence Number) vererek takip eder
- ✅ **Flow control** (akış kontrolü)
- ⏱️ **Yavaş** ama **güvenilir**

**Kullanıldığı Yerler:**
- Web taraması (HTTP/HTTPS)
- E-posta gönderme
- Dosya indirme
- SSH bağlantısı

**Siber Güvenlik Açısından Önemi:**
TCP veri bütünlüğünü önemsediği için güvenlik kritik uygulamalar TCP kullanır.

### Three-Way Handshake (Üç Yönlü El Sıkışma)

Eğitmen "Private Handshake" olarak bahsetti – ilerleyen derslerde detaylı işlenecek. Kısaca:

**Günlük Hayat Analogisi:** 📞 Telefon Görüşmesi
> "Alo?" → "Evet, duydun mu?" → "Duyuyorum, konuşabiliriz!" ve artık konuşma başlar.
> TCP de bağlantı kurulmadan önce böyle bir "tokalaşma" yapar.

---

## UDP – User Datagram Protocol

**Çalıştığı Katman:** Transport (Katman 4) – TCP ile aynı!

**Karakteri:** Hızlı, özgür ruhlu, sonuçtan habersiz

**Günlük Hayat Analogisi:** 📻 Canlı Radyo Yayını
> Radyo yayını yapılıyor. Kim dinledi, kim dinlemedi, sinyal bozuldu mu, ilgilenmez! Yayın devam eder. UDP de böyle – paket gitti mi gitmedi mi umursamaz, devam eder!

**UDP'nin Özellikleri:**
- ❌ **Bağlantısız** (Connectionless) – direkt gönderir
- ❌ **Hata kontrolü yok** – kayıp paketler tekrar gönderilmez
- ❌ **Sıra numarası yok**
- ⚡ **Çok hızlı**
- ⚠️ **IP sahteciliğine (IP Spoofing) açık**

**Kullanıldığı Yerler:**
- Video/ses akışı (YouTube, Netflix, Zoom)
- DNS sorguları
- DHCP
- Online oyunlar

**Neden Kabul Edilebilir?**
Video izlerken birkaç frame eksik olsa fark etmeyiz bile! Ama gecikme (lag) varsa çok rahatsız oluruz → Hız öncelikli durumlarda UDP.

---

## KARMAŞTIRMA! ⚠️ TCP vs UDP

| Özellik | **TCP** | **UDP** |
|---|---|---|
| Bağlantı | Bağlantı kurar (handshake) | Direkt gönderir |
| Hız | Yavaş | Hızlı |
| Güvenilirlik | Yüksek (kayıplar tekrar gönderilir) | Düşük (kayıplar umursanmaz) |
| Sıralama | Sıra numaralı | Sıra yok |
| Kullanım | Web, e-posta, dosya | Video, ses, DNS, DHCP |
| Veri birimi | Segment | Datagram |
| Hata kontrolü | Var | Yok |

---

## 📦 HATIRLA!
> - TCP = **Güvenilir ama yavaş** → Kritik veri için
> - UDP = **Hızlı ama güvensiz** → Hız öncelikli için
> - **İkisi de Transport katmanında (Layer 4) çalışır**
> - Her ikisi de **Port numaraları** kullanır

---

## 🧪 KENDİNİ TEST ET – BÖLÜM 9

**Soru 1:** Transport katmanında verinin adı ne?
> **Cevap:** Segment

**Soru 2:** DHCP hangi Transport protokolünü kullanır? Neden?
> **Cevap:** UDP. Çünkü hızlı olması önemlidir ve kayıp olan DHCP paketleri büyük sorun yaratmaz.

**Soru 3:** TCP'nin "güvenilir" olmasının sebebi nedir?
> **Cevap:** Sıra numaraları kullanır, kayıp olan paketleri tespit eder ve tekrar gönderir. Karşı tarafın alındı (ACK) bildirmesini bekler.

---

# 🏁 GENEL TEKRAR VE ÖZET

## Tüm Konuları Tek Cümleyle:

| Konu | Tek Cümle Özet |
|---|---|
| **ICMP** | IP haberleşmesinde hata ve kontrol mesajlarını taşıyan protokoldür; Ping ve Traceroute'un temelidir |
| **PING** | ICMP Echo Request/Reply kullanarak bir cihazın erişilebilir olup olmadığını test eden **komuttur** |
| **Traceroute** | Hedef bir adrese giden yoldaki tüm router'ları (hop'ları) listeleyen; TTL mekanizmasıyla çalışan araçtır |
| **Wireshark** | Ağın "röntgenini" çeken, ücretsiz ve açık kaynaklı ağ trafiği yakalama ve analiz programıdır |
| **Capture Filter** | Yakalamadan önce ayarlanan, sadece istenen paketleri kaydeden ve diski/CPU'yu koruyan filtredir |
| **Display Filter** | Yakalanan paketler arasında istenen paketleri görüntülemek için kullanılan, her an değiştirilebilen filtredir |
| **TCP** | Bağlantı tabanlı, güvenilir ama yavaş Transport protokolüdür; kayıp paketleri tekrar gönderir |
| **UDP** | Bağlantısız, hızlı ama güvensiz Transport protokolüdür; video/ses akışı gibi hız gerektiren yerlerde kullanılır |

---

## Öğrenilen Komutlar Özeti

```bash
# Ping komutu
ping google.com
ping 192.168.1.1

# Traceroute (Linux)
traceroute google.com

# Tracert (Windows)
tracert google.com

# ifconfig (Linux) - IP adresini öğren
ifconfig

# ipconfig /all (Windows) - DNS dahil tüm ağ bilgileri
ipconfig /all
```

## Wireshark'ta Sık Kullanılan Display Filtreleri

```
icmp                              # Sadece ICMP paketleri
arp                               # Sadece ARP paketleri
dns                               # Sadece DNS paketleri
tcp                               # Sadece TCP paketleri
udp                               # Sadece UDP paketleri
dhcp                              # Sadece DHCP paketleri
http                              # Sadece HTTP paketleri

ip.addr == 192.168.1.1            # Bu IP'den veya bu IP'ye
ip.src == 192.168.1.1             # Sadece bu IP'den
ip.dst == 192.168.1.1             # Sadece bu IP'ye

ip.addr == 10.0.0.0/24            # Bu subnet'e ait

tcp.port == 80                    # TCP port 80

ip.addr == 192.168.1.1 && icmp    # Bu IP + ICMP (VE)
ip.addr == 192.168.1.1 || icmp    # Bu IP VEYA ICMP (VEYA)
```

---

## 💡 Eğitmenin Verdiği Altın Öğütler

1. **"Veri asla yalan söylemez"** – Wireshark ham gerçeği gösterir, başka araçların gözden kaçırdıklarını yakalar.

2. **"Wireshark tek başına bir saldırıyı durduramaz"** – Ama neyin neden olduğunu anlamana yardım eder.

3. **"Paket Tracer sadece network için kullanılır"** – Ama Wireshark hem network hem de bundan sonraki tüm güvenlik modüllerinde kullanılacak.

4. **"Bu programı ezberlemenize gerek yok"** – İhtiyaç duyduğunuzda açıp kullanabileceğiniz bir araç. Ama temellerini bilmek şart.

5. **"Şifreli olmayan protokoller açık metin gider"** – Ve Wireshark onları okuyabilir! Bu yüzden HTTPS, SSH önemli.

---

