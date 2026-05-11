# Ağ Temelleri — Ders 14
## HTTP Tekrarı · Mail Protokolleri · SNMP · NTP · Telnet · SSH · RDP · SMB · FTP · DMZ

# 🛡️ AĞ TEMELLERİ
## DERS 14 — UZMAN SİBER GÜVENLİK EĞİTİM NOTU

**HTTP | HTTPS | SMTP | POP3 | IMAP | SNMP | NTP | Telnet | SSH | RDP | SMB | FTP | DMZ**  
**20 Ocak 2026 · Transkript tabanlı kapsamlı ders notu**

---

# 📌 Bu Derste Ne Öğreniyoruz?

| Konu | Ne Yapar? | Neden Önemli? |
|---|---|---|
| HTTP Tekrarı | Web istek/cevap mantığını açıklar | Web güvenliği ve log analizi için temel |
| SMTP | E-posta gönderir | Mail güvenliği ve phishing analizinde gerekir |
| POP3 / IMAP | E-posta alır | Mail istemcisi yapılandırmasını anlamayı sağlar |
| SNMP | Ağ cihazlarını izler/yönetir | Monitoring ve zafiyet analizi için önemlidir |
| NTP | Zaman senkronizasyonu yapar | Log, forensic ve sertifika doğrulamada kritiktir |
| Telnet | Uzak terminal bağlantısı sağlar | Güvensiz olduğu için risk analizi gerekir |
| SSH | Güvenli uzak terminal bağlantısı sağlar | Linux yönetimi ve güvenli erişim için temel |
| RDP | Windows uzak masaüstü sağlar | Windows sistem yönetiminde kullanılır |
| SMB | Dosya/yazıcı paylaşımı sağlar | WannaCry gibi saldırılarla ilişkilidir |
| FTP / SFTP | Dosya transferi sağlar | Güvensiz/güvenli aktarım farkını öğretir |
| DMZ | Dış servisleri iç ağdan ayırır | Kurumsal ağ güvenliği için kritik tasarım alanıdır |

---

# 📚 BÖLÜM 1 — HTTP Tekrarı: Web Trafiğini Anlamak

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

HTTP, web trafiğinin merkezindedir. Siber güvenlikte web uygulaması, log analizi, trafik inceleme, hata kodları ve saldırı tespiti için HTTP’yi temel seviyede bilmek zorundayız.

## 1.1 — HTTP Nedir?

HTTP (Hypertext Transfer Protocol), web sayfalarına erişmek için kullanılan uygulama katmanı protokolüdür.

Web tarayıcı bir istekte bulunur, sunucu cevap döner.

```text
Client → HTTP Request → Server
Client ← HTTP Response ← Server
```

## 1.2 — HTTP Stateless Çalışır

HTTP stateless yani hafızasızdır.

Her istek bağımsız değerlendirilir. Sunucu, önceki isteği doğal olarak hatırlamaz.

## 1.3 — Cookie Neden Var?

Cookie (Çerez), HTTP’nin hafızasızlık problemini azaltır.

Cookie sayesinde:

- Oturum bilgisi saklanır.
- Kullanıcı hatırlanır.
- Login bilgileri korunabilir.
- Sepet ve tercih bilgileri tutulabilir.

## 🏠 Günlük Hayat Analojisi

HTTP stateless ise her defasında seni ilk kez gören güvenlik görevlisi gibidir. Cookie ise sana verilen ziyaretçi kartıdır. Kartı gösterince sistem seni tekrar tanır.

## ⚠️ KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| HTTP | Web iletişim protokolü |
| Stateless | Önceki isteği hatırlamama |
| Cookie | Kullanıcıyı hatırlatan küçük veri |
| Session | Kullanıcının oturum durumu |

## ✅ HATIRLA!

> HTTP hafızasızdır. Cookie, web sitesinin seni hatırlamasını sağlar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
HTTP hangi katmanda çalışır?

**CEVAP:** Application Layer (Uygulama Katmanı).

### ❓ Soru 2
Stateless ne demektir?

**CEVAP:** Her isteğin bağımsız değerlendirilmesi ve önceki durumun tutulmamasıdır.

### ❓ Soru 3
Cookie ne işe yarar?

**CEVAP:** Kullanıcı oturumunu ve tercihlerini hatırlamak için kullanılır.

---

# 📚 BÖLÜM 2 — HTTP Method ve Status Code

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Web güvenliği analizinde hangi isteğin ne yaptığı bilinmelidir. GET, POST, PUT, PATCH ve DELETE farkı bilinmeden web trafiği okunamaz.

## 2.1 — HTTP Methodları

| Method | Ne Yapar? |
|---|---|
| GET | Veri ister |
| POST | Yeni veri gönderir |
| PUT | Mevcut veriyi tamamen günceller |
| PATCH | Verinin bir kısmını günceller |
| DELETE | Veri siler |
| HEAD | Sadece başlık bilgisi ister |
| OPTIONS | Desteklenen methodları sorar |

## 2.2 — HTTP Status Code Grupları

| Kod Grubu | Anlamı |
|---|---|
| 1xx | Bilgilendirme |
| 2xx | Başarılı |
| 3xx | Yönlendirme |
| 4xx | İstemci hatası |
| 5xx | Sunucu hatası |

## Derste Geçen Örnekler

| Kod | Anlamı |
|---|---|
| 200 OK | Başarılı |
| 204 No Content | İçerik yok |
| 304 Not Modified | Değişiklik yok |
| 401 Unauthorized | Yetkisiz |
| 404 Not Found | Sayfa bulunamadı |
| 500 Serisi | Sunucu hatası |

## 🏠 Günlük Hayat Analojisi

Bir restoranda sipariş verdin:

- 200: Sipariş geldi.
- 301/302: Bu ürün başka şubede.
- 404: Menüde böyle ürün yok.
- 500: Mutfakta sorun var.

## ✅ HATIRLA!

> 4xx genelde client tarafı hatadır. 5xx genelde server tarafı hatadır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
GET ne işe yarar?

**CEVAP:** Sunucudan veri almak için kullanılır.

### ❓ Soru 2
404 ne demektir?

**CEVAP:** Sayfa bulunamadı.

### ❓ Soru 3
500’lü hata neyi gösterir?

**CEVAP:** Sunucu tarafında problem olduğunu gösterir.

---

# 📚 BÖLÜM 3 — HTTP/3 ve QUIC

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Modern web trafiğinde artık HTTP/3 ve QUIC görülebilir. Wireshark, browser developer tools veya firewall loglarında QUIC ifadesi karşımıza çıkabilir.

## 3.1 — HTTP/3 Nedir?

HTTP/3, HTTP protokolünün modern versiyonudur.

Önceki HTTP sürümlerinden farklı olarak TCP yerine UDP tabanlı QUIC protokolünü kullanır.

## 3.2 — QUIC Nedir?

QUIC, Google tarafından geliştirilen, UDP üzerinde çalışan, hızlı ve şifreli bir aktarım protokolüdür.

Amaç:

- Daha hızlı bağlantı kurmak
- Gecikmeyi azaltmak
- Varsayılan şifreleme sağlamak

## ⚠️ KARMAŞTIRMA!

| Kavram | Açıklama |
|---|---|
| HTTP/1.1 | TCP kullanır |
| HTTP/2 | TCP + TLS kullanır |
| HTTP/3 | UDP tabanlı QUIC kullanır |
| UDP | Normalde bağlantısızdır |
| QUIC | UDP üzerinde güvenli/hızlı yapı sağlar |

## ✅ HATIRLA!

> HTTP/3 = QUIC + UDP + Şifreleme

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
HTTP/3 hangi taşıma protokolünü temel alır?

**CEVAP:** UDP tabanlı QUIC protokolünü.

### ❓ Soru 2
QUIC neden geliştirilmiştir?

**CEVAP:** Gecikmeyi azaltmak ve bağlantıyı hızlandırmak için.

### ❓ Soru 3
UDP normalde güvenli midir?

**CEVAP:** Hayır. Ancak QUIC, UDP üzerinde güvenli yapı kurar.

---

# 📚 BÖLÜM 4 — SMTP, POP3 ve IMAP

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

E-posta saldırıları siber güvenliğin en yaygın saldırı alanlarından biridir. Phishing, spoofing, credential theft ve mail server zafiyetlerini anlamak için bu protokolleri bilmek gerekir.

## 4.1 — SMTP Nedir?

SMTP (Simple Mail Transfer Protocol), e-posta göndermek için kullanılır.

```text
Kullanıcı → SMTP → Kendi Mail Serverı → SMTP → Alıcının Mail Serverı
```

## SMTP Portları

| Port | Açıklama |
|---|---|
| 25 | Eski/güvensiz SMTP |
| 465 | Güvenli SMTP |
| 587 | Modern önerilen mail gönderme portu |

## 4.2 — POP3 Nedir?

POP3 (Post Office Protocol v3), mail sunucusundan e-postayı cihaza indirir.

Özellikleri:

- Eski modeldir.
- Mail genelde cihaza iner.
- Sunucuda kopya kalmayabilir.
- Çoklu cihaz kullanımı zayıftır.

## 4.3 — IMAP Nedir?

IMAP (Internet Message Access Protocol), e-postaları sunucuda tutar ve cihazlarla senkronize eder.

Özellikleri:

- Mail sunucuda kalır.
- Telefon, tablet, bilgisayar aynı mailbox’ı görür.
- Okundu/silindi bilgisi senkronize olur.
- Modern kullanımda daha uygundur.

## 🏠 Günlük Hayat Analojisi

SMTP: Mektubu postaneye teslim etmek.  
POP3: Mektubu postaneden alıp eve götürmek.  
IMAP: Mektubu postanede tutup her cihazdan aynı kutuya bakmak.

## ⚠️ KARMAŞTIRMA!

| Protokol | Görev |
|---|---|
| SMTP | Mail gönderir |
| POP3 | Mail indirir |
| IMAP | Mail senkronize eder |

## ✅ HATIRLA!

> SMTP gönderir. POP3 indirir. IMAP senkronize eder.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
SMTP ne işe yarar?

**CEVAP:** E-posta göndermek için kullanılır.

### ❓ Soru 2
POP3’ün dezavantajı nedir?

**CEVAP:** Mail cihaza indiği için başka cihazlardan erişim ve senkronizasyon zayıftır.

### ❓ Soru 3
IMAP neden modern kullanımda daha uygundur?

**CEVAP:** Mail ve klasörleri cihazlar arasında senkronize eder.

---

# 📚 BÖLÜM 5 — SNMP: Ağ Cihazlarını İzleme

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Kurumsal ağlarda router, switch, yazıcı, sunucu, IoT cihazları gibi sistemlerin merkezi olarak izlenmesi gerekir. SNMP bu işi yapar.

## 5.1 — SNMP Nedir?

SNMP (Simple Network Management Protocol), ağ cihazlarını izlemek ve bazı durumlarda yönetmek için kullanılan protokoldür.

## 5.2 — SNMP Bileşenleri

| Bileşen | Açıklama |
|---|---|
| SNMP Manager | Merkezi yönetim/izleme sistemi |
| SNMP Agent | Cihaz üzerinde çalışan izleme ajanı |
| Managed Device | Switch, router, sunucu, yazıcı |
| MIB | Cihazın raporlayabileceği veri sözlüğü |
| OID | Belirli bir verinin benzersiz kimliği |

## 5.3 — SNMP Portları

| Port | Açıklama |
|---|---|
| UDP 161 | SNMP sorguları |
| UDP 162 | SNMP Trap bildirimleri |
| 10161 / 10162 | Güvenli SNMP varyantları |

## 5.4 — Gerçek Hayat Araçları

Derste geçen monitoring araçları:

- SolarWinds
- Zabbix
- PRTG
- Grafana

SolarWinds saldırısı da kritik örnek olarak anıldı.

## 🏠 Günlük Hayat Analojisi

SNMP, hastanedeki hasta monitörü gibidir.

- Nabız
- Tansiyon
- Ateş
- Oksijen

Ağda da:

- CPU
- RAM
- Sıcaklık
- Port durumu
- Trafik yoğunluğu

takip edilir.

## ✅ HATIRLA!

> SNMP monitoring için kullanılır. UDP 161 ve 162 portları önemlidir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
SNMP ne işe yarar?

**CEVAP:** Ağ cihazlarını merkezi olarak izlemek ve yönetmek için kullanılır.

### ❓ Soru 2
SNMP Agent nedir?

**CEVAP:** Yönetilen cihaz üzerinde çalışan ve verileri merkeze gönderen yazılımdır.

### ❓ Soru 3
OID nedir?

**CEVAP:** Cihazdaki belirli bir veriyi tanımlayan benzersiz kimliktir.

---

# 📚 BÖLÜM 6 — NTP: Zaman Senkronizasyonu

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Log analizi, forensic, sertifika doğrulama, VPN bağlantısı ve olay inceleme için zaman bilgisinin doğru olması şarttır.

## 6.1 — NTP Nedir?

NTP (Network Time Protocol), cihazların saatlerini merkezi zaman sunucularıyla senkronize eder.

## 6.2 — NTP Portu

```text
UDP 123
```

## 6.3 — NTP Neden Kritik?

- Log zamanları doğru olur.
- Olay sırası net çıkar.
- Sertifika geçerlilik kontrolü doğru çalışır.
- VPN ve kimlik doğrulama hataları azalır.
- Forensic analiz güvenilir olur.

## 6.4 — Stratum Mantığı

NTP katmanlı çalışır.

| Katman | Açıklama |
|---|---|
| Stratum 0 | Atom saati/GPS gibi ana zaman kaynağı |
| Stratum 1 | Doğrudan ana kaynağa bağlı sunucu |
| Stratum 2+ | Üst katmandan zaman alan sistemler |

## Derste Geçen Örnekler

- Windows saat ayarları
- `time.windows.com`
- `time.nist.gov`
- Microsoft NTP sunucuları
- NIST
- Log analizi ve timestamp doğruluğu
- Eski virüslerde sistem saatini değiştirme örnekleri
- Antivirüs deneme süresini sistem saatiyle kandırma örneği

## 🏠 Günlük Hayat Analojisi

NTP okul zilidir.

Tüm sınıfların saati farklıysa ders düzeni bozulur. Tüm cihazların saati farklıysa log analizi bozulur.

## ✅ HATIRLA!

> Log analizi yapacaksan zaman senkronizasyonu şarttır.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
NTP hangi portu kullanır?

**CEVAP:** UDP 123.

### ❓ Soru 2
NTP forensic için neden önemlidir?

**CEVAP:** Olayların doğru zaman sırasına koyulmasını sağlar.

### ❓ Soru 3
Stratum neyi ifade eder?

**CEVAP:** Zaman kaynağına olan katman/uzaklık seviyesini ifade eder.

---

# 📚 BÖLÜM 7 — Telnet: Eski ve Güvensiz Uzak Bağlantı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Telnet artık güvenli kabul edilmez. Ama eski cihazlarda hâlâ bulunabilir. Siber güvenlikte riskli servis olarak tanınmalıdır.

## 7.1 — Telnet Nedir?

Telnet, uzak bir cihaza terminal üzerinden bağlanmak için kullanılan eski bir protokoldür.

## 7.2 — Telnet Portu

```text
TCP 23
```

Bazı sistemlerde `2323` de görülebilir.

## 7.3 — Neden Güvensiz?

Çünkü Telnet verileri clear text yani açık metin olarak iletir.

Bu açık metin içinde:

- Kullanıcı adı
- Parola
- Komutlar
- Cevaplar

görülebilir.

## Derste Geçen Wireshark Örneği

Telnet trafiği incelendiğinde:

- Login bilgisi
- Password bilgisi
- `ping yahoo.com`
- `ls`
- `exit`

gibi komutların açıkça görülebildiği anlatıldı.

## 🏠 Günlük Hayat Analojisi

Telnet, şifresiz telsiz konuşması gibidir. Frekansı dinleyen herkes konuşmayı duyar.

## ✅ HATIRLA!

> Telnet kullanıyorsan, parolanı yolda herkese göstermiş olabilirsin.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
Telnet hangi portu kullanır?

**CEVAP:** TCP 23.

### ❓ Soru 2
Telnet neden güvensizdir?

**CEVAP:** Verileri açık metin olarak taşır.

### ❓ Soru 3
Telnet yerine ne kullanılmalıdır?

**CEVAP:** SSH kullanılmalıdır.

---

# 📚 BÖLÜM 8 — SSH: Güvenli Uzak Terminal

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Linux sistem yönetimi, firewall yönetimi, sunucu erişimi ve siber güvenlik laboratuvarlarında SSH temel araçtır.

## 8.1 — SSH Nedir?

SSH (Secure Shell), uzak bir sisteme güvenli terminal bağlantısı sağlar.

## 8.2 — SSH Portu

```text
TCP 22
```

## 8.3 — SSH Ne Sağlar?

- Şifreli bağlantı
- Güvenli kimlik doğrulama
- Uzak komut çalıştırma
- Dosya transferi
- Linux/Unix sistem yönetimi

## 8.4 — Derste Yapılan Pratik

Eğitmen TryHackMe AttackBox üzerinden kullanıcı oluşturdu:

```bash
adduser oak
```

Sonra SSH bağlantısı gösterildi:

```bash
ssh oak@10.81.102.35
```

Bağlantı sonrası komutlar:

```bash
whoami
ls
ls -a
mkdir supri
exit
```

## 8.5 — SSH ve Çoklu Kullanıcı

SSH ile aynı Linux cihaza birden fazla kişi aynı anda bağlanabilir.

Bağlı kullanıcıları görmek için:

```bash
w
```

## ⚠️ KARMAŞTIRMA!

| Telnet | SSH |
|---|---|
| TCP 23 | TCP 22 |
| Şifresiz | Şifreli |
| Eski | Modern |
| Güvensiz | Güvenli |
| Kullanıcı/parola açıkta kalabilir | Trafik şifrelenir |

## ✅ HATIRLA!

> Telnet eski ve açık metindir. SSH modern ve şifrelidir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
SSH hangi portu kullanır?

**CEVAP:** TCP 22.

### ❓ Soru 2
SSH ile aynı cihaza birden fazla kişi bağlanabilir mi?

**CEVAP:** Evet.

### ❓ Soru 3
`whoami` komutu ne gösterir?

**CEVAP:** Sistemde hangi kullanıcı olarak çalıştığını gösterir.

---

# 📚 BÖLÜM 9 — RDP: Windows Uzak Masaüstü

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Windows sistemlerde uzak masaüstü yönetimi için RDP sık kullanılır. Pentest, blue team, SOC ve sistem yönetiminde bilinmesi gerekir.

## 9.1 — RDP Nedir?

RDP (Remote Desktop Protocol), Microsoft tarafından geliştirilen uzak masaüstü protokolüdür.

## 9.2 — RDP Portu

```text
TCP/UDP 3389
```

## 9.3 — SSH ile RDP Farkı

| Özellik | SSH | RDP |
|---|---|---|
| Arayüz | Terminal | Grafik masaüstü |
| Yaygın ortam | Linux/Unix | Windows |
| Port | 22 | 3389 |
| Kullanım | Komut çalıştırma | Masaüstü yönetimi |

## 9.4 — Derste Yapılan Pratik

Windows cihazdan başka Windows cihaza Remote Desktop Connection ile bağlantı yapıldı.

Gerekli bilgiler:

- IP adresi
- Username
- Password
- Sertifika onayı

## 9.5 — Aynı Anda Kaç Kişi Bağlanabilir?

Standart Windows RDP’de genelde aynı anda tek kullanıcı bağlanır. İkinci kişi bağlanırsa birinci kullanıcı düşebilir.

Windows Server sürümlerinde özel ayarlarla çoklu oturum mümkün olabilir.

## 🏠 Günlük Hayat Analojisi

SSH telefonda teknik komut vermek gibidir. RDP ise karşıdaki bilgisayarın ekranını önüne almak gibidir.

## ✅ HATIRLA!

> RDP görsel masaüstü sağlar. SSH terminal sağlar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
RDP hangi portu kullanır?

**CEVAP:** TCP/UDP 3389.

### ❓ Soru 2
RDP hangi firma tarafından geliştirilmiştir?

**CEVAP:** Microsoft.

### ❓ Soru 3
RDP ile SSH arasındaki temel fark nedir?

**CEVAP:** RDP grafik masaüstü sağlar; SSH terminal bağlantısı sağlar.

---

# 📚 BÖLÜM 10 — SMB: Dosya ve Yazıcı Paylaşımı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

SMB, Windows ağlarında dosya/yazıcı paylaşımının temelidir. Ancak WannaCry gibi büyük saldırılar SMB açıkları üzerinden yayılmıştır.

## 10.1 — SMB Nedir?

SMB (Server Message Block), ağ üzerinde dosya, yazıcı ve kaynak paylaşımı sağlayan protokoldür.

## 10.2 — SMB Portu

```text
TCP 445
```

## 10.3 — Samba Nedir?

Samba, Linux sistemlerin Windows SMB paylaşımıyla uyumlu çalışmasını sağlayan açık kaynak yazılımdır.

## 10.4 — SMB Güvenlik Riski

SMB’nin eski sürümleri ciddi risklidir.

Özellikle:

- SMBv1
- EternalBlue
- WannaCry
- NotPetya / Petya

Derste NSA, Shadow Brokers ve WannaCry saldırılarından bahsedildi.

## 10.5 — Derste Yapılan Paylaşım Örneği

Windows klasörü paylaşıma açıldı:

1. Klasöre sağ tık
2. Properties
3. Sharing
4. Share
5. Everyone ekleme
6. Read veya Read/Write yetkisi verme

Paylaşıma erişim örneği:

```text
\\10.81.148.190\test
```

## 🏠 Günlük Hayat Analojisi

SMB, ofisteki ortak klasör dolabı gibidir.

Herkes okuyabilir ama sadece yetkili kişi dosya ekleyebilir veya silebilir.

## ✅ HATIRLA!

> SMB kullanıyorsan izinleri dikkatli ver. Everyone + Write ciddi risktir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
SMB hangi portu kullanır?

**CEVAP:** TCP 445.

### ❓ Soru 2
WannaCry hangi protokoldeki zafiyetle ilişkilidir?

**CEVAP:** SMBv1 / EternalBlue zafiyetiyle.

### ❓ Soru 3
`Everyone` kullanıcısına Write yetkisi vermek neden risklidir?

**CEVAP:** Herkesin dosya değiştirmesine veya silmesine yol açabilir.

---

# 📚 BÖLÜM 11 — FTP, TFTP ve SFTP

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Dosya transferi ağlarda sık yapılır. Ancak her dosya transfer protokolü güvenli değildir.

## 11.1 — FTP Nedir?

FTP (File Transfer Protocol), dosya transferi için kullanılan eski protokoldür.

## 11.2 — FTP Portları

| Port | Görev |
|---|---|
| TCP 20 | Veri aktarımı |
| TCP 21 | Komut/kontrol |

## 11.3 — FTP Neden Risklidir?

FTP varsayılan olarak şifreleme kullanmaz.

Riskler:

- Kullanıcı adı açıkta kalabilir.
- Parola açıkta kalabilir.
- Dosya içeriği okunabilir.
- Brute force saldırılarına açık olabilir.

## 11.4 — TFTP Nedir?

TFTP (Trivial File Transfer Protocol), UDP tabanlı daha basit dosya transfer protokolüdür.

Daha hızlıdır ama güvenliği daha zayıftır.

## 11.5 — SFTP Nedir?

SFTP, SSH üzerinden güvenli dosya transferi sağlar.

Bu yüzden FTP yerine SFTP tercih edilmelidir.

## ⚠️ KARMAŞTIRMA!

| Protokol | Güvenlik |
|---|---|
| FTP | Güvensiz |
| TFTP | Daha basit ve daha güvensiz |
| SFTP | SSH ile güvenli |
| FTPS | TLS/SSL ile güvenli FTP |

## ✅ HATIRLA!

> FTP açık metin olabilir. SFTP SSH üzerinden güvenli aktarım sağlar.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
FTP hangi portları kullanır?

**CEVAP:** TCP 20 ve TCP 21.

### ❓ Soru 2
TFTP hangi taşıma protokolünü kullanır?

**CEVAP:** UDP.

### ❓ Soru 3
Güvenli dosya transferi için ne tercih edilmelidir?

**CEVAP:** SFTP veya FTPS.

---

# 📚 BÖLÜM 12 — DMZ: İç Ağı Dış Servislerden Ayırmak

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Kurumsal ağlarda web server, mail server, DNS server gibi dış dünyaya açık servisler doğrudan iç ağa konulmaz. DMZ bu ayrımı sağlar.

## 12.1 — DMZ Nedir?

DMZ (Demilitarized Zone), dış dünyaya açık servislerin iç ağdan ayrıldığı yarı güvenli ağ bölgesidir.

## 12.2 — DMZ’de Hangi Servisler Olabilir?

- Web Server
- Mail Server
- DNS Server
- Proxy Server
- Public servisler

## 12.3 — DMZ Mantığı

```text
Internet → Firewall → DMZ → Firewall → Internal Network
```

DMZ, internet ile iç ağ arasında tampon bölge gibi çalışır.

## 🏠 Günlük Hayat Analojisi

Bir AVM düşün.

- Alt kat: Herkesin girebildiği alışveriş alanı = DMZ
- Üst kat: Sadece yetkililerin girebildiği ofis/konut alanı = İç ağ

Herkes AVM’ye girebilir ama herkes ofislere çıkamaz.

Derste Sur Yapı AVM örneği bu mantık için kullanıldı.

## ✅ HATIRLA!

> Public servisleri doğrudan iç ağa koymak ciddi hatadır. DMZ iç ağı koruyan tampon bölgedir.

## 🧪 KENDİNİ TEST ET

### ❓ Soru 1
DMZ ne işe yarar?

**CEVAP:** Dış dünyaya açık servisleri iç ağdan ayırır.

### ❓ Soru 2
DMZ’ye hangi servisler konulabilir?

**CEVAP:** Web, mail, DNS gibi public servisler.

### ❓ Soru 3
DMZ neden güvenlik sağlar?

**CEVAP:** Saldırgan public servise erişse bile doğrudan iç ağa geçmesini zorlaştırır.

---

# 🗺️ GENEL TEKRAR VE ÖZET

## Tek Cümlelik Özet — Her Konu

| Konu | Tek Cümle Özet |
|---|---|
| HTTP | Web istemci-sunucu iletişimini sağlar. |
| HTTP Method | GET, POST, PUT, PATCH, DELETE gibi işlem türlerini belirtir. |
| HTTP Status Code | Sunucunun isteğe verdiği sonucu gösterir. |
| HTTP/3 | UDP tabanlı QUIC ile çalışan modern HTTP sürümüdür. |
| SMTP | E-posta göndermek için kullanılır. |
| POP3 | E-postayı sunucudan cihaza indirir. |
| IMAP | E-postaları cihazlar arasında senkronize eder. |
| SNMP | Ağ cihazlarını merkezi olarak izler ve yönetir. |
| NTP | Cihazların saatini doğru zaman kaynağıyla senkronize eder. |
| Telnet | Eski ve şifresiz uzak terminal protokolüdür. |
| SSH | Güvenli uzak terminal bağlantısı sağlar. |
| RDP | Windows uzak masaüstü bağlantısı sağlar. |
| SMB | Windows ağlarında dosya/yazıcı paylaşımı sağlar. |
| FTP | Eski dosya transfer protokolüdür. |
| SFTP | SSH üzerinden güvenli dosya transferi sağlar. |
| DMZ | Public servisleri iç ağdan ayıran tampon güvenlik bölgesidir. |

---

# Kritik Port Listesi

| Port | Protokol | Açıklama |
|---|---|---|
| 20 | FTP Data | FTP veri aktarımı |
| 21 | FTP Control | FTP komut kanalı |
| 22 | SSH | Güvenli uzak terminal |
| 23 | Telnet | Güvensiz uzak terminal |
| 25 | SMTP | Eski mail gönderme |
| 80 | HTTP | Şifresiz web |
| 110 | POP3 | Mail alma |
| 123 | NTP | Zaman senkronizasyonu |
| 143 | IMAP | Mail alma/senkronizasyon |
| 161 | SNMP | SNMP sorgu |
| 162 | SNMP Trap | SNMP bildirim |
| 443 | HTTPS | Güvenli web |
| 445 | SMB | Dosya/yazıcı paylaşımı |
| 465 | SMTPS | Güvenli SMTP |
| 587 | SMTP Submission | Modern SMTP gönderim |
| 993 | IMAPS | Güvenli IMAP |
| 3389 | RDP | Windows uzak masaüstü |

---

# Eğitmenin Önemli Uyarıları

1. HTTP siber güvenlikte çok merkezi bir protokoldür.
2. Hata kodları log analizinde anlamlı izler verir.
3. HTTP/3 ve QUIC modern trafikte sık görülebilir.
4. SMTP gönderir; POP3/IMAP alır.
5. IMAP modern kullanım için POP3’ten daha uygundur.
6. SNMP monitoring için kullanılır; eski/güvensiz yapılandırmalar risklidir.
7. NTP forensic ve log analizi için kritiktir.
8. Telnet açık metin olduğu için güvenli değildir.
9. SSH güvenli uzak bağlantı için temel araçtır.
10. RDP grafiksel Windows uzak bağlantısı sağlar.
11. SMB eski sürümleri büyük saldırılara zemin hazırlamıştır.
12. FTP yerine SFTP/FTPS tercih edilmelidir.
13. Public servisler DMZ’ye konulmalı, iç ağ doğrudan internete açılmamalıdır.

---

# Sıradaki Derslerde Beklenen Konular

1. Wireshark ile HTTP paket analizi
2. SMTP / POP3 / IMAP paket inceleme
3. FTP ve Telnet trafik analizi
4. SMB güvenlik senaryoları
5. Network CTF çalışması
6. Operating Systems modülüne geçiş
