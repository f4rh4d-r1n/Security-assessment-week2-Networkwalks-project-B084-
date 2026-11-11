# 🧪 Security Assessment – Networkwalks Project (B084)

![Domain](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Tool](https://img.shields.io/badge/Tool-Kali%20Linux-blue)
![Focus](https://img.shields.io/badge/Focus-Network%20Reconnaissance-brightgreen)
![Skill](https://img.shields.io/badge/Skill-DNS%20Enumeration-orange)
![Topic](https://img.shields.io/badge/Topic-Web%20Fingerprinting-purple)
![Field](https://img.shields.io/badge/Field-Network%20Security-black)

![Tool](https://img.shields.io/badge/Tool-Nmap-blue)
![Tool](https://img.shields.io/badge/Tool-Zenmap-blue)
![Tool](https://img.shields.io/badge/Tool-DNSRecon-blue)
![Tool](https://img.shields.io/badge/Tool-Whois-blue)
![Tool](https://img.shields.io/badge/Tool-WhatWeb-blue)
![Tool](https://img.shields.io/badge/Tool-WAFW00F-blue)
![Tool](https://img.shields.io/badge/Tool-cURL-blue)
![Technique](https://img.shields.io/badge/Technique-Passive%20Footprinting-yellow)
![Technique](https://img.shields.io/badge/Technique-Host%20Discovery-yellow)

---

## 📌 Executive Overview

This repository documents a cybersecurity reconnaissance and network-discovery assessment completed as part of an internship project. The work used Kali Linux and a collection of standard security tools to gather domain-registration and DNS information, identify publicly observable web technologies, check for a web application firewall (WAF), inspect HTTP response headers, and discover active hosts on a separate private lab network.

The public-domain reconnaissance focused on **`networkwalks.com`**. The Zenmap/Nmap evidence documents a separate private-subnet host-discovery exercise on **`10.0.0.0/24`**; it should not be interpreted as a scan of the public website.

## 🎯 Scope and Authorization

| Assessment area | Target / environment | Activity documented |
|---|---|---|
| Domain reconnaissance | `networkwalks.com` | WHOIS lookup, DNS enumeration and DNS resolution checks |
| Web fingerprinting | `networkwalks.com` | Technology identification, WAF detection and HTTP-header inspection |
| Local network discovery | `10.0.0.0/24` | Ping/host discovery using Nmap and Zenmap |

> **Authorization:** Perform security testing only when you have explicit permission from the system owner and only within the agreed scope. The private subnet is documented separately from the public domain.

## 🧰 Tools Used

| Tool | Purpose in this project |
|---|---|
| Kali Linux | Security-testing operating system and workspace |
| WHOIS | Retrieved domain-registration, registrar and nameserver information |
| NSLookup | Queried DNS to check domain name resolution |
| DNSRecon | Enumerated available DNS record information |
| WhatWeb | Identified publicly observable web technologies |
| WAFW00F | Checked whether a web application firewall was detected |
| cURL | Requested the site and inspected its HTTP response headers |
| Nmap | Performed host discovery on the private lab subnet |
| Zenmap | Provided a graphical interface and topology view for Nmap results |

## 🔍 Methodology

### 1. Domain and registration reconnaissance

WHOIS was used to review the domain's registrar, registration status and nameserver information. DNSRecon and NSLookup were then used to collect and verify DNS-related information.

```bash
whois networkwalks.com
nslookup networkwalks.com
dnsrecon -d networkwalks.com
```

### 2. Web technology fingerprinting

WhatWeb was used to identify technologies observable from the website's responses. These are technology fingerprints, not proof that a particular component is vulnerable.

```bash
whatweb https://networkwalks.com
```

### 3. Web application firewall detection

WAFW00F was used to check whether a WAF could be identified in front of the website.

```bash
wafw00f https://networkwalks.com
```

### 4. HTTP response inspection

cURL was used to request the website and review the returned status and HTTP headers.

```bash
curl -I https://networkwalks.com
```

### 5. Private-network host discovery

Nmap/Zenmap was used separately to perform a ping scan of the private `10.0.0.0/24` lab subnet.

```bash
nmap -sn 10.0.0.0/24
```

This is host discovery; it does not establish which TCP or UDP ports are open.

## 📊 Key Observations

| Area | Observation from the captured output |
|---|---|
| WHOIS | GoDaddy was listed as the registrar, with HostGator nameservers. The captured record showed DNSSEC as unsigned. |
| DNSRecon | SOA, NS, A, MX, TXT and SRV-related records were returned. The tool reported eight records found. |
| NSLookup | `networkwalks.com` resolved to `192.232.216.135` in the displayed response. The output also showed a DNS query timeout before the answer. |
| WhatWeb | The output identified Apache and WordPress-related technologies, as well as other web components. |
| WAFW00F | The output reported a ModSecurity (SpiderLabs) WAF. |
| cURL | The captured request returned `HTTP/2 200` and displayed several response headers, including `referrer-policy` and `permissions-policy`. |
| Nmap / Zenmap | The ping scan reported four responsive hosts: `10.0.0.1`, `10.0.0.2`, `10.0.0.4` and `10.0.0.5`. |

## 🖼️ Evidence and Screenshots

Add your screenshots in the spaces below. For a tidy repository, create a folder named `assets/screenshots/`, upload the images there, and replace each placeholder note with the corresponding Markdown image link.

Before publishing, review screenshots for tokens, credentials, session values and personal contact information, and redact anything not necessary to demonstrate the result.

### 1. WHOIS – Domain registration information

<img width="814" height="425" alt="Screenshot 2026-11-10 220742" src="https://github.com/user-attachments/assets/cf9a5904-18c1-4bad-aee7-eaa0f2704264" />


<!-- Replace with: ![WHOIS output](assets/screenshots/01-whois.png) -->

### 2. NSLookup – DNS resolution

<img width="704" height="411" alt="Screenshot 2026-11-11 151111" src="https://github.com/user-attachments/assets/eb26e491-78d1-4b5f-8160-7a2cc1d50ede" />


<!-- Replace with: ![NSLookup output](assets/screenshots/02-nslookup.png) -->

### 3. DNSRecon – DNS enumeration

<img width="904" height="450" alt="dnsrecon" src="https://github.com/user-attachments/assets/7e41875b-2357-4d70-8849-85a09dcf74e3" />


<!-- Replace with: ![DNSRecon output](assets/screenshots/03-dnsrecon.png) -->

### 4. WhatWeb – Web technology fingerprinting

<img width="779" height="420" alt="Screenshot 2026-11-10 222033" src="https://github.com/user-attachments/assets/6628a5ae-098c-4667-82b4-db113911ef44" />


<!-- Replace with: ![WhatWeb output](assets/screenshots/04-whatweb.png) -->

### 5. WAFW00F – Web application firewall detection

<img width="732" height="418" alt="Screenshot 2026-11-11 150848" src="https://github.com/user-attachments/assets/c009b98a-b96a-4add-8fba-3547d72e8c09" />


<!-- Replace with: ![WAFW00F output](assets/screenshots/05-wafw00f.png) -->

### 6. cURL – HTTP response headers

<img width="712" height="418" alt="Screenshot 2026-11-11 151048" src="https://github.com/user-attachments/assets/ddbfd5b4-315b-4798-b16c-874375458bc8" />


<!-- Replace with: ![cURL headers](assets/screenshots/06-curl-headers.png) -->

### 7. Zenmap – Private-network topology view

<img width="949" height="447" alt="Screenshot 2026-11-11 150450" src="https://github.com/user-attachments/assets/571f762c-7461-4bd0-904c-ad3c37fe74c7" />



<!-- Replace with: ![Zenmap topology](assets/screenshots/07-zenmap-topology.png) -->

### 8. Nmap / Zenmap – Host discovery results

<img width="744" height="413" alt="Screenshot 2026-11-11 150645" src="https://github.com/user-attachments/assets/154d2288-b155-46dc-a532-40b7324af0ed" />


<!-- Replace with: ![Nmap host discovery](assets/screenshots/08-nmap-host-discovery.png) -->

## 🛡️ Recommendations and Learning Outcomes

- Review DNS configuration and assess whether DNSSEC signing is appropriate for the domain.
- Keep web-server, CMS, themes and plugins maintained, and avoid exposing unnecessary version details where practical.
- Review HTTP security headers against the application's requirements.
- Treat WAF detection as one layer of defense, not as proof that the application is protected from every attack.
- Maintain an inventory of private-network devices and restrict access between systems according to their roles.
- Validate suspected weaknesses with additional evidence before assigning severity or reporting a confirmed vulnerability.

This project provided practical experience with information gathering, DNS enumeration, web fingerprinting, WAF identification, HTTP response inspection and network host discovery using Kali Linux tools.

## ⚠️ Limitations

- The supplied screenshots document reconnaissance and host discovery. They do not, by themselves, demonstrate exploitation, a confirmed vulnerability, or a completed port/service scan.
- The Nmap evidence shown is a ping scan (`-sn`) of a private subnet, not a port scan of `networkwalks.com`.
- Technology and DNS observations are time-specific and may change.
- Findings should be checked against the original assessment report and the authorized scope before being presented as final conclusions.

## 👤 Project Information

- **Project:** Security Assessment – Week 2
- **Project identifier:** Networkwalks – B084
- **Platform:** Kali Linux
- **Assessment window shown in evidence:** 11–12 November 2026
- **Focus:** Cybersecurity reconnaissance and network discovery

---

<p align="center">
  <i>Documented for learning and professional cybersecurity portfolio purposes.</i>
</p>
