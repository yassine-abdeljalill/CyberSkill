# Analogy Bank

Everyday mental models for core cybersecurity ideas. Use them as a **first handle** on a concept, then replace them with the precise definition.

**How to use an analogy well**
1. State it simply, tied to the concept.
2. Map the parts explicitly ("the address is the IP, the apartment number is the port").
3. **Say where it breaks.** Every analogy lies somewhere; naming that spot prevents misconceptions and deepens understanding.
4. Better still, after you give one, ask the student to extend it ("what would a *fake* delivery person be in this picture?"). Inventing their own analogy is a strong learning move.
5. If one analogy does not land, offer a different one. Do not repeat the same words louder.

Contents: Networking | Security concepts | Cryptography | Attacks | Defense | Cloud | Process

---

## Networking

| Concept | Analogy | Where it breaks |
|---|---|---|
| **IP address** | A home street address. Tells the network where to deliver. | Home addresses rarely change; IPs often do (DHCP). |
| **Port** | The apartment or door number inside the building. IP finds the building, port finds the door (web is door 443, SSH is door 22). | Ports are virtual; a "door" can be opened or closed by software. |
| **DNS** | The phone's contact list: names to numbers. | DNS is a distributed hierarchy, not one list. |
| **DHCP** | A hotel front desk handing each new guest a room number for their stay. | Rooms (leases) expire and get reassigned. |
| **Router** | A traffic roundabout/post office that sends packets toward the right city (network). | Real routers also apply rules and NAT. |
| **Switch** | A mail clerk inside one office building who knows which desk (device) each letter goes to. | Works with MAC addresses within one network. |
| **NAT** | A company receptionist: many employees call out through one main phone number. | Inbound calls need extra setup (port forwarding). |
| **OSI model** | Mailing a letter: write it (application), put it in an envelope (transport), add the address (network), hand to the courier truck (data link), the road itself (physical). | Real protocols do not always follow the 7 layers strictly. |
| **TCP handshake** | Phone call start: "Hello?" -> "Hello, can you hear me?" -> "Yes, I can." Both sides confirm before talking. | Only for TCP; UDP just starts talking. |
| **TCP vs UDP** | Registered mail with a signature (TCP) vs a postcard (UDP): reliable and slower vs fast and might get lost. | Not literally mail; UDP is used for streaming and DNS. |
| **VLAN** | Separate colored lanes in a shared swimming pool: same pool, different groups kept apart. | Misconfiguration can let swimmers cross lanes (VLAN hopping). |
| **DMZ** | The lobby of a building: visitors can enter the lobby but not the private offices. | Lobby servers are still attackable and must be hardened. |
| **VPN** | A private, sealed tunnel through a public road. | The tunnel protects the road, not the destination: the other end can still be hostile. |
| **Subnet mask** | A cookie cutter showing which part of the address is the "neighborhood" and which is the "house". | -- |
| **Default gateway** | The town's exit road: the way out of your neighborhood. | -- |

## Security concepts

| Concept | Analogy | Where it breaks |
|---|---|---|
| **CIA triad** | A bank: Confidentiality = only you see your account; Integrity = nobody can quietly change your balance; Availability = the bank is open when you need it. | Real systems trade these off against each other. |
| **Authentication vs authorization** | Airport: passport check proves who you are (authN); boarding pass decides which plane you may board (authZ). | -- |
| **MFA** | A door that needs a key *and* a fingerprint: stealing one is not enough. | Weak second factors (SMS) can still be tricked. |
| **Defense in depth** | A castle: moat, walls, gate, guards, locked rooms, a safe. | Digital layers can share the same flaw. |
| **Zero Trust** | A building where every door checks your badge every time, even for employees. | Costs speed and complexity. |
| **Least privilege** | Giving a house-sitter only the front-door key, not the safe key. | -- |
| **Risk** | Walking in a stormy area: the chance of lightning (threat), your metal umbrella (vulnerability), and what you would lose (impact). | -- |
| **False positive / negative** | Smoke alarm: goes off for burnt toast (false positive) vs stays silent in a real fire (false negative). | -- |
| **Firewall** | A security guard at the gate checking a list of who may pass. | Cannot stop an attacker who is already inside or who is on the allowed list. |
| **IDS vs IPS** | IDS is a burglar alarm (tells you); IPS is a guard who stops the burglar. | IPS can block legitimate users if it is wrong. |
| **Honeypot** | A fake safe left out to see who tries to break in. | Must be isolated, or the trap becomes a path in. |
| **Sandbox** | A test tube: examine a dangerous thing without letting it touch the rest of the lab. | Advanced malware may detect it is in a sandbox. |
| **Patching** | Fixing a known weak lock before burglars find out about it. | Patching can break things, so teams test first. |
| **Backups** | A spare house key stored somewhere else; useless if you never test it. | -- |
| **Hardening** | Removing all unneeded doors and windows from a building. | -- |
| **Segmentation** | Watertight compartments on a ship: a leak in one does not sink the ship. | -- |

## Cryptography

| Concept | Analogy | Where it breaks |
|---|---|---|
| **Hashing** | A fingerprint: unique to the person, you cannot rebuild the person from it. | Different inputs can in theory share a hash (collisions); good hashes make that practically impossible. |
| **Salting** | Adding a unique pinch of random "spice" to each password before blending, so two identical passwords look different. | Salt is stored openly; its job is to stop precomputed lookups, not to be secret. |
| **Symmetric encryption** | One key that locks and unlocks a box; both people need a copy. | The hard problem is sharing the key safely. |
| **Asymmetric encryption** | A mailbox: anyone can drop a letter in (public key), only the owner with the key can open it (private key). | Digital signatures work the other way round: sign with private, verify with public. |
| **Key exchange** | Two people mixing paint colors in public so both end up with the same secret shade that onlookers cannot recreate. | The paint-mixing story simplifies the math (Diffie-Hellman). |
| **PKI / certificates** | A passport office: a trusted authority vouches that this public key belongs to this website. | If the authority is compromised, trust breaks. |
| **TLS handshake** | Meeting a stranger: check their ID (certificate), agree on a secret code, then talk privately. | -- |
| **Encoding vs encryption vs hashing** | Encoding = translating to another alphabet (anyone can reverse); encryption = locked box (key needed); hashing = one-way fingerprint. | -- |
| **Obfuscation** | Writing a note in messy handwriting: harder to read, not secret. | Not security on its own. |

## Attacks

| Concept | Analogy | Where it breaks |
|---|---|---|
| **Phishing** | A fake bank letter with a convincing logo asking for your PIN. | Modern phishing can be very targeted (spear phishing). |
| **Social engineering** | Convincing the guard to open the door by acting like you belong. | -- |
| **Brute force vs password spray** | Brute force: trying every key on one lock. Password spray: trying one common key on every lock in the building. | Spray avoids lockouts, which is why it works. |
| **DoS / DDoS** | Hundreds of people calling one shop at once so real customers cannot get through. | -- |
| **MITM** | A mail carrier who secretly opens, reads, and reseals letters. | Encryption and certificates are the defense. |
| **Spoofing** | Putting a fake return address on an envelope. | -- |
| **DNS poisoning** | Someone swaps the numbers in the phone book so "Mom" now rings a scammer. | -- |
| **Evil twin / rogue AP** | A fake "Free Airport WiFi" hotspot that looks real. | -- |
| **SQL injection** | Writing extra instructions in a form field that the system mistakenly treats as commands, like writing "and also give me the safe's contents" on a bank slip and the clerk obeys. | -- |
| **XSS** | Leaving a booby-trapped note on a public noticeboard that runs when others read it. | -- |
| **CSRF** | Tricking you, while logged in, into signing a form you did not mean to sign. | -- |
| **Buffer overflow** | Pouring a liter of water into a cup that holds half: it spills onto things it should not touch. | -- |
| **Privilege escalation** | A visitor badge that somehow works on the manager's floor. | -- |
| **Replay attack** | Recording a valid "open sesame" and playing it back later. | -- |
| **Pass-the-hash** | Using a copied key *template* instead of the original password. | -- |
| **Typosquatting** | A shop called "Amazom" waiting for people who mistype. | -- |
| **Watering hole** | Poisoning the one river that a specific group drinks from. | -- |
| **Zero-day** | A burglar finding a flaw in a lock before the manufacturer knows it exists: zero days to prepare a fix. | -- |
| **Ransomware** | Locking your files in a safe and demanding payment for the code. | Paying does not guarantee recovery. |
| **Living off the land (LOLBAS)** | A burglar using the house's own tools instead of bringing theirs, so nothing looks unusual. | -- |

## Cloud

| Concept | Analogy | Where it breaks |
|---|---|---|
| **IaaS / PaaS / SaaS** | Pizza as a service: IaaS = buy ingredients and kitchen, PaaS = use a kitchen but you cook, SaaS = order delivered ready to eat. The more you outsource, the less you manage and the less you control. | -- |
| **Shared responsibility** | A rented apartment: the landlord secures the building, you lock your own door. | The dividing line shifts with each service model. |
| **Infrastructure as Code** | A recipe for your whole data center that can be rebuilt exactly, on demand. | A flawed recipe makes a hundred flawed copies. |
| **Serverless** | Taking a taxi instead of owning a car: pay per ride, no maintenance. | Servers still exist, someone else runs them. |

## Process

| Concept | Analogy | Where it breaks |
|---|---|---|
| **Incident response phases** | Fighting a fire: prepare (extinguishers), spot the fire, contain it (close doors), put it out, rebuild, then investigate how to prevent the next. | -- |
| **Chain of custody** | The paper trail that proves evidence was not tampered with between collection and court. | -- |
| **Red / Blue / Purple team** | Red = sparring partner attacking, Blue = defenders, Purple = coach helping both learn from each round. | -- |
| **Threat hunting** | A detective actively searching for clues instead of waiting for the alarm. | -- |
| **Vulnerability management** | Regular home inspections plus a repair schedule, ranked by danger. | -- |

---

**If a concept is not listed:** build an analogy on the spot using this recipe: (1) What *job* does it do? (2) Where does everyday life have that same job? (3) What does each part map to? (4) Where does it break?