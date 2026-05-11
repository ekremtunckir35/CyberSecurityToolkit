# 🛡️ AĞ TEMELLERİ — DERS 11
## Uzman Siber Güvenlik Eğitim Notu
### Konu: DNS, TCPDump, Netstat, Network Miner



# 🔗 BÖLÜMLER ARASINDAKİ BÜYÜK RESİM

Bu derste 4 ana konu var. Hepsi birbiriyle bağlantılı:

```
DNS              →   Ağda isimler IP'ye çevrilir
TCPDump          →   Bu trafiği terminalde yakalar & filtreleriz  
Netstat          →   Kendi cihazımızdaki bağlantı durumunu görürüz
Network Miner    →   Yakalanan trafiği adli bilişim aracıyla analiz ederiz
```

---

# 📚 BÖLÜM 1: DNS — İnternetin Telefon Defteri

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Çünkü internette her şey DNS'le başlar. Bir web sitesine girerken, e-posta gönderirken, hatta bir uygulamayı açarken mutlaka DNS devreye girer. Hacker'lar DNS'i manipüle eder. Güvenlik uzmanları DNS kayıtlarını inceleyerek saldırı izleri bulur. DNS'i anlamayan, ağı anlamaz.

---

## 1.1 — Domain (Alan Adı) Nedir?

**"Bu nedir?" sorusuyla başlayalım:**

İnternetteki her web sitesinin bir adresi vardır. Bu adrese **Domain** (Alan Adı) diyoruz. Mesela:
- `cnn.com`
- `wikipedia.org`
- `google.com`

Bunlar bizim yazıp tarayıcıya girdiğimiz isimler.

**🏠 Günlük Hayat Analojisi:**

Düşün: Bir arkadaşının evine gitmek istiyorsun. Onun adını biliyorsun ama evi nerede bilmiyorsun. Ne yaparsın? Adres sorarsın. Yani isimden adrese geçersin.

İnternette de bilgisayarlar birbirleriyle **isimle değil, sayısal IP adresleriyle** konuşur. `google.com` yazdığında bilgisayarın arka tarafta aslında `216.58.208.132` gibi bir sayı kullanması gerekiyor. Ama biz bunları ezberleyemeyiz. İşte DNS tam burada devreye giriyor.

---

## 1.2 — DNS (Domain Name System) Nedir?

**DNS = İnternetin Telefon Defteri**

Eğitmenimiz dersteki ifadesiyle: **"The Phone Book of the Internet"** — İnternetin Telefon Defteri.

Eski tip telefon defterlerinde ne vardı? Bir kişinin adı ve yanında numarası. DNS de tam böyle çalışıyor:

| Telefon Defterinde | DNS'te |
|--------------------|--------|
| Ahmet Yılmaz | google.com |
| 0532 123 45 67 | 216.58.208.132 |

**Bu sistemin neden gerekli olduğunu eğitmenimiz şöyle anlattı:**
"Normal şartlarda Emrah Hocam'ın şunu bilmesi lazımdır: Google.com yazmak yerine 216.58.208.132 yazması gerekir. Tamam. Bunu öğrendik. Hadi ezberleyelim. Peki ne olur, Google bu IP adresini değiştirirse? Yeni IP adresini nereden bulacağız?"

İşte bu sorun DNS ile çözülüyor.

---

## 1.3 — DNS Nasıl Çalışır? (Adım Adım Senaryo)

Bu kısım çok önemli. Derste eğitmenimiz adım adım anlattı, biz de adım adım gidelim.

**Senaryo:** `mail.google.com` adresine gitmek istiyorsun.

### Adım 1: Önce Kendi Bilgisayarına Sor

Tarayıcıya `mail.google.com` yazdın. Bilgisayarın önce kendi belleğine (cache/önbellek) bakar: "Ben bunu daha önce ziyaret ettim mi? Adresi var mı elimde?"

**Eğer var:** Doğrudan gider. DNS süreci biter.
**Eğer yok:** 2. adıma geçilir.

### Adım 2: Local DNS Server'a Sor (Resolver)

Bilgisayar, internet servis sağlayıcının (ISP) sana verdiği **Local DNS Server**'a (Yerel DNS Sunucu) sorar. Bunu görmek için terminale `ipconfig /all` (Windows) veya `ifconfig` (Linux) yazabilirsin. Orada "DNS Server" yazan satıra bak.

Local DNS server da önce kendi önbelleğine bakar. Eğer son 30 dakika içinde birisi aynı adresi sormuşsa, kayıt var demektir. Doğrudan cevap verir.

**Eğer yoksa:** 3. adıma geçilir.

### Adım 3: Root Server'a Sor

Local DNS server, dünya üzerindeki **Root Server**'lardan birine gider ve sorar:
> "mail.google.com nerede?"

Root Server cevap verir:
> "Bilmiyorum. Ama sana COM uzantılı sitelerin bilgisini tutan sunucunun adresini verebilirim."

### Adım 4: TLD Server'a Sor (Top Level Domain)

Local DNS server, COM uzantılı TLD Server'a gider ve sorar:
> "mail.google.com nerede?"

TLD Server cevap verir:
> "google.com'un tüm bilgilerini tutan Otorite DNS Server'ın adresini sana söyleyebilirim."

### Adım 5: Otorite DNS Server'dan Cevabı Al

Local DNS server, Otorite DNS Server'a gider ve sorar:
> "mail.google.com nerede?"

Otorite DNS Server cevap verir:
> "İşte IP adresi: 444.444.444.444"

### Adım 6: Bağlantı Kurulur

Bu IP adresi bilgisayarına gelir ve artık `mail.google.com`'a bağlanırsın.

**⏱️ Tüm bu süreç milisaniyeler içinde gerçekleşir. Sen fark bile etmezsin.**

---

> ### 🔴 KARMAŞTIRMA! — Cache mi, Server mı?
>
> **Cache (Önbellek):** Daha önce gittiğin sitelerin adres bilgileri geçici olarak saklanır. Hızlı erişim sağlar.
>
> **DNS Server:** IP adreslerini tutan gerçek sunucu. Cache'de bulunmadığında buraya gidilir.
>
> **Fark:** Cache geçicidir (30 dakika, 1 saat gibi). DNS Server kalıcı ve sürekli güncellenir.

---

## 1.4 — DNS'teki 3 Katmanlı Sunucu Yapısı

### Root Server'lar

Dünyanın en tepe DNS sunucuları. **A'dan M harfine kadar 13 adet** root server vardır. Ama bu 13 sunucu dünyaya dağılmış yüzlerce kopyasıyla çalışır. Derste eğitmenimiz o gün baktıklarında **1958 adet** root server olduğunu gördüklerini belirtti.

**ICANN** adlı kuruluş bu root serverları yönetir. Eğitmenimizin anlattığına göre bu 13 sunucudan:
- 1 tanesi Amerikan Savunma Bakanlığı'na ait
- 1 tanesi Amerikan Askeri'ne ait
- 2 tanesi Amerikalı üniversitelere ait
- Geri kalanları çeşitli kurumsal yapılara ait

Root serverların görevi: **Sadece TLD serverlarının nerede olduğunu bilmek.**

**🏠 Analoji:** Şehrin merkezindeki büyük bir harita gibi. Bu harita sana "com uzantılı siteler şu binadayken, net uzantılılar şu binadayken" der. Tek tek daireleri bilmez.

### TLD Server'lar (Top Level Domain)

Top Level Domain = Üst Düzey Alan Adı.

`.com`, `.net`, `.org`, `.tr`, `.de`, `.uk` gibi uzantılar TLD'dir. Her uzantının kendi sunucusu vardır.

**Örnek:**
- `.com` için ayrı bir TLD sunucusu var
- `.net` için ayrı
- `.tr` için ayrı

TLD serverların görevi: **Sadece o uzantıdaki sitelerin Otorite DNS Server'larının adresini bilmek.**

### Otorite DNS Server'lar

En alttaki, en özel bilgiyi tutan sunucular. `google.com`'un tüm IP adreslerini, alt domain'lerini, mail server bilgilerini burada saklar.

Sen yeni bir web sitesi kurduğunda, alan adını kayıt ettirdiğinde, bilgiler buraya yazılır.

**🏠 Analoji:** Bir apartmandaki kapıcı gibi. Hem hangi dairede kim oturduğunu hem de o kişilerin telefon numaralarını bilir.

---

> ### ✅ HATIRLA!
> - **Root Server:** TLD serverların nerede olduğunu bilir
> - **TLD Server:** Otorite DNS serverların nerede olduğunu bilir
> - **Otorite DNS Server:** Gerçek IP adreslerini bilir ve saklar

---

## 1.5 — DNS Güvenlik Tehdidi: DNS Spoofing (Cache Poisoning)

Derste bir öğrenci çok zekice bir soru sordu:

**Öğrenci:** "O zaman hacker bunu değiştirirse, o cache'e girerse sizi başka yere de yönlendirebilir. Bu atağın adı ne oluyordu hocam?"

**Eğitmen:** "Burada IP Spoofing diyebiliriz. Ama daha doğrusu **DNS Spoofing** diyebiliriz. DNS Sahtekarlığı. Oradaki IP adreslerini hatalı şekilde değiştirip kendine yönlendirebilir."

**🔐 Bu ne anlama gelir?**

Diyelim ki DNS cache'ine `google.com = 1.2.3.4` yazılmış. Normalde bu doğruydu. Ama bir saldırgan bu cache'e girip `google.com = 5.5.5.5 (kendi sahte sunucusu)` yazarsa, sen `google.com` yazdığında gerçek Google'a değil, saldırganın sahte sitesine gidersin. Şifreni girersin, çalınır.

**🕐 Cache ne kadar süre tutulur?**

Eğitmen: "En fazla 30 dakika diye biliyorum ama tekrar araştırabilirim."

Yani cache çok kısa süre tutulur. Hem:
1. Yönetilen bellekte yer açılması için
2. IP adresleri değiştiğinde güncel kalmak için
3. Güvenlik riski nedeniyle

---

## 1.6 — DNS Kayıt Tipleri

Otorite DNS Serverlar birden fazla tür kayıt tutar. Eğitmenimiz `nslookup.io` sitesinden bunları gösterdi.

### A Kaydı (Address Record)
Alan adını **IPv4** adresine eşler.
```
ornek.com  →  192.168.1.1
```
**"A Kaydı = Alan adının evininin IPv4 adresi"**

### AAAA Kaydı
Alan adını **IPv6** adresine eşler. (A kaydının IPv6 versiyonu)

### CNAME Kaydı (Canonical Name)
Bir alan adını başka bir alan adına yönlendirir. Takma ad (alias) gibi düşün.

**Örnek:** `www.ornek.com` → `ornek.com`

Eğitmenin dersteki örneği: `twitter.com` yazdığında seni `x.com`'a götürür. Bu bir CNAME yönlendirmesidir.

Aynı şekilde: `http://` yazdığında otomatik `https://`'ye yönlendirme de CNAME ile yapılabilir.

### MX Kaydı (Mail Exchanger)
E-posta sunucusunun adresini belirtir. Bu kayıt sayesinde sana gönderilen e-postalar doğru sunucuya iletilir.

**🏠 Analoji:** Şirketin posta kutusu nerede? MX kaydı bunu söyler.

MX kaydında **öncelik (priority)** değeri önemlidir. Sayı ne kadar küçükse, öncelik o kadar yüksektir.

### TXT Kaydı (Text Record)
Serbest metin bilgisi tutar. Genellikle şunlar için kullanılır:
- Alan adı sahipliğini doğrulamak
- SPF (Spam filtresi) ayarları
- Güvenlik yapılandırmaları

Eğitmen derste bir CTF (Capture The Flag) yarışmasında TXT kaydının içinde gizli bir bilgi bulunduğunu ve onu kopyalayıp yapıştırarak soruyu çözdüğünü anlattı.

### NS Kaydı (Name Server)
Bu alan adının DNS sorgularından sorumlu olan Otorite DNS Server'ları isimlendirir.

### SOA Kaydı (Start of Authority)
Bir DNS bölgesi hakkında yetkili bilgileri içerir: ana isim sunucusu, yöneticinin e-posta adresi, seri numarası. Her DNS bölgesinde bulunması zorunlu ilk kayıttır.

**Örnek:** `amazon.com` için SOA sorgusu yapıldığında Cloudflare veya Amazon AWS üzerindeki DNS bölge bilgisi gelir.

### PTR Kaydı (Pointer)
Reverse DNS için kullanılır: IP adresi → Alan adı dönüşümü.

### SRV Kaydı
Belirli hizmetlere özel kayıt (örn: VoIP, video konferans servisleri).

---

> ### 🔴 KARMAŞTIRMA! — A Kaydı mı, CNAME mi?
>
> | | A Kaydı | CNAME Kaydı |
> |---|---|---|
> | **Ne yapar?** | İsim → IP adresi | İsim → Başka isim |
> | **Sonuç** | Direkt IP'ye ulaşır | Önce isim çözülür, sonra IP |
> | **Örnek** | google.com → 216.x.x.x | www.google.com → google.com |

---

## 1.7 — nslookup Komutu ile DNS Sorgulama

Eğitmenimiz terminalde `nslookup` komutunu kullanarak bu kayıtları canlı olarak gösterdi.

```bash
# Temel kullanım - A kaydı (IPv4) sorgulama
nslookup google.com

# MX kaydı sorgulama (set q yöntemi)
nslookup
> set q=mx
> google.com

# MX kaydı sorgulama (type yöntemi - TryHackMe'de karşılaşılan versiyon)
nslookup --type=mx google.com

# NS kaydı sorgulama
nslookup -type=ns oaccademy.d

# Alternatif: nslookup.io web sitesi
# Terminale erişimin olmadığı durumlarda tarayıcıdan kullanılabilir
```

**⚠️ Önemli Not — Farklı Platformlarda Farklı Sözdizimi:**

Eğitmenimiz şunu vurguladı: TryHackMe platformunda `set q` yerine `--type` parametresi kullanılıyor. Farklı ortamlarda farklı sözdizimi görebilirsiniz. Önemli olan **komutun ne yaptığını** bilmek.

---

## 1.8 — DNS Port Numarası

```
DNS = UDP Port 53
```

**Bilgisayar ↔ Local DNS Server:** UDP Port 53 (hızlı, güvendiğimiz yer)

**DNS Serverlar ↔ Aralarında:** Genellikle TCP Port 53 (güvenilir iletim gerektiği için)

**🏠 Analoji:** Hızlı mesaj atmak için SMS kullan (UDP), önemli belgeleri göndermek için taahhütlü posta kullan (TCP).

---

## 1.9 — Forward ve Reverse DNS Lookup

**Forward Lookup:** Alan adı → IP adresi (normal yön)
```
google.com → 216.58.208.132
```

**Reverse Lookup:** IP adresi → Alan adı (ters yön)
```
216.58.208.132 → google.com
```

Eğitmen: "Bu çok şartlı bir durum, bizim için gerekli bir şey değil." Yani her IP'nin reverse DNS kaydı olmayabilir. Ama bilmek işe yarayabilir.

---

## 1.10 — Domain Kayıt Sistemi: ICANN, Registrar, Reseller

**📊 Hiyerarşi (en üstten en alta):**

```
ICANN
  ↓
Registry Operatörleri (.com, .net, .org yöneticileri)
  ↓
Registrar (GoDaddy, Namecheap, Cloudflare gibi kayıt firmaları)
  ↓
Reseller (yerel aracılar, web hosting firmaları)
  ↓
Registrant (sen - alan adını satın alan kişi/kurum)
```

**ICANN:** İnternetin en üst yönetim kuruluşu. Kar amacı gütmez. Hem alan adı sistemini hem de IP adreslerinin ve port numaralarının dağıtımını yönetir.

**Registry Operatörleri:** `.com`, `.net`, `.org` gibi uzantıları tutan merkezi veritabanını yöneten kuruluşlar.

**Registrar:** ICANN tarafından akredite edilmiş, alan adı satış yetkisi olan firmalar.
- Dünya çapı: **GoDaddy, Namecheap, Squarespace, Cloudflare**
- Türkiye: **Trabis** (kamu kurumu, `.tr` uzantıları için)

**Reseller:** Registrar'lardan yetki alarak aracılık yapan firmalar. Web hosting şirketlerinin çoğu böyledir.

**Registrant:** Alan adını satın alan kişi veya şirket. Aslında satın almak değil, **kiralamak** daha doğru bir ifade. 1 yıllık, 3 yıllık, 5 yıllık kullanım hakkı alınır. Süre bitince yenilemek zorundasın.

**🏠 Analoji:** Sigorta şirketi bayileri gibi. Büyük sigorta firmasının (Registrar = ICANN ile bağlantılı) bayisine (Reseller) gidip poliçeni (alan adını) yaptırırsın.

---

## 1.11 — Ülke Kodu Alan Adları (ccTLD) ve İlginç Örnekler

Eğitmenimiz bu konuda çok eğlenceli örnekler anlattı:

**ccTLD = Country Code Top Level Domain**

Her ülkenin kendi iki harfli uzantısı var:
- Türkiye: `.tr`
- Almanya: `.de`
- Birleşik Krallık: `.uk`
- Amerika: `.us`

**İlginç Örnekler — Küçük Ülkelerin Büyük İşleri:**

Bazı küçük ülkeler kendi uzantılarını, anlam çakışması olan sektörlere satıyor ve iyi paralar kazanıyor:

| Uzantı | Gerçek Sahibi | Kullanan Sektör | Örnek |
|--------|--------------|-----------------|-------|
| `.tv` | **Tuvalu** (küçük ada devleti) | Televizyon kanalları | abc.tv |
| `.ai` | **Anguilla** (Karayip adası) | Yapay Zeka şirketleri | openai.com → açıkça AI |
| `.io` | **İngiliz Hint Okyanusu** | Teknoloji/bulut şirketleri | github.io |
| `.ly` | **Libya** | URL kısaltma servisleri | bit.ly |
| `.co` | **Kolombiya** | Şirket alternatifleri | company yerine .co |

Eğitmen: "Yapay zeka AI uzantısı. AI, Artificial Intelligence diye geçiyor. Ama Anguilla diye küçük bir Karayip adasının uzantısı. Popüler uzantılarından biri haline geldi. Oradan güzel paralar kazandı."

**Türkiye `.tr` uzantısını 1990'da almış.** (Diğer ülkeler 1985'lerden itibaren almaya başlamış.)

---

## 1.12 — Whois Sorgulama ve Güvenlik Riski

**Whois nedir?**

Bir alan adının kimin tarafından, ne zaman kayıt edildiğini, ne zaman süresinin dolacağını gösteren sorgu sistemi.

**Kullanım yöntemleri:**
```
# Web üzerinden
whois.com  → alan adını girerek sorgulayabilirsin
icann.org/lookup  → ICANN'ın kendi sorgu sayfası

# Terminal üzerinden
whois google.com
```

**Eğitmenin dersteki örneği:**
- `google.com` → 1997'de kayıt edilmiş, 14 Eylül 2028'de süresi dolacak
- `netflix.com` → 1997'de kayıt edilmiş, Mark Monitor şirketi kayıt etmiş

**⚠️ Güvenlik Riski:**

Whois sorgusunda çok fazla bilgi çıkabilir: kayıt sahibinin adı, adresi, e-postası, telefonu...

Bu bilgiler açık kaynak (OSINT) olduğu için saldırganlar tarafından kullanılabilir:
- Sosyal mühendislik saldırıları
- Hedefli saldırılar (spear phishing)
- Spam saldırıları
- Alan adı hırsızlığı

**✅ Güvenlik Çözümü — Whois Gizliliği:**

**Domain Privacy** veya **Whois Masking** adı verilen hizmetle kişisel bilgilerini gizleyebilirsin. Bu hizmette Whois'te senin bilgilerin yerine kayıt firmasının (Registrar) bilgileri görünür.

**Eğitmenin tavsiyesi:** "Kişisel bilgilerinizin yerine alan adı kayıt kuruluşunun bilgilerinin bulunması yeterli. GDPR kapsamında da bu değerlendirilmeli."

---

> ### ✅ HATIRLA! — DNS Özeti
> - DNS = İnternetin telefon defteri (isim → IP)
> - Root Server → TLD Server → Otorite Server (hiyerarşi)
> - UDP Port 53 kullanır
> - Cache poisoning = DNS sahtekarlığı
> - Whois gizliliği = kişisel veri koruması

---

## 🧪 KENDİNİ TEST ET — BÖLÜM 1

**Soru 1:** `mail.google.com` adresine gittiğinde DNS çözümleme süreci hangi sırayla ilerler?

**Cevap:** Önce kendi bilgisayarın → Local DNS Server → Root Server → TLD Server → Otorite DNS Server. Bu süreç milisaniyeler içinde tamamlanır.

---

**Soru 2:** MX kaydı ne işe yarar ve neden önemlidir?

**Cevap:** MX (Mail Exchanger) kaydı, bir alan adına gönderilen e-postaların hangi sunucuya iletileceğini belirtir. Bu kayıt olmasa e-postalar doğru sunucuya ulaşamaz. Öncelik değeri (sayı) düşük olan sunucu tercih edilir.

---

**Soru 3:** DNS Spoofing nedir ve nasıl gerçekleşir?

**Cevap:** DNS Spoofing (Cache Poisoning), saldırganın DNS cache'indeki kayıtları sahte IP adresleriyle değiştirmesidir. Kullanıcı doğru alan adını yazdığında sahte siteye yönlendirilerek kimlik bilgileri çalınabilir.

---

# 📚 BÖLÜM 2: TCPDump — Terminalin Wireshark'ı

## 🔗 Önceki Konuyla Bağlantı

Önceki derslerde **Wireshark** ile ağ trafiğini görsel arayüzde incelemiştik. Şimdi aynı işi **komut satırından (terminal)** yapacağız. Neden? Çünkü gerçek hayatta her zaman ekran olmaz. Uzaktan bağlandığın sistemlerde sadece metin ekranı olabilir.

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Bir sisteme uzaktan bağlandın (SSH ile). Sadece siyah bir terminal ekranı var. Wireshark açamazsın. Ama ağ trafiğini incelemen gerekiyor. İşte burada TCPDump devreye giriyor.

---

## 2.1 — TCPDump Nedir?

**TCPDump** = Terminal tabanlı paket yakalama aracı.

- Wireshark gibi ağdaki paketleri yakalar ve analiz eder
- **Ücretsiz ve Açık Kaynak (Free & Open Source)**
- Linux ve macOS'te doğrudan çalışır
- Windows'ta doğrudan çalışmaz; **WinDump** veya resmi sitesinden TCPDump kurulabilir
- Wireshark'ın kullandığı `libpcap` kütüphanesini o da kullanır
- `.pcap` formatında dosya okuyup yazabilir → **Wireshark ile açılabilir!**

**🏠 Analoji:** Wireshark bir CCTV kamera sistemi gibi; renkli, görsel, anlaşılması kolay. TCPDump ise aynı kameranın sadece metin dosyasına yazdığı log kaydı gibi. İkisi de aynı trafiği kaydeder, ama biri görsel, diğeri metin.

---

## 2.2 — Temel Kullanım

```bash
# Sadece tcpdump yazmak başlatır - dinlemeye başlar
tcpdump

# Yardım menüsü
tcpdump --help

# Mevcut ağ arayüzlerini listele
tcpdump -D
```

**Çıkan listede şunları görürsün:**
- `ens5` → Gerçek Ethernet kartı (TryHackMe'de genellikle bu seçilir)
- `lo` → Loopback (localhost, 127.0.0.1)
- `docker0` → Docker sanal ağı
- `any` → Tüm arayüzler

**"up and running" yazanlar:** Şu an aktif ve dinlenebilir durumdalar.

---

## 2.3 — Temel Parametreler

| Parametre | Anlamı | Örnek |
|-----------|--------|-------|
| `-D` | Ağ arayüzlerini listele | `tcpdump -D` |
| `-i <arayüz>` | Hangi arayüzü dinle | `tcpdump -i ens5` |
| `-n` | İsimleri sayıya çevir (localhost→127.0.0.1, http→80) | `tcpdump -n` |
| `-c <sayı>` | Kaç paket yakala, sonra dur | `tcpdump -c 5` |
| `-v` | Verbose - ayrıntılı bilgi | `tcpdump -v` |
| `-vv` | Daha ayrıntılı | `tcpdump -vv` |
| `-w <dosya>` | Dosyaya yaz (.pcap formatında) | `tcpdump -w test.pcap` |
| `-r <dosya>` | Dosyadan oku | `tcpdump -r test.pcap` |
| `-A` | ASCII karakterleri göster | `tcpdump -A` |
| `-X` | Hem ASCII hem hexadecimal göster | `tcpdump -X` |
| `-x` | Sadece hexadecimal göster | `tcpdump -x` |

**⚡ Pratik İpucu:**

Parametreleri birleştirebilirsin:
```bash
tcpdump -i ens5 -n -c 5
# Veya
tcpdump -nic 5 ens5  # (değer gerektiren parametre sonda olmalı)
```

---

## 2.4 — Filtreler

Filtreler, sadece istediğin paketleri görmeni sağlar.

### Protokol Filtreleri

```bash
# Sadece TCP paketleri
tcpdump tcp

# Sadece UDP paketleri
tcpdump udp

# Sadece ICMP paketleri (ping gibi)
tcpdump icmp

# Sadece ARP paketleri
tcpdump arp

# Sadece IPv4
tcpdump ip

# Sadece IPv6
tcpdump ip6
```

### Port Filtreleri

```bash
# Sadece DNS trafiği (Port 53)
tcpdump port 53

# Sadece HTTP trafiği (Port 80)
tcpdump port 80

# Sadece HTTPS trafiği (Port 443)
tcpdump port 443
```

**⚠️ Önemli Fark — Wireshark vs TCPDump:**

Wireshark'ta `http` ya da `https` yazabilirsin. TCPDump'ta bunları yazamazsın. **Port numarasıyla** çözmen gerekir:
- `http` → `port 80`
- `https` → `port 443`
- `dns` → `port 53`

### IP Adresi Filtreleri

```bash
# Belirli bir IP'den gelen veya giden trafik
tcpdump host 192.168.1.1

# Belirli bir ağdan gelen trafik
tcpdump net 192.168.1.0/24

# Sadece kaynak (gönderen) IP
tcpdump src 192.168.1.1

# Sadece hedef (alan) IP
tcpdump dst 192.168.1.1
```

### Mantıksal Operatörler

```bash
# VE (and) - her iki koşul da sağlanmalı
tcpdump -i ens5 icmp and host 10.80.82.4

# VEYA (or) - koşullardan biri sağlanmalı
tcpdump port 80 or port 443

# 10 tane HTTP veya HTTPS paketi yakala
tcpdump -c 10 port 80 or port 443
```

---

## 2.5 — TCPDump Çıktısını Okumak

```
09:34:52.123456 IP 10.80.92.35.34746 > 10.15.0.1.53: UDP, length 32
```

| Kısım | Anlamı |
|-------|--------|
| `09:34:52.123456` | Zaman damgası (sistem saati + milisaniye) |
| `IP` | Protokol |
| `10.80.92.35` | Kaynak IP adresi |
| `34746` | Kaynak port numarası |
| `>` | Yönü gösterir (nereden nereye) |
| `10.15.0.1` | Hedef IP adresi |
| `53` | Hedef port numarası |
| `UDP` | Taşıma protokolü |
| `length 32` | Paketin boyutu (byte) |

**TCP paketlerinde flag'ler de görürsün:**
- `[S]` → SYN (bağlantı başlatma isteği)
- `[A]` → ACK (onay)
- `[F]` → FIN (bağlantı sonlandırma)
- `[R]` → RST (bağlantı sıfırlama)

Eğitmen derste şunu sormak istedi: "Win neydi?" → **Window Size** — "Ben senden bu kadar büyüklükte paket kabul edebilirim" anlamına gelir.

**`-n` parametresi ne değiştirir?**

`-n` olmadan: `localhost > http` (isim olarak gösterir)
`-n` ile: `127.0.0.1 > 80` (sayısal gösterir)

---

## 2.6 — Dosyaya Yazma ve Okuma

```bash
# Yakalanan paketleri dosyaya yaz
tcpdump -i ens5 -w test.pcap

# Dosyayı oku
tcpdump -r test.pcap

# Sadece ICMP paketlerini yakala, 20 tane, kaydet
tcpdump -i ens5 -c 20 icmp -w test1.pcap

# Belirli ağdan gelen ICMP paketleri kaydet
tcpdump -i ens5 net 10.80.0.0/16 and icmp -w kayit.pcap
```

**💡 Önemli:** `-w` ile dosyaya yazarken ekranda bir şey görmezsin. Trafik dosyaya yazılır. Durdurmak için `Ctrl+C` yap. Sonra `-r` ile oku.

**Dosya formatı:** `.pcap` — Wireshark ile de açılabilir! (Çift tıklayınca Wireshark açılır)

---

## 2.7 — Dersteki Pratik Senaryolar

### Senaryo 1: ICMP (Ping) Paketleri Yakalamak

```bash
# ICMP dinlemeye başla
tcpdump -i any icmp

# Başka terminalde ping at
ping 10.80.82.4

# Sonuç: Echo request gönderildi, echo reply geldi/gelmedi
```

Eğitmenin notu: ICMP'nin port numarası yoktur. Çünkü port numaraları Transport katmanında (4. katman) kullanılır. ICMP, Network katmanında (3. katman) çalışır.

### Senaryo 2: DNS Trafiği İzlemek

```bash
tcpdump -i ens5 port 53

# Başka terminalde DNS sorgusu yap
nslookup oaccademy.d

# Sonuç: Query gönderildi, cevap geldi
```

### Senaryo 3: Belirli IP'den Gelen HTTPS Paketleri

```bash
tcpdump -i ens5 host 10.80.94.24 and port 443
```

### Senaryo 4: Bütün Ağdan Gelen ICMP Paketleri

```bash
tcpdump -i ens5 net 10.80.0.0/16 and icmp
```

---

> ### ✅ HATIRLA! — TCPDump Özeti
> - `-D` → Arayüzleri listele
> - `-i` → Hangi arayüz
> - `-n` → Sayısal değerler
> - `-c` → Kaç paket
> - `-w` / `-r` → Yaz / Oku
> - TCPDump = Wireshark'ın terminal versiyonu
> - `.pcap` dosyaları Wireshark'ta da açılır

---

## 🧪 KENDİNİ TEST ET — BÖLÜM 2

**Soru 1:** "ens5 arayüzünde, adres çözümlemesi yapma, 10 tane paket yakala ve sadece DNS sorgularını göster" komutunu yaz.

**Cevap:**
```bash
tcpdump -i ens5 -n -c 10 port 53
```

---

**Soru 2:** TCPDump'ta `http` veya `https` diye filtre yazabilir miyiz? Yazamazsak nasıl yapabiliriz?

**Cevap:** Hayır, Wireshark'ın aksine TCPDump'ta protokol adı yazamayız. Port numarasıyla çözüyoruz: `port 80` (HTTP) veya `port 443` (HTTPS). Ya da her ikisi için: `port 80 or port 443`.

---

**Soru 3:** `-w` parametresiyle kaydedilen `.pcap` dosyası sadece TCPDump'ta mı açılabilir?

**Cevap:** Hayır. `.pcap` dosyaları evrensel bir format. Wireshark, Tshark ve diğer ağ analiz araçlarında da açılabilir.

---

# 📚 BÖLÜM 3: Netstat — Kendi Bağlantı Durumum

## 🔗 Önceki Konuyla Bağlantı

TCPDump ile ağdan geçen tüm trafiği izledik. Netstat ise farklı bir bakış açısı sunar: **Sadece bu bilgisayardaki** bağlantı durumunu gösterir. Hangi port açık? Kim dinliyor? Hangi bağlantı kurulmuş?

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Siber güvenlikte en önemli sorulardan biri: "Bu cihazda hangi portlar açık?" Açık portlar potansiyel giriş noktaları. Güvenlik açığı olan bir servis açık porttan istismar edilebilir. Netstat bu soruyu saniyeler içinde cevaplar.

---

## 3.1 — Netstat Nedir?

**Netstat = Network Statistics** (Ağ İstatistikleri)

- Ağ bağlantılarının durumunu gösterir
- Hem Windows hem Linux hem Unix'te çalışır (Eğitmenin notu: temelde Windows için yapılmış, ama diğerleri de rahatlıkla kullanıyor)
- Terminal/komut satırı aracı

**Temel çıktı başlıkları:**
- `Proto` → Protokol (TCP, UDP vb.)
- `Recv-Q` → Alma kuyruğu (gelen, henüz işlenmemiş paketler)
- `Send-Q` → Gönderme kuyruğu (gönderilmeyi bekleyen paketler)
- `Local Address` → Bu cihazın adresi ve portu
- `Foreign Address` → Karşı tarafın adresi ve portu
- `State` → Bağlantının durumu

---

## 3.2 — Bağlantı Durumları (State'ler)

Bu kısım çok önemli. Her state'in ne anlama geldiğini net bilelim.

### LISTEN (Dinleme)

Soket, gelen bağlantılar için hazır bekliyor. Henüz kimse bağlanmamış.

**🏠 Analoji:** Eğitmenin dersteki analojisi mükemmeldi: "Berko Hocam sen konuşuyorsun şimdi ya da konuşacaksın diye mikrofonu açıyorsun ya. Ben seni dinlemeye hazırlanıyorum. Bu LISTEN."

Yani: Kulağını açmış, bekliyorsun. Henüz ses gelmiyor ama gelirse hazırsın.

### ESTABLISHED (Kurulmuş)

Bağlantı kurulmuş, veri alışverişi yapılıyor.

**🏠 Analoji:** "Established ise, biz zaten seninle konuşuyoruz karşılıklı. Bağlantı kurulmuş yani. Trafik akıyor."

### TIME_WAIT (Bekleme Zamanı)

Bağlantı kapatılmış. Ama sistem kısa bir süre daha bekliyor.

**Neden?** TCP'de bağlantı kapatma süreci: FIN → ACK → FIN → ACK şeklinde. Bu paketlerin hepsi ulaştıktan sonra bile sistem kısa süre bekler. "Yolda kalmış, yeniden iletilmesi gereken paket var mı?" diye kontrol eder.

### CLOSE_WAIT (Kapatma Bekleme)

Karşı taraf bağlantıyı kapattı, senin kapatmanı bekliyor.

**Eğitmenin örneği:** "Ahmet hocamla bağlantı kurdum. Ahmet hocam server, ben istemciyim. Ahmet hocam makineyi kapattı, bağlantıyı sonlandırdı. CLOSE_WAIT ise benim de sonlandırmamı bekliyor."

### SYN_SENT

Sen karşıya SYN paketi gönderdin ve cevap bekliyorsun. (TCP El Sıkışması başladı)

### SYN_RECEIVED

Karşıdan SYN geldi, sen de SYN+ACK gönderdin, karşının ACK'ini bekliyorsun.

---

> ### 🔴 KARMAŞTIRMA! — LISTEN vs ESTABLISHED
>
> | | LISTEN | ESTABLISHED |
> |---|---|---|
> | **Durum** | Hazır, bekliyor | Bağlantı kurulmuş, aktif |
> | **Trafik** | Yok | Var |
> | **Risk** | Yüksek (saldırıya açık) | Normal |
>
> **Eğitmen:** "Bizim için asıl tehlikeli olanlar dinleme modundakiler. Çünkü onlar hazır bekliyor, onlar daha kolay sömürülebilir."

---

## 3.3 — 0.0.0.0 Nedir?

Netstat çıktısında `0.0.0.0:5901` gibi satırlar görürsün. Bu ne demek?

Eğitmenin açıklaması: "0.0.0.0 lokaldeki herhangi bir IP demek."

Yani bu bilgisayarda:
- `lo` (localhost): 127.0.0.1
- `ens5` (Ethernet): 10.80.92.35
- Docker: 172.x.x.x
- vb. birçok interface ve IP var

`0.0.0.0:5901` → "Bu bilgisayardaki TÜM arayüzlerin 5901 portunu dinle" demek.

**🏠 Analoji:** Bir binanın tüm kapılarını aynı anda izleyen güvenlik görevlisi gibi.

---

## 3.4 — Netstat Parametreleri

```bash
# Temel
netstat

# Tüm bağlantılar ve dinlenen portlar
netstat -a

# Sayısal değerler (localhost yerine 127.0.0.1, http yerine 80)
netstat -n

# Hem tümü hem sayısal
netstat -an

# Sadece dinlenen portlar
netstat -l

# Sadece TCP
netstat -t

# Sadece UDP
netstat -u

# Hem TCP hem UDP
netstat -tu

# Hem TCP hem UDP hem dinlenen portlar
netstat -tul  # veya -utl

# Program adı ve PID göster
netstat -p  # Linux'ta

# İstatistikler
netstat -s
```

**💡 Kombinasyonlar mükemmeldir:**

Eğitmenin ders sırasında önerdiği "nümerik, tüm portlar, dinlenenler, program" kombinasyonu:
```bash
netstat -nap  # veya netstat -tlunp
```

---

## 3.5 — PID ve Servis Bağlantısı

`-p` parametresiyle her bağlantının hangi program/servis tarafından kullanıldığını görürsün.

```
Proto  Local Address      Foreign Address  State     PID/Program
TCP    0.0.0.0:5901       0.0.0.0:*        LISTEN    1159/Xvnc
```

Bu bilgi siber güvenlik açısından kritik:
- Hangi servis hangi portu kullanıyor?
- O servisin güvenlik açığı var mı?
- Eski sürümde mi çalışıyor?

Eğitmenin örneği: "Burada PostgreSQL var. Bu SQL servisi eğer out of date ise (eski sürüm), saldırı için güzel bir imkan sunacak."

**PID ne işe yarar?**

PID (Process ID) = Program Kimlik Numarası. Her çalışan program bir PID alır.

```bash
# Bir programı PID ile kapat (Linux'ta)
kill 1159
```

Eğitmen: "Servisi öldürmek. Kill deyip PID numarasını verdiğimizde o servis öldürülecek."

---

## 3.6 — Netstat -s: İstatistik Modu

```bash
netstat -s
```

IP, ICMP, TCP, UDP için bağlantı sayıları, gelen/giden paket istatistikleri gibi detaylı raporlar verir.

---

> ### ✅ HATIRLA! — Netstat Özeti
> - LISTEN = Hazır bekliyor
> - ESTABLISHED = Aktif bağlantı
> - TIME_WAIT = Kapandı, az daha bekliyor
> - 0.0.0.0 = Bu cihazdaki tüm arayüzler
> - `-p` → Hangi program kullanıyor
> - PID → Kill ile servisi kapat

---

## 🧪 KENDİNİ TEST ET — BÖLÜM 3

**Soru 1:** "Tüm TCP ve UDP bağlantıları, sayısal değerlerle, dinlenen portlar dahil, program adıyla göster" komutunu yaz.

**Cevap:**
```bash
netstat -tulnp
```

---

**Soru 2:** Netstat çıktısında LISTEN ve ESTABLISHED arasındaki fark nedir?

**Cevap:** LISTEN: Port açık, bağlantı gelmesini bekliyor, henüz trafik yok. ESTABLISHED: Bağlantı kurulmuş, aktif veri alışverişi yapılıyor.

---

**Soru 3:** Netstat ve TCPDump arasındaki temel fark nedir?

**Cevap:** TCPDump ağdan geçen tüm trafiği yakalar ve içeriğini gösterir. Netstat sadece bu bilgisayardaki bağlantı durumlarını (hangi port açık, hangi servis hangi durumda) gösterir. TCPDump = Ağ trafiği analizi. Netstat = Yerel bağlantı durumu.

---

# 📚 BÖLÜM 4: Network Miner — Adli Bilişim Aracı

## 🔗 Önceki Konuyla Bağlantı

TCPDump ile `.pcap` dosyalarına paket kaydettik. Network Miner bu dosyaları alır ve dedektif gibi analiz eder. Tek tek paketlere bakmak yerine otomatik olarak önemli bilgileri çıkarır.

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Siber güvenlik olayı sonrasında (post-incident): "Bu saldırı nasıl oldu? Ne kadar sürdü? Hangi veriler çalındı?" gibi soruları yanıtlamak için adli bilişim çalışmaları yapılır. Network Miner bu çalışmalarda büyük kolaylık sağlar.

---

## 4.1 — Network Miner Nedir?

- **Açık Kaynak (Open Source)** ağ analiz ve adli bilişim (Network Forensics) aracı
- Wireshark, TCPDump veya Tshark ile yakalanan `.pcap` dosyalarını analiz eder
- **Pasif çalışır** — ağa hiçbir paket göndermez, sadece okur
- Windows üzerinde GUI (grafik arayüz) ile çalışır
- **Ücretsiz sürümü mevcut** — en büyük avantajı bu

**🏠 Analoji:** Wireshark bir film kamerası gibi her şeyi kaydeder. TCPDump metin loglarına yazar. Network Miner ise bu kayıtları alıp dedektif gibi analiz eder: "Burada şüpheli bir şifre geçmiş, burada bir resim aktarılmış, bu IP'den bu IP'ye bağlantı kurulmuş" gibi raporlar çıkarır.

---

## 4.2 — Network Miner Ne Gösterir?

Yüklenen `.pcap` dosyasından otomatik olarak çıkardığı bilgiler:

| Sekme | İçerik |
|-------|--------|
| **Hosts** | Trafikte görülen tüm IP'ler ve bilgileri |
| **Files** | Aktarılan dosyalar (.png, .jpg, .html, .js vb.) |
| **Images** | Trafikten çıkarılan resim dosyaları |
| **Messages** | Oturumlar ve mesajlar |
| **Credentials** | **Şifrelenmemiş protokollerdeki kullanıcı adı ve parolalar!** |
| **Sessions** | Oturum bilgileri |
| **DNS** | DNS sorgulamaları |
| **Parameters** | Parametreler |

**⚠️ En Kritik Özellik — Credentials:**

HTTP gibi şifrelenmemiş protokoller üzerinden geçen kullanıcı adı ve parolaları otomatik olarak tespit eder. Bu yüzden her zaman HTTPS kullanmak hayati önem taşır!

---

## 4.3 — Free vs Professional Sürüm

| Özellik | Free | Professional |
|---------|------|-------------|
| Canlı dinleme | ✅ | ✅ |
| .pcap analizi | ✅ | ✅ |
| .pcapng desteği | ❌ | ✅ |
| IPv6 desteği | Sınırlı | ✅ |
| Fiyat | Ücretsiz | Ücretli |

Eğitmen: "Profesyonel alırsanız fiyatı bulmuşlar. Bizim ilgilendirmiyor. Kurumumuz, çalıştığımız birim bunu alabilir. İhtiyacı varsa kullanabilir."

---

## 4.4 — Adli Bilişimde Kullanım

Eğitmenin anlattığı senaryo:

"Sizin kurumunuz bir siber saldırıya uğradığında, saldırı sonrasında oradaki delilleri toplamak istediğinizde, oradan veri elde edeceksiniz. Bu saldırı neden oldu, nasıl oldu, neden kaynaklandı, ne hata yaptık biz diye. Bununla ilgili bir adli çalışma yapmak istediğimizde, Network Miner sizlere belli konularda yardımcı olacak."

**Network Miner'ın temel prensibi:**
- Ağ trafiğine **müdahale etmez**
- Hiçbir paket **göndermez**
- Sadece mevcut `.pcap` dosyasını **analiz eder**
- Tek tek paket incelemek yerine **otomatik** analiz yapar

---

> ### ✅ HATIRLA! — Network Miner Özeti
> - Adli bilişim (Forensics) aracı
> - .pcap dosyalarını analiz eder
> - Şifrelenmemiş şifreleri otomatik bulur
> - Dosyaları, resimleri, oturumları çıkarır
> - Pasif — ağa paket göndermez
> - Ücretsiz sürümü var

---

## 🧪 KENDİNİ TEST ET — BÖLÜM 4

**Soru 1:** Network Miner ile Wireshark arasındaki temel fark nedir?

**Cevap:** Wireshark tek tek paketleri detaylı gösterir, analist manuel inceleme yapar. Network Miner ise `.pcap` dosyasını alıp otomatik analiz eder: şifreler, dosyalar, resimler, oturumları otomatik ayıklar. Network Miner daha çok adli bilişim amacıyla kullanılır.

---

**Soru 2:** Network Miner neden "pasif araç" olarak tanımlanır?

**Cevap:** Çünkü ağa hiçbir paket göndermez. Sadece mevcut kayıtları (`.pcap` dosyaları) okur ve analiz eder. Bu sayede izlenen ağda şüphe uyandırmaz.

---

**Soru 3:** Credentials sekmesinde ne görürsün ve bu neden önemlidir?

**Cevap:** Şifrelenmemiş protokoller (HTTP gibi) üzerinden geçen kullanıcı adı ve parolaları gösterir. Bu, her zaman HTTPS gibi şifreli protokol kullanmanın önemini gösterir. Saldırgan bu şifreler olmasa yakalayamayacağı kimlik bilgilerine böyle ulaşabilir.

---

# 🗺️ GENEL TEKRAR VE ÖZET

## Tek Cümlelik Özet — Her Konu

| Konu | Tek Cümle Özet |
|------|---------------|
| **DNS** | İnternetteki alan adlarını (google.com) bilgisayarların anladığı IP adreslerine çeviren hiyerarşik bir sistemdir. |
| **TCPDump** | Wireshark'ın terminal versiyonu; ağdaki paketleri komut satırında yakalar, filtreler ve `.pcap` dosyasına kaydeder. |
| **Netstat** | Yerel bilgisayardaki ağ bağlantılarının durumunu (açık portlar, bağlantı durumları, hangi servis ne kullanıyor) gösteren istatistik aracıdır. |
| **Network Miner** | Yakalanan `.pcap` dosyalarını adli bilişim amacıyla otomatik analiz eden, şifrelenmemiş kimlik bilgilerini, dosyaları ve oturumları çıkaran ücretsiz araçtır. |

---

## Büyük Resim — Her Şey Nasıl Bağlanıyor?

```
Bir web sitesine giriyorsun:
   ↓
DNS çözümlemesi → alan adı → IP adresi (UDP port 53)
   ↓
Bağlantı kuruluyor (TCP el sıkışması)
   ↓
Bu trafik ağda akıyor
   ↓
TCPDump veya Wireshark ile yakalanabilir
   ↓
.pcap dosyasına kaydedilebilir
   ↓
Network Miner ile adli analiz yapılabilir
   ↓
Netstat ile bu bilgisayardaki bağlantı durumu izlenebilir
```

---

## 🔑 Kritik Port Numaraları — Aklında Kalsın

| Port | Protokol | Açıklama |
|------|----------|----------|
| 53 | DNS | Domain çözümleme (UDP) |
| 80 | HTTP | Şifresiz web |
| 443 | HTTPS | Şifreli web |
| 22 | SSH | Uzak terminal bağlantısı |
| 25/587 | SMTP | E-posta gönderme |
| 5901 | VNC | Uzak masaüstü |

---

## 📌 Eğitmenin Önemli Uyarıları

1. **"Bütün öğretilen komutları hemen ezberleyeceksiniz diye bir beklentimiz yok."** Zaman içinde pratikle pekişir. Önemli olan neyin ne işe yaradığını bilmek.

2. **Yapay zeka yardımı:** "Yapay zekalar var. Oralarda küçücük bir araştırma yaparak parametreleri öğrenebiliriz."

3. **Farklı platformlar:** TryHackMe'de veya farklı sistemlerde aynı aracın farklı parametreleri olabilir. Esneklik önemli.

4. **DNS ve Root Serverlar:** "İnternetin temel omurgası Amerika'nın elinde. Oradan ne gelip gittiğini takip edebilirler."

5. **Whois gizliliği:** Alan adı kaydederken mutlaka Domain Privacy aktive et.

6. **Şifrelenmemiş protokol tehlikesi:** HTTP üzerinden geçen her şey Network Miner gibi araçlarla okunabilir. Her zaman HTTPS kullan.

---

## 📅 Sıradaki Dersler

Eğitmenin dersin sonunda belirttiğine göre yakında işlenecekler:
- Network Miner ile `.pcap` analizi (TryHackMe odası)
- TCPDump ile ilgili TryHackMe odası çözümü
- Netstat ile ilgili ödev/uygulama
- SSH komutunun ayrıntılı anlatımı
- `traceroute`, `arp`, `dig`, `ss` komutları
- Linux Network komutları tekrarı

---

