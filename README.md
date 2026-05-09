<div align="center">

# 🛡️ CyberSecurity Toolkit

**Sıfırdan ileri seviyeye kapsamlı siber güvenlik ders notları, lab senaryoları ve araç rehberleri.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Kali%20Linux%20%7C%20Windows-blue.svg)]()
[![TryHackMe](https://img.shields.io/badge/Lab-TryHackMe-red.svg)](https://tryhackme.com/)

</div>

---

## ⚠️ Yasal Uyarı

> **Bu repository yalnızca EĞİTİM AMAÇLIDIR.**
> Tüm teknikler yalnızca aşağıdaki ortamlarda uygulanabilir:
> - ✅ Yetkili pentest ortamları (yazılı izinle)
> - ✅ CTF platformları (TryHackMe, HackTheBox vb.)
> - ✅ Kişisel izole lab kurulumları
>
> İzinsiz sistemlerde uygulanması **suç teşkil eder.**
> `TR: TCK 243-245` · `US: CFAA` · `EU: Directive 2013/40/EU`

---

## 📖 Hakkında

Bu repository; ağ güvenliği, sistem yönetimi ve saldırı/savunma tekniklerini kapsayan yapılandırılmış bir siber güvenlik öğrenme yolunu sunar. Her bölüm:

- 📋 **Ders notları** — temel kavramlar ve tanımlar
- 🔬 **Lab senaryoları** — adım adım uygulamalı çalışmalar
- 🃏 **Flashcard'lar** — spaced repetition ile kalıcı öğrenme
- 📄 **Cheat sheet** — hızlı başvuru komutları

---

## 📚 Müfredat

| # | Bölüm | İçerik | Durum |
|:---:|---|---|:---:|
| 01 | [**IT Fundamentals**](./01-IT-FUNDAMENTALS/) | Donanım, yazılım, işletim sistemi temelleri | 📝 Yakında |
| 02 | [**Network Fundamentals**](./02-NETWORK-FUNDAMENTALS/) | OSI modeli, TCP/IP, protokoller, subnetting | 📝 Yakında |
| 03 | [**Linux**](./03-LINUX/) | Komut satırı, dosya sistemi, kullanıcı yönetimi | 📝 Yakında |
| 04 | [**Server Management**](./04-SERVER-MANAGEMENT/) | Linux, Windows Server ve Active Directory | 📝 Yakında |
| ↳ | [4.1 Linux Server](./04-SERVER-MANAGEMENT/4.1-LINUX/) | Servis yönetimi, SSH, cron, firewall | 📝 Yakında |
| ↳ | [4.2 Windows Server](./04-SERVER-MANAGEMENT/4.2-WINDOWS-SERVER/) | Roller, özellikler, IIS, DNS, DHCP | 📝 Yakında |
| ↳ | [4.3 Windows AD](./04-SERVER-MANAGEMENT/4.3-WINDOWS-AD/) | Domain, GPO, kullanıcı/grup yönetimi | 📝 Yakında |
| 05 | [**Intro to Security**](./05-INTRO-TO-SECURITY/) | Tehdit modelleme, pentest metodolojisi, CIA üçgeni | 📝 Yakında |
| 06 | [**Cryptography**](./06-CRYPTOGRAPHY/) | Simetrik/asimetrik şifreleme, PKI, hash fonksiyonları | 📝 Yakında |
| 07 | [**Firewall**](./07-FIREWALL/) | Firewall türleri, kural yönetimi, trafik analizi | 📝 Yakında |
| 08 | [**EDR**](./08-EDR/) | Uç nokta güvenliği, tehdit tespiti, olay müdahalesi | 📝 Yakında |
| 09 | [**Network Scanning — Nmap**](./09-NETWORK-SCANNING-NMAP/) | Host keşfi, port tarama, servis/versiyon tespiti | 📝 Yakında |
| 10 | [**Metasploit — Exploitation**](./10-METASPLOIT-EXPLOITATION/) | MSF Venom, payload, persistence, AV evasion | 📝 Yakında |

**Durum:** ✅ Tamamlandı · 🔄 Devam Ediyor · 📝 Yakında

---

## 🗺️ Öğrenme Yolu

```
Başlangıç
    │
    ▼
01 IT Fundamentals ──► 02 Network Fundamentals ──► 03 Linux
                                                        │
                                                        ▼
                                            04 Server Management
                                           (Linux / Windows / AD)
                                                        │
                                                        ▼
                                           05 Intro to Security
                                                        │
                              ┌─────────────────────────┤
                              ▼                         ▼
                       06 Cryptography            07 Firewall
                              │                         │
                              └──────────┬──────────────┘
                                         ▼
                                     08 EDR
                                         │
                                         ▼
                              09 Network Scanning (Nmap)
                                         │
                                         ▼
                           10 Metasploit — Exploitation
```

---

## 🛠️ Lab Ortamı

### Gerekli Araçlar

| Araç | Amaç | İndirme |
|---|---|---|
| **Kali Linux** | Saldırgan işletim sistemi | [kali.org](https://www.kali.org/) |
| **VirtualBox** | Yerel sanallaştırma | [virtualbox.org](https://www.virtualbox.org/) |
| **TryHackMe** | Rehberli online lab | [tryhackme.com](https://tryhackme.com/) |
| **HackTheBox** | İleri seviye online lab | [hackthebox.com](https://www.hackthebox.com/) |

### Minimum Sistem Gereksinimleri

```
RAM  : 8 GB  (Kali 4 GB + Hedef VM 4 GB)
CPU  : 4 çekirdek  (VT-x / AMD-V aktif olmalı)
Disk : 80 GB boş alan
```

### Hızlı Başlangıç

```bash
# 1. Repoyu klonla
git clone https://github.com/ekremtunckir35/CyberSecurityToolkit.git
cd CyberSecurityToolkit

# 2. İlgilendiğin bölümü aç
cd 01-IT-FUNDAMENTALS
cat README.md
```

---

## 📂 Repo Yapısı

```
CyberSecurityToolkit/
│
├── 01-IT-FUNDAMENTALS/
├── 02-NETWORK-FUNDAMENTALS/
├── 03-LINUX/
├── 04-SERVER-MANAGEMENT/
│   ├── 4.1-LINUX/
│   ├── 4.2-WINDOWS-SERVER/
│   └── 4.3-WINDOWS-AD/
├── 05-INTRO-TO-SECURITY/
├── 06-CRYPTOGRAPHY/
├── 07-FIREWALL/
├── 08-EDR/
├── 09-NETWORK-SCANNING-NMAP/
└── 10-METASPLOIT-EXPLOITATION/
```

---

## 🔗 Faydalı Kaynaklar

| Kaynak | Açıklama |
|---|---|
| [MITRE ATT&CK](https://attack.mitre.org/) | Saldırı tekniği taksonomisi |
| [NIST Cybersecurity](https://www.nist.gov/cyberframework) | Güvenlik çerçevesi |
| [CVE Details](https://www.cvedetails.com/) | Zafiyet veritabanı |
| [Exploit-DB](https://www.exploit-db.com/) | Exploit arşivi |
| [OWASP](https://owasp.org/) | Web uygulama güvenliği |
| [HackerOne](https://www.hackerone.com/) | Bug bounty platformu |

---

## 🤝 Katkıda Bulunma

1. Repoyu **fork**'layın
2. Yeni branch oluşturun: `git checkout -b feat/yeni-icerik`
3. Değişikliklerinizi commit edin: `git commit -m "feat: yeni içerik eklendi"`
4. Branch'i push edin: `git push origin feat/yeni-icerik`
5. **Pull Request** açın

---

## 📄 Lisans

```
MIT License — Eğitim amaçlı serbestçe kullanılabilir.
Ticari amaçlı kullanım veya gerçek saldırılarda kullanım yasaktır.
```

---

<div align="center">

**⭐ Faydalı bulduysan yıldız vermeyi unutma!**

*Son güncelleme: 2025 · [@ekremtunckir35](https://github.com/ekremtunckir35)*

</div>
