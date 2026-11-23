# Teaching Techniques: How to Apply Them

Read this when you want concrete wording and procedures for the memory techniques named in `SKILL.md`. Every technique has: *what it is*, *why it works*, *how to run it*, and *sample wording*.

## Contents
1. Active recall (retrieval practice)
2. Spaced repetition
3. Feynman technique (teach-back)
4. Interleaving
5. Elaboration ("why" questions)
6. Worked examples and fading
7. Dual coding (visuals)
8. Confidence calibration
9. Mnemonics and chunking
10. Hands-on learning and write-ups
11. Diagnosing misconceptions
12. Motivation and momentum
13. Quick reference: pick a technique for the situation

---

## 1. Active recall (retrieval practice)

**What:** the student pulls information from memory without looking.
**Why:** the effort of retrieving is what strengthens memory. Recognizing something ("oh yes, that looks familiar") is much weaker than producing it.
**How:**
- Ask open questions before showing the answer: "What are the three parts of the CIA triad?" not "The CIA triad has confidentiality, integrity, and availability, right?"
- Use short blank-filling and "what happens if" questions.
- Do a 2-3 question warm-up at the start of every session on older material.
- If they cannot recall, give a *cue* (first letter, a related fact), not the answer.

**Sample wording:**
- "Without scrolling up: what does the 'S' in HTTPS add, and why does it matter?"
- "Quick warm-up from last time: what is the difference between a hash and encryption?"

## 2. Spaced repetition

**What:** reviewing a topic at increasing gaps.
**Why:** forgetting is natural; each review just before forgetting makes the memory last longer.
**How:**
- Schedule reviews at about **1 day -> 3 days -> 1 week -> 3 weeks -> 2 months**.
- When a review answer is correct and fast, move to the next gap. If wrong, move back one step.
- Keep reviews short (5-10 minutes) and as questions, not re-reading.
- Track due items in the Save Point.
- Offer flashcards (see `templates.md`) for Anki or Quizlet, which do the scheduling automatically.

**Sample wording:** "It's been about a week since we did subnetting. Quick check: how many usable hosts in a /26? Show me how you worked it out."

## 3. Feynman technique (teach-back)

**What:** the student explains the concept in plain words, as if to a friend with no background.
**Why:** vague understanding hides until you try to explain. Gaps appear immediately.
**How:**
1. Ask them to explain it simply.
2. Listen for: jargon used without meaning, skipped steps, "it just does that".
3. Point to *one* gap and ask a follow-up ("what actually happens in that step?").
4. Have them re-explain the fixed part.
5. Optionally: you play a curious 12-year-old who keeps asking "but why?".

**Sample wording:** "Explain how HTTPS keeps a password safe, as if talking to a friend who has never studied tech. Don't worry about being perfect; I'm looking for the gaps."

## 4. Interleaving

**What:** mixing different topics in practice rather than finishing one before starting another.
**Why:** it forces the brain to *choose* the right method each time, which is exactly what exams and real incidents demand. It feels harder and works better.
**How:** in quizzes and reviews, alternate topics: DNS -> hashing -> firewall -> phishing -> subnetting. Include "which one is this?" classification questions (is this phishing, vishing, or smishing?).

## 5. Elaboration ("why" questions)

**What:** connecting a fact to reasons, causes, and consequences.
**Why:** facts with reasons are stored with hooks, so they are easier to retrieve and apply.
**How:** keep asking:
- "Why was it designed this way?"
- "What would break if we removed this?"
- "How is this similar to / different from X?"
- "What would an attacker do about this? What would a defender do?"

**Sample wording:** "Telnet sends passwords in plain text. Why is that a problem, and which tool could an attacker on the same WiFi use to see it?"

## 6. Worked examples and fading

**What:** study a fully solved example, then solve with less and less help.
**Why:** beginners learn faster from examples than from solving blind; gradually removing help builds independence.
**How:**
1. **I do:** solve a problem aloud, explaining each decision.
2. **We do:** solve a similar one together; you ask guiding questions.
3. **You do:** a new variant, with a hint available.
4. **You do alone:** a harder variant, no hints.

Works well for subnetting, log analysis, reading Wireshark output, writing a firewall rule, and cert-style scenario questions.

## 7. Dual coding (words + visuals)

**What:** presenting information both verbally and as a picture.
**Why:** two memory routes are better than one.
**How:**
- Draw layer models (OSI), flows (handshakes), topologies (star/ring/mesh/bus), kill chains, and network diagrams with DMZ and segments.
- Use comparison tables for look-alike pairs (symmetric vs asymmetric, IDS vs IPS, TCP vs UDP).
- Ask the student to **draw it from memory** and compare.

## 8. Confidence calibration

**What:** the student rates how sure they are before the answer is revealed.
**Why:** it trains self-awareness and makes "confidently wrong" corrections stick (the surprise is memorable). It also shows what they *think* they know vs what they know.
**How:** "Before you answer: confidence 1-5?" Compare confidence to correctness afterwards, and discuss high-confidence misses. Do this occasionally, not every question.

## 9. Mnemonics and chunking

**What:** compressing lists into memorable pieces.
**Why:** working memory holds about 4 chunks; mnemonics bundle many items into one.
**How:**
- Use well-known ones (OSI: *Please Do Not Throw Sausage Pizza Away* = Physical, Data link, Network, Transport, Session, Presentation, Application).
- Chunk long lists into groups of 3-4 (the IR phases: *Prepare -> Detect -> Contain -> Remove -> Recover -> Learn*).
- Ask the student to make their own (funny or personal sticks best). A mnemonic in their native language is perfectly good.
- Pair every mnemonic with the meaning; a mnemonic without understanding collapses under pressure.

## 10. Hands-on learning and write-ups

**What:** doing the thing in a safe lab, then writing it up.
**Why:** skills are procedural memory; they need practice. Writing forces clear thinking.
**How:**
- After a concept, give one tiny task: "Run `ping` to your gateway and tell me what the `ttl` number suggests."
- After a lab/CTF challenge, ask for a **mini write-up** (4 lines): Goal / What I tried / What worked / What defenders would notice.
- Ask them to predict a result before running a command, then compare.
- Encourage them to keep a personal knowledge base (notes app) of commands, write-ups, and "mistakes I made".

## 11. Diagnosing misconceptions

Common confusions in cybersecurity learners, worth probing for:

| Confusion | Probe question |
|---|---|
| Encryption = hashing = encoding | "Can you get the original back? Do you need a key?" |
| Authentication = authorization | "Proving who you are vs what you may do. Which is a passport, which a boarding pass?" |
| HTTPS means the site is safe | "HTTPS means the connection is private. Can a phishing site have HTTPS?" |
| VPN makes you anonymous/safe | "Who can see your traffic at the VPN's end?" |
| Antivirus = full protection | "What can an antivirus not see (zero-days, social engineering)?" |
| Hacking tool = illegal tool | "What makes a nmap scan legal or illegal?" (authorization) |
| Private browsing = invisible | "Who can still see your activity?" |
| Strong password alone is enough | "What if the site itself is breached?" |
| Subnet and VLAN are the same | "One is addressing (layer 3), one is switching separation (layer 2)." |

Method: ask the probe, let them answer, find the root belief, correct it, then ask a variant.

## 12. Motivation and momentum

- Keep **early wins** small and frequent (the first successful `nmap` on their own lab VM, the first solved picoCTF).
- Show **progress**: "Two weeks ago you could not read this output; now you did it alone."
- Connect to their **goal** (job, cert, CTF rank) often.
- Normalize difficulty: subnetting, crypto, and protocol details confuse almost everyone at first.
- Offer **choice**: "Want a diagram, an analogy, or a quick example next?"
- End sessions on a **success**, with a clear next step, and a Save Point.

## 13. Quick reference: which technique, when

| Situation | Reach for |
|---|---|
| Brand-new concept | Analogy -> worked example -> check question |
| Student nods but answers vaguely | Feynman teach-back |
| Looks-alike concepts get mixed up | Comparison table + interleaved quiz |
| Long list to memorize | Mnemonic + chunking + flashcards |
| Skill (subnetting, logs, commands) | Worked example -> fading -> lots of practice |
| Returning after a break | Warm-up recall + spaced review |
| Student frustrated | Shrink step, show progress, change angle |
| Preparing for an exam | Cert-style questions + explain every option + timed mixed quizzes |
| Concept feels abstract | Hands-on lab + write-up |