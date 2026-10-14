# DG Interns Hub - SOC Analyst Internship

## Week 2 - Networking, Log Types, Wireshark and MITRE ATT&CK

This README is the master index for the week: the folder structure, what every document contains, the
hands-on work, and each deliverable.

| **Programme** | DG Interns Hub - SOC Analyst Internship |
| **Week** | Week 2 - Networking, Log Types, Wireshark and MITRE ATT&CK |
| **Theme** | Network traffic, log formats, and mapping attacker behaviour with MITRE ATT&CK |
| **Submission deadline** | 14 October 2026, 11:59 PM |
| **Lab host** | Windows host `EDITH` (192.168.0.205) and an Ubuntu VM |
| **Frameworks** | MITRE ATT&CK (Enterprise / Mobile / ICS), Cyber Kill Chain |

---

## Folder Structure

```
DG Interns Hub
    |
    |-- Week 2
            |
            |-- Notes/                                   # Theory - one file per question (10)
            |       |-- 01 What is MITRE ATT&CK.docx.pdf
            |       |-- 02 Tactics vs Techniques.docx.pdf
            |       |-- 03 ATT&CK Matrices.docx.pdf
            |       |-- 04 Mapping Alerts to ATT&CK.docx.pdf
            |       |-- 05 ATT&CK vs Cyber Kill Chain.docx.pdf
            |       |-- 06 Protocols and Default Ports.docx.pdf
            |       |-- 07 How DNS Resolution Works.docx.pdf
            |       |-- 08 DHCP DORA Process.docx.pdf
            |       |-- 09 Comparing Log Formats.docx.pdf
            |       |-- 10 Inbound vs Outbound Traffic.docx.pdf
            |
            |-- Writeups/                                # Labs - one file per room (6)
            |       |-- TryHackMe-Network-Traffic-Basics-Walkthrough.pdf
            |       |-- TryHackMe-Intro-To-Logs-Walkthrough.pdf
            |       |-- TryHackMe-Intro-To-Log-Analysis-Walkthrough.pdf
            |       |-- TryHackMe-Snort-Walkthrough.pdf
            |       |-- TryHackMe-DNS-In-Detail-Walkthrough.pdf
            |       |-- TryHackMe-HTTP-In-Detail-Walkthrough.pdf
            |
            |-- Findings Folder/                         # Hands-on - documents + images
            |       |-- 0_Screenshot_Capture_Checklist.pdf
            |       |-- 1 Wireshark_Traffic_Capture_Analysis.pdf
            |       |-- 2 Make_Your_Own_Traffic_Findings.pdf
            |       |-- 3 Linux_Logs_Findings.pdf
            |       |-- 4 Web_Server_Log_Analysis.pdf
            |       |-- 5 MITRE_ATTACK_Mapping_Findings.pdf
            |       |-- 6_Snort_IDS_Setup_Findings.pdf
            |       |-- 1a-1t, 2a-2r, 3a-3f, 4a-4d, 5a-5b, 6a-6f   # 52 images, all from real tools/data
            |
            |-- Week 2 Report - Weekly Work.pdf          # PDF report of the weekly work
            |-- Week 2 Presentation - Weekly Work.pptx   # Presentation report of the weekly work
            |-- README.md                                # This file
            |-- LinkedIn Posts.md                        # Ready-to-publish LinkedIn posts
            |-- _build/                                  # Source markdown + generator scripts
```

---

## 1. Theory - `Notes/` (10 documents, 25 pages)

Each question from the brief is answered in its own document, in my own words, using bullet points and
tables.

| # | Topic | Covers |
|---|-------|--------|
| 01 | What is MITRE ATT&CK? | Definition, origin (MITRE, public since 2015), why it matters to a SOC, and its building blocks: tactic, technique, sub-technique, procedure, group, software, mitigation, data source |
| 02 | Tactics vs Techniques | Why = tactic / how = technique, a side-by-side comparison, and 13 Enterprise tactics each with an example technique |
| 03 | ATT&CK Matrices | Enterprise, Mobile and ICS: what each covers, why they are separate, and where the same act carries a different ID |
| 04 | Mapping Alerts to ATT&CK | An 8-step mapping method plus a full worked scenario: Word spawning encoded PowerShell, mapped to T1059.001 with supporting techniques and the ticket wording |
| 05 | ATT&CK vs Cyber Kill Chain | The seven Kill Chain phases, a full comparison table, where the two overlap, and when to use each |
| 06 | Protocols and Default Ports | HTTP 80, HTTPS 443, DNS 53, DHCP 67/68, SSH 22, FTP 20/21, SMTP 25 (587/465) with a Protocol / Port / Purpose table, plus encrypted-versus-plaintext analysis |
| 07 | How DNS Resolution Works | Browser cache to authoritative nameserver in seven steps, the referral chain, record types, TTL, and the SOC angle (tunnelling and DGA) |
| 08 | DHCP DORA | Discover, Offer, Request, Acknowledge step by step, the message table, the lease lifecycle, and rogue-DHCP / starvation attacks |
| 09 | Comparing Log Formats | Windows Event Log, syslog, JSON and CSV compared on structure, use case and example - plus the same failed-login event written in all four formats |
| 10 | Inbound vs Outbound Traffic | Definitions, a triage decision table, east-west versus north-south, and how direction drives containment decisions |

**Highlights**

- **Note 04** ends with the mapping that would go on a real ticket:
  *Execution / T1059.001 - PowerShell (confirmed)*, with T1027, T1562.001 and T1071.001 as supporting
  techniques.
- **Note 06** separates the ports that leak evidence (HTTP, FTP, Telnet, SMTP, DNS) from the encrypted
  ones where only metadata is available.
- **Note 09** shows one failed SSH login written four ways, which makes the parsing and normalisation
  problem obvious at a glance.

---

## 2. Practice - `Writeups/` (6 documents, 23 pages)

One writeup per lab. Each walks through every task, states the question, explains the reasoning, and
gives the answer.

| Lab / Room | Platform | Tasks | Path |
|------------|----------|-------|------|
| Network Traffic Basics | TryHackMe | 6 | Cyber Security 101 / SOC Level 1 |
| Intro to Logs | TryHackMe | 7 | SOC Level 1 - Log Analysis |
| Intro to Log Analysis | TryHackMe | 9 | SOC Level 1 / SOC Level 2 - Log Analysis |
| Snort | TryHackMe | 11 | SOC Level 1 - Snort module |
| DNS in Detail | TryHackMe | 5 | Pre Security / Cyber Security 101 - How the Web Works |
| HTTP in Detail | TryHackMe | 7 | Pre Security / Cyber Security 101 - How the Web Works |

**Coverage by room**

- **Network Traffic Basics** - why traffic analysis matters, what a packet contains, fragmentation as
  IDS evasion, TCP sequence numbers and session hijacking, traffic sources and flows, the three
  collection methods, and the two flags recovered from HTTP and DNS traffic.
- **Intro to Logs** - anatomy of a log entry, log types and formats, `rsyslog` collection and
  configuration, a reverse shell hidden inside a cron job, `logrotate` retention, and the parsing /
  normalisation / enrichment pipeline.
- **Intro to Log Analysis** - super timelines, threat-intel indicators as hashes, path traversal decoded
  from `%2E%2E%2F`, manual versus automated analysis, and a full investigation using the command line,
  regular expressions, CyberChef, Sigma and YARA.
- **Snort** - IDS versus IPS families, all four operation modes, PCAP investigation, and four local rules
  written from scratch (IP ID, SYN flag, Push-Ack flags, same-source-destination).
- **DNS in Detail** - the hierarchy and its length limits, all five record types, the complete request
  path, and a practical record-hunting exercise.
- **HTTP in Detail** - URLs, methods, status codes, headers, cookies, and five hands-on requests.

---

## 3. Hands-On - `Findings Folder/` (7 documents + 52 images, all real evidence)

### 3.1 The supplied packet capture (real analysis)

`wireshark_capture.bin` - pcap 2.4, little-endian, Ethernet, 204,849 bytes, **1,171 packets** over
**36.88 seconds** (20 September 2020, 21:21:36 to 21:22:13 UTC). Every figure below was measured from
the file itself.

| Question in the brief | Answer found |
|---|---|
| Source and destination IP addresses | `192.168.100.128` (client), `192.168.100.6` (server), `192.168.100.1` (gateway), `54.193.240.194` (external), `239.255.255.250` (SSDP multicast) |
| HTTP requests | None over TCP. 10 SSDP `M-SEARCH * HTTP/1.1` requests inside UDP port 1900 |
| DNS queries | **None.** Filters `dns`, `udp.port == 53` and `tcp.port == 53` all return zero packets |
| Dominant activity | SMB2 (113 frames) and MS RPC (423 DCE/RPC frames) between two internal hosts |
| AD-related RPC | **Netlogon 126 frames, DRSUAPI 52 frames**, endpoint mapper 64 frames |
| External traffic | UDP 1194 OpenVPN to `54.193.240.194` |
| TCP flags | ACK 1078, PSH 497, SYN 132 (of which **66** are connection attempts), FIN 129, RST 2 |
| Verdict | Normal internal file/RPC administration, an OpenVPN tunnel and UPnP discovery - no attack evidence |

This is reported honestly rather than worked around: the supplied file simply does not contain the DNS
or HTTP-over-TCP traffic the task describes, and proving that with display filters is itself the lesson
that **a capture only shows its own window**.

The RPC traffic is worth calling out. Wireshark's Protocol Hierarchy shows **Netlogon (126 frames)** and
**DRSUAPI (52 frames)**, which means this is not generic RPC but an Active Directory conversation -
DRSUAPI is the replication interface behind **DCSync (T1003.006)**. On this capture it fits a machine
doing legitimate directory work, but it is exactly the pattern an analyst has to be able to recognise,
because the same frames from a host with no business replicating the directory is a credential-theft
incident.

### 3.2 My own traffic (real output from the lab host)

`nslookup` for A, MX, TXT and NS records - all answered from the local resolver with
*"non-authoritative answer"*, which proves caching. The TXT records reveal the SPF record (Google
Workspace plus Chargebee and HubSpot) and four domain-verification tokens. Also captured: four ICMP
echo pairs at 17-19 ms with TTL 246, a full `curl` TLS handshake with request and response headers, a
7,076-byte download, HTTP 200 and 429 status codes, and `ipconfig` output showing a real DHCP lease
alongside two **APIPA 169.254.x.x** addresses that prove DORA failed on those adapters.

### 3.3 Web server log analysis (real data)

A real public Apache `access.log` - **10,000 requests**, 2,370,789 bytes, combined format, 17-20 May
2015 - downloaded and analysed.

| Rank | IP address | Requests | Share |
|---|---|---|---|
| 1 | `66.249.73.135` | 482 | 4.82% |
| 2 | `46.105.14.53` | 364 | 3.64% |
| 3 | `130.237.218.86` | 357 | 3.57% |

Status codes: 9,126 x 200, 445 x 304, 213 x 404, 164 x 301, 45 x 206, 3 x 500, 2 x 403, 2 x 416.

The 404s cluster on CMS admin paths, which is automated reconnaissance: `208.91.156.11` produced 60
errors probing WordPress paths, and `91.236.75.25` requested `/administrator/index.php` on a site that
is not Joomla - a single-request proof of hostile scanning (ATT&CK **T1595.002**).

### 3.4 MITRE ATT&CK mapping

| Behaviour | Tactic | Technique | ID |
|---|---|---|---|
| Phishing with an attachment | Initial Access | Phishing: Spearphishing Attachment | T1566.001 |
| Hidden / encoded PowerShell | Execution (+ Defense Evasion) | Command and Scripting Interpreter: PowerShell | T1059.001 |
| Port scanning from outside | Reconnaissance | Active Scanning: IP Blocks / Vulnerability Scanning | T1595.001, T1595.002 |
| Port scanning from inside | Discovery | Network Service Discovery | T1046 |
| Path guessing with a word list | Reconnaissance | Active Scanning: Wordlist Scanning | T1595.003 |

### 3.5 Linux logs - read on a real Ubuntu 22.04.5 machine

A genuine **Ubuntu 22.04.5 LTS** cloud image (kernel 5.15.0-198-generic) was booted as a QEMU guest, the
account `analyst` was created, privileged commands were run through `sudo`, and the logs were read back.
This is the machine's own `/var/log/auth.log`:

```
$ grep -i 'sudo' /var/log/auth.log | tail -20
Oct 14 07:41:51 ubuntu-vm sudo:  analyst : PWD=/home/analyst ; USER=root ; COMMAND=/usr/bin/ls -l /root
Oct 14 07:41:51 ubuntu-vm sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Oct 14 07:41:51 ubuntu-vm sudo: pam_unix(sudo:session): session closed for user root
```

| Measurement | Value |
|---|---|
| `auth.log` total lines | 44 |
| `sudo` lines in `auth.log` | 17 |
| `COMMAND=` entries | 5 - exactly the five privileged commands that were run |
| `syslog` total lines | 1,119 |
| Root filesystem | `/dev/sda1`, 14 GiB, 12% used |

The same events appear in `/var/log/syslog`, which is the practical lesson: deleting `auth.log` does not
delete the evidence.

### 3.6 Snort - real alerts, not a procedure

**Snort 2.9.20-WIN64 (Build 82)** was installed, its configuration validated with `-T`, nine local rules
written, and the rules run against five real capture files:

| Capture | Alerts | Rules that fired |
|---|---|---|
| `icmp.pcapng` | 3 | echo request (x1) and `ICMP Ping Detected` (x2: request + reply) |
| `dns_icmp.pcapng` | 45 | DNS query x6, DNS response x5, ICMP x34 |
| `http.pcap` | 1 | HTTP request on port 80 - the method was `HEAD`, so `content:"GET"` correctly did not match |
| `dhcp.pcap` | 2 | DHCP client messages |
| **the supplied capture** | **66** | TCP SYN connection attempts |

The 66 is corroborated by three independent tools - Snort's `flags:S` rule, Wireshark's
`tcp.flags.syn==1 && tcp.flags.ack==0`, and the Python dissector all report exactly 66.

`Findings Folder/0_Screenshot_Capture_Checklist.pdf` now serves as the evidence log: it lists every
image, the tool or command that produced it, and the file name.

---

## 4. Deliverables

| Deliverable | File | Description |
|-------------|------|-------------|
| PDF report of weekly work | `Week 2 Report - Weekly Work.pdf` | 9-page report: executive summary, objectives, notes, writeups, hands-on investigations, key learnings, LinkedIn activity, deliverables and appendices |
| Presentation report | `Week 2 Presentation - Weekly Work.pptx` | 35-slide 16:9 deck covering the whole week, including the capture analysis, the Apache access-log findings and the ATT&CK chain |
| Readme file | `README.md` | This file - the whole week in a structured format |
| LinkedIn posts | `LinkedIn Posts.md` | The two required posts, ready to publish |
| Screenshot checklist | `Findings Folder/0_Screenshot_Capture_Checklist.pdf` | What still has to be captured on the lab machines |

---

## 5. LinkedIn Activity

Two posts were drafted, as required by the brief:

1. **"How does MITRE ATT&CK help a SOC analyst investigate an alert?"** - five main points in my own
   words.
2. **Week 2 experience** - a reflective post about the week, tagging **DG Interns Hub** and attaching
   the report or the key findings screenshots.

The exact post text, the attachment options and the publishing steps are in
[`LinkedIn Posts.md`](LinkedIn%20Posts.md).

---

## 6. Timeline

| Date | Work completed |
|------|----------------|
| 05-10 October 2026 | Completed the six TryHackMe rooms and wrote their walkthroughs; drafted the theory notes |
| 13 October 2026 | Downloaded and dissected the supplied capture; generated and captured own traffic; analysed the real Apache access log; built the ATT&CK mapping |
| 14 October 2026 | Finalised the notes, findings documents, weekly report, presentation, README and LinkedIn posts |

---

## 7. Key Learnings

1. **ATT&CK is a behaviour catalogue, not a malware catalogue** - mapping starts from the telemetry and
   ends at a technique ID, never the reverse.
2. **Tactic is the goal, technique is the method**, and one technique can serve several tactics at once.
3. **Enterprise, Mobile and ICS exist because those environments behave, log and prioritise
   differently** - and IDs are not interchangeable between them.
4. **ATT&CK and the Cyber Kill Chain are complementary:** the Kill Chain gives the seven-phase story,
   ATT&CK gives the technique-level detail defenders act on.
5. **Ports are strong hints, never proof.** Protocol and port mismatches are the cheapest, highest-signal
   network detections available.
6. **DNS is the most valuable and most abused protocol** - rarely encrypted, it precedes almost every
   connection and carries both SPF records and attacker command-and-control.
7. **DHCP has no authentication**, which is exactly why rogue servers, DHCP snooping and lease logs
   matter in an investigation.
8. **Direction decides meaning.** Inbound usually means attempted compromise; outbound after a
   compromise usually means command-and-control or exfiltration.
9. **A capture only shows its own window** - the supplied file had no DNS because resolution had already
   happened, which is why DNS logging has to be on *before* an incident.
10. **Retention is an investigative control.** An hourly `logrotate` keeping 24 copies leaves roughly one
    day of history.
11. **Automate the known, investigate the unknown manually** - then turn the manual finding into a rule.
12. **The 404 is evidence.** A burst of 404s for paths that do not exist is the fingerprint of a scanner,
    and one of the easiest detections to write.

---

## 8. Tools and Platforms Used

| Purpose | Tool |
|---------|------|
| Virtualisation | VirtualBox (Ubuntu VM) |
| Packet analysis | **Wireshark 4.6.9** and `tshark` 4.6.9, plus a purpose-written Python pcap dissector for cross-checking |
| Traffic generation | `nslookup`, `ping`, `curl`, `ipconfig` |
| Linux environment | Ubuntu 22.04.5 LTS cloud image booted as a QEMU guest (pure emulation, no administrator rights) |
| Log analysis | `grep`, `awk`, `cut`, `sort`, `uniq`, `wc` on that real Ubuntu machine, Microsoft Excel, CyberChef |
| Intrusion detection | **Snort 2.9.20-WIN64 (Build 82)** in IDS mode with nine custom local rules |
| Frameworks | MITRE ATT&CK (`attack.mitre.org`), Cyber Kill Chain |
| Training platforms | TryHackMe - Cyber Security 101 and SOC Level 1 |
| Documentation | Word-processed notes exported to PDF, plus a generated PDF report and PPTX deck |

---

## 9. Notes and Known Issues

- **The supplied capture does not contain the HTTP and DNS traffic described in the brief.** It contains
  SMB2, MS RPC (Netlogon and DRSUAPI), SSDP and OpenVPN traffic instead. This is documented honestly
  with the exact display filters that prove it, rather than being worked around.
- **Every image in the Findings folder is real evidence** - a Wireshark GUI screenshot, a tool's actual
  output, or a table computed from a real artefact - and is badged `REAL DATA` or `REAL OUTPUT`. There
  are no placeholders left to replace.
- **Timezone in the capture tables.** `tshark` and `capinfos` print packet times in local time
  (`2026-09-21 02:51:36`) while the Python dissector reports UTC (`2026-09-20 21:21:36`). They are the
  same packet; the findings document states which is which.
- **No SNI in one TLS capture.** `tls13-rfc8446.pcap` returns `(no SNI extension)`, so there is no
  hostname to read. Reported as a genuine limitation of SNI-based detection.
- **`journalctl -u sudo` returns nothing** on the Ubuntu VM because `sudo` is not a systemd unit. The
  correct forms are `journalctl -t sudo` or `journalctl _COMM=sudo`.
- **`Notes/01 What is a SOC.docx.pdf`** is the Week 1 note that was used as the formatting reference for
  the Week 2 notes. It is Week 1 content, so it can be removed from the Week 2 folder before submission.
- Where a TryHackMe answer depends on a particular room or VM version (for example the rule count loaded
  by `snort.conf`, or alert counts in the pcap exercises), the writeup says so and gives the command used
  so the figure can be reproduced on the current build.
- `_build/` holds the markdown sources and the Python scripts that generated the PDFs, the images and the
  presentation. It is not a submission deliverable and can be left out or kept as a record of how the
  documents were produced.
