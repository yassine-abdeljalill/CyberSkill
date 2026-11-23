# Templates

Reusable formats for study materials. Adapt length and depth to the student's level. Keep them tidy so the student can paste them into a notes app.

## Contents
1. Concept lesson skeleton
2. Tool lesson skeleton
3. Attack-and-defense lesson skeleton
4. Quiz formats
5. Flashcards (and CSV export)
6. One-page cheat sheet
7. Weekly study plan
8. Lab / CTF write-up
9. End-of-session wrap-up

---

## 1. Concept lesson skeleton

Use for ideas like CIA triad, DNS, Zero Trust, hashing.

```
Why it matters:  (1-2 sentences, real scenario)
Analogy:         (everyday picture, + where it breaks)
30-second version: (plain words)
Details:         (layer 2: define terms as they appear)
Example:         (one concrete case, step by step; diagram if structural)
Security angle:  (how it is attacked / protected)
Check:           (1-2 thinking questions)   <- stop here and wait
Anchor:          (one-liner or mnemonic)
Connects to:     (earlier and upcoming topics)
```

## 2. Tool lesson skeleton

Use for nmap, Wireshark, dig, tcpdump, grep, Autopsy, etc.

```
Problem it solves:     (when would a pro reach for this?)
Safe place to run it:  (own lab VM / authorized target only)
Basic command:         (smallest useful command, each part explained)
Predict:               (ask the student what they expect to see)
Read the output:       (line-by-line: what each field means)
What it tells you:     (the conclusion a defender or tester draws)
Common mistakes:       (and how to fix)
Detect/defend view:    (what this activity looks like in logs; how to protect)
Practice task:         (tiny, specific, with an expected result to compare)
```

Reminder: use tools only on systems the student owns or is authorized to test. Teach the output-reading skill as much as the command.

## 3. Attack-and-defense lesson skeleton

Use for phishing, MITM, SQL injection, ransomware, etc. Stay at concept, detection, and prevention level; no ready-to-use weaponized code.

```
The story:        (short realistic incident or scenario)
Goal of attacker: (what do they want: credentials, data, access, disruption?)
How it works:     (concept, step by step, in plain words)
Kill chain stage / ATT&CK tactic:  (where it fits)
What it looks like: (logs, traffic, user experience, indicators of compromise)
How to detect:    (tools, alerts, logs)
How to prevent:   (controls, ranked: quick wins -> strong fixes)
How to respond:   (first three actions, link to IR phases)
Practice:         (legal lab idea, e.g. intentionally vulnerable app / CTF category)
Check:            (scenario question)
```

## 4. Quiz formats

**Rules:** mix topics (interleaving). Mix types. Ask one question at a time unless the student wants a batch. Give feedback after each answer. Never reveal the answer in the question text.

### 4a. Question types
- **Recall:** "What port does HTTPS use by default?"
- **Explain-why:** "Why do we salt passwords?"
- **Compare:** "TCP vs UDP: which would you use for a video call and why?"
- **Scenario:** "An employee reports an email from the 'CEO' asking for gift cards. What type of attack is this and what do you do first?"
- **Spot the mistake:** "This firewall rule allows any source to port 22 on the whole network. What is wrong?"
- **Classify:** "A caller pretends to be IT and asks for your password. Phishing, vishing, or smishing?"
- **Order the steps:** "Put these incident response phases in order."
- **Log reading:** short log excerpt; "what happened here?"

### 4b. Cert-style multiple choice
```
Q: <scenario or question>
A) ...  B) ...  C) ...  D) ...
```
After the student answers, give:
```
Correct: C
Why C is right: ...
Why A is wrong: ...  (the specific misconception it tests)
Why B is wrong: ...
Why D is wrong: ...
Exam tip: (keyword or pattern to spot)
```

### 4c. Quiz wrap-up
```
Score: x/5
Strong: (topics)
Shaky: (topics) - what exactly went wrong
Do next: (2-3 specific actions, e.g. "redo subnetting practice; re-explain TLS in your own words")
Review due: (date)
```

## 5. Flashcards

**Rules:** one fact per card (atomic), question on front that forces recall, short answer on back, optional "why/hook" line. Avoid yes/no cards. Make some scenario cards, not only definitions.

```
Front: What does the 'availability' part of the CIA triad protect?
Back:  Systems and data are accessible when needed (e.g. protection against DDoS and hardware failure).
Hook:  The bank must be open when you need it.
Tags:  security-foundations, CIA
```

**CSV export** (for Anki / Quizlet import), when asked:
```
Front,Back,Tags
"What does the 'availability' part of the CIA triad protect?","Systems and data are accessible when needed (e.g. DDoS protection, redundancy).","foundations CIA"
```
Save as a `.csv` file and present it if file tools are available. Quote fields that contain commas.

## 6. One-page cheat sheet

```
# <Topic> cheat sheet
**In one sentence:** ...
**Key terms:** term - plain meaning (3-8 items)
**How it works:** (3-5 step list or small diagram)
**Compare:** (small table of look-alikes)
**Security angle:** attacks | defenses | logs to check
**Commands / tools:** (only the essential 3-6)
**Common mistakes:** ...
**Remember:** (mnemonic / anchor)
**Test yourself:** 3 questions
```
Keep it to one page. A cheat sheet that is too long is just a textbook.

## 7. Weekly study plan

First ask: goal, hours per week, deadline, current level. Then:

```
# Plan: <goal> | <hours>/week | <N> weeks

Week 1: <Topic from roadmap>
  Learn:   (2 sessions: Teaching Loop)
  Lab:     (1 hands-on task, e.g. build a VM network)
  Recall:  (flashcards, explain-it-back)
  Quiz:    (5 mixed questions on Friday)
  Done when: (the mastery checks from the roadmap for this topic)

Week 2: ...
Every 4th week: review week (spaced review + mixed quiz + one write-up) - no new topics.
```
Make it realistic: better a plan the student actually follows at 4 hours/week than a heroic plan they abandon. Build in a lighter week every month.

## 8. Lab / CTF write-up template

```
Challenge / lab:   
Date:
Goal:              (what was I trying to achieve?)
What I tried:      (steps, including dead ends)
What worked:       
Key concept used:  (link to a roadmap topic)
Tools/commands:    
What defenders would see: (logs, alerts) / how to prevent it
What I learned:    (one sentence)
What I still don't understand:
```
Writing the last line is what drives the next study session.

## 9. End-of-session wrap-up

Close every substantial session with:

```
Today you learned: (2-4 bullets in plain language)
You showed you can: (what they actually did/answered correctly)
Still shaky: (honest and kind)
Try before next time: (one small task, ~15 minutes)
Next session: (what's coming)
```
Then offer: flashcards, a cheat sheet, and a **Save Point** block they can paste into their next chat.