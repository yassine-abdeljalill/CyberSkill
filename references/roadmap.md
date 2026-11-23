# Cybersecurity Learning Roadmap

This is the student's curriculum, reorganized from their roadmap (roadmap.sh Cyber Security) into a **teaching order with prerequisites**. The original map is a web of topics; learners need a path. Follow the stages in order unless the student already knows a stage (check with 2-3 diagnostic questions, never assume).

## Contents
- How to use this file
- Stage 0: IT fundamentals
- Stage 1: Operating systems
- Stage 2: Networking
- Stage 3: Security foundations
- Stage 4: Tools, logs, and hardening
- Stage 5: Attacks and defenses
- Stage 6: Incident response, forensics, and threat work
- Stage 7: Cloud
- Stage 8: Programming (runs in parallel)
- Parallel track A: CTFs and labs
- Parallel track B: Certifications
- Suggested pacing

## How to use this file

- **Making a plan:** ask goal + hours per week + deadline, pick the stages that fit, and give a weekly rhythm (see `templates.md`).
- **Student is stuck:** find the topic below, look at its **Needs first**, and test that prerequisite.
- **Choosing the next topic:** go to the next item in the same stage, or the next stage if the student has met every **Mastery check** in the current one.
- **Mastery checks** are things the student should be able to *do or explain* without help. Use them as quiz material. A topic is "learned" only when they pass these, not when you have explained it.
- Notes on the source map: it contains the typo "Whishing" (it means **vishing**, voice phishing) and "Perimiter" (perimeter). Gently use the correct terms.

---

## Stage 0: IT fundamentals

**Why first:** you can't secure what you don't understand. Everything later assumes this.

| Topic (from the map) | Mastery check |
|---|---|
| Computer hardware components (CPU, RAM, storage, motherboard, NIC, PSU) | Explain what each part does and what happens when each one fails. Say where malware could hide (firmware, disk, memory). |
| Connection types and their function (USB, Ethernet, plus **NFC, WiFi, Bluetooth, Infrared**) | Compare range, speed, and typical security risks for each wireless type (e.g. Bluetooth pairing attacks, WiFi eavesdropping, NFC relay). |
| OS-independent troubleshooting | Follow the method: identify the problem, form a theory, test it, fix it, verify, document. Apply it to "my computer can't get online". |
| Basics of popular suites (iCloud, Google Suite, MS Office Suite) | Describe what each suite offers and one security setting in each (sharing permissions, macros in Office, 2FA). |
| Basics of computer networking | Describe what a network is, what a router and switch do, and trace "what happens when I open a website" at a high level. |

**Practice:** take a computer apart virtually (watch a teardown), then troubleshoot a deliberately broken home network setup on paper.

---

## Stage 1: Operating systems (Windows, Linux, macOS)

**Needs first:** Stage 0 hardware basics.
**Teaching order:** Linux first (most security tools live there), then Windows (most targets and enterprises live there), then macOS.

Learn the same checklist for each OS (this is what the map says: "learn the following for each"):

| Topic | Mastery check |
|---|---|
| Installation and configuration | Install it in a VM and describe the choices made. |
| Different versions and differences | Name major versions/distros and one difference that matters for security (e.g. Windows Home vs Pro vs Enterprise features; Debian vs Red Hat families). |
| Navigating with GUI and CLI | Move around, list, search, and read files from the command line. |
| Understand permissions | Linux: read `rwx`, explain `chmod 754`, owner/group/other. Windows: explain NTFS permissions and the difference between users, groups, and admin. |
| Installing software and applications | Use a package manager (`apt`, etc.), explain why installing from untrusted sources is risky. |
| CRUD on files (Create, Read, Update, Delete) | Perform each via CLI (`touch`, `cat`, `nano`, `rm`) and explain what "delete" really does to data. |
| Troubleshooting | Read logs and system status to find why something failed. |
| Common commands | Use ~20 core commands without looking them up. |

**Practice:** TryHackMe Linux fundamentals style rooms; set up a Linux VM and do everything from the terminal for a week.

---

## Stage 2: Networking knowledge

**Needs first:** Stage 0 networking basics, Stage 1 CLI skills.
**This is the most important stage for a security career.** Spend extra time here and revisit it often.

### 2.1 The foundation
| Topic | Mastery check |
|---|---|
| **OSI model** (7 layers) | Name the layers in order (mnemonic: "Please Do Not Throw Sausage Pizza Away"), say what each does, and place HTTP, TCP, IP, Ethernet, and a switch on the right layers. |
| Common protocols and their uses | Match protocols to jobs (HTTP, DNS, DHCP, SMTP, SSH, FTP...) without help. |
| Common ports and their uses | Recall the top ~20 ports (21, 22, 23, 25, 53, 67/68, 80, 110, 143, 443, 445, 3389...) and which are insecure. |
| SSL and TLS basics | Explain in plain words what TLS protects and roughly how the handshake builds trust. |
| NAS and SAN basics | Explain the difference in one sentence each. |
| Subnetting basics | Convert `/24` to a subnet mask, count hosts in a small subnet. Practice daily; it is a skill, not a fact. |
| Public vs private IP addresses | List the private ranges and explain NAT's role. |

### 2.2 IP terminology
`localhost / loopback`, `CIDR`, `subnet mask`, `default gateway`. **Mastery:** given an IP, mask, and gateway, explain whether two devices can talk directly or need the router.

### 2.3 Terminology to understand
VLAN, DMZ, ARP, VM, DHCP, DNS, NAT, IP, router, switch, VPN, MAN, LAN, WAN, WLAN. **Mastery:** one-sentence definition + one security angle for each (e.g. ARP: spoofing; VLAN: hopping; DMZ: where public servers live).

### 2.4 Services to understand
DHCP, DNS, NTP, IPAM. **Mastery:** explain what breaks if each stops working (NTP: logs and Kerberos time drift are a classic).

### 2.5 Network topologies
Star, Ring, Mesh, Bus. **Mastery:** draw each, say one strength and one weakness (single point of failure).

### 2.6 Network protocols
SSH, RDP, FTP, SFTP, HTTP/HTTPS, SSL/TLS. **Mastery:** pick the secure alternative to FTP/Telnet/HTTP and explain why.

### 2.7 Virtualization
Hypervisor, VM, Guest OS, Host OS; VMware, VirtualBox, ESXi, Proxmox. **Mastery:** explain Type 1 vs Type 2 hypervisors and build a working VM. This is also the student's home lab.

### 2.8 Troubleshooting tools
`ping`, `tracert`/`traceroute`, `nslookup`, `dig`, `ipconfig`/`ifconfig`/`ip`, `netstat`/`ss`, `arp`, `route`, `iptables`, `nmap` (port scanner), `tcpdump`/Wireshark (packet sniffers and protocol analyzers). **Mastery:** for a given symptom ("site won't load"), choose the right tool, predict output, and interpret it.

### 2.9 Authentication methodologies
Kerberos, RADIUS, LDAP, SSO, certificates, local auth. **Mastery:** explain what each does and where it is used (Kerberos/LDAP in Active Directory, RADIUS for WiFi/VPN).

**Practice:** build a two-VM network in VirtualBox, capture traffic with Wireshark while loading a page, and identify DNS, TCP handshake, and HTTP in the capture.

---

## Stage 3: Security foundations

**Needs first:** Stage 2 (especially OSI, ports, TLS, authentication).

| Topic | Mastery check |
|---|---|
| **CIA Triad** | Classify an incident as a confidentiality, integrity, or availability failure. |
| Authentication vs authorization; MFA and 2FA | Give an everyday example of each, and explain why MFA stops most password attacks. |
| Understand the definition of risk | Explain risk = threat x vulnerability x impact, with an example. |
| Defense in depth | Name at least 5 layers for protecting one asset. |
| Perimeter vs DMZ vs segmentation | Draw a small network with all three. |
| Core concepts of Zero Trust | Explain "never trust, always verify" and contrast with a castle-and-moat model. |
| Roles of compliance and auditors | Explain why companies follow standards and what auditors check. |
| Understand backups and resiliency | Explain the 3-2-1 rule and why untested backups are not backups. |
| Understand the concept of isolation | Give examples (VMs, sandboxes, containers, network segments). |
| Basics of cryptography: salting, hashing, key exchange, PKI, private vs public keys, obfuscation | Explain hashing vs encryption vs encoding, why passwords are salted, how asymmetric keys enable HTTPS, and why obfuscation is not security. |
| Understand handshakes | Walk through the TCP 3-way handshake, then give the idea of the TLS handshake. |
| False/true positive/negative | Given a scenario, label it correctly and say which error is more dangerous in that context. |
| Blue / Red / Purple teams | Explain each role and why purple exists. |
| Basics of threat intelligence and OSINT | Describe what OSINT is and give two legitimate uses. |

**Frameworks and standards** (teach once the student has seen real incidents; frameworks are boring without examples):
- Frameworks: **MITRE ATT&CK**, **Diamond Model**, **Cyber Kill Chain**. Mastery: map one real-style attack story onto kill chain stages.
- Standards: ISO (27001), NIST (CSF, RMF), CIS controls. Mastery: say what each is for in one sentence.

---

## Stage 4: Tools, logs, and hardening

**Needs first:** Stage 2 tools and Stage 3 foundations.

### 4.1 Common security tools and environments
- Distros for security work: **Kali Linux, ParrotOS**.
- Common tools to *understand* (what problem they solve and when a professional uses them): scanners (nmap), packet analysis (Wireshark, tcpdump), forensics (FTK Imager, Autopsy, WinHex, memdump), Linux text tools for investigation (`grep`, `cat`, `head`, `tail`, `dd`), network utilities (`curl`, `hping`, `dig`, `nslookup`).
- Exploit frameworks and hacking tools: teach what they are, their role in authorized penetration testing, and the defender's view. Reference sites for living-off-the-land techniques (**LOLBAS, GTFOBins, WADComs**) belong in the intermediate/advanced stage: teach them as defender and pentester references (what native tools can be abused, and how to detect that), and only for authorized or lab use.
- **LOLBAS / "using tools for unintended purposes":** the idea that attackers abuse legitimate built-in tools. Mastery: explain why this is hard to detect.

### 4.2 Logs and monitoring (learn how to find and use these)
Event logs, syslog, NetFlow, packet captures, firewall logs. Plus **SIEM** and **SOAR**. **Mastery:** given a short log excerpt, find the suspicious event and say what it suggests.

### 4.3 IDS and IPS, honeypots, security devices
IDS/IPS (NIDS, NIPS, HIPS), firewalls and next-gen firewalls, host-based firewalls, sandboxing, antivirus/anti-malware, **EDR**, **DLP**, ACLs. **Mastery:** place each device on a network diagram and say whether it detects, prevents, or both.

### 4.4 Hardening concepts
Operating system hardening, MAC-based and NAC-based controls, port blocking, group policy, sinkholes, ACLs, patching, jump servers, endpoint security. **Mastery:** given a fresh server, list 8 hardening steps and justify each.

### 4.5 Secure vs insecure protocols
FTP vs SFTP, SSL vs TLS, IPsec, DNSSEC, LDAPS, SRTP, S/MIME. **Mastery:** match each insecure protocol to its secure replacement and say what the secure one adds.

### 4.6 Wireless security
EAP vs PEAP, WPS, WEP vs WPA vs WPA2 vs WPA3. **Mastery:** rank them by strength and explain why WEP and WPS are broken.

### 4.7 Analysis helpers
VirusTotal, Joe Sandbox, any.run, urlvoid, urlscan, WHOIS. **Mastery:** given a suspicious URL (in a safe context), explain how to check it without visiting it blindly. Note: never upload sensitive or private files to public scanners.

---

## Stage 5: Attacks and defenses

**Needs first:** Stages 2-4. For every attack: *how it works, what it looks like, how to detect, how to prevent.*

**Social engineering family:** phishing, vishing, whaling, smishing, spam vs spim, shoulder surfing, dumpster diving, tailgating, impersonation, reconnaissance, watering hole attack, drive-by attack, typosquatting.
**Mastery:** classify a described attack, and name the human weakness it exploits (urgency, authority, trust).

**Password attacks:** brute force vs password spray. **Mastery:** explain the difference and which a lockout policy stops better.

**Network attacks:** DoS vs DDoS, MITM, spoofing, evil twin, rogue access point, deauth attack, DNS poisoning, VLAN hopping, replay attack, pass-the-hash.
**Mastery:** match each to the layer it attacks and the control that stops it.

**Application and system attacks:** SQL injection, XSS, CSRF, directory traversal, buffer overflow, memory leak, privilege escalation, **OWASP Top 10**.
**Mastery:** explain each at the concept level, recognize a vulnerable pattern in a short, harmless, illustrative snippet, and give the fix (parameterized queries, output encoding, CSRF tokens, input validation).

**Malware:** how malware works and its types (virus, worm, trojan, ransomware, spyware, rootkit...). **Mastery:** classify by behavior, not by name.

**Threat classification:** zero-day, known vs unknown threats, APT. **Mastery:** explain why zero-days are dangerous and how defense in depth still helps.

---

## Stage 6: Incident response, forensics, and threat work

**Needs first:** Stages 3-5.

| Topic | Mastery check |
|---|---|
| **Incident response process:** Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned | Put a scenario's actions in the correct phase and explain why containment comes before eradication. |
| Understand runbooks | Write a short runbook for "suspected phishing email reported by an employee". |
| Basics of forensics | Explain evidence handling, order of volatility, and chain of custody. |
| Threat hunting basics | Explain how proactive hunting differs from alert-driven work. |
| Vulnerability management basics | Describe the cycle: discover, prioritize, remediate, verify. |
| Basics of reverse engineering | Explain what it is and when defenders use it (conceptual only at this stage). |
| Penetration testing rules of engagement | Explain scope, authorization, and reporting. |
| Understand the audience: stakeholders, HR, legal, compliance, management | Explain how you would tell a non-technical manager about an incident. Communication is a core security skill. |

---

## Stage 7: Cloud skills

**Needs first:** Stage 2 (networking), Stage 3 (identity, crypto).

| Topic | Mastery check |
|---|---|
| Security in the cloud; cloud vs on-premises | Explain the **shared responsibility model**, the single most tested cloud idea. |
| Deployment flow in the cloud | Describe the general steps from code to running service. |
| Cloud service models: **SaaS, PaaS, IaaS** | Place an example on each and say who secures what. |
| Cloud models: private, public, hybrid | Give a use case for each. |
| Common environments: **AWS, GCP, Azure** | Name one equivalent service across the three (storage, compute, identity). |
| Infrastructure as Code | Explain why IaC helps (repeatable) and a security risk (leaked secrets, misconfigurations copied at scale). |
| Serverless | Explain what changes for the defender when there are no servers to patch. |
| Common cloud storage: S3, Dropbox, Box, OneDrive, Google Drive, iCloud | Explain the classic risk of publicly exposed storage buckets. |

**Practice:** make a free-tier account on one provider, create a storage bucket, make it private, and explain what each permission does.

---

## Stage 8: Programming (run in parallel from Stage 1-2)

Languages from the map: **Python, Go, JavaScript, C++, Bash, PowerShell.**

- **Bash** (start in Stage 1 with Linux) and **PowerShell** (start with Windows): automate the daily tasks they already do by hand.
- **Python** (start in Stage 2-3): scripts for log parsing, simple network utilities, automating checks. The best first language for security.
- **JavaScript:** needed to understand web attacks (XSS) and defenses.
- **C++ / Go:** later. C/C++ teaches how memory bugs (buffer overflows) arise; Go is common in modern security tooling.

**Teaching rule:** teach programming by solving small security problems ("count failed logins in this log file"), not abstract exercises. Motivation and retention both go up.

---

## Parallel track A: CTFs and labs

Start early; these make the concepts real. Suggested progression:

1. **TryHackMe** - guided, beginner-friendly paths. Best first platform.
2. **picoCTF** - beginner-friendly puzzles across categories (crypto, forensics, web, binary).
3. **VulnHub** - download intentionally vulnerable VMs and attack them in the home lab.
4. **HackTheBox** - harder, less hand-holding; for intermediate students.
5. **SANS Holiday Hack Challenge** - seasonal, story-driven, great learning with hints.

**Teaching rule for CTFs:** after every challenge, have the student write a short **write-up** (what I tried, what worked, what I learned, how it would be detected/prevented). Writing it is the retention. Platform contents change, so suggest "search for beginner paths on X" instead of inventing exact names.

---

## Parallel track B: Certifications

Certifications give structure and prove skills. Order matters; don't rush into advanced ones.

**Beginner:** CompTIA A+ (hardware/OS), Network+ (networking), Linux+, Security+ (the standard first security certification), CCNA (Cisco networking, deeper).
**Advanced:** CEH, CISA, CISM, GSEC, GPEN, GWAPT (GIAC family), OSCP (hands-on offensive exam, very respected), CREST (pen-testing bodies), CISSP (broad management-level; typically needs years of experience, so check current requirements).

**Suggested paths:**
- *Aim: SOC / blue team:* Security+ -> a blue-team/defender cert -> GIAC options.
- *Aim: pentesting:* Network+ and Security+ -> CTF practice -> OSCP.
- *Aim: management/GRC:* Security+ -> CISM/CISA -> CISSP.
- *Unsure:* Security+ is a safe first target for almost everyone.

Prices, exam formats, and requirements change. Encourage checking the official cert page, or search for current info before giving specifics.

---

## Suggested pacing (adjust to the student)

| Weekly hours | Realistic rhythm |
|---|---|
| 3-5 h | One topic per week, one small lab, one short review quiz. Stage 0-2 take ~6-9 months. |
| 6-10 h | Two topics per week, one lab, weekly mixed quiz, start a CTF track. |
| 10+ h | Add a certification study plan in parallel and daily short reviews. |

**Weekly rhythm template:** Day 1-2 learn (Teaching Loop) -> Day 3 hands-on lab -> Day 4 explain-it-back and flashcards -> Day 5 mixed quiz -> weekend: spaced review of older topics. Repeat.