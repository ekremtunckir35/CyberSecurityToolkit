# 02 — Network Fundamentals

> Ağ temellerini sıfırdan alıp; OSI/TCP-IP modeli, temel protokoller, paket analizi, ağ cihazları, uzak erişim ve güvenli ağ tasarımı ekseninde yapılandırılmış siber güvenlik ders notları.

---

## 🎯 Amaç

Bu bölüm, network bilgisini yalnızca teorik olarak değil, siber güvenlik operasyonlarında kullanılabilir şekilde öğretmek için hazırlanmıştır.

Odak noktası şudur:

- Ağ trafiği nasıl oluşur?
- Cihazlar birbirleriyle nasıl haberleşir?
- Paketler nasıl analiz edilir?
- Hangi protokol hangi portu kullanır?
- Hangi ağ servisi güvenlik riski oluşturabilir?
- Bir SOC analisti, pentester veya sistem yöneticisi bu bilgiyi nerede kullanır?

---

## 📚 Ders İçeriği

| Ders | Başlık | Ana Konular | Durum |
|---|---|---|:---:|
| 11 | DNS · TCPDump · Netstat · Network Miner | DNS hiyerarşisi, nslookup, tcpdump, netstat, pcap analizi | ✅ |
| 12 | TCPDump · Network Miner · Topoloji · Switch · Router | Paket filtreleme, network forensic, topolojiler, MAC table, routing, IPsec, AP | ✅ |
| 13 | HTTP/HTTPS · URL · Mail Protokolleri | HTTP request/response, status code, SSL/TLS, URL yapısı, SMTP/POP3/IMAP | ✅ |
| 14 | SNMP · NTP · Telnet · SSH · RDP · SMB · FTP · DMZ | Monitoring, zaman senkronizasyonu, uzak erişim, dosya paylaşımı, DMZ | ✅ |

> Not: Markdown arşivindeki diğer Network Fundamentals dersleri eklendikçe bu tablo genişletilecektir.

---

## 🧭 Öğrenme Haritası

```text
Network Fundamentals
│
├── 1. Temel Ağ Mantığı
│   ├── LAN / WAN / Internet
│   ├── IP Address / MAC Address
│   └── Port / Protocol / Service
│
├── 2. Ağ Modelleri
│   ├── OSI Model
│   └── TCP/IP Model
│
├── 3. Temel Protokoller
│   ├── DNS
│   ├── HTTP / HTTPS
│   ├── SMTP / POP3 / IMAP
│   ├── FTP / SFTP
│   ├── SMB
│   ├── SNMP
│   └── NTP
│
├── 4. Trafik Analizi
│   ├── TCPDump
│   ├── Wireshark
│   ├── Network Miner
│   └── .pcap İnceleme
│
├── 5. Ağ Cihazları
│   ├── Switch
│   ├── Router
│   ├── Access Point
│   └── Firewall / DMZ
│
└── 6. Güvenlik Perspektifi
    ├── Cleartext Protocol Riskleri
    ├── Açık Port Analizi
    ├── Credential Exposure
    ├── Legacy Protocol Zafiyetleri
    └── Segmentation / DMZ Tasarımı
```

---

## 🧪 Pratik Araçlar

| Araç | Kullanım Amacı |
|---|---|
| `tcpdump` | Terminal üzerinden paket yakalama |
| `Wireshark` | Grafik arayüzle paket analizi |
| `Network Miner` | `.pcap` dosyalarından forensic analiz |
| `netstat` | Açık port ve bağlantı analizi |
| `nslookup` | DNS kayıt sorgulama |
| `whois` | Domain kayıt bilgisi analizi |
| `ssh` | Güvenli uzak terminal bağlantısı |
| `rdp` | Windows uzak masaüstü bağlantısı |
| `nmap` | Host keşfi, port ve servis tarama |

---

## 🔐 Siber Güvenlik Açısından Kritik Noktalar

### 1. Cleartext protokoller risklidir

Aşağıdaki protokoller şifreleme olmadan kullanıldığında kullanıcı adı, parola veya veri içeriği ağda okunabilir hale gelebilir:

- HTTP
- Telnet
- FTP
- POP3
- IMAP
- SMTP

Güvenli alternatifler:

| Güvensiz | Güvenli Alternatif |
|---|---|
| HTTP | HTTPS |
| Telnet | SSH |
| FTP | SFTP / FTPS |
| POP3 | POP3S |
| IMAP | IMAPS |
| SMTP | SMTPS / SMTP Submission TLS |

---

### 2. Açık port = potansiyel saldırı yüzeyi

Bir sistemde açık olan her port şu sorularla analiz edilmelidir:

- Bu port neden açık?
- Hangi servis çalışıyor?
- Servisin versiyonu güncel mi?
- Dış dünyaya açık olması gerekiyor mu?
- Kimlik doğrulama ve şifreleme var mı?

---

### 3. Paket analizi temel SOC becerisidir

`.pcap` dosyaları ile şunlar incelenebilir:

- Hangi IP hangi IP ile konuşmuş?
- Hangi portlar kullanılmış?
- DNS sorguları neler?
- HTTP request/response içeriği nedir?
- Şifrelenmemiş credential geçmiş mi?
- Anomali var mı?

---

### 4. Zaman senkronizasyonu forensic için kritiktir

NTP çalışmayan sistemlerde log korelasyonu bozulur. Bu da olay müdahalesinde yanlış zaman çizelgesi oluşturur.

```text
Yanlış saat = yanlış olay sırası = zayıf forensic analiz
```

---

### 5. DMZ, public servisleri iç ağdan ayırır

Web, mail ve DNS gibi dış dünyaya açık servisler doğrudan internal network içine konulmamalıdır.

```text
Internet → Firewall → DMZ → Firewall → Internal Network
```

---

## 📌 Kritik Port Listesi

| Port | Protokol | Açıklama |
|---:|---|---|
| 20 | FTP Data | FTP veri aktarımı |
| 21 | FTP Control | FTP komut kanalı |
| 22 | SSH | Güvenli uzak terminal |
| 23 | Telnet | Güvensiz uzak terminal |
| 25 | SMTP | Eski/güvensiz mail gönderme |
| 53 | DNS | Alan adı çözümleme |
| 80 | HTTP | Şifresiz web trafiği |
| 110 | POP3 | Mail alma |
| 123 | NTP | Zaman senkronizasyonu |
| 143 | IMAP | Mail alma/senkronizasyon |
| 161 | SNMP | SNMP sorguları |
| 162 | SNMP Trap | SNMP bildirimleri |
| 443 | HTTPS | Şifreli web trafiği |
| 445 | SMB | Windows dosya/yazıcı paylaşımı |
| 465 | SMTPS | Güvenli SMTP |
| 587 | SMTP Submission | Modern SMTP gönderim |
| 993 | IMAPS | Güvenli IMAP |
| 3389 | RDP | Windows uzak masaüstü |

---

## 📁 Önerilen Klasör Yapısı

```text
02-NETWORK-FUNDAMENTALS/
│
├── README.md
├── notes/
│   ├── ders-11-dns-tcpdump-netstat-networkminer.md
│   ├── ders-12-tcpdump-topology-switch-router.md
│   ├── ders-13-http-https-url-mail-protocols.md
│   └── ders-14-snmp-ntp-remote-access-smb-ftp-dmz.md
│
├── cheat-sheets/
│   ├── ports.md
│   ├── tcpdump.md
│   ├── http-status-codes.md
│   └── protocol-comparison.md
│
└── labs/
    ├── tcpdump-pcap-analysis.md
    ├── wireshark-http-analysis.md
    └── networkminer-forensics.md
```

---

## ✅ Öğrenme Hedefleri

Bu bölümü tamamlayan kişi şunları açıklayabilmelidir:

- DNS çözümleme akışını
- TCPDump ile temel paket yakalamayı
- Netstat ile açık port analizini
- Network Miner ile `.pcap` forensic analizini
- Switch ve router arasındaki farkı
- HTTP request/response yapısını
- HTTP status code gruplarını
- HTTPS, SSL/TLS ve sertifika mantığını
- SMTP, POP3 ve IMAP farklarını
- SNMP ve NTP’nin kurumsal ağdaki rolünü
- Telnet, SSH ve RDP farklarını
- SMB ve FTP güvenlik risklerini
- DMZ tasarımının güvenlik değerini

---

## 🧠 Hızlı Tekrar

```text
DNS     → Alan adını IP adresine çevirir
TCPDump → Paket yakalar
Netstat → Açık bağlantıları gösterir
Switch  → MAC adresiyle LAN içinde iletir
Router  → IP adresiyle ağlar arası yönlendirir
HTTP    → Web iletişimi sağlar
HTTPS   → HTTP'yi şifreler
SMTP    → Mail gönderir
POP3    → Mail indirir
IMAP    → Mail senkronize eder
SNMP    → Ağ cihazlarını izler
NTP     → Saatleri senkronize eder
SSH     → Güvenli uzak terminal sağlar
RDP     → Windows uzak masaüstü sağlar
SMB     → Dosya/yazıcı paylaşımı sağlar
DMZ     → Public servisleri iç ağdan ayırır
```

---

## ⚠️ Yasal ve Etik Kullanım

Bu notlar yalnızca eğitim, kişisel lab, CTF ve yetkili kurumsal test ortamları için hazırlanmıştır.

İzinsiz ağ taraması, servis analizi, credential yakalama veya sisteme bağlanma girişimi hukuki sorumluluk doğurur.

---

## 📚 İlgili Modüller

- [`03-LINUX`](../03-LINUX/) — Linux komut satırı ve sistem yönetimi
- [`07-FIREWALL`](../07-FIREWALL/) — Ağ güvenliği ve trafik kontrolü
- [`09-NETWORK-SCANNING-NMAP`](../09-NETWORK-SCANNING-NMAP/) — Host keşfi ve port tarama
- [`10-METASPLOIT-EXPLOITATION`](../10-METASPLOIT-EXPLOITATION/) — Exploitation mantığı

---

*Lisans: MIT · Yalnızca eğitim amaçlıdır.*
