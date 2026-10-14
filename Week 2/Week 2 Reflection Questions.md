# Week 2 - Reflection Questions and Answers

## 1. What did you learn this week?

This week I learned how a SOC analyst moves from raw evidence to an ATT&CK technique, and how to read
network traffic and logs to support that move. Specifically:

- The MITRE ATT&CK framework: the difference between a **tactic** (the goal) and a **technique** (the
  method), and how the Enterprise, Mobile and ICS matrices differ.
- How to map an alert to a technique ID systematically, and how ATT&CK complements the Cyber Kill Chain.
- Core networking: default ports, how DNS resolution works, the DHCP DORA process, and the difference
  between inbound and outbound traffic.
- Log types and formats (Windows Event Log, syslog, JSON, CSV) and how the same event looks in each.
- Hands-on analysis with **Wireshark, Snort, and the Linux command line** on real captures and logs.

## 2. Explain your learning in your own words.

ATT&CK is a **behaviour catalogue, not a malware catalogue** - you start from the telemetry and end at a
technique ID, never the other way around. Tactic is *why* the attacker acts, technique is *how*, and the
same action can serve several tactics at once - hidden PowerShell is both Execution and Defense Evasion.

Ports are strong hints but never proof; a protocol/port mismatch is one of the cheapest, highest-signal
detections available. Direction changes meaning: inbound traffic usually means an attempted compromise,
while outbound traffic *after* a compromise usually means command-and-control or exfiltration.

DNS is the most valuable and most abused protocol - it is rarely encrypted, it precedes almost every
connection, and it carries both legitimate records and attacker C2. DHCP has no authentication, which is
exactly why rogue servers and lease logs matter.

On the log side, the same events appear in multiple files, so deleting one log doesn't delete the
evidence; and retention is an investigative control - an hourly `logrotate` keeping 24 copies leaves
roughly one day of history. The practical rule is: automate the known, investigate the unknown manually,
then turn the manual finding into a rule.

The biggest lesson was that **a capture only shows its own window**: the supplied pcap had no DNS or
HTTP-over-TCP traffic despite the brief describing it, which proves DNS logging has to be on *before* an
incident.

## 3. What challenges did you face?

- **The supplied capture did not match the brief.** It contained SMB2, MS RPC (Netlogon and DRSUAPI),
  SSDP and OpenVPN traffic instead of the HTTP and DNS described - proving that with display filters was
  itself the lesson.
- **No HTTP request was actually captured over TCP** - the only HTTP-looking traffic was SSDP requests
  inside UDP. Snort's `content:"GET"` rule correctly did not match because the method was `HEAD`.
- **Timezone confusion:** `tshark`/`capinfos` print local time while my Python dissector printed UTC,
  so the same packet looked like two different times.
- **Tooling friction on the Ubuntu VM:** `journalctl -u sudo` returned nothing because `sudo` is not a
  systemd unit, and I was working without administrator rights.
- **Missing detail in one capture:** a TLS capture returned `(no SNI extension)`, so there was no
  hostname to read at all.

## 4. How did you solve those challenges?

- I validated the honest result instead of working around it: I used display filters (`dns`,
  `udp.port == 53`, `tcp.port == 53` - all zero packets) to *prove* the capture didn't contain what the
  brief assumed, and documented it as a genuine limitation.
- I cross-checked every important number with independent tools. The 66 TCP SYN attempts were confirmed
  by Snort's `flags:S` rule, Wireshark's `tcp.flags.syn==1 && tcp.flags.ack==0` filter, and a
  purpose-written Python dissector - all three agreed.
- I stated clearly which timezone each table used so the local-vs-UTC difference was not mistaken for
  two events.
- I found the correct systemd forms (`journalctl -t sudo` and `journalctl _COMM=sudo`) and used `sudo`
  for privileged commands on the real Ubuntu 22.04.5 machine.
- I reported the missing SNI as a real limitation of SNI-based detection rather than inventing a value.
- I backed every finding with real evidence - Wireshark GUI screenshots, actual command output, or
  tables computed from real artefacts - badged `REAL DATA` or `REAL OUTPUT`.
