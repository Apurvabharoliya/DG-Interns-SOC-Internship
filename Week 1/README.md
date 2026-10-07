# DG Interns Hub - SOC Analyst Internship

## Week 1 - The Basics: Security and the SOC

Welcome to my Week 1 submission. This README is the master index for the entire week: it shows the
folder structure, what each document contains, the hands-on lab work, and every deliverable produced.

| **Programme** | DG Interns Hub - SOC Analyst Internship |
| **Week** | Week 1 - The Basics: Security and the SOC |
| **Theme** | Security fundamentals and the Security Operations Center |
| **Submission deadline** | 07 October 2026, 11:59 PM |
| **Lab host** | `DESKTOP-QKP3UOG` (Windows 10 virtual machine) |

---

## Folder Structure

```
DG Interns Hub
    |
    |-- Week 1
            |
            |-- Notes/                                   # Theory - one file per question
            |       |-- 01 What is a SOC.docx.pdf
            |       |-- 02 SOC Analyst Levels L1 L2 L3.docx.pdf
            |       |-- 03 CIA Triad.docx.pdf
            |       |-- 04 TCP IP vs OSI Model.docx.pdf
            |       |-- 05 Phishing.docx.pdf
            |       |-- 06 Malware Case Study.docx.pdf
            |
            |-- Writeups/                                # Labs - one file per lab/room
            |       |-- LetsDefend-SOC-Fundamentals-Walkthrough.pdf
            |       |-- TryHackMe-Cyber-Kill-Chain-Walkthrough.pdf
            |       |-- TryHackMe-Introductory-Networking-Walkthrough.pdf
            |       |-- TryHackMe-SOC-Role-In-Blue-Team-Walkthrough.pdf
            |       |-- TryHackMe-Windows-Fundamentals-1-Walkthrough.pdf
            |       |-- Tryhackme Walkthrogh What is networking.pdf
            |
            |-- Findings Folder/                         # Hands-on - Event Viewer screenshots
            |       |-- Event_4624_Account_Successful_Logon.png
            |       |-- Event_4625_Account_Failed_Logon.png
            |       |-- Event_4688_Process_Creation.png
            |       |-- Event_4720_User_Account_Created.png
            |       |-- Windows_Security_Event_Findings.pdf      # Standalone findings report
            |
            |-- Week 1 Report - Weekly Work.pdf          # PDF report of the weekly work
            |-- Week 1 Presentation - Weekly Work.pptx   # Presentation report of the weekly work
            |-- README.md                                # This file - the whole week, structured
            |-- LinkedIn Posts.md                        # Ready-to-publish LinkedIn posts
```

---

## 1. Theory - `Notes/` (6 documents, 19 pages)

Each question from the brief is answered in its own document, in my own words, using bullet points
and tables.

| # | Topic | File | Pages | Covers |
|---|-------|------|-------|--------|
| 01 | What is a SOC? | `01 What is a SOC.docx.pdf` | 3 | Definition, main objectives, the SOC workflow, what a SOC monitors, SIEM / EDR / SOAR / threat intel, analyst duties |
| 02 | SOC Analyst Levels | `02 SOC Analyst Levels L1 L2 L3.docx.pdf` | 3 | L1 triage, L2 investigation, L3 advanced analysis, worked examples per tier, comparison table |
| 03 | The CIA Triad | `03 CIA Triad.docx.pdf` | 2 | Confidentiality, Integrity, Availability - controls, example attacks, banking scenario |
| 04 | TCP/IP vs OSI Model | `04 TCP IP vs OSI Model.docx.pdf` | 4 | All 7 OSI layers, the 4-layer TCP/IP model, layer mapping, TCP vs UDP, example web request |
| 05 | Phishing | `05 Phishing.docx.pdf` | 3 | Definition, channels, 6 warning signs, a fictional training email, user response steps, analyst investigation |
| 06 | Malware Case Study | `06 Malware Case Study.docx.pdf` | 4 | Malware families, a fictional attack chain, impact areas, detection sources, the 8-step response lifecycle |

**Highlights**

- **Note 01** documents the full SOC workflow: Security Events -> Logs/Telemetry -> SIEM -> Alert ->
  L1 Analyst -> Investigation -> L2/L3 & IR -> Containment -> Closure -> Lessons Learned.
- **Note 02** closes with the tiering chain: L1 Triage -> L2 Investigation -> L3 / Specialist.
- **Note 05** includes a safe fictional phishing email, clearly labelled as a training simulation with
  no real credentials.
- **Note 06** concludes that malware can violate all three pillars of the CIA Triad at once.

---

## 2. Practice - `Writeups/` (6 documents, 75 pages)

One writeup per lab. Each document walks through every task, states the question, explains how to
reach the answer, and gives the answer itself.

| Lab / Room | Platform | Pages | Learning path |
|------------|----------|-------|---------------|
| SOC Fundamentals | LetsDefend | 14 | SOC Analyst Learning Path (free badge course) |
| Cyber Kill Chain | TryHackMe | 13 | SOC Level 1 / Jr Penetration Tester - Cyber Defence Frameworks |
| Introductory Networking | TryHackMe | 17 | Network Fundamentals / Pre-Security |
| SOC Role in the Blue Team | TryHackMe | 9 | SOC Level 1 - Blue Team Introduction |
| Windows Fundamentals 1 | TryHackMe | 13 | Pre Security / Cyber Security 101 - Windows |
| What is Networking? | TryHackMe | 9 | Pre-Security / Network Fundamentals |

**Coverage by lab**

- **LetsDefend - SOC Fundamentals:** the three pillars of a SOC, SOC types and roles, analyst
  responsibilities and skills, SIEM, log management, EDR, SOAR, threat intelligence, common analyst
  mistakes, plus a quiz and answer key.
- **TryHackMe - Cyber Kill Chain:** all seven phases (Reconnaissance, Weaponisation, Delivery,
  Exploitation, Installation, Command & Control, Actions on Objectives), mapping the 2013 Target
  breach onto the model, and the model's limitations.
- **TryHackMe - Introductory Networking:** the OSI model, encapsulation, the TCP/IP model, the TCP
  three-way handshake, and the practical tools `ping`, `traceroute`, `whois` and `dig`.
- **TryHackMe - SOC Role in the Blue Team:** security hierarchy and the CISO, Red vs Blue vs GRC
  teams, the SOC and the CIRT, specialised defensive roles, and the SOC L1 to L2 career path.
- **TryHackMe - Windows Fundamentals 1:** Windows editions and BitLocker, the desktop GUI, NTFS,
  `Windows\System32`, user accounts / profiles / permissions, UAC, Control Panel and Task Manager.
- **TryHackMe - What is Networking?:** what a network and the Internet are, IP addresses (IPv4 vs
  IPv6), MAC addresses and MAC spoofing, and `ping` over ICMP.

---

## 3. Hands-On - `Findings Folder/` (4 screenshots)

### Lab build

- Hypervisor: **VirtualBox**
- Virtual machines: **Windows 10** + **Linux**
- On the Windows 10 VM: opened **Event Viewer**, navigated to
  `Windows Logs -> Security`, filtered for each Event ID, and captured a screenshot of each match.

### Events captured

All four events were recorded on host **`DESKTOP-QKP3UOG`** on **07 October 2026**, within a
four-and-a-half minute window.

| Time | Event ID | Meaning | Result |
|------|----------|---------|--------|
| 12:36:15 PM | **4720** | A user account was created | Audit Success |
| 12:37:48 PM | **4624** | An account was successfully logged on | Audit Success |
| 12:40:26 PM | **4688** | A new process has been created | Audit Success |
| 12:40:44 PM | **4625** | An account failed to log on | Audit Failure |

### Event detail

**4720 - A user account was created (12:36:15 PM)**
A new local account **`apura`** was created by the SYSTEM account (logon ID `0x3E7`) - the standard
identity when account management is triggered programmatically.
- New Account SID: `DESKTOP-QKP3UOG\apura`
- New Account Domain: `WIN-JAA2UBRBPD` (differs from the computer field - the creation record carries
  the original computer name)
- Display Name / Home Directory / Script Path: `<value not set>`

**4624 - An account was successfully logged on (12:37:48 PM)**
A successful logon followed roughly 90 seconds after the account was created, indicating the new
account was usable immediately. The General tab is collapsed in the capture, so the New Logon SID
list is not visible.

**4688 - A new process has been created (12:40:26 PM)**
Process creation auditing captured `C:\Windows\System32\lsass.exe` (the Local Security Authority
Subsystem) - a normal Windows system process.
- New Process ID: `0x280` | Creator Subject: SYSTEM (`0x3E7`) | Creator Process ID: `0x1e8`
- Token Elevation Type: `%%1936` (TokenElevationTypeFull)

**4625 - An account failed to log on (12:40:44 PM)**
An interactive (Type 2) logon for `apura` failed because the user name or password was incorrect.
The failed account carries a **NULL SID**, meaning authentication never succeeded.
- Failure Reason: `Unknown user name or bad password.`
- Status: `0xC000006D` (STATUS_LOGON_FAILURE)
- Sub Status: `0xC000006A` (STATUS_WRONG_PASSWORD)

### Analysis

- **Only one of the four events is a failure** - Event 4625.
- Sub Status `0xC000006A` specifically means **the account existed but the password was wrong**;
  `0xC0000064` would indicate an unknown user name instead.
- The sequence as a whole is consistent with **normal account provisioning and testing**, not
  malicious activity.
- In a production environment the single wrong-password failure would be worth a follow-up, and
  repeated failures would warrant a lockout or brute-force investigation.

A standalone write-up of these findings is also included as
`Findings Folder/Windows_Security_Event_Findings.pdf`.

---

## 4. Deliverables

| Deliverable | File | Description |
|-------------|------|-------------|
| PDF report of weekly work | `Week 1 Report - Weekly Work.pdf` | 19-page report: executive summary, objectives, notes, writeups, hands-on investigation, LinkedIn activity, deliverables, and appendices with the document inventory and previews |
| Presentation report | `Week 1 Presentation - Weekly Work.pptx` | 30-slide 16:9 deck covering the whole week, including all four Event Viewer screenshots and previews of every note and writeup |
| Readme file | `README.md` | This file - the whole week in a structured format |
| LinkedIn posts | `LinkedIn Posts.md` | Post 1 published; Post 2 ready to publish with the presentation report attached |
| Findings report | `Findings Folder/Windows_Security_Event_Findings.pdf` | Standalone analysis of Event IDs 4624, 4625, 4688 and 4720 |

---

## 5. LinkedIn Activity

Two posts were drafted, as required by the brief:

1. **"What does a SOC analyst do every day?"** - five main points in my own words. **Published.**
2. **Week 1 experience** - a reflective post about the week, tagging **DG Interns Hub** and attaching
   the presentation report (or the key findings screenshots). **Ready to publish.**

The exact post text, the attachment options and the publishing steps are in
[`LinkedIn Posts.md`](LinkedIn%20Posts.md).

---

## 6. Timeline

| Date | Work completed |
|------|----------------|
| 05 October 2026 | Wrote all six theoretical notes; completed five TryHackMe rooms and wrote their walkthroughs |
| 07 October 2026 | Completed the LetsDefend SOC Fundamentals course writeup; built the VirtualBox lab and captured the four Windows Security events from Event Viewer |

---

## 7. Key Learnings

1. A SOC is **people, process and technology** working together to monitor, detect and respond.
2. The **L1/L2/L3 model** shows how triage escalates into deeper investigation and detection engineering.
3. The **CIA Triad** is the lens for judging the impact of any incident.
4. **OSI and TCP/IP** models underpin how defenders see network traffic; TCP is reliable and
   connection-oriented, UDP is fast and connectionless.
5. **Phishing and malware** remain the most common entry points - and the most preventable.
6. **Windows Event Viewer** is the starting point for endpoint investigation on Windows hosts.
7. Event IDs **4624, 4625, 4688 and 4720** answer *who logged in, who failed, what ran, and who was
   created* - and correlating them by time and host turns isolated log entries into a defensible
   narrative.

---

## 8. Tools and Platforms Used

| Purpose | Tool |
|---------|------|
| Virtualisation | VirtualBox |
| Guest operating systems | Windows 10, Linux |
| Log analysis | Windows Event Viewer (Security log) |
| Training platforms | TryHackMe, LetsDefend |
| Documentation | Microsoft Word (exported to PDF) |
| Reporting | Generated PDF report and PPTX presentation |

---

## 9. Notes and Known Issues

- The file `Writeups/Tryhackme Walkthrogh What is networking.pdf` contains a typo in its filename
  ("Walkthrogh" instead of "Walkthrough"); the document content is correct.
- The `Notes/` and `Writeups/` PDFs are text-only documents and contain no embedded screenshots.
  The only screenshots in this submission are the four Event Viewer captures in `Findings Folder/`.
- In the Event 4624 and Event 4688 captures, the General tab is collapsed / command-line logging was
  disabled, so the New Logon SID list and the full process command line are not visible. Expanding
  those sections would complete the evidence.
