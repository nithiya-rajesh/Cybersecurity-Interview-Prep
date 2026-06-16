# SOC Analyst Interview Questions (0–5 Years)

A curated collection of beginner and intermediate level SOC (Security Operations Center) interview questions. Includes theory-based Q&A and real-world scenario/incident-response questions.

---

## Table of Contents
1. [Networking & Security Fundamentals](#networking--security-fundamentals)
2. [SOC Concepts & Monitoring](#soc-concepts--monitoring)
3. [SIEM, Logs & Detection](#siem-logs--detection)
4. [Malware & Endpoint Security](#malware--endpoint-security)
5. [Email Security & Phishing](#email-security--phishing)
6. [Incident Response & Forensics](#incident-response--forensics)
7. [Threat Intelligence & MITRE ATT&CK](#threat-intelligence--mitre-attck)
8. [Tools](#tools)
9. [Windows/Linux Security Basics](#windowslinux-security-basics)
10. [Scenario-Based Questions (Beginner)](#scenario-based-questions-beginner)
11. [Scenario-Based Questions (Intermediate)](#scenario-based-questions-intermediate)
12. [Mini Case Study Scenarios](#mini-case-study-scenarios)

---

## Networking & Security Fundamentals

**Q1. What is the difference between TCP and UDP, and why does it matter for a SOC analyst?**
A: TCP is connection-oriented and reliable (handshake-based); UDP is connectionless and faster but unreliable. It matters because protocol behavior helps distinguish normal traffic from anomalies — e.g., unexpected UDP floods may indicate DDoS, while malformed TCP handshakes can indicate scanning.

**Q2. Explain the OSI model layers briefly.**
A: Physical, Data Link, Network, Transport, Session, Presentation, Application — 7 layers describing how data moves from physical transmission to application-level interaction. SOC analysts use this to pinpoint where an attack/anomaly is occurring (e.g., Layer 2 ARP spoofing vs Layer 7 web attacks).

**Q3. What is the difference between a firewall, IDS, and IPS?**
A: A firewall filters traffic based on rules (ports, IPs, protocols). An IDS (Intrusion Detection System) monitors traffic and alerts on suspicious activity but doesn't block it. An IPS (Intrusion Prevention System) sits inline and can actively block/drop malicious traffic in real time.

**Q4. What are common ports and protocols a SOC analyst should know?**
A: 21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP), 53 (DNS), 80/443 (HTTP/HTTPS), 110 (POP3), 143 (IMAP), 389/636 (LDAP/LDAPS), 445 (SMB), 3389 (RDP), 3306 (MySQL), 1433 (MSSQL).

**Q5. What is the difference between a public IP and a private IP?**
A: Private IPs (e.g., 10.x.x.x, 172.16–31.x.x, 192.168.x.x) are used within internal networks and aren't routable on the internet. Public IPs are globally routable and unique. NAT translates between them.

**Q6. What is the difference between a VPN and a proxy?**
A: A VPN encrypts and tunnels all traffic between a client and a remote network, often used for secure remote access. A proxy forwards specific traffic (often just web traffic) on behalf of a client, which may or may not be encrypted, and is often used for content filtering or anonymity.

**Q7. What is DNS and why is it commonly abused by attackers?**
A: DNS resolves domain names to IP addresses. Attackers abuse it for DNS tunneling (data exfiltration), DGA (domain generation algorithms) for C2 communication, and DNS spoofing/cache poisoning to redirect users to malicious sites.

**Q8. What is the CIA triad?**
A: Confidentiality, Integrity, and Availability — the foundational principles guiding all security operations and the impact analysis of any incident.

**Q9. What is the difference between a vulnerability, a threat, and a risk?**
A: A vulnerability is a weakness; a threat is anything that could exploit that weakness; risk is the likelihood and impact if the threat exploits the vulnerability.

**Q10. What is the difference between symmetric and asymmetric encryption?**
A: Symmetric encryption uses one shared key for both encryption and decryption (fast, e.g., AES). Asymmetric encryption uses a public/private key pair (slower, used for key exchange/digital signatures, e.g., RSA).

---

## SOC Concepts & Monitoring

**Q11. What is a SOC and what are its main functions?**
A: A Security Operations Center is a centralized team/function responsible for continuously monitoring, detecting, analyzing, and responding to cybersecurity incidents across an organization's IT environment.

**Q12. What are the different tiers/levels in a SOC?**
A: Tier 1 (Triage Analyst) — monitors alerts, performs initial triage, escalates. Tier 2 (Incident Responder) — deeper investigation, correlates data, contains threats. Tier 3 (Threat Hunter/Senior Analyst) — proactive threat hunting, advanced forensics, tuning detection rules. Some SOCs also have a Tier 4 (SOC Manager/Architect).

**Q13. What is the difference between a SOC analyst's role and a penetration tester's role?**
A: A SOC analyst works on the defensive side — monitoring, detecting, and responding to threats in real time (blue team). A penetration tester works on the offensive side — proactively finding vulnerabilities by simulating attacks (red team).

**Q14. What is an alert, an event, and an incident?**
A: An event is any recorded occurrence (e.g., a login). An alert is a notification triggered when an event matches a detection rule (e.g., failed login threshold exceeded). An incident is a confirmed security event that has actual or potential adverse impact, requiring formal response.

**Q15. What is alert fatigue and how can it be managed?**
A: Alert fatigue occurs when analysts are overwhelmed by a high volume of alerts (often with many false positives), leading to slower response times or missed real threats. Managed through proper tuning of detection rules, prioritization/severity scoring, automation (SOAR), and suppressing known benign noise.

**Q16. What is the difference between a false positive and a false negative?**
A: A false positive is an alert triggered for benign/non-malicious activity. A false negative is when malicious activity occurs but no alert is triggered — generally more dangerous since the threat goes undetected.

**Q17. What is the Cyber Kill Chain?**
A: A model describing the stages of a cyberattack: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command & Control (C2), and Actions on Objectives. SOC analysts use it to identify which stage an attack is in and disrupt it as early as possible.

**Q18. What is the difference between detection and prevention?**
A: Detection identifies that malicious activity is occurring or has occurred (e.g., IDS, SIEM alerts). Prevention actively stops the activity before it succeeds (e.g., IPS, firewall blocks, endpoint blocking).

**Q19. What is SOAR and how does it help a SOC?**
A: Security Orchestration, Automation, and Response — platforms that automate repetitive triage/response tasks (e.g., enriching IOCs, blocking IPs, opening tickets) and orchestrate actions across multiple security tools, reducing analyst workload and response time.

**Q20. What is the difference between a vulnerability scan and continuous monitoring?**
A: A vulnerability scan is a point-in-time check for known weaknesses. Continuous monitoring (the core SOC function) is ongoing, real-time observation of logs, traffic, and endpoints to detect active threats as they happen.

**Q21. What is "defense in depth"?**
A: A layered security strategy where multiple controls (firewalls, endpoint protection, IDS/IPS, email filtering, awareness training, etc.) are deployed so that if one layer fails, others still provide protection.

**Q22. What is the difference between a Security Analyst and a Threat Hunter?**
A: A Security Analyst typically reacts to alerts generated by existing tools (reactive). A Threat Hunter proactively searches for hidden/undetected threats in the environment using hypotheses, without waiting for an alert to trigger (proactive).

---

## SIEM, Logs & Detection

**Q23. What is a SIEM and what is its role in a SOC?**
A: Security Information and Event Management — a platform that aggregates, correlates, and analyzes log data from across the organization (endpoints, network devices, applications) to detect threats and provide centralized visibility, alerting, and reporting.

**Q24. Name some commonly used SIEM tools.**
A: Splunk, IBM QRadar, Microsoft Sentinel, Elastic (ELK Stack), ArcSight, LogRhythm, Sumo Logic, Securonix.

**Q25. What is log correlation and why is it important?**
A: Log correlation combines events from multiple sources (firewall, AV, AD, proxy) to identify patterns that wouldn't be apparent from a single source alone — e.g., a failed login on a firewall combined with a successful login on AD from the same IP minutes later.

**Q26. What are Windows Event IDs, and name a few important ones for SOC analysis.**
A: Windows generates Event IDs for system activities. Important ones: 4624 (successful logon), 4625 (failed logon), 4634 (logoff), 4720 (user account created), 4732 (member added to a security-enabled local group), 4768/4769 (Kerberos TGT/TGS request), 1102 (audit log cleared).

**Q27. What is the difference between a syslog and a Windows Event Log?**
A: Syslog is a standard logging protocol primarily used by Linux/Unix systems and network devices, sending log messages to a centralized syslog server. Windows Event Log is Microsoft's native logging mechanism, stored locally (and often forwarded to a SIEM via agents like Winlogbeat or WEF).

**Q28. What is a use case/correlation rule in a SIEM?**
A: A predefined logic pattern that triggers an alert when specific conditions are met across one or more log sources — e.g., "5 failed logins followed by 1 successful login from the same source IP within 5 minutes" (possible brute force success).

**Q29. What is log retention and why does it matter?**
A: The duration logs are stored before deletion/archival. It matters for forensic investigations (being able to look back at historical activity), compliance requirements (e.g., PCI-DSS requires 1 year), and detecting slow/long-term attacks (APTs).

**Q30. What is the difference between an IOC and an IOA?**
A: An IOC (Indicator of Compromise) is evidence that a breach has already occurred (e.g., a malicious file hash, known bad IP). An IOA (Indicator of Attack) focuses on the attacker's behavior/intent in real time (e.g., process injection patterns), allowing detection before damage occurs.

**Q31. What is a baseline in the context of anomaly detection?**
A: A baseline represents "normal" behavior for a user, system, or network over time. Deviations from this baseline (e.g., a user logging in at 3 AM from a new country) can indicate anomalous or malicious activity (UEBA - User and Entity Behavior Analytics).

**Q32. What is the difference between signature-based and behavior-based (anomaly) detection?**
A: Signature-based detection matches activity against known patterns/signatures of malicious behavior (fast, but misses unknown/new threats). Behavior-based detection identifies deviations from established normal behavior, capable of catching zero-days but with potentially higher false positive rates.

---

## Malware & Endpoint Security

**Q33. What is the difference between a virus, worm, and trojan?**
A: A virus attaches itself to legitimate files/programs and requires user action to spread. A worm self-replicates and spreads across networks without user interaction. A trojan disguises itself as legitimate software but performs malicious actions once executed.

**Q34. What is ransomware and how does a typical ransomware attack unfold?**
A: Malware that encrypts victim files/systems and demands payment for decryption. Typical flow: initial access (phishing/RDP brute force) → privilege escalation → lateral movement → data exfiltration (double extortion) → mass encryption → ransom note/demand.

**Q35. What is the difference between EDR and traditional antivirus?**
A: Traditional AV relies mainly on signature-based detection of known malware. EDR (Endpoint Detection and Response) provides continuous behavioral monitoring, visibility into process/file/network activity on endpoints, and supports investigation, containment, and response actions (isolating a host, killing a process).

**Q36. What is a fileless malware attack?**
A: Malware that operates in memory without writing a malicious file to disk, often using legitimate system tools (e.g., PowerShell, WMI) to execute malicious activity — making it harder to detect via traditional file-based AV signatures.

**Q37. What is "living off the land" (LOLBins)?**
A: An attack technique where adversaries use legitimate, pre-installed system tools/binaries (e.g., PowerShell, certutil, mshta, rundll32) to carry out malicious actions, blending in with normal admin activity and evading detection.

**Q38. What is a C2 (Command and Control) server?**
A: A server an attacker uses to remotely control compromised systems (malware/implants), issuing commands and receiving exfiltrated data — often communicating over common protocols (HTTP/S, DNS) to blend in with normal traffic.

**Q39. What is process injection and why is it used by malware?**
A: A technique where malicious code is injected into the memory space of a legitimate, running process to evade detection (since the malicious activity appears to originate from a trusted process) and potentially gain its privileges.

**Q40. What is the difference between static and dynamic malware analysis?**
A: Static analysis examines the malware file without executing it (strings, hashes, headers, disassembly). Dynamic analysis runs the malware in a controlled/sandboxed environment to observe its actual behavior (network connections, file changes, registry modifications).

---

## Email Security & Phishing

**Q41. What is phishing and what are its common variants?**
A: Phishing is a social engineering attack to trick users into revealing sensitive info or executing malicious actions, usually via email. Variants: Spear phishing (targeted at specific individuals), Whaling (targeting executives), Vishing (voice/phone-based), Smishing (SMS-based), and Business Email Compromise (BEC).

**Q42. What is SPF, DKIM, and DMARC?**
A: SPF (Sender Policy Framework) specifies which mail servers are authorized to send email for a domain. DKIM (DomainKeys Identified Mail) adds a digital signature to verify the email wasn't tampered with in transit. DMARC builds on both, telling receiving servers what to do (reject/quarantine/none) if SPF/DKIM checks fail, and provides reporting.

**Q43. How would you analyze a suspicious email header to determine if it's phishing?**
A: Check the "Return-Path" and "From" address for mismatches/spoofing, review the "Received" chain for unexpected/suspicious relay hops, verify SPF/DKIM/DMARC results (pass/fail), check the sender's actual IP against known reputation, and compare the displayed sender name against the actual email address.

**Q44. What is email spoofing and how is it different from a compromised account?**
A: Spoofing forges the "From" address to impersonate a sender without actually having access to that account (often defeated by proper SPF/DKIM/DMARC enforcement). A compromised account means the attacker has actual legitimate access to a real mailbox, making detection harder since DKIM/SPF will pass.

**Q45. What is a URL defanging and why do analysts do it?**
A: Defanging modifies a malicious URL/IP so it can't be accidentally clicked or auto-linked when shared in reports/tickets (e.g., `hxxp://malicious[.]com` instead of `http://malicious.com`).

**Q46. What is Business Email Compromise (BEC)?**
A: A targeted scam where attackers compromise or spoof a business email account (often an executive's) to trick employees into making fraudulent wire transfers or revealing sensitive data, usually without malware involvement.

---

## Incident Response & Forensics

**Q47. What are the phases of Incident Response (per NIST/SANS)?**
A: Preparation, Identification (Detection & Analysis), Containment, Eradication, Recovery, and Lessons Learned (Post-Incident Activity).

**Q48. What is the difference between containment and eradication?**
A: Containment limits the spread/impact of an incident (e.g., isolating an infected host from the network) without necessarily removing the threat. Eradication involves completely removing the root cause (e.g., deleting malware, closing the vulnerability that allowed access).

**Q49. What is chain of custody in digital forensics?**
A: A documented, chronological record of how evidence was collected, handled, transferred, and stored, ensuring its integrity and admissibility (especially important for legal/compliance purposes).

**Q50. What is the order of volatility in digital forensics?**
A: The principle of collecting the most volatile (easily lost) evidence first: CPU registers/cache → RAM → network connections/processes → disk data → logs → archival media. This guides forensic collection priority during live response.

**Q51. What is the difference between a disk image and a memory dump?**
A: A disk image is a complete, bit-for-bit copy of a storage drive used for forensic analysis of files, deleted data, etc. A memory dump captures the contents of RAM at a point in time, useful for analyzing running processes, injected code, and encryption keys that may not exist on disk.

**Q52. What is a playbook (in IR context) and why is it important?**
A: A predefined, step-by-step procedure for responding to a specific type of incident (e.g., phishing, ransomware, malware infection), ensuring consistent, efficient, and complete response regardless of which analyst handles it.

**Q53. What is the difference between root cause analysis and impact analysis during an incident?**
A: Root cause analysis identifies how/why the incident occurred (the initial vulnerability or vector exploited). Impact analysis assesses what was affected (systems, data, business operations) and the severity of damage caused.

**Q54. What is a "lessons learned" or post-incident review, and what should it cover?**
A: A review conducted after incident closure to evaluate what happened, how effectively the team responded, what worked/didn't work, and to recommend improvements to detection, processes, or controls to prevent recurrence.

**Q55. What is the difference between an IR plan and a Business Continuity Plan (BCP)?**
A: An IR plan focuses specifically on detecting, responding to, and recovering from security incidents. A BCP is broader, covering how the entire business continues operating during any major disruption (natural disasters, outages, incidents included).

---

## Threat Intelligence & MITRE ATT&CK

**Q56. What is Threat Intelligence and how is it used in a SOC?**
A: Information about existing or emerging threats (actors, TTPs, IOCs) gathered, analyzed, and used to improve detection, prioritize alerts, and inform proactive defense decisions.

**Q57. What are the types of threat intelligence?**
A: Strategic (high-level trends for executives/decision-makers), Tactical (TTPs used by adversaries, informs detection rules), Operational (details on specific campaigns/attacks), and Technical (specific IOCs like hashes, IPs, domains).

**Q58. What is MITRE ATT&CK and how do SOC analysts use it?**
A: A globally accessible knowledge base of adversary tactics and techniques based on real-world observations, organized into a matrix (Tactics like Initial Access, Execution, Persistence, etc., each with specific Techniques). SOC analysts use it to map detected activity to known attacker behavior, identify detection coverage gaps, and standardize reporting/communication.

**Q59. What is the difference between a TTP and an IOC?**
A: TTP (Tactics, Techniques, and Procedures) describes how an attacker operates/behaves (the methodology). An IOC is a specific, often static artifact of an attack (a malicious hash, IP, domain) — TTPs are harder for attackers to change than IOCs, making TTP-based detection more resilient.

**Q60. What is a threat actor, and what are the common categories?**
A: An individual or group responsible for conducting (or having the intent/capability to conduct) malicious activity. Categories: Nation-state/APT (Advanced Persistent Threat) groups, cybercriminals (financially motivated), hacktivists (ideologically motivated), and insider threats.

**Q61. What is an APT (Advanced Persistent Threat)?**
A: A sophisticated, often state-sponsored threat actor that gains unauthorized access to a network and remains undetected for an extended period, typically pursuing long-term objectives like espionage or data theft rather than quick financial gain.

---

## Tools

**Q62. What is Wireshark used for in a SOC context?**
A: A network protocol analyzer used to capture and inspect packet-level traffic, helping analysts investigate suspicious network activity, verify alerts, and perform deep-dive traffic analysis during incident investigations.

**Q63. What is the difference between Splunk SPL queries and basic log searching?**
A: SPL (Search Processing Language) allows analysts to filter, transform, correlate, and visualize log data with powerful commands (`stats`, `eval`, `join`, `timechart`), going far beyond simple keyword/string searching to enable complex correlation and dashboarding.

**Q64. What is Sysmon and why is it valuable for SOC monitoring?**
A: A Windows system service/driver (part of Sysinternals) that logs detailed system activity (process creation, network connections, file changes, registry modifications) far beyond default Windows logging, providing rich telemetry critical for detection engineering and investigations.

**Q65. What is VirusTotal and how would a SOC analyst use it?**
A: An online service that scans files/URLs/hashes/IPs against dozens of antivirus engines and threat intelligence sources. Analysts use it to quickly check the reputation/maliciousness of an IOC encountered during an investigation.

**Q66. What is the difference between CrowdStrike Falcon, SentinelOne, and Microsoft Defender for Endpoint?**
A: All three are EDR/XDR platforms providing endpoint visibility, threat detection, and response capabilities (isolating hosts, killing processes). They differ in their detection engines, cloud architecture, integrations, and specific feature sets, but conceptually serve the same SOC purpose: real-time endpoint monitoring and response.

**Q67. What is a sandbox (e.g., Any.Run, Cuckoo) used for?**
A: An isolated environment used to safely execute and observe suspicious files/URLs, allowing analysts to determine their behavior (network calls, file drops, persistence mechanisms) without risking the production environment.

---

## Windows/Linux Security Basics

**Q68. What is the difference between Event ID 4624 and 4625?**
A: 4624 indicates a successful logon; 4625 indicates a failed logon attempt. Monitoring patterns of 4625 followed by 4624 from the same source can indicate a successful brute-force attempt.

**Q69. What is PowerShell logging and why is it important for SOC visibility?**
A: PowerShell logging (Script Block Logging, Module Logging, Transcription) records the commands/scripts executed via PowerShell, which is critical since attackers heavily abuse PowerShell for fileless attacks and post-exploitation activity that wouldn't otherwise be visible.

**Q70. What is the purpose of `/var/log/auth.log` (or `/var/log/secure`) on Linux?**
A: It logs authentication-related events (SSH logins, sudo usage, failed password attempts), critical for detecting brute-force attempts or unauthorized access on Linux systems.

**Q71. What is the difference between a local account and a domain account in Windows/AD?**
A: A local account exists only on a single machine with access limited to that machine. A domain account is managed centrally by Active Directory and can authenticate/access resources across multiple machines in the domain, making domain account compromise far more impactful.

**Q72. What is UAC (User Account Control) and how can attackers bypass it?**
A: UAC is a Windows security feature that prompts for elevation when an action requires administrative privileges, helping prevent unauthorized changes. Attackers can bypass it using techniques like DLL hijacking, certain trusted binaries (auto-elevating without a prompt), or exploiting specific known bypass techniques (UACMe).

---

## Scenario-Based Questions (Beginner)

**S1. You receive an alert: "Multiple failed login attempts followed by a successful login" for a user account from an unfamiliar external IP. What are your first steps?**
A: Verify if the user is expected to log in remotely/internationally (check with the user or HR/travel records), check the IP's reputation via threat intel tools, review the account's recent activity for anomalies (data access, privilege changes), and if suspicious, initiate containment (disable account/force password reset) and escalate per the playbook.

**S2. An end user reports they clicked a link in a suspicious email and entered their credentials on a page that "looked like Office 365 login." What do you do?**
A: Immediately reset the user's password and revoke active sessions/tokens, check for any suspicious mailbox rules or forwarding set up (common BEC follow-up), review login history for unauthorized access from new locations/devices, block the phishing URL/domain at the email gateway and proxy, and notify other users if the campaign appears widespread.

**S3. You see an alert that a workstation is communicating with an IP address flagged as malicious in threat intelligence feeds. What is your triage process?**
A: Confirm the alert isn't a false positive (check if the IP/domain is genuinely malicious via VirusTotal/other TI sources), identify the process/application responsible for the connection on the endpoint, check for any related file drops or persistence mechanisms, and if confirmed malicious, isolate the host from the network and escalate for deeper investigation.

**S4. A user calls the help desk saying their files have ".locked" extensions and a ransom note appeared on their desktop. What is your immediate action?**
A: Immediately isolate/disconnect the affected machine from the network (pull network cable/disable Wi-Fi, or isolate via EDR) to prevent lateral spread, do not power off the machine (preserve memory for forensics), notify the IR team/management per the ransomware playbook, and begin identifying the scope (other affected systems/shares).

**S5. While reviewing firewall logs, you notice an internal host making thousands of outbound connection attempts to many different external IPs on port 445. What does this suggest and what's your next step?**
A: This pattern suggests possible malware attempting SMB-based lateral movement/scanning (e.g., worm-like behavior similar to WannaCry). Investigate the source host for signs of compromise, check EDR/AV logs on that host, and consider isolating it while investigating further.

**S6. You receive a low-severity alert for a single failed login attempt on a critical server. Should you escalate this immediately? Why or why not?**
A: A single failed login is typically low risk on its own (could be a typo) and doesn't usually warrant immediate escalation, but it should still be logged and monitored for a pattern (repeated attempts, multiple accounts, off-hours timing) before deciding whether further investigation/escalation is warranted — context and correlation matter more than a single isolated event.

**S7. An alert fires for "antivirus detected and quarantined malware" on an endpoint. The AV says the threat was successfully removed. Do you close the ticket immediately?**
A: Not immediately — verify the quarantine was fully successful, check how the malware got onto the system in the first place (download, email attachment, USB), check for any related IOCs or persistence mechanisms that may not have been caught by AV, and confirm no further malicious activity (e.g., outbound C2 attempts) occurred before closing.

**S8. You notice a user account that normally logs in only during business hours (9 AM–6 PM) suddenly has a successful login at 2 AM. What should you investigate?**
A: Check if the user had any legitimate reason (e.g., approved after-hours work, travel to a different time zone), verify the login's source IP/location/device against their normal pattern, check what resources/data were accessed during that session, and treat it as suspicious until proven otherwise given the deviation from baseline behavior.

**S9. A junior colleague asks you the difference between an "alert" and an "incident." How do you explain it in a SOC context?**
A: An alert is simply a notification generated when monitoring tools detect activity matching a rule/pattern — it may or may not be malicious. An incident is a confirmed event that has caused (or has the potential to cause) actual harm/impact to the organization, requiring formal investigation and response — not every alert becomes an incident.

**S10. You're monitoring the SIEM dashboard and see a sudden spike in DNS queries to randomly generated domain names (e.g., `xkqj3ndlas.com`) from a single internal host. What does this likely indicate?**
A: This pattern is characteristic of a Domain Generation Algorithm (DGA), often used by malware to dynamically generate C2 domains to evade static blocklists. Investigate the source host for malware infection, check what process is generating the DNS queries, and consider isolating the host while blocking the suspicious domains.

---

## Scenario-Based Questions (Intermediate)

**S11. During an investigation, you find that a compromised user account was used to access and download an unusually large volume of files from a file server, followed by outbound traffic to an external cloud storage IP. How would you assess and respond to this?**
A: This pattern suggests data exfiltration following account compromise. Immediately disable/contain the compromised account, identify exactly which files/data were accessed (for impact/compliance assessment — e.g., PII triggering breach notification requirements), block the destination IP/domain, review how the account was initially compromised (phishing, credential stuffing), and escalate to incident response/legal if sensitive data was confirmed exfiltrated.

**S12. You're investigating a host that triggered an EDR alert for "suspicious PowerShell execution with encoded command." How do you proceed with the investigation?**
A: Retrieve and decode the Base64-encoded PowerShell command (commonly seen via `-EncodedCommand` flag) to understand its actual function, check the parent process that spawned PowerShell (e.g., Word/Excel spawning PowerShell suggests a malicious macro), review network connections initiated by the script (possible C2 callback), and check for persistence mechanisms (scheduled tasks, registry run keys) created afterward.

**S13. A SIEM correlation rule fires indicating "Kerberoasting activity detected" — multiple TGS requests for different service accounts from a single user in a short time window. What's your response process?**
A: Confirm legitimacy by checking if the requesting account/user has a valid business reason for this activity (some legitimate admin tools behave similarly), identify which service accounts were targeted and their privilege level, check if any of those service accounts show signs of subsequent misuse (logins from new sources), and if confirmed malicious, force password rotation on the targeted service accounts and investigate the source user account for compromise.

**S14. You receive an alert that a privileged domain admin account logged in from two geographically distant locations within a short timeframe ("impossible travel"). What do you do?**
A: Treat this as high priority given the account's privilege level — immediately verify with the actual account owner if both logins are legitimate (e.g., VPN usage could explain it), check session activity from both logins for signs of malicious action, if compromise is suspected, disable the account, terminate active sessions, force a password reset, and review all actions taken by that account during the suspicious window for potential damage/persistence.

**S15. While threat hunting, you find a scheduled task on multiple servers that runs a PowerShell script downloading content from a Pastebin-like URL. None of these were flagged by existing alerts. What does this indicate, and what's your next step?**
A: This indicates a detection gap — the activity (LOLBin abuse via PowerShell + scheduled task persistence) evaded existing rules, suggesting potential successful persistence by an attacker (or red team) using "living off the land" techniques. Investigate the script's actual payload/purpose, check creation timestamps and the account that created the tasks, scope how many systems are affected, and recommend new detection rules/use cases to catch this pattern in the future.

**S16. You're reviewing a phishing email reported by a user. The headers show SPF: pass, DKIM: pass, DMARC: pass, but the content urgently requests a wire transfer "from the CEO." What's happening and how do you respond?**
A: Passing SPF/DKIM/DMARC suggests either the sender's actual domain/account was compromised (not spoofed) or it's a lookalike domain that has its own valid records — review the actual sending domain carefully (e.g., `compnay.com` vs `company.com`). Treat as a likely Business Email Compromise (BEC)/CEO fraud attempt — alert the finance team to halt any pending transfers, verify through an out-of-band channel (phone call) before any action is taken, and block the sending domain/address.

**S17. An EDR alert indicates "process hollowing" detected on a critical server. Explain what this technique is and your investigative approach.**
A: Process hollowing is a technique where an attacker creates a legitimate process in a suspended state, removes (hollows out) its original code from memory, and replaces it with malicious code, making the malicious process appear as a trusted one (e.g., svchost.exe) in process listings. Investigate by capturing a memory dump for forensic analysis, identifying the parent process and how it was spawned, checking for network connections originating from the hollowed process, and isolating the host immediately given the severity/stealth of this technique.

**S18. You discover that a workstation has an active RDP session originating from an unrecognized internal IP address that doesn't correspond to any known admin workstation, occurring at 3 AM. What's your investigation path?**
A: Identify the source IP/host and determine if it's a legitimate but unrecorded asset or potentially attacker-controlled (a pivot point from an earlier compromise), check the credentials used for the RDP session and whether they show signs of being stolen (recent phishing reports, password spray alerts on that account), review what actions were taken during the RDP session on the destination workstation, and if malicious, isolate both the source and destination hosts and trace back to find the initial point of compromise.

**S19. While investigating a malware sample flagged by EDR, you find it's making HTTPS connections to a domain that was registered only two days ago. Why is this significant, and what other indicators would you check?**
A: Recently registered domains are a common indicator of malicious infrastructure (attackers frequently spin up new domains for C2 to evade reputation-based blocklists). Check domain WHOIS data, SSL certificate details (self-signed or from a free CA, issued recently), passive DNS history (any other malware samples communicating with the same domain via threat intel platforms), and the hosting provider's reputation, in addition to standard sandboxing of the sample for full behavioral analysis.

**S20. A SOC dashboard shows a 300% increase in failed VPN login attempts across the organization over the last hour, spread across many different user accounts, each with only 1–2 attempts. What attack does this suggest, and how is it different from typical brute force?**
A: This pattern (low attempts per account, many accounts targeted) suggests a password spraying attack rather than traditional brute force (which targets one account with many password attempts — easily caught by lockout policies). Password spraying tries a small number of common passwords across many accounts to evade lockout thresholds. Response includes identifying the source IP(s), checking if any spray attempts succeeded, enforcing/verifying MFA on all accounts, and potentially blocking the source IP at the VPN gateway/firewall.

**S21. During a routine log review, you notice Event ID 1102 (audit log cleared) on a domain controller, with no corresponding change-management ticket. What's the significance and your response?**
A: Clearing the security event log is a classic anti-forensic/cover-tracks technique (MITRE ATT&CK: Indicator Removal), often performed by an attacker after completing malicious activity to hide evidence. This should be treated as a high-severity incident — identify which account performed the clear action, check other DCs/log forwarding (SIEM) for any retained copies of the cleared logs, investigate that account and surrounding timeframe for related suspicious activity, and escalate immediately given the implication of an active, sophisticated threat.

**S22. You're handling an incident where a user's laptop was confirmed compromised, but the user insists they need it back immediately for an urgent client deliverable. How do you balance business pressure with proper incident response?**
A: Explain the risk clearly to the user/management — returning a compromised device prematurely could allow continued attacker access, further damage, or evidence destruction. Offer alternatives (provision a clean temporary device, restore the deliverable from clean backups/cloud storage) while the original device undergoes proper forensic imaging, eradication, and rebuilding — prioritizing security and following the IR playbook rather than yielding to business pressure without appropriate compensating measures.

**S23. While analyzing network traffic, you find a large volume of data being sent out over DNS queries (TXT records) to an external domain, even though there's no apparent DNS-heavy application on that host. What technique does this represent, and how do you confirm it?**
A: This pattern suggests DNS tunneling, used for data exfiltration or C2 communication by encoding data within DNS queries/responses to evade traditional network monitoring (since DNS is rarely blocked). Confirm by analyzing the query patterns (high entropy/randomized-looking subdomains, abnormal query volume/size, TXT/NULL record usage), correlate with the host's process activity, and block the destination domain while investigating the source process.

**S24. A vulnerability scan recently flagged a critical RCE vulnerability on a public-facing server, but patching is scheduled for next maintenance window (2 weeks away). As a SOC analyst, what would you proactively do in the meantime?**
A: Recommend/implement compensating controls — such as a WAF rule or IPS signature specifically targeting that vulnerability's exploitation pattern, increase monitoring/alerting sensitivity for that specific host, restrict network access to the service if feasible (IP allowlisting), and communicate the residual risk clearly to stakeholders, pushing for expedited patching if the exposure is severe enough to warrant an emergency change.

**S25. You're asked to write a detection rule to catch Kerberoasting attempts in your environment. What log source and logic would you use?**
A: Use Windows Security Event ID 4769 (Kerberos service ticket request) logs, focusing on alerting when a single user requests TGS tickets for an unusually high number of distinct service accounts within a short time window, especially where the encryption type is RC4 (0x17) rather than AES (a common indicator since RC4 tickets are easier to crack offline), combined with filtering out known legitimate service accounts/admin tools that produce similar patterns.

---

## Mini Case Study Scenarios

**C1. The "Slow Burn" Account Compromise**
*Scenario:* Over the course of three weeks, a single user account shows a gradual pattern: first, a successful login from a new country (flagged but dismissed as a false positive due to "VPN usage" assumption by a junior analyst). A week later, the account's mailbox rules show a new rule forwarding emails containing "invoice" or "payment" to an external address. Two weeks after that, finance reports a fraudulent wire transfer based on what appeared to be a legitimate internal email thread.
*Discussion points:* Where did the initial triage go wrong? How could correlation across these three separate, weeks-apart events have caught this earlier? What detection rule/use case would you propose to catch "new mailbox forwarding rule to external domain" as a standalone high-priority alert?

**C2. The Noisy Decoy**
*Scenario:* Your SOC spends most of a shift dealing with a large volume of alerts from a known false-positive-prone vulnerability scanner running its scheduled scan (correctly identified and suppressed). Buried among the noise, a single alert for "unusual outbound connection from domain controller to external IP on port 443" goes unnoticed for 6 hours until a threat hunter notices it during a routine review — by which time the attacker had already exfiltrated NTDS.dit (the AD database).
*Discussion points:* What does this illustrate about the danger of alert fatigue and poor noise suppression practices? How should critical asset alerts (e.g., domain controllers) be treated differently from general alerts in terms of priority/SLA? What compensating process (e.g., dedicated critical-asset monitoring queue) could prevent this in the future?

**C3. The Insider with Legitimate Access**
*Scenario:* An employee in the finance department, who has legitimate access to the finance file share as part of their job, starts downloading significantly more files than their historical baseline, including some files outside their usual project scope, over a weekend when they weren't scheduled to work. No malware or external IOC is involved — this is a fully "living" legitimate account doing legitimate-looking actions.
*Discussion points:* Since no traditional IOC or malware signature exists, how would behavior/UEBA-based detection catch this? What's the difference in handling an insider threat investigation versus an external attacker investigation (e.g., HR/legal involvement)? What data points (volume, timing, file sensitivity, historical baseline) would build the case for escalation?

**C4. The Multi-Stage Ransomware Build-Up**
*Scenario:* Two days before a ransomware deployment that ultimately encrypts 40% of the organization's servers, the following individually low/medium severity alerts had fired and were each closed without escalation: (1) a successful RDP brute force on a jump server (closed as "scanner noise"), (2) a Mimikatz-like credential dumping alert on that same server (closed because EDR auto-quarantined the file), (3) a new admin-level account creation on a domain controller (closed as "likely an approved but undocumented IT change").
*Discussion points:* How does this illustrate the importance of treating "auto-remediated" alerts with the same investigative rigor as unremediated ones? What process change (e.g., mandatory escalation for credential-dumping tool detections regardless of auto-quarantine status) could have disrupted this kill chain? How would you write up the post-incident "lessons learned" findings for SOC leadership?

**C5. The Cloud Misconfiguration Discovery**
*Scenario:* During a routine review of cloud access logs (AWS CloudTrail), you notice an IAM user (a service account tied to a CI/CD pipeline) made an API call to list all S3 buckets and then accessed several buckets it had never touched before, from an IP address belonging to a cloud hosting provider rather than the company's known CI/CD infrastructure IP range.
*Discussion points:* What does this suggest about how the service account's credentials might have been compromised (e.g., leaked in a public GitHub repo)? How is investigating cloud-based incidents (IAM roles, API calls, ephemeral infrastructure) different from traditional on-prem endpoint investigations? What preventive controls (least privilege IAM policies, credential rotation, secret scanning) would you recommend post-incident?

---

## How to Use This for Practice

- For **0–1 years (Tier 1/Triage)**: Focus on Networking & Fundamentals, SOC Concepts, basic SIEM/log Q&A, and Beginner Scenarios.
- For **1–3 years (Tier 1/Tier 2)**: Add Malware/Endpoint, Email Security, Incident Response basics, Tools, and Intermediate Scenarios.
- For **3–5 years (Tier 2/Tier 3)**: Focus on Threat Intelligence/MITRE ATT&CK, advanced forensics, detection engineering, mini case studies, and be ready to discuss process improvements and cross-team escalation in depth.

---

*Feel free to fork, expand, and contribute additional questions via pull requests.*
