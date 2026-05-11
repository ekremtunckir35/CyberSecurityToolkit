# Ağ Temelleri — Ders 12

<div align="center">

![Ders İnfografiği](../assets/12-network-management-topology-switch-router.png)

</div>

---

## TCPDump · Network Miner · Netstat · Network Topolojileri · Switch · Router · Access Point

# 🛡️ AĞ TEMELLERİ
## DERS 12 — UZMAN SİBER GÜVENLİK EĞİTİM NOTU

**TCPDump | Network Miner | Netstat | Topoloji | Switch | Router | IPsec | Access Point**  
---

# 📌 Bu Derste Ne Öğreniyoruz?

Bu derste ağ trafiğini yakalama, analiz etme, bağlantı durumlarını görme ve ağ cihazlarının çalışma mantığı işlendi.

| Konu | Ne Yapar? | Neden Önemli? |
|---|---|---|
| TCPDump | Terminalde paket yakalar | Grafik arayüz olmayan sistemlerde trafik analizi sağlar |
| Network Miner | `.pcap` dosyalarını adli analiz eder | Saldırı sonrası delil çıkarır |
| Netstat | Açık bağlantıları ve portları gösterir | Backdoor ve şüpheli servisleri tespit etmeye yardım eder |
| Network Topolojileri | Ağın fiziksel/mantıksal yerleşimini açıklar | Doğru ağ tasarımı için temel bilgidir |
| Switch | Aynı ağdaki cihazları bağlar | MAC tablosu ve VLAN mantığını anlamayı sağlar |
| Router | Farklı ağları birbirine bağlar | İnternete çıkış, NAT, VPN ve routing için kritiktir |
| IPsec | IP trafiğini güvenli hale getirir | VPN tünellerinin temel güvenlik mekanizmalarındandır |
| Access Point | Kablolu ağı kablosuz yayına çevirir | Wi-Fi altyapısı ve kablosuz güvenlik için gereklidir |

---

# 📚 BÖLÜM 1 — Komutlara Aşinalık: Ezber Değil, Mantık

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Siber güvenlikte her komutun tüm parametrelerini ezberlemek gerçekçi değildir. Önemli olan komutun **ne işe yaradığını**, **hangi durumda kullanılacağını** ve gerektiğinde nasıl araştırılacağını bilmektir.

Eğitmenin ana mesajı şudur:

> “Komutların tüm parametrelerini ezberlemenizi beklemiyoruz. Ama ihtiyaç olduğunda notlarınıza bakıp kullanabilir durumda olmalısınız.”

## 1.1 — Linux, Windows ve macOS Ortamlarına Aşinalık

Bir güvenlik uzmanı farklı işletim sistemleriyle karşılaşır:

- Windows
- Linux
- macOS
- Sanal makineler
- AttackBox / TryHackMe ortamları
- Sunucu sistemleri

Her ortama tamamen hâkim olmak zorunda değilsin. Ama yabancı kalmamalısın.

## 🏠 Günlük Hayat Analojisi

Yeni bir arabaya bindiğini düşün. Marka değişebilir: Toyota, BMW, Renault. Ama temel mantık aynıdır: direksiyon, fren, gaz, vites ve gösterge paneli.

İşletim sistemleri de böyledir. Menü ve komutlar değişebilir ama mantık benzer kalır.

## ⚠️ KARMAŞTIRMA!

| Kavram | Yanlış Düşünce | Doğru Anlam |
|---|---|---|
| Komut bilmek | Her parametreyi ezberlemek | Komutun amacını bilmek |
| Linux bilmek | Tüm Linux’u ezberlemek | Terminale ve temel araçlara aşina olmak |
| Araştırmak | Bilgisizlik göstergesi | Profesyonel çalışma yöntemi |

## ✅ HATIRLA!

- Ezber değil, mantık önemlidir.
- Komutun ne yaptığını bilmek, parametreyi araştırmaktan daha değerlidir.
- Not tutmak uzun vadede teknik refleks kazandırır.

## 🧪 KENDİNİ TEST ET — Bölüm 1

### ❓ Soru 1
Bir komutun tüm parametrelerini ezberlemek zorunda mıyız?

**CEVAP:** Hayır. Komutun ne işe yaradığını bilmek ve gerektiğinde araştırarak kullanmak yeterlidir.

### ❓ Soru 2
Linux neden siber güvenlikte önemlidir?

**CEVAP:** Çünkü birçok güvenlik aracı, sunucu ve CTF ortamı Linux tabanlıdır.

### ❓ Soru 3
Komut satırı neden önemlidir?

**CEVAP:** Çünkü her ortamda grafik arayüz olmayabilir. Terminal üzerinden analiz yapabilmek gerekir.

---

# 📚 BÖLÜM 2 — TCPDump: Terminalde Paket Yakalama

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Her zaman Wireshark açabileceğin grafik bir sistem olmayabilir. SSH ile bağlandığın bir Linux sunucusunda sadece terminal vardır. Böyle durumlarda TCPDump kullanılır.

## 2.1 — TCPDump Nedir?

TCPDump, ağ paketlerini terminal üzerinden yakalayan bir araçtır.

Temel komut:

```bash
tcpdump
```

Bu komut, varsayılan ağ arayüzündeki trafiği yakalamaya başlar.

## 🏠 Günlük Hayat Analojisi

TCPDump, yol kenarındaki trafik kamerası gibidir.

- Hangi araç geçti?
- Nereden geldi?
- Nereye gidiyor?
- Ne kadar veri taşıyor?

TCPDump da ağdaki paketleri böyle izler.

## 2.2 — Interface Listeleme

```bash
tcpdump -D
```

Bu komut sistemdeki ağ arayüzlerini listeler.

Örnek arayüzler:

- Docker interface
- ens5
- loopback
- virtual ethernet
- Bluetooth interface

## 2.3 — Belirli Arayüzü Dinleme

```bash
tcpdump -i any
```

Tüm arayüzleri dinler.

```bash
tcpdump -i ens5
```

Sadece `ens5` arayüzünü dinler.

## 2.4 — Belirli Sayıda Paket Yakalama

```bash
tcpdump -i any -c 5
```

Sadece 5 paket yakalar ve durur.

## 2.5 — Sayısal Gösterim

```bash
tcpdump -i any -n
```

İsim çözümlemesi yapmadan IP ve portları sayısal gösterir.

Örneğin:

- `http` yerine `80`
- `domain` yerine `53`

## ⚠️ Önemli Not

Linux’ta ana komut başta olur:

```bash
tcpdump -i any -n -c 5
```

Ama parametrelerin sırası, değer gerektirip gerektirmediğine göre değişebilir.

## ✅ HATIRLA!

- `tcpdump` paket yakalar.
- `-D` arayüzleri listeler.
- `-i` hangi arayüzü dinleyeceğini belirtir.
- `-c` kaç paket yakalayacağını belirtir.
- `-n` isim çözümlemesini kapatır.

## 🧪 KENDİNİ TEST ET — Bölüm 2

### ❓ Soru 1
Tüm arayüzleri dinlemek için hangi komut kullanılır?

**CEVAP:**

```bash
tcpdump -i any
```

### ❓ Soru 2
Sadece 5 paket yakalamak için hangi parametre kullanılır?

**CEVAP:** `-c 5`

### ❓ Soru 3
`-n` parametresi ne işe yarar?

**CEVAP:** İsim çözümlemesi yapmadan IP ve portları sayısal gösterir.

---

# 📚 BÖLÜM 3 — TCPDump Filtreleri

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Ağ trafiği çok yoğundur. Tüm paketleri izlemek yerine sadece ihtiyacımız olan paketleri filtrelemek gerekir.

## 3.1 — Protokol Filtreleri

```bash
tcpdump -i any icmp
```

Sadece ICMP paketlerini gösterir.

```bash
tcpdump -i any arp
```

Sadece ARP paketlerini gösterir.

```bash
tcpdump -i any udp
```

Sadece UDP paketlerini gösterir.

```bash
tcpdump -i any tcp
```

Sadece TCP paketlerini gösterir.

## 3.2 — IP Filtreleri

```bash
tcpdump -i any host 10.82.115.13
```

Bu IP ile ilgili tüm paketleri gösterir.

```bash
tcpdump -i any src 10.82.115.13
```

Kaynak IP bu olan paketleri gösterir.

```bash
tcpdump -i any dst 10.82.115.13
```

Hedef IP bu olan paketleri gösterir.

## 3.3 — Port Filtreleri

```bash
tcpdump -i any port 53
```

DNS trafiğini gösterir.

```bash
tcpdump -i any src port 53
```

Kaynak portu 53 olan paketleri gösterir.

```bash
tcpdump -i any dst port 53
```

Hedef portu 53 olan paketleri gösterir.

## 🏠 Günlük Hayat Analojisi

Trafik kamerasının sadece kırmızı arabaları göstermesini düşün. TCPDump filtresi de ağdaki sadece istediğin trafiği gösterir.

## ⚠️ KARMAŞTIRMA!

| Filtre | Anlamı |
|---|---|
| `host` | Kaynak veya hedef IP olabilir |
| `src` | Sadece kaynak |
| `dst` | Sadece hedef |
| `port` | Kaynak veya hedef port |
| `src port` | Sadece kaynak port |
| `dst port` | Sadece hedef port |

## ✅ HATIRLA!

- DNS genellikle port 53 kullanır.
- ICMP’nin port numarası yoktur.
- `host` iki yönlüdür.
- `src` ve `dst` tek yönlü filtreleme yapar.

## 🧪 KENDİNİ TEST ET — Bölüm 3

### ❓ Soru 1
DNS trafiğini yakalamak için hangi komut kullanılabilir?

**CEVAP:**

```bash
tcpdump -i any port 53
```

### ❓ Soru 2
Sadece hedef IP’ye göre filtrelemek için hangi ifade kullanılır?

**CEVAP:** `dst`

### ❓ Soru 3
`src port 53` ne demektir?

**CEVAP:** Kaynak portu 53 olan paketleri gösterir.

---

# 📚 BÖLÜM 4 — Paketleri Dosyaya Yazma ve Okuma

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Canlı trafik her zaman o anda analiz edilemeyebilir. Paketleri dosyaya kaydedip daha sonra Wireshark veya Network Miner ile incelemek gerekir.

## 4.1 — Dosyaya Yazma

```bash
tcpdump -i any -c 5 -w test.pcap
```

Bu komut 5 paket yakalar ve `test.pcap` dosyasına yazar.

## 4.2 — Dosyadan Okuma

```bash
tcpdump -r test.pcap
```

Bu komut daha önce kaydedilmiş `.pcap` dosyasını okur.

## 🏠 Günlük Hayat Analojisi

Canlı kamera görüntüsünü kaydedip sonra tekrar izlemek gibidir.

## ✅ HATIRLA!

- `-w` dosyaya yazar.
- `-r` dosyadan okur.
- `.pcap` dosyaları Wireshark ve Network Miner ile açılabilir.

## 🧪 KENDİNİ TEST ET — Bölüm 4

### ❓ Soru 1
Paketleri dosyaya yazmak için hangi parametre kullanılır?

**CEVAP:** `-w`

### ❓ Soru 2
Paket dosyasını okumak için hangi parametre kullanılır?

**CEVAP:** `-r`

### ❓ Soru 3
`.pcap` dosyası hangi araçlarla açılabilir?

**CEVAP:** TCPDump, Wireshark, Tshark ve Network Miner.

---

# 📚 BÖLÜM 5 — Network Miner: Ağ Adli İnceleme Aracı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Bir saldırı olduktan sonra şu sorulara cevap ararız:

- Saldırı nereden geldi?
- Hangi cihazlar konuştu?
- Hangi dosyalar aktarıldı?
- Kullanıcı adı/parola geçti mi?
- Hangi DNS sorguları yapıldı?
- Trafikte anomali var mı?

Network Miner bu soruları cevaplamaya yardım eder.

## 5.1 — Network Miner Nedir?

Network Miner, açık kaynaklı bir network forensic aracıdır.

Yani ağ trafiği üzerinden adli inceleme yapar.

## 5.2 — Derste Geçen Özel Bilgiler

- Firma: **Netresec**
- Araç: **Network Miner**
- Açıklama: **Open Source Network Forensic Tool**
- Ücretsiz sürümü vardır.
- Corporate/Professional sürümü ücretlidir.
- Eğitmen 1300 dolarlık lisans ücretinden bahsetti.
- TryHackMe odası üzerinden pratik yapılacağı söylendi.
- 1.6.1, 2.7.2 ve 3.1 sürümlerinden bahsedildi.
- 3.1 sürümünün 1 Aralık 2025’te çıktığı söylendi.

## 5.3 — Network Miner Sekmeleri

| Sekme | Ne Gösterir? | Güvenlik Önemi |
|---|---|---|
| Hosts | Trafikteki IP ve cihaz bilgileri | Yüksek |
| Files | Aktarılan dosyalar | Yüksek |
| Images | Trafikten çıkarılan görseller | Orta |
| Messages | Mesaj içerikleri | Orta |
| Credentials | Kullanıcı adı/parola bilgileri | Kritik |
| Sessions | Oturum bilgileri | Yüksek |
| DNS | DNS sorguları | Yüksek |
| Parameters | HTTP parametreleri | Orta |
| Anomalies | Normal dışı durumlar | Kritik |

## 5.4 — Derste Açılan Örnekler

Eğitmen farklı `.pcap` dosyaları açtı:

- Exercise Files
- Case 1
- Case 2
- 4 numaralı pcap dosyası

Örneklerde:

- Linux host tespit edildi.
- Windows NT 4.0 benzeri sistem görüldü.
- SAMR ve ISARPC dosyaları görüldü.
- `Administrator` kullanıcısı yakalandı.
- `Spring 2015` parolası örnek olarak görüldü.
- DNS sorguları incelendi.
- Anomaly sekmesinde normal dışı frame tespit edildi.

## 🏠 Günlük Hayat Analojisi

Network Miner, olay yeri inceleme ekibi gibidir.

Wireshark tüm kamera kaydını verir. Network Miner ise der ki:

- “Şu kişi içeri girmiş.”
- “Şu dosya taşınmış.”
- “Şu parola açıkta geçmiş.”
- “Şu IP şüpheli davranmış.”

## ⚠️ KRİTİK — Credentials Sekmesi

Eğer trafik şifrelenmemişse, kullanıcı adı ve parolalar Network Miner ile görülebilir.

Bu yüzden:

- HTTP yerine HTTPS kullanılmalı.
- Telnet yerine SSH tercih edilmeli.
- FTP yerine SFTP/FTPS kullanılmalı.

## ✅ HATIRLA!

- Network Miner adli analiz aracıdır.
- `.pcap` dosyalarından bilgi çıkarır.
- Credentials sekmesi çok kritiktir.
- Saldırı sonrası hasar tespiti için kullanılır.

## 🧪 KENDİNİ TEST ET — Bölüm 5

### ❓ Soru 1
Network Miner ne işe yarar?

**CEVAP:** `.pcap` dosyalarını analiz ederek host, dosya, credential, DNS ve oturum bilgilerini çıkarır.

### ❓ Soru 2
Credentials sekmesi neden kritiktir?

**CEVAP:** Şifrelenmemiş trafikte geçen kullanıcı adı ve parolaları gösterebilir.

### ❓ Soru 3
Network Miner hangi alanda kullanılır?

**CEVAP:** Network Forensics, yani ağ adli bilişim alanında.

---

# 📚 BÖLÜM 6 — Netstat: Sistemde Hangi Bağlantılar Var?

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Bir sistemde açık portlar ve çalışan bağlantılar saldırı yüzeyini gösterir. Netstat, cihazın hangi portları dinlediğini ve hangi bağlantıların aktif olduğunu gösterir.

## 6.1 — Netstat Nedir?

Netstat = Network Statistics.

Ağ bağlantılarını, portları, servisleri ve PID bilgilerini gösterir.

## 6.2 — Derste Geçen Komutlar

```bash
netstat -pltn
```

| Parametre | Anlamı |
|---|---|
| `p` | Program/PID gösterir |
| `l` | Listening portları gösterir |
| `t` | TCP bağlantılarını gösterir |
| `n` | Sayısal gösterim yapar |

```bash
netstat -patu
```

TCP ve UDP bağlantılarını gösterir.

## 6.3 — Bağlantı Durumları

| State | Anlamı |
|---|---|
| LISTEN | Port bağlantı bekliyor |
| ESTABLISHED | Bağlantı kurulmuş |
| TIME_WAIT | Bağlantı kapanma sürecinde |
| CLOSE_WAIT | Karşı taraf kapattı, bizim sistem bekliyor |

## 6.4 — Siber Güvenlikte Kullanımı

Netstat ile şunları ararız:

- Bilinmeyen servis
- Şüpheli açık port
- Beklenmeyen outbound bağlantı
- Backdoor ihtimali
- Yetkisiz uzak bağlantı

Örnek: Eğitmen `Python 3.8`, `Xvnc`, `BADR` gibi servislerden bahsetti. Bilinmeyen servisler araştırılmalıdır.

## 🏠 Günlük Hayat Analojisi

Netstat, binadaki açık kapıları ve hangi kapıda kimin beklediğini gösteren güvenlik panelidir.

## ✅ HATIRLA!

> Bilmediğin açık port, araştırılması gereken risktir.

## ⚠️ KARMAŞTIRMA!

| Araç | Görev |
|---|---|
| TCPDump | Trafikteki paketleri yakalar |
| Netstat | Cihazdaki bağlantı durumlarını gösterir |
| Network Miner | Yakalanmış trafiği adli analiz eder |

## 🧪 KENDİNİ TEST ET — Bölüm 6

### ❓ Soru 1
LISTEN ne demektir?

**CEVAP:** Port bağlantı bekliyor demektir.

### ❓ Soru 2
ESTABLISHED ne demektir?

**CEVAP:** Bağlantı kurulmuş ve veri akışı var demektir.

### ❓ Soru 3
Netstat siber güvenlikte neden önemlidir?

**CEVAP:** Açık portları, aktif bağlantıları ve şüpheli servisleri görmeyi sağlar.

---

# 📚 BÖLÜM 7 — Network Topolojileri

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Ağ cihazlarının nasıl bağlandığını bilmeden güvenli ağ tasarlanamaz. Topoloji, ağın fiziksel ve mantıksal haritasıdır.

## 7.1 — Network Topology Nedir?

Network topolojisi, cihazların ağ içinde nasıl yerleştiğini ve birbirine nasıl bağlandığını gösterir.

## 🏠 Günlük Hayat Analojisi

Bir şehirde yolların düzenini düşün:

- Bazı yollar tek hat gider.
- Bazıları kavşakta birleşir.
- Bazıları halka şeklindedir.
- Bazılarında her mahalle birbirine bağlıdır.

Ağ topolojisi de cihazların yol haritasıdır.

## 7.2 — Point-to-Point Topoloji

İki cihazın doğrudan birbirine bağlanmasıdır.

Örnekler:

- Bilgisayar ↔ Yazıcı
- Bilgisayar ↔ Endüstriyel cihaz
- Bilgisayar ↔ Bilgisayar

Derste eğitmen, endüstriyel boyama bilgisayarlarından bahsetti. Ethernet kablosuyla bu cihazlara program atılabildiğini anlattı.

## 7.3 — Bus Topoloji

Tek ana hat üzerine cihazların bağlanmasıdır.

Kullanılan yapılar:

- Koaksiyel kablo
- T-Connector
- BNC Connector

Günümüzde yaygın değildir.

## 7.4 — Ring Topoloji

Cihazların halka şeklinde bağlanmasıdır.

Token Ring mantığı vardır. Sırası gelen cihaz hattı kullanır.

## 7.5 — Star Topoloji

Günümüzde en yaygın kullanılan topolojidir.

Ortada switch bulunur. Tüm cihazlar switch’e bağlanır.

## 7.6 — Tree Topoloji

Birden fazla star topolojinin birleşmesidir.

Örnek:

3 katlı okul:

- Her katta bir laboratuvar
- Her laboratuvarda bir switch
- Switch’ler birbirine bağlı

## 7.7 — Mesh Topoloji

Her cihazın diğer cihazlara doğrudan bağlı olduğu topolojidir.

Avantajları:

- Çok yüksek yedeklilik
- Hızlı veri aktarımı
- Alternatif yollar fazla

Dezavantajları:

- Çok maliyetli
- Kurulumu zor
- Çok kablo ve port gerekir

## 7.8 — Hybrid Topoloji

Birden fazla topolojinin birlikte kullanılmasıdır.

Örnek:

- Star + Ring + Bus

## ✅ HATIRLA!

- En yaygın yapı Star Topology’dir.
- Mesh hızlı ve dayanıklıdır ama pahalıdır.
- Hybrid esnektir ama tasarımı zordur.

## ⚠️ KARMAŞTIRMA!

| Topoloji | Avantaj | Dezavantaj |
|---|---|---|
| Point-to-Point | Basit | Ölçeklenmez |
| Bus | Az kablo | Arıza tespiti zor |
| Ring | Sıralı iletişim | Kopma riski |
| Star | Kolay yönetim | Merkez cihaz kritik |
| Mesh | Yüksek yedeklilik | Pahalı |
| Tree | Büyük yapılara uygun | Planlama ister |
| Hybrid | Esnek | Karmaşık |

## 🧪 KENDİNİ TEST ET — Bölüm 7

### ❓ Soru 1
Günümüzde en yaygın kullanılan topoloji hangisidir?

**CEVAP:** Star Topology.

### ❓ Soru 2
Mesh topoloji neden pahalıdır?

**CEVAP:** Her cihazın diğer cihazlarla doğrudan bağlantı kurması çok kablo, port ve işçilik gerektirir.

### ❓ Soru 3
Tree topoloji nedir?

**CEVAP:** Birden fazla star topolojinin birbirine bağlanmasıdır.

---

# 📚 BÖLÜM 8 — Draw.io ile Network Diagramı

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Gerçek ağ kurulmadan önce tasarım yapılmalıdır. Firewall, switch, router, yazıcı, kullanıcı cihazları ve VPN bağlantıları diyagramla gösterilir.

## 8.1 — Draw.io Nedir?

Draw.io / diagrams.net, ücretsiz diagram çizme aracıdır.

## Kullanım Alanları

- Network diagramı
- Firewall yerleşimi
- VPN tüneli
- Kurum hiyerarşisi
- Switch-router bağlantısı
- PDF/PNG dışa aktarma

## 🏠 Günlük Hayat Analojisi

Bir bina yapmadan önce mimari proje çizilir. Ağ kurulmadan önce de network diagramı çizilir.

## ✅ HATIRLA!

> Çizilmeyen ağ, yönetilmesi zor ağdır.

## 🧪 KENDİNİ TEST ET — Bölüm 8

### ❓ Soru 1
Draw.io ne işe yarar?

**CEVAP:** Ağ ve sistem diagramları çizmek için kullanılır.

### ❓ Soru 2
Network diagramı neden önemlidir?

**CEVAP:** Kurulum, bakım, güvenlik ve maliyet planlamasını kolaylaştırır.

### ❓ Soru 3
Draw.io çıktıları hangi formatlarda alınabilir?

**CEVAP:** PDF, PNG, SVG, HTML gibi formatlarda.

---

# 📚 BÖLÜM 9 — Switch Türleri

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Switch, yerel ağın temel cihazıdır. Hangi switch türünün hangi ortamda kullanılacağını bilmek ağ güvenliği açısından önemlidir.

## 9.1 — Switch Nedir?

Switch, aynı yerel ağdaki cihazları birbirine bağlayan cihazdır.

Bilgisayarlar, yazıcılar, sunucular switch üzerinden haberleşebilir.

## 9.2 — Unmanaged Switch

Tak-çalıştır mantığıyla çalışır.

Özellikler:

- Yönetim arayüzü yoktur.
- VLAN desteği yoktur.
- Güvenlik özellikleri sınırlıdır.
- Küçük ağlar için uygundur.

## 9.3 — Smart / Hybrid Switch

Kısmen yönetilebilir switch’tir.

Özellikler:

- Basit VLAN desteği
- Basit web arayüzü
- Temel QoS
- Orta seviye güvenlik

## 9.4 — Managed Switch

Tam yönetilebilir switch’tir.

Özellikler:

- VLAN
- QoS
- SNMP
- Port security
- CLI/Web yönetimi
- Gelişmiş güvenlik ayarları

## ⚠️ KARMAŞTIRMA!

| Switch Türü | Yönetim | VLAN | Güvenlik | Maliyet |
|---|---|---|---|---|
| Unmanaged | Yok | Yok | Düşük | Düşük |
| Smart | Kısmi | Temel | Orta | Orta |
| Managed | Tam | Gelişmiş | Yüksek | Yüksek |

## ✅ HATIRLA!

> Siber güvenlik hassasiyeti olan kurumlarda unmanaged switch yetersiz kalır.

## 🧪 KENDİNİ TEST ET — Bölüm 9

### ❓ Soru 1
Unmanaged switch ne demektir?

**CEVAP:** Yönetilemeyen, tak-çalıştır mantığıyla çalışan switch’tir.

### ❓ Soru 2
Managed switch neden güvenlik açısından önemlidir?

**CEVAP:** VLAN, port security, QoS ve gelişmiş yönetim özellikleri sağlar.

### ❓ Soru 3
Smart switch nerede konumlanır?

**CEVAP:** Unmanaged ve Managed switch arasında, kısmi yönetilebilir cihaz olarak konumlanır.

---

# 📚 BÖLÜM 10 — Switch Nasıl Çalışır?

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Switch’in MAC tablosu mantığını bilmek VLAN, port security, MAC flooding ve LAN güvenliği konularını anlamak için şarttır.

## 10.1 — MAC Address Table Nedir?

Switch şu eşleşmeyi tutar:

```text
Port ↔ MAC Address
```

Örneğin:

| Port | MAC Address |
|---|---|
| 1 | AA:AA:AA |
| 2 | BB:BB:BB |
| 3 | CC:CC:CC |

## 10.2 — Switch Öğrenme Süreci

1. Switch ilk açıldığında MAC tablosu boştur.
2. Bir cihaz paket gönderir.
3. Switch gelen portu ve kaynak MAC adresini öğrenir.
4. Hedef MAC bilinmiyorsa broadcast yapar.
5. Hedef cihaz cevap verirse switch onun MAC adresini de öğrenir.
6. Sonraki trafik doğrudan ilgili porta yönlendirilir.

## 10.3 — ARP ile İlişki

ARP, IP adresinden MAC adresini öğrenmek için kullanılır.

Switch ARP tablosu tutmaz. Layer 2 switch, MAC Address Table tutar.

## 10.4 — Aging Time

Switch MAC tablosundaki eski kayıtları belirli süre sonra siler.

Derste bu süre için **300 saniye** örneği verildi.

## 10.5 — MAC Flooding

Saldırgan switch’e çok sayıda sahte MAC adresi gönderirse tablo dolar. Switch hub gibi davranmaya başlayabilir.

Bu durumda trafik gereğinden fazla porta yayılabilir.

## 🏠 Günlük Hayat Analojisi

Switch bir apartman görevlisi gibidir. İlk başta kim hangi dairede bilmiyor. Gelenleri gördükçe not alıyor.

Sonra mektupları doğru daireye götürüyor.

## ✅ HATIRLA!

- Layer 2 switch MAC Address Table tutar.
- ARP Table PC, Router ve Layer 3 Switch üzerinde olur.
- Aging Time eski kayıtları temizler.
- MAC Flooding ciddi bir LAN saldırısıdır.

## 🧪 KENDİNİ TEST ET — Bölüm 10

### ❓ Soru 1
Switch hangi tabloyu tutar?

**CEVAP:** MAC Address Table.

### ❓ Soru 2
Aging Time ne işe yarar?

**CEVAP:** Kullanılmayan MAC kayıtlarını belirli süre sonra temizler.

### ❓ Soru 3
MAC Flooding nedir?

**CEVAP:** Sahte MAC adresleriyle switch tablosunu doldurma saldırısıdır.

---

# 📚 BÖLÜM 11 — Router: Ağlar Arası Yönlendirme

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Router, farklı ağların konuşmasını sağlar. İnternete çıkış, NAT, VPN, routing ve ağ güvenliği router mantığıyla anlaşılır.

## 11.1 — Router Nedir?

Router, farklı ağları birbirine bağlayan cihazdır.

Örnek:

- LAN ↔ WAN
- Ev ağı ↔ İnternet
- 192.168.1.0/24 ↔ 10.0.0.0/8

## 11.2 — Router’ın Görevleri

- Farklı ağları birbirine bağlar.
- IP adresine göre yönlendirme yapar.
- Routing Table tutar.
- En iyi rotayı seçer.
- NAT yapabilir.
- VPN destekleyebilir.
- Firewall özellikleri sunabilir.

## 11.3 — Router ve NAT

Evdeki modem/router, içerideki private IP’leri dış dünyaya public IP ile çıkarır.

Bu işleme NAT — Network Address Translation denir.

## 🏠 Günlük Hayat Analojisi

Router şehirlerarası kavşak gibidir.

Hangi yolun hangi şehre gittiğini bilir ve trafiği doğru yöne yollar.

## ✅ HATIRLA!

> Switch aynı ağdaki cihazları bağlar. Router farklı ağları bağlar.

## 🧪 KENDİNİ TEST ET — Bölüm 11

### ❓ Soru 1
Router hangi OSI katmanında çalışır?

**CEVAP:** Layer 3, Network katmanı.

### ❓ Soru 2
Router neye göre yönlendirme yapar?

**CEVAP:** IP adreslerine göre.

### ❓ Soru 3
NAT ne işe yarar?

**CEVAP:** Private IP adreslerini public IP üzerinden internete çıkarır.

---

# 📚 BÖLÜM 12 — Routing Table, Metric ve Next Hop

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Bir paketin hedefe hangi yoldan gittiğini anlamak için routing table, metric ve next hop kavramları bilinmelidir.

## 12.1 — Routing Table Nedir?

Router’ın yol haritasıdır.

İçinde genellikle şunlar bulunur:

- Destination Network
- Netmask
- Gateway
- Interface
- Metric
- Next Hop

## 12.2 — Metric Nedir?

Metric, bir yolun maliyet değeridir.

Düşük metric = daha tercih edilen yol.

## 12.3 — Next Hop Nedir?

Paketin nihai hedefe gitmeden önce uğrayacağı bir sonraki router’dır.

## 🏠 Günlük Hayat Analojisi

Navigasyon uygulamasını düşün:

- Hedef: İstanbul
- Alternatif yollar: TEM, D100, köy yolu
- Metric: süre, trafik, mesafe
- Next Hop: bir sonraki kavşak

## ✅ HATIRLA!

> Router en uygun yolu routing table ve metric değerine göre seçer.

## 🧪 KENDİNİ TEST ET — Bölüm 12

### ❓ Soru 1
Metric ne demektir?

**CEVAP:** Bir yolun maliyet veya tercih değeridir.

### ❓ Soru 2
Next Hop ne demektir?

**CEVAP:** Paketin gideceği bir sonraki router’dır.

### ❓ Soru 3
Routing Table ne işe yarar?

**CEVAP:** Router’ın hedef ağlara hangi yoldan ulaşacağını belirlemesini sağlar.

---

# 📚 BÖLÜM 13 — IPsec ve VPN

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Uzaktan çalışma, site-to-site bağlantılar ve firewall projelerinde güvenli tünel kurmak gerekir. IPsec bu güvenliğin temel taşlarından biridir.

## 13.1 — IPsec Nedir?

IPsec = Internet Protocol Security.

IP trafiğine güvenlik ekler.

Sağladığı temel güvenlik özellikleri:

- Confidentiality (Gizlilik)
- Integrity (Bütünlük)
- Authentication (Kimlik Doğrulama)

## 13.2 — Nerede Kullanılır?

En yaygın kullanım alanı VPN’dir.

Örnek: Evden çalışan bir kullanıcı şirket ağına IPsec VPN ile güvenli şekilde bağlanır.

## 13.3 — Dersteki Açıklama

Eğitmen IPsec’in özellikle VPN tüneli kurarken iki nokta arasında güvenli iletişim sağladığını anlattı.

Bu tünelde:

- Veri şifrelenir.
- Karşı taraf doğrulanır.
- Veri bütünlüğü korunur.

## 🏠 Günlük Hayat Analojisi

Normal internet açık yoldur. IPsec VPN ise zırhlı, kilitli ve kimlik kontrollü özel tüneldir.

## ✅ HATIRLA!

> IPsec, IP trafiğini güvenli hale getirir. VPN tünellerinde kritik rol oynar.

## 🧪 KENDİNİ TEST ET — Bölüm 13

### ❓ Soru 1
IPsec ne sağlar?

**CEVAP:** Gizlilik, bütünlük ve kimlik doğrulama sağlar.

### ❓ Soru 2
IPsec en çok nerede kullanılır?

**CEVAP:** VPN bağlantılarında.

### ❓ Soru 3
VPN neden kullanılır?

**CEVAP:** Güvensiz internet üzerinden güvenli özel bağlantı kurmak için.

---

# 📚 BÖLÜM 14 — Hub vs Switch vs Router

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Ağ cihazlarını karıştırmak çok yaygın bir hatadır. Hub, switch ve router aynı şey değildir.

## 14.1 — Temel Karşılaştırma

| Cihaz | Katman | Görev |
|---|---|---|
| Hub | Layer 1 | Gelen sinyali herkese yollar |
| Switch | Layer 2 | MAC adresine göre iletir |
| Router | Layer 3 | IP adresine göre ağlar arası yönlendirir |

## 14.2 — Hub

- Akıllı değildir.
- Gelen veriyi herkese yollar.
- Half duplex çalışır.
- Günümüzde yaygın kullanılmaz.

## 14.3 — Switch

- MAC adres tablosu tutar.
- Aynı ağdaki cihazları bağlar.
- Full duplex destekleyebilir.

## 14.4 — Router

- Farklı ağları bağlar.
- IP adresleriyle çalışır.
- NAT, VPN ve firewall özellikleri sunabilir.

## 🏠 Günlük Hayat Analojisi

| Cihaz | Analojisi |
|---|---|
| Hub | Herkese bağıran kişi |
| Switch | Doğru kişiye mektup veren görevli |
| Router | Şehirlerarası kargo yönlendirme merkezi |

## ✅ HATIRLA!

- Hub herkese gönderir.
- Switch doğru porta gönderir.
- Router doğru ağa gönderir.

## 🧪 KENDİNİ TEST ET — Bölüm 14

### ❓ Soru 1
Hub neden güvenli değildir?

**CEVAP:** Gelen veriyi herkese gönderdiği için.

### ❓ Soru 2
Switch neye göre çalışır?

**CEVAP:** MAC adresine göre.

### ❓ Soru 3
Router neye göre çalışır?

**CEVAP:** IP adresine göre.

---

# 📚 BÖLÜM 15 — Access Point

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Kablosuz ağlar modern kurumların vazgeçilmez parçasıdır. Ancak Wi-Fi güvenliği, kapsama alanı ve erişim mimarisi doğru anlaşılmalıdır.

## 15.1 — Access Point Nedir?

Access Point, kablolu ağı kablosuz sinyale çeviren cihazdır.

## 15.2 — Root Access Point

Kablolu ağı kablosuz yayına çevirir.

## 15.3 — Repeater

Var olan kablosuz sinyali alır, güçlendirir ve yeniden yayar.

## 15.4 — Bridge Mode

İki farklı kablolu ağı kablosuz olarak birbirine bağlar.

Örnek: İki ayrı bina arasında kablo çekmeden ağ bağlantısı kurmak.

## 15.5 — SSID, BSSID, ESSID

| Kavram | Anlamı |
|---|---|
| SSID | Wi-Fi ağının görünen adı |
| BSSID | Wi-Fi cihazının MAC adresi |
| ESSID | Aynı SSID’nin geniş alanda yayılmış hali |

## 🏠 Günlük Hayat Analojisi

Access Point, kabloyla gelen interneti havaya dağıtan bir yayın cihazı gibidir.

## ✅ HATIRLA!

> Access Point genelde IP dağıtmaz. IP’yi router/DHCP verir.

## 🧪 KENDİNİ TEST ET — Bölüm 15

### ❓ Soru 1
Access Point ne yapar?

**CEVAP:** Kablolu ağı kablosuz hale getirir.

### ❓ Soru 2
Repeater ne yapar?

**CEVAP:** Kablosuz sinyalin menzilini artırır.

### ❓ Soru 3
SSID nedir?

**CEVAP:** Wi-Fi ağının görünen adıdır.

---

# 📚 BÖLÜM 16 — Kablosuz Ağ Güvenliği

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Kablosuz sinyaller havadan yayıldığı için kablolu ağlara göre daha kolay dinlenebilir ve taklit edilebilir.

## 16.1 — Temel Riskler

- Yetkisiz bağlantı
- Rogue Access Point
- Evil Twin saldırısı
- Trafik dinleme
- Kimlik bilgisi çalma
- Sahte captive portal

## 16.2 — Kablolu vs Kablosuz Güvenlik

| Ağ Türü | Risk |
|---|---|
| Kablolu | Fiziksel erişim gerekir |
| Kablosuz | Sinyal havadan yakalanabilir |

## 🏠 Günlük Hayat Analojisi

Kablolu ağ kapalı borudan akan su gibidir. Kablosuz ağ ise havaya yayılan ses gibidir; yakındaki herkes duyabilir.

## ✅ HATIRLA!

> Wi-Fi kolaylık sağlar ama saldırı yüzeyini büyütür.

## 🧪 KENDİNİ TEST ET — Bölüm 16

### ❓ Soru 1
Kablosuz ağ neden daha risklidir?

**CEVAP:** Sinyal havadan yayıldığı için saldırgan tarafından yakalanabilir.

### ❓ Soru 2
Evil Twin nedir?

**CEVAP:** Gerçek Wi-Fi ağına benzeyen sahte kablosuz ağdır.

### ❓ Soru 3
Kablosuz güvenlikte ne yapılmalıdır?

**CEVAP:** Güçlü şifreleme, segmentasyon, captive portal ve güvenli yapılandırma kullanılmalıdır.

---

# 📚 BÖLÜM 17 — PoE: Power over Ethernet

## 🎯 BUNU NEDEN ÖĞRENİYORUZ?

Access Point, IP kamera ve VoIP telefon gibi cihazlarda hem veri hem enerji gerekebilir. PoE bu ihtiyacı tek kabloyla çözer.

## 17.1 — PoE Nedir?

PoE = Power over Ethernet.

Ethernet kablosu üzerinden hem veri hem elektrik taşınmasını sağlar.

## 17.2 — Nerede Kullanılır?

- Access Point
- IP kamera
- VoIP telefon
- Dış mekan Wi-Fi cihazları
- Güvenlik kameraları

## 17.3 — Derste Geçen Örnek

Eğitmen dış mekan Wi-Fi cihazlarından bahsetti. Büyük park, bahçe, site, havuz ve açık alanlarda outdoor access point kullanılabileceğini anlattı.

Bu cihazlarda PoE sayesinde ayrı elektrik kablosu çekmeden enerji sağlanabilir.

## 🏠 Günlük Hayat Analojisi

Tek kablodan hem iletişim hem enerji taşımak gibidir. Bir cihazı hem konuşturur hem çalıştırır.

## ✅ HATIRLA!

> PoE kablo karmaşasını azaltır ve dış mekan kurulumlarını kolaylaştırır.

## 🧪 KENDİNİ TEST ET — Bölüm 17

### ❓ Soru 1
PoE ne işe yarar?

**CEVAP:** Ethernet kablosu üzerinden hem veri hem enerji taşır.

### ❓ Soru 2
PoE hangi cihazlarda kullanılır?

**CEVAP:** Access point, IP kamera, VoIP telefon gibi cihazlarda.

### ❓ Soru 3
PoE’nin avantajı nedir?

**CEVAP:** Ayrı elektrik hattı ihtiyacını azaltır.

---

# 🗺️ GENEL TEKRAR VE ÖZET

## Tek Cümlelik Özet — Her Konu

| Konu | Tek Cümle Özet |
|---|---|
| Komut Aşinalığı | Komutları ezberlemek değil, ne işe yaradığını bilmek önemlidir. |
| TCPDump | Terminal üzerinden ağ paketlerini yakalayan araçtır. |
| TCPDump Filtreleri | Trafikte sadece istenen protokol, IP veya portu görmeyi sağlar. |
| `.pcap` | Yakalanmış ağ paketlerinin kayıt dosyasıdır. |
| Network Miner | `.pcap` dosyalarını adli analiz eden araçtır. |
| Netstat | Sistemdeki açık portları ve bağlantıları gösterir. |
| Network Topolojisi | Ağdaki cihazların bağlantı düzenidir. |
| Star Topology | Günümüzde en yaygın kullanılan ağ topolojisidir. |
| Mesh Topology | Çok dayanıklı ama pahalı ağ topolojisidir. |
| Draw.io | Ağ diyagramı çizmek için kullanılan ücretsiz araçtır. |
| Switch | Aynı ağdaki cihazları MAC adresine göre bağlar. |
| Managed Switch | VLAN ve gelişmiş güvenlik ayarları sunar. |
| MAC Address Table | Switch’in port-MAC eşleşmesini tuttuğu tablodur. |
| Router | Farklı ağları IP adreslerine göre bağlar. |
| Routing Table | Router’ın yol haritasıdır. |
| Metric | En iyi yolu seçmek için kullanılan maliyet değeridir. |
| IPsec | IP trafiğine güvenlik ekler. |
| VPN | Güvenli ağ tüneli oluşturur. |
| Access Point | Kablolu ağı kablosuz yayına çevirir. |
| PoE | Ethernet kablosuyla hem veri hem elektrik taşır. |

---

# Kritik Port ve Kavram Listesi

| Kavram / Port | Açıklama |
|---|---|
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 22 | SSH |
| 5901 | VNC / Xvnc |
| ICMP | Ping gibi hata ve kontrol mesajları |
| ARP | IP adresinden MAC adresi bulma |
| MAC Address | Ağ kartının fiziksel kimliği |
| IP Address | Ağdaki mantıksal adres |
| VLAN | Aynı switch üzerinde sanal ağ bölümlendirme |
| NAT | Private IP’leri public IP ile internete çıkarma |
| IPsec | IP katmanında güvenlik |
| SSID | Wi-Fi adı |
| BSSID | Wi-Fi cihazının MAC adresi |
| ESSID | Genişletilmiş kablosuz ağ adı |

---

# Eğitmenin Önemli Uyarıları

1. Komutları ezberlemeye çalışma; mantığını öğren.
2. TCPDump, grafik arayüz olmayan sistemlerde çok değerlidir.
3. `.pcap` dosyaları Wireshark ve Network Miner ile analiz edilebilir.
4. Network Miner saldırı sonrası delil toplamada kullanılır.
5. Netstat ile bilinmeyen servis ve açık portlar araştırılmalıdır.
6. Star topoloji günümüzde en yaygın kullanılan yapıdır.
7. Mesh güçlüdür ama pahalıdır.
8. Managed switch güvenlik açısından unmanaged switch’ten çok daha yeteneklidir.
9. Layer 2 switch ARP tablosu değil MAC Address Table tutar.
10. Router farklı ağları birbirine bağlar.
11. IPsec VPN bağlantılarında kritik önemdedir.
12. Kablosuz ağlar pratik ama güvenlik riski daha yüksektir.
13. PoE, dış mekan access point ve IP kamera kurulumlarında kablo karmaşasını azaltır.

---


