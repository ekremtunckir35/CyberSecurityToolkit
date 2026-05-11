
<div align="center">

<img src="assets/01-it-to-network-security-overview.png" alt="Network Fundamentals Banner" width="100%"/>

# 02 — Network Fundamentals

> Ağ temellerini sıfırdan alıp; OSI/TCP-IP modeli, temel protokoller, paket analizi,  
> ağ cihazları, uzak erişim ve güvenli ağ tasarımı ekseninde yapılandırılmış siber güvenlik ders notları.

[![14 Ders](https://img.shields.io/badge/Ders-14-blue?style=flat-square)](#-ders-i̇çeriği)
[![Markdown](https://img.shields.io/badge/Format-Markdown-lightgrey?style=flat-square)](#)
[![Dil](https://img.shields.io/badge/Dil-Türkçe-red?style=flat-square)](#)
[![Lisans](https://img.shields.io/badge/Lisans-MIT-green?style=flat-square)](#)

</div>

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

| # | Ders | Başlık | Ana Konular |
|:---:|:---:|---|---|
| 🟢 | [01](notes/01-network-fundamentals-intro.md) | **Ağa Giriş & IT'den Güvenliğe** | IT → Network → Security yolu, temel kavramlar, hash, imza, cloud |
| 🟢 | [02](notes/02-network-internet-protocols-osi.md) | **Network, İnternet & OSI Modeli** | Network nedir, endpoint, internet, protokoller, OSI/TCP-IP modeli |
| 🟢 | [03](notes/03-data-link-ethernet-mac-arp-vlan.md) | **Data Link · Ethernet · MAC · ARP · VLAN** | Data Link Layer, LLC/MAC, Ethernet, ARP, Broadcast/Collision Domain, VLAN |
| 🟢 | [04](notes/04-wireless-network-layer-ipv4.md) | **Wireless LAN & Network Layer & IPv4 Girişi** | Wireless LAN, PDU, Network Layer, IPv4 temelleri |
| 🟢 | [05](notes/05-ipv4-ipv6-nat-subnetting-dhcp.md) | **IPv4 · IPv6 · NAT · Subnetting · DHCP** | IPv4/IPv6 karşılaştırma, NAT, Default Gateway, Subnetting temelleri, DHCP |
| 🟢 | [06](notes/06-subnetting-dhcp-icmp-wireshark.md) | **Subnetting · DHCP · ICMP · Wireshark Girişi** | Subnetting derinlemesine, DHCP akışı, ICMP temelleri, Wireshark tanışma |
| 🟢 | [07](notes/07-icmp-ping-traceroute-wireshark.md) | **ICMP · Ping · Traceroute · Wireshark** | ICMP protokolü, Ping analizi, Traceroute, Wireshark paket yakalama |
| 🟢 | [08](notes/08-icmp-ping-traceroute-transport.md) | **ICMP Derinlemesine & Transport Layer Girişi** | ICMP derinlemesine, Wireshark analizi, TCP/UDP temelleri |
| 🟢 | [09](notes/09-transport-layer-tcp-udp-ports.md) | **Transport Layer · TCP · UDP · Port Kavramı** | Transport Layer, TCP handshake, UDP, port numaraları, soket kavramı |
| 🟢 | [10](notes/10-transport-review-application-dns.md) | **Transport Tekrarı & Application Layer & DNS** | Transport tekrar, Application Layer, DNS hiyerarşisi, DNS kayıt tipleri |
| 🟢 | [11](notes/11-dns-tcpdump-netstat-networkminer.md) | **DNS · TCPDump · Netstat · Network Miner** | DNS derinlemesine, nslookup, tcpdump, netstat, .pcap analizi |
| 🟢 | [12](notes/12-tcpdump-topology-switch-router.md) | **TCPDump · Topoloji · Switch · Router** | Paket filtreleme, network forensic, topolojiler, MAC table, routing, IPsec |
| 🟢 | [13](notes/13-http-https-url-mail-protocols.md) | **HTTP/HTTPS · URL · Mail Protokolleri** | HTTP request/response, status code, SSL/TLS, URL yapısı, SMTP/POP3/IMAP |
| 🟢 | [14](notes/14-snmp-ntp-remote-access-smb-ftp-dmz.md) | **SNMP · NTP · Uzak Erişim · SMB · FTP · DMZ** | Monitoring, zaman senkronizasyonu, Telnet/SSH/RDP, dosya paylaşımı, DMZ |

---

## 🗺️ Ders Görselleri

<table>
<tr>
<td align="center" width="25%">
<a href="notes/01-network-fundamentals-intro.md">
<img src="assets/01-it-to-network-security-overview.png" width="100%"/>
</a>
<b>Ders 01</b><br/>IT'den Network Security'ye
</td>
<td align="center" width="25%">
<a href="notes/02-network-internet-protocols-osi.md">
<img src="assets/02-data-packet-digital-journey.png" width="100%"/>
</a>
<b>Ders 02</b><br/>Network & Internet & OSI
</td>
<td align="center" width="25%">
<a href="notes/03-data-link-ethernet-mac-arp-vlan.md">
<img src="assets/03-data-link-mac-arp-vlan.png" width="100%"/>
</a>
<b>Ders 03</b><br/>Data Link & MAC & ARP
</td>
<td align="center" width="25%">
<a href="notes/04-wireless-network-layer-ipv4.md">
<img src="assets/04-layer2-to-layer3-network-communication.png" width="100%"/>
</a>
<b>Ders 04</b><br/>Wireless & Network Layer
</td>
</tr>
<tr>
<td align="center" width="25%">
<a href="notes/05-ipv4-ipv6-nat-subnetting-dhcp.md">
<img src="assets/05-network-fundamentals-backbone.png" width="100%"/>
</a>
<b>Ders 05</b><br/>IPv4 & IPv6 & NAT
</td>
<td align="center" width="25%">
<a href="notes/06-subnetting-dhcp-icmp-wireshark.md">
<img src="assets/06-ipv4-ipv6-nat-subnetting-dhcp.png" width="100%"/>
</a>
<b>Ders 06</b><br/>Subnetting & DHCP & ICMP
</td>
<td align="center" width="25%">
<a href="notes/07-icmp-ping-traceroute-wireshark.md">
<img src="assets/07-layer3-dhcp-icmp-wireshark.png" width="100%"/>
</a>
<b>Ders 07</b><br/>ICMP & Ping & Traceroute
</td>
<td align="center" width="25%">
<a href="notes/08-icmp-ping-traceroute-transport.md">
<img src="assets/08-packet-analysis-wireshark-network-tools.png" width="100%"/>
</a>
<b>Ders 08</b><br/>Wireshark & Transport Girişi
</td>
</tr>
<tr>
<td align="center" width="25%">
<a href="notes/09-transport-layer-tcp-udp-ports.md">
<img src="assets/09-transport-layer-tcp-udp-ports.png" width="100%"/>
</a>
<b>Ders 09</b><br/>TCP & UDP & Port
</td>
<td align="center" width="25%">
<a href="notes/10-transport-review-application-dns.md">
<img src="assets/10-transport-application-layer-dns.png" width="100%"/>
</a>
<b>Ders 10</b><br/>Application Layer & DNS
</td>
<td align="center" width="25%">
<a href="notes/11-dns-tcpdump-netstat-networkminer.md">
<img src="assets/11-dns-tcpdump-netstat-networkminer.png" width="100%"/>
</a>
<b>Ders 11</b><br/>DNS & TCPDump & Netstat
</td>
<td align="center" width="25%">
<a href="notes/12-tcpdump-topology-switch-router.md">
<img src="assets/12-network-management-topology-switch-router.png" width="100%"/>
</a>
<b>Ders 12</b><br/>Topoloji & Switch & Router
</td>
</tr>
<tr>
<td align="center" width="25%">
<a href="notes/13-http-https-url-mail-protocols.md">
<img src="assets/13-topologies-devices-http-mail-protocols.png" width="100%"/>
</a>
<b>Ders 13</b><br/>HTTP & HTTPS & Mail
</td>
<td align="center" width="25%">
<a href="notes/14-snmp-ntp-remote-access-smb-ftp-dmz.md">
<img src="assets/14-snmp-ntp-remote-access-smb-ftp-dmz.png" width="100%"/>
</a>
<b>Ders 14</b><br/>SNMP & NTP & DMZ
</td>
<td></td>
<td></td>
</tr>
</table>

---

## 🧭 Öğrenme Haritası

```text
Network Fundamentals
│
├── 1. Temel Ağ Mantığı (Ders 01-02)
│   ├── IT → Network → Security
│   ├── LAN / WAN / Internet
│   ├── IP Address / MAC Address
│   └── Port / Protocol / Service
│
├── 2. Ağ Modelleri (Ders 02-03)
│   ├── OSI Model (7 Katman)
│   └── TCP/IP Model (4 Katman)
│
├── 3. Katman 2 — Data Link (Ders 03-04)
│   ├── Ethernet & Frame Yapısı
│   ├── MAC Adresi & ARP
│   ├── VLAN & Segmentasyon
│   └── Wireless LAN (802.11)
│
├── 4. Katman 3 — Network Layer (Ders 04-07)
│   ├── IPv4 & IPv6
│   ├── NAT & Default Gateway
│   ├── Subnetting & CIDR
│   ├── DHCP
│   └── ICMP / Ping / Traceroute
│
├── 5. Katman 4 — Transport Layer (Ders 08-10)
│   ├── TCP & Three-Way Handshake
│   ├── UDP
│   └── Port Numaraları & Soket
│
├── 6. Katman 7 — Application Layer (Ders 10-14)
│   ├── DNS
│   ├── HTTP / HTTPS
│   ├── SMTP / POP3 / IMAP
│   ├── FTP / SFTP
│   ├── SMB
│   ├── SNMP
│   └── NTP
│
├── 7. Trafik Analizi (Ders 08, 11-12)
│   ├── TCPDump
│   ├── Wireshark
│   ├── Network Miner
│   └── .pcap İnceleme
│
├── 8. Ağ Cihazları (Ders 12)
│   ├── Switch (L2 / L3)
│   ├── Router
│   ├── Access Point
│   └── Firewall / DMZ
│
└── 9. Uzak Erişim & Güvenlik (Ders 14)
    ├── Telnet vs SSH
    ├── RDP
    ├── SMB & FTP Riskleri
    ├── Cleartext Protocol Analizi
    └── DMZ Tasarımı
```

---

## 🧪 Pratik Araçlar

| Araç | Kullanım Amacı | İlgili Ders |
|---|---|:---:|
| `tcpdump` | Terminal üzerinden paket yakalama | 08, 11, 12 |
| `Wireshark` | Grafik arayüzle paket analizi | 07, 08 |
| `Network Miner` | `.pcap` dosyalarından forensic analiz | 11, 12 |
| `netstat` | Açık port ve bağlantı analizi | 11 |
| `nslookup` | DNS kayıt sorgulama | 10, 11 |
| `ping` | ICMP echo testi | 07, 08 |
| `traceroute` | Rota izleme | 07, 08 |
| `ssh` | Güvenli uzak terminal bağlantısı | 14 |
| `nmap` | Host keşfi, port ve servis tarama | 09, 14 |

---

## 🔐 Siber Güvenlik Açısından Kritik Noktalar

### 1. Cleartext Protokoller Risklidir

Aşağıdaki protokoller şifreleme olmadan kullanıldığında kullanıcı adı, parola veya veri içeriği ağda okunabilir hale gelir:

| ⚠️ Güvensiz | ✅ Güvenli Alternatif | Port Farkı |
|---|---|---|
| HTTP | HTTPS | 80 → 443 |
| Telnet | SSH | 23 → 22 |
| FTP | SFTP / FTPS | 21 → 22 / 990 |
| POP3 | POP3S | 110 → 995 |
| IMAP | IMAPS | 143 → 993 |
| SMTP | SMTPS / Submission TLS | 25 → 465 / 587 |

---

### 2. Açık Port = Potansiyel Saldırı Yüzeyi

Bir sistemde açık olan her port şu sorularla analiz edilmelidir:

```
✔ Bu port neden açık?
✔ Hangi servis çalışıyor ve versiyonu güncel mi?
✔ Dış dünyaya açık olması gerekiyor mu?
✔ Kimlik doğrulama ve şifreleme var mı?
✔ Default credentials değiştirildi mi?
```

---

### 3. Paket Analizi Temel SOC Becerisidir

`.pcap` dosyaları ile şunlar incelenebilir:

```
→ Hangi IP hangi IP ile konuşmuş?
→ Hangi portlar kullanılmış?
→ DNS sorguları neler?
→ HTTP request/response içeriği nedir?
→ Şifrelenmemiş credential geçmiş mi?
→ C2 (Command & Control) trafiği var mı?
→ Anomali veya port tarama var mı?
```

---

### 4. DMZ Tasarımı

Web, mail ve DNS gibi dış dünyaya açık servisler doğrudan internal network içine konulmamalıdır.

```
Internet ──► Firewall ──► DMZ (Web, Mail, DNS)
                              │
                          Firewall
                              │
                     Internal Network
```

---

## 📌 Kritik Port Referans Listesi

| Port | Protokol | Kategori | Açıklama |
|---:|---|---|---|
| 20 | FTP Data | Dosya Transfer | FTP veri aktarımı |
| 21 | FTP Control | Dosya Transfer | FTP komut kanalı |
| 22 | SSH / SFTP | Uzak Erişim | Güvenli uzak terminal & dosya transfer |
| 23 | Telnet | Uzak Erişim | ⚠️ Güvensiz uzak terminal |
| 25 | SMTP | Mail | ⚠️ Eski/güvensiz mail gönderme |
| 53 | DNS | İsim Çözümleme | Alan adı → IP dönüşümü |
| 67/68 | DHCP | IP Yönetimi | Dinamik IP dağıtımı |
| 80 | HTTP | Web | ⚠️ Şifresiz web trafiği |
| 110 | POP3 | Mail | ⚠️ Mail indirme |
| 123 | NTP | Zaman | Zaman senkronizasyonu |
| 143 | IMAP | Mail | ⚠️ Mail senkronizasyon |
| 161 | SNMP | Monitoring | SNMP sorguları (UDP) |
| 162 | SNMP Trap | Monitoring | SNMP bildirimleri |
| 443 | HTTPS | Web | ✅ Şifreli web trafiği |
| 445 | SMB | Dosya Paylaşımı | Windows dosya/yazıcı paylaşımı |
| 465 | SMTPS | Mail | ✅ Güvenli SMTP |
| 587 | SMTP Submission | Mail | ✅ Modern SMTP gönderim |
| 993 | IMAPS | Mail | ✅ Güvenli IMAP |
| 995 | POP3S | Mail | ✅ Güvenli POP3 |
| 3389 | RDP | Uzak Erişim | Windows uzak masaüstü |

---

## 📁 Klasör Yapısı

```text
02-NETWORK-FUNDAMENTALS/
│
├── README.md                                          ← Bu dosya
│
├── notes/                                             ← Ders notları (14 adet)
│   ├── 01-network-fundamentals-intro.md
│   ├── 02-network-internet-protocols-osi.md
│   ├── 03-data-link-ethernet-mac-arp-vlan.md
│   ├── 04-wireless-network-layer-ipv4.md
│   ├── 05-ipv4-ipv6-nat-subnetting-dhcp.md
│   ├── 06-subnetting-dhcp-icmp-wireshark.md
│   ├── 07-icmp-ping-traceroute-wireshark.md
│   ├── 08-icmp-ping-traceroute-transport.md
│   ├── 09-transport-layer-tcp-udp-ports.md
│   ├── 10-transport-review-application-dns.md
│   ├── 11-dns-tcpdump-netstat-networkminer.md
│   ├── 12-tcpdump-topology-switch-router.md
│   ├── 13-http-https-url-mail-protocols.md
│   └── 14-snmp-ntp-remote-access-smb-ftp-dmz.md
│
└── assets/                                            ← Ders görselleri (14 adet)
    ├── 01-it-to-network-security-overview.png
    ├── 02-data-packet-digital-journey.png
    ├── 03-data-link-mac-arp-vlan.png
    ├── 04-layer2-to-layer3-network-communication.png
    ├── 05-network-fundamentals-backbone.png
    ├── 06-ipv4-ipv6-nat-subnetting-dhcp.png
    ├── 07-layer3-dhcp-icmp-wireshark.png
    ├── 08-packet-analysis-wireshark-network-tools.png
    ├── 09-transport-layer-tcp-udp-ports.png
    ├── 10-transport-application-layer-dns.png
    ├── 11-dns-tcpdump-netstat-networkminer.png
    ├── 12-network-management-topology-switch-router.png
    ├── 13-topologies-devices-http-mail-protocols.png
    └── 14-snmp-ntp-remote-access-smb-ftp-dmz.png
```

---

## ✅ Öğrenme Hedefleri

Bu bölümü tamamlayan kişi şunları açıklayabilmelidir:

**Temel Ağ Kavramları**
- [ ] OSI modelinin 7 katmanını ve her katmanın görevini
- [ ] TCP/IP modelini ve OSI ile farkını
- [ ] IP adresi, MAC adresi ve port kavramlarını

**Katman 2-3 Protokolleri**
- [ ] Ethernet frame yapısını ve ARP çalışma mantığını
- [ ] IPv4 ve IPv6 farkını, NAT mekanizmasını
- [ ] Subnetting hesaplamalarını (/24, /25, CIDR)
- [ ] DHCP DORA sürecini

**Trafik Analizi**
- [ ] TCPDump ile temel paket yakalamayı
- [ ] Netstat ile açık port analizini
- [ ] Network Miner ile `.pcap` forensic analizini
- [ ] Wireshark'ta HTTP, DNS ve TCP trafiği okumayı

**Uygulama Katmanı Protokolleri**
- [ ] DNS çözümleme akışını (recursive / iterative)
- [ ] HTTP request/response yapısını ve status code gruplarını
- [ ] HTTPS, SSL/TLS ve sertifika mantığını
- [ ] SMTP, POP3 ve IMAP farklarını
- [ ] SNMP ve NTP'nin kurumsal ağdaki rolünü

**Ağ Cihazları ve Güvenlik**
- [ ] Switch ve router arasındaki farkı
- [ ] Telnet, SSH ve RDP farklarını
- [ ] SMB ve FTP güvenlik risklerini
- [ ] DMZ tasarımının güvenlik değerini

---

## 🧠 Hızlı Tekrar Kartı

```
OSI Model      → 7 katmanlı referans modeli
TCP/IP Model   → 4 katmanlı uygulama modeli
MAC Address    → Fiziksel adres, L2'de çalışır
IP Address     → Mantıksal adres, L3'te çalışır
ARP            → IP adresini MAC adresine çevirir
DNS            → Alan adını IP adresine çevirir
DHCP           → Otomatik IP atama protokolü
NAT            → Özel IP'leri genel IP'ye çevirir
ICMP           → Ağ tanılaması (ping, traceroute)
TCP            → Güvenilir, bağlantı tabanlı taşıma
UDP            → Hızlı, bağlantısız taşıma
TCPDump        → Terminal paket yakalama aracı
Wireshark      → Grafik paket analiz aracı
HTTP           → ⚠️ Şifresiz web iletişimi
HTTPS          → ✅ SSL/TLS ile şifreli web iletişimi
SMTP           → Mail gönderme protokolü
POP3           → Mail indirme protokolü
IMAP           → Mail senkronizasyon protokolü
Switch         → MAC adresiyle LAN içinde iletir
Router         → IP adresiyle ağlar arası yönlendirir
SSH            → ✅ Güvenli uzak terminal
Telnet         → ⚠️ Güvensiz uzak terminal
RDP            → Windows uzak masaüstü (port 3389)
SMB            → Windows dosya/yazıcı paylaşımı
FTP            → ⚠️ Güvensiz dosya transfer
SFTP           → ✅ SSH üzerinden güvenli dosya transfer
SNMP           → Ağ cihazı izleme protokolü
NTP            → Saat senkronizasyon protokolü
DMZ            → Public servisleri iç ağdan ayırır
```

---

## 📚 İlgili Modüller

| Modül | Bağlantı | İlişki |
|---|---|---|
| 03 — Linux | [`../03-LINUX/`](../03-LINUX/) | Komut satırı araçları (tcpdump, netstat, ssh) |
| 07 — Firewall | [`../07-FIREWALL/`](../07-FIREWALL/) | Ağ güvenliği ve trafik kontrolü |
| 09 — Nmap | [`../09-NETWORK-SCANNING-NMAP/`](../09-NETWORK-SCANNING-NMAP/) | Host keşfi ve port tarama |
| 10 — Metasploit | [`../10-METASPLOIT-EXPLOITATION/`](../10-METASPLOIT-EXPLOITATION/) | Exploitation ve zayıf protokol sömürüsü |

---

## ⚠️ Yasal ve Etik Kullanım

> Bu notlar yalnızca **eğitim**, **kişisel lab**, **CTF** ve **yetkili kurumsal test** ortamları için hazırlanmıştır.
>
> İzinsiz ağ taraması, servis analizi, credential yakalama veya sisteme bağlanma girişimi **hukuki sorumluluk** doğurur.

---

<div align="center">

*Lisans: MIT · Yalnızca eğitim amaçlıdır.*

</div>
