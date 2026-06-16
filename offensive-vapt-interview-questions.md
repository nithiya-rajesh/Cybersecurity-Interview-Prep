# Offensive Security / VAPT Interview Questions (0–5 Years)

A curated collection of beginner and intermediate level questions for Offensive Security, Penetration Testing, and VAPT roles. Includes theory-based Q&A and real-world scenario questions.

---

## Table of Contents
1. [Networking & Fundamentals](#networking--fundamentals)
2. [Web Application Security](#web-application-security)
3. [Network Penetration Testing](#network-penetration-testing)
4. [Active Directory / Windows](#active-directory--windows)
5. [Linux & Privilege Escalation](#linux--privilege-escalation)
6. [Tools & Methodology](#tools--methodology)
7. [Cryptography & Misc](#cryptography--misc)
8. [Scenario-Based Questions (Beginner)](#scenario-based-questions-beginner)
9. [Scenario-Based Questions (Intermediate)](#scenario-based-questions-intermediate)
10. [Mini Case Study Scenarios](#mini-case-study-scenarios)

---

## Networking & Fundamentals

**Q1. What is the difference between TCP and UDP?**
A: TCP is connection-oriented, reliable, and uses a three-way handshake (SYN, SYN-ACK, ACK) with error checking and ordered delivery. UDP is connectionless, faster, and does not guarantee delivery or order — commonly used for DNS, streaming, and VoIP.

**Q2. Explain the TCP three-way handshake.**
A: SYN (client requests connection) → SYN-ACK (server acknowledges and responds) → ACK (client confirms). This establishes a reliable connection before data transfer begins.

**Q3. What is the OSI model and why is it important for pentesting?**
A: A 7-layer conceptual framework (Physical, Data Link, Network, Transport, Session, Presentation, Application) describing how data flows. Pentesters use it to identify where vulnerabilities exist — e.g., ARP spoofing (Layer 2), IP spoofing (Layer 3), SQLi (Layer 7).

**Q4. What is the difference between a port scan and a vulnerability scan?**
A: A port scan identifies open ports and running services on a host. A vulnerability scan goes further by checking those services/versions against known CVEs and misconfigurations.

**Q5. What are common TCP/UDP ports and their services?**
A: 21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP), 53 (DNS), 80 (HTTP), 443 (HTTPS), 445 (SMB), 3389 (RDP), 3306 (MySQL), 1433 (MSSQL), 389 (LDAP), 88 (Kerberos).

**Q6. What is the difference between a vulnerability assessment and a penetration test?**
A: Vulnerability assessment identifies and lists potential weaknesses (often automated). A penetration test goes further by actively exploiting those weaknesses to demonstrate real-world impact.

**Q7. What is the difference between black box, white box, and grey box testing?**
A: Black box = no internal knowledge (simulates external attacker). White box = full access to source code/architecture. Grey box = partial knowledge (e.g., user-level credentials), simulating an insider or compromised account.

**Q8. What is a CVE and a CVSS score?**
A: CVE (Common Vulnerabilities and Exposures) is a unique identifier for a publicly known vulnerability. CVSS (Common Vulnerability Scoring System) rates severity from 0–10 based on factors like attack vector, complexity, and impact.

**Q9. What is the difference between a vulnerability, a threat, and a risk?**
A: A vulnerability is a weakness; a threat is a potential cause of harm exploiting that weakness; risk is the likelihood and impact of the threat exploiting the vulnerability — risk = threat × vulnerability × impact.

**Q10. What is the CIA triad?**
A: Confidentiality, Integrity, and Availability — the three core principles of information security that every assessment ultimately protects.

---

## Web Application Security

**Q11. What is SQL Injection and how does it work?**
A: SQLi occurs when user input is improperly sanitized and gets concatenated into a SQL query, allowing an attacker to manipulate the query logic — e.g., `' OR '1'='1` to bypass authentication.

**Q12. What are the types of SQL Injection?**
A: In-band (Union-based, Error-based), Blind (Boolean-based, Time-based), and Out-of-band SQLi (using DNS/HTTP requests to exfiltrate data).

**Q13. What is Cross-Site Scripting (XSS) and its types?**
A: XSS allows an attacker to inject malicious scripts into web pages viewed by other users. Types: Reflected (input reflected immediately), Stored (persisted in DB and served to other users), DOM-based (vulnerability in client-side JS).

**Q14. What is CSRF and how is it different from XSS?**
A: CSRF (Cross-Site Request Forgery) tricks an authenticated user's browser into sending unwanted requests to a site they're logged into. Unlike XSS, CSRF doesn't inject code — it abuses existing trust/session via forged requests.

**Q15. How do you prevent CSRF attacks?**
A: Anti-CSRF tokens, SameSite cookie attribute, checking the Origin/Referer header, and requiring re-authentication for sensitive actions.

**Q16. What is an IDOR vulnerability?**
A: Insecure Direct Object Reference — occurs when an application exposes internal object references (e.g., `?id=1001`) without proper authorization checks, allowing users to access others' data by changing the ID.

**Q17. What is SSRF (Server-Side Request Forgery)?**
A: SSRF occurs when an attacker can make the server send requests to unintended locations (internal services, cloud metadata endpoints like `169.254.169.254`), potentially leading to internal network access or credential theft.

**Q18. What is the difference between authentication and authorization, and how do vulnerabilities differ in each?**
A: Authentication verifies identity (who you are); authorization determines access rights (what you can do). Broken authentication includes weak password policies/session issues; broken authorization includes privilege escalation and IDOR.

**Q19. What is a File Inclusion vulnerability (LFI/RFI)?**
A: LFI (Local File Inclusion) allows an attacker to include files from the local server (e.g., `/etc/passwd`) via unsanitized input. RFI (Remote File Inclusion) allows including a remote file, often leading to RCE.

**Q20. What is XXE (XML External Entity) injection?**
A: An attack against applications that parse XML input, allowing attackers to read local files, perform SSRF, or cause denial of service by defining malicious external entities in the XML.

**Q21. What is the difference between stored and reflected XSS in terms of impact?**
A: Stored XSS is generally more severe because it persists and affects every user who views the affected page, whereas reflected XSS requires the victim to click a crafted link.

**Q22. What is Command Injection?**
A: Occurs when user input is passed unsanitized into a system shell command, allowing arbitrary OS command execution (e.g., `; cat /etc/passwd`).

**Q23. What is a Content Security Policy (CSP) and how does it help mitigate XSS?**
A: CSP is an HTTP header that restricts which sources of content (scripts, styles, images) a browser is allowed to load, reducing the impact of injected scripts.

**Q24. What is the OWASP Top 10?**
A: A standard awareness document listing the most critical web application security risks, e.g., Broken Access Control, Cryptographic Failures, Injection, Insecure Design, Security Misconfiguration, Vulnerable Components, Identification/Authentication Failures, Software/Data Integrity Failures, Logging Failures, and SSRF.

**Q25. What is JWT and what are common JWT vulnerabilities?**
A: JWT (JSON Web Token) is used for stateless authentication. Common issues: "none" algorithm bypass, weak signing secrets (brute-forceable), algorithm confusion (RS256 to HS256), and lack of expiration validation.

**Q26. What is clickjacking and how is it prevented?**
A: An attack where a malicious site overlays an invisible iframe of a legitimate site to trick users into clicking unintended elements. Prevented using `X-Frame-Options` header or CSP `frame-ancestors` directive.

**Q27. What is HTTP request smuggling?**
A: An attack that exploits discrepancies in how front-end and back-end servers parse the `Content-Length` and `Transfer-Encoding` headers, allowing attackers to "smuggle" a second request that gets processed differently.

**Q28. What is a path traversal/directory traversal vulnerability?**
A: Occurs when user input controlling file paths isn't sanitized, allowing access to files outside the intended directory using sequences like `../../etc/passwd`.

**Q29. What is the difference between encoding, encryption, and hashing? Why does it matter in security testing?**
A: Encoding transforms data format reversibly (Base64) without security purpose; encryption is reversible with a key (confidentiality); hashing is one-way (integrity/password storage). Misusing encoding as "security" is a common finding (e.g., Base64 mistaken for encryption).

**Q30. What is a race condition vulnerability in web apps?**
A: Occurs when multiple simultaneous requests exploit timing windows to bypass logic checks — e.g., redeeming a discount code multiple times before the balance updates.

---

## Network Penetration Testing

**Q31. What is the difference between Nmap TCP connect scan and SYN scan?**
A: SYN scan (`-sS`) sends only SYN packets and doesn't complete the handshake — stealthier and faster, requires root. Connect scan (`-sT`) completes the full TCP handshake, slower and more easily logged.

**Q32. What is ARP spoofing/poisoning?**
A: An attack where the attacker sends forged ARP messages to associate their MAC address with the IP of another host (often the gateway), enabling man-in-the-middle attacks.

**Q33. What is a man-in-the-middle (MITM) attack?**
A: An attack where the attacker intercepts communication between two parties without their knowledge, allowing eavesdropping or data manipulation — e.g., via ARP spoofing, rogue Wi-Fi APs, or SSL stripping.

**Q34. What is SMB and why is it commonly targeted in internal pentests?**
A: SMB (Server Message Block, port 445) is used for file/printer sharing on Windows networks. It's frequently targeted due to vulnerabilities like EternalBlue (MS17-010), null sessions, and weak share permissions.

**Q35. What is a pass-the-hash attack?**
A: An attack where the attacker uses a captured NTLM password hash (without cracking it) to authenticate to other systems, exploiting how Windows authentication works.

**Q36. What is the difference between a vulnerability scanner like Nessus and a manual pentest?**
A: A scanner automates detection of known vulnerabilities based on signatures/CVEs but cannot understand business logic. A manual pentest validates findings, chains vulnerabilities, and identifies business-logic and contextual issues scanners miss.

**Q37. What is VLAN hopping?**
A: An attack technique where a host on one VLAN gains access to traffic on another VLAN, typically via switch spoofing or double tagging (802.1Q).

**Q38. What is DNS zone transfer and why can it be a risk?**
A: A DNS zone transfer (AXFR) replicates DNS records between servers. If misconfigured to allow transfers to anyone, attackers can enumerate the entire internal/external DNS infrastructure (subdomains, hostnames, IPs).

**Q39. What is a reverse shell vs a bind shell?**
A: A reverse shell has the target connect back to the attacker's listener (useful when the target is behind NAT/firewall). A bind shell has the target open a listening port that the attacker connects to.

**Q40. What is the difference between a vulnerability in a service and a misconfiguration?**
A: A vulnerability is a flaw in the software itself (e.g., unpatched buffer overflow); a misconfiguration is an insecure setting by the administrator (e.g., default credentials, anonymous FTP enabled) — both are equally exploitable but require different remediation.

---

## Active Directory / Windows

**Q41. What is Kerberoasting?**
A: An attack where an authenticated user requests service tickets (TGS) for accounts with SPNs set, then attempts to crack the ticket's encrypted portion offline to recover the service account's plaintext password.

**Q42. What is an ASREPRoast attack?**
A: Targets accounts with "Do not require Kerberos preauthentication" enabled — an attacker can request an AS-REP for such accounts and crack it offline to recover the password without needing valid credentials.

**Q43. What is the difference between NTLM and Kerberos authentication?**
A: NTLM is a challenge-response protocol vulnerable to relay/pass-the-hash attacks. Kerberos uses ticket-based authentication with a trusted KDC (Key Distribution Center) and is generally more secure but vulnerable to Kerberoasting/Golden Ticket attacks.

**Q44. What is LLMNR/NBT-NS poisoning?**
A: LLMNR and NBT-NS are fallback name resolution protocols. An attacker (using tools like Responder) can respond to these broadcast requests, capturing NTLM hashes from victims trying to resolve non-existent hostnames.

**Q45. What is a Golden Ticket attack?**
A: An attack where an attacker who has compromised the KRBTGT account hash can forge Kerberos TGTs (Ticket Granting Tickets) for any user, granting domain-wide persistent access.

**Q46. What is the difference between a domain admin and an enterprise admin in AD?**
A: Domain Admins have full control over a single domain; Enterprise Admins have control across all domains in a forest — a much higher-value target.

**Q47. What is BloodHound used for?**
A: A tool that visualizes Active Directory relationships (group memberships, ACLs, trust relationships) to identify attack paths to privileged accounts like Domain Admin.

**Q48. What is the difference between local privilege escalation and domain privilege escalation?**
A: Local privesc gains higher privileges on a single machine (e.g., user to local admin). Domain privesc leverages AD misconfigurations/relationships to escalate from a regular domain user to Domain Admin across the network.

**Q49. What is SMB relay attack?**
A: An attack where captured NTLM authentication attempts (via LLMNR poisoning, etc.) are relayed in real-time to another machine to authenticate as the victim, often gaining SMB/admin access.

**Q50. What are GPOs and why are they relevant to attackers?**
A: Group Policy Objects control settings across the domain. Misconfigured GPO permissions can allow attackers to push malicious scripts/settings to all machines in an OU, leading to mass compromise.

---

## Linux & Privilege Escalation

**Q51. What is SUID and how can it be abused for privilege escalation?**
A: SUID (Set User ID) makes a binary run with the file owner's privileges (often root) regardless of who executes it. If a SUID binary can be manipulated to execute arbitrary commands (e.g., via GTFOBins), it can lead to privilege escalation.

**Q52. What is the difference between sudo misconfiguration and SUID exploitation?**
A: Sudo misconfiguration occurs when a user is allowed to run specific commands as root without proper restriction (e.g., `sudo vim` allows escaping to a root shell). SUID exploitation abuses binaries with the setuid bit set, independent of sudo rules.

**Q53. What is a kernel exploit and when would you use one?**
A: An exploit targeting a vulnerability in the OS kernel itself, often used for privilege escalation when no other vector (misconfigurations, weak permissions) is found — but it's considered higher-risk due to potential system instability.

**Q54. What are cron jobs and how can they be exploited?**
A: Cron jobs are scheduled tasks. If a cron job (especially one run as root) references a script that is world-writable, an attacker can modify that script to execute arbitrary commands with root privileges.

**Q55. What is the difference between `/etc/passwd` and `/etc/shadow`?**
A: `/etc/passwd` contains user account information (readable by all) but no longer stores password hashes. `/etc/shadow` stores the actual hashed passwords and is readable only by root.

**Q56. How would you enumerate a Linux system for privilege escalation opportunities?**
A: Check `sudo -l`, SUID/SGID binaries (`find / -perm -4000`), writable cron jobs, kernel/OS version for known exploits, world-writable files/directories, stored credentials in config files/history, and running processes/services with elevated privileges.

**Q57. What is a "writable PATH" privilege escalation technique?**
A: If a script run by a privileged process calls a binary without a full path, and an attacker can write to a directory earlier in the `$PATH`, they can place a malicious binary with that name to be executed with elevated privileges.

**Q58. What is the difference between horizontal and vertical privilege escalation?**
A: Horizontal privilege escalation means gaining access to another user's resources at the same privilege level (e.g., user A accessing user B's data). Vertical privilege escalation means gaining higher privileges (e.g., user to admin/root).

---

## Tools & Methodology

**Q59. Name the phases of a typical penetration testing methodology.**
A: Pre-engagement/Scoping → Reconnaissance (OSINT) → Scanning & Enumeration → Vulnerability Analysis → Exploitation → Post-Exploitation → Reporting → Remediation/Retesting.

**Q60. What is the difference between active and passive reconnaissance?**
A: Passive recon gathers information without directly interacting with the target (OSINT, WHOIS, search engines, certificate transparency logs). Active recon directly interacts with the target (port scanning, banner grabbing).

**Q61. What is Burp Suite used for and name some of its core tools.**
A: Burp Suite is a web app proxy/testing toolkit. Core tools: Proxy (intercept traffic), Repeater (resend/modify requests), Intruder (automated fuzzing/brute force), Decoder (encode/decode data), and Scanner (automated vulnerability detection in Pro version).

**Q62. What is the difference between Nmap, Nikto, and Nessus?**
A: Nmap is primarily a network/port scanner. Nikto is a web server vulnerability scanner checking for outdated software/misconfigurations. Nessus is a comprehensive vulnerability scanner across hosts, network devices, and applications using CVE databases.

**Q63. What is Metasploit and what is the purpose of msfvenom?**
A: Metasploit is an exploitation framework containing exploits, payloads, and auxiliary modules. `msfvenom` is used to generate standalone payloads (e.g., reverse shells) in various formats for different platforms.

**Q64. What is the purpose of a wordlist in pentesting, and name a commonly used one.**
A: Wordlists are used for brute-forcing (passwords, directories, subdomains, usernames). A commonly used one is `rockyou.txt` for password attacks, and `SecLists` for general-purpose wordlists.

**Q65. What is the difference between Hydra and John the Ripper?**
A: Hydra is an online brute-forcing tool used against live services (SSH, FTP, HTTP login forms). John the Ripper is an offline password-cracking tool used against captured hashes.

**Q66. What is a payload, an exploit, and a listener?**
A: An exploit is the code that takes advantage of a vulnerability. A payload is the code that runs after successful exploitation (e.g., reverse shell). A listener is the process on the attacker's machine waiting to receive a connection from the payload.

**Q67. What should a good penetration test report include?**
A: Executive summary (business-level risk overview), scope and methodology, findings with CVSS/severity ratings, proof-of-concept/evidence (screenshots), business impact, and detailed remediation recommendations.

**Q68. What is the difference between a CTF and a real-world pentest engagement?**
A: CTFs are designed puzzles with a defined "win condition" and usually no production impact. Real pentests involve live systems, require careful scoping, rules of engagement, communication with stakeholders, evidence of due care (avoiding disruption), and professional reporting.

---

## Cryptography & Misc

**Q69. What is the difference between symmetric and asymmetric encryption?**
A: Symmetric encryption uses the same key for encryption and decryption (fast, e.g., AES). Asymmetric encryption uses a public/private key pair (slower, e.g., RSA), commonly used for key exchange and digital signatures.

**Q70. What is a hash collision?**
A: When two different inputs produce the same hash output. Weak hashing algorithms like MD5 are vulnerable to collisions, undermining their use for integrity verification.

**Q71. Why is MD5 considered insecure for password storage?**
A: MD5 is fast (allows rapid brute-forcing), has known collision vulnerabilities, and lacks built-in salting — making it unsuitable compared to algorithms designed for password hashing like bcrypt, scrypt, or Argon2.

**Q72. What is salting in password storage?**
A: Adding a unique random value to each password before hashing, ensuring identical passwords produce different hashes and defeating precomputed rainbow table attacks.

**Q73. What is the difference between HTTP and HTTPS, and what does TLS provide?**
A: HTTPS is HTTP over TLS, providing encryption (confidentiality), data integrity, and authentication of the server (via certificates) — preventing eavesdropping and tampering.

**Q74. What is a digital certificate and what does a Certificate Authority (CA) do?**
A: A digital certificate binds a public key to an identity (domain/organization), digitally signed by a trusted CA, allowing clients to verify the server's authenticity during a TLS handshake.

---

## Scenario-Based Questions (Beginner)

**S1. During an Nmap scan, you find port 21 (FTP) open with anonymous login allowed. What would you do next?**
A: Connect via FTP using anonymous credentials, enumerate accessible files/directories for sensitive data (configs, credentials, source code), check for write permissions (which could allow uploading a malicious file), and document the finding with risk impact (information disclosure or potential for further compromise).

**S2. You find a login page that returns "Invalid username" for some usernames and "Invalid password" for others. What vulnerability does this represent and what's the risk?**
A: This is a username enumeration vulnerability via verbose error messages. It allows attackers to build a list of valid usernames, which can then be used for targeted brute-force or credential stuffing attacks. Recommend generic error messages like "Invalid username or password."

**S3. While testing a web app, you notice the URL `https://site.com/profile?user_id=1023` shows your profile. Changing it to `1024` shows another user's profile. What is this and how would you confirm/exploit it?**
A: This is an IDOR (Insecure Direct Object Reference). Confirm by systematically testing other IDs while logged in as a low-privileged user and checking if you can view/modify other users' data without authorization. Document the impact (data exposure scope) and recommend object-level access control checks.

**S4. You run `whatweb` or check response headers and find the server discloses `Server: Apache/2.4.49`. Why is this important?**
A: Version disclosure helps attackers identify known CVEs for that specific version (e.g., Apache 2.4.49 had a critical path traversal/RCE — CVE-2021-41773). Recommend removing/obscuring version banners as a defense-in-depth measure, though the underlying patching is the real fix.

**S5. A client asks you to test their login page, but it has no CAPTCHA and no account lockout policy. What would you test for?**
A: Test for brute-force/credential-stuffing susceptibility using tools like Hydra or Burp Intruder with a wordlist, while being mindful of scope/rate-limiting agreements. Also check for username enumeration and weak default credentials (admin/admin, etc.).

**S6. While scanning, you discover an open SMB share readable by "Everyone" containing what looks like an HR spreadsheet. What is your next step?**
A: Do not open/exfiltrate sensitive personal data unnecessarily — note the file names/types as evidence of the misconfiguration, document the exposure (PII risk), and report it immediately as a high-priority finding given potential GDPR/compliance implications, following responsible disclosure within the engagement scope.

**S7. You find a directory listing enabled on `/uploads/` revealing a `.bak` file of the website's config. What should you check inside?**
A: Check for hardcoded database credentials, API keys, internal hostnames/IPs, and other secrets that could lead to further compromise (e.g., direct DB access). Recommend disabling directory listing and removing backup files from web-accessible directories.

**S8. A web form accepts a file upload for profile pictures with no extension validation. How would you test this for exploitation?**
A: Attempt to upload a web shell (e.g., `shell.php`) and check if it executes when accessed. If `.php` is blocked, try alternate extensions (`.phtml`, `.php5`), double extensions (`shell.jpg.php`), null byte tricks, or MIME-type/content-type manipulation, and check for content-based filtering bypass (e.g., embedding PHP in an image's EXIF/comment fields).

**S9. You receive scope documentation listing only `app.example.com`. During recon, you discover `dev.example.com` is also live and appears vulnerable. What do you do?**
A: Do not test `dev.example.com` — it's outside the agreed scope. Document the discovery and inform the client/point of contact, recommending they consider adding it to scope in a future engagement (or immediate scope expansion via written authorization if critical).

**S10. A target's web app sets a session cookie without the `Secure` or `HttpOnly` flags over HTTPS. What's the risk and how do you test it?**
A: Without `Secure`, the cookie could be sent over unencrypted HTTP if available, risking interception. Without `HttpOnly`, the cookie is accessible via JavaScript, making it stealable via XSS. Test by inspecting cookies in browser dev tools/Burp and attempting to access `document.cookie` if an XSS vector exists.

---

## Scenario-Based Questions (Intermediate)

**S11. During an internal pentest, you capture NTLMv2 hashes using Responder from multiple users on the network. What are your next steps?**
A: Attempt offline cracking using hashcat with a strong wordlist/rules against the captured hashes. In parallel, consider relaying the hashes (using tools like ntlmrelayx) to systems where SMB signing is not enforced, potentially gaining direct access without cracking.

**S12. You've gained a low-privilege shell on a Linux web server. Describe your privilege escalation enumeration approach.**
A: Run automated enumeration scripts (LinPEAS/linux-exploit-suggester) alongside manual checks: `sudo -l`, SUID binaries (`find / -perm -u=s -type f 2>/dev/null`), writable files in cron jobs, kernel version for known exploits, readable config files with credentials, and running processes/services owned by root that might be exploitable.

**S13. While testing a REST API, you notice the JWT token has `alg: none` accepted by the server. How would you exploit this?**
A: Modify the JWT header to set `alg` to `none`, remove the signature portion entirely (keeping the trailing dot), and modify the payload (e.g., change `role` to `admin`). If the server doesn't validate the algorithm and accepts unsigned tokens, this results in authentication/authorization bypass.

**S14. You find that an internal application is vulnerable to SSRF, allowing requests to arbitrary URLs. How would you escalate this in a cloud environment (e.g., AWS)?**
A: Attempt to access the cloud metadata service at `http://169.254.169.254/latest/meta-data/iam/security-credentials/` to retrieve temporary IAM credentials associated with the instance, which could then be used to access other AWS resources depending on the role's permissions.

**S15. You're performing a Kerberoasting attack and successfully retrieve a TGS ticket for a service account, but it doesn't crack with rockyou.txt. What would you try next?**
A: Try more targeted wordlists (company name variations, common patterns), use rule-based attacks with hashcat (e.g., appending years, special characters), check for password reuse against other discovered credentials, and consider whether the account might have a strong password requiring a different attack vector (e.g., looking for ACL-based privilege escalation paths via BloodHound instead).

**S16. During a web app test, you find a blind SQL injection point where the response doesn't change regardless of the query result. How do you confirm and exploit it?**
A: Use time-based techniques — inject payloads like `' AND IF(1=1, SLEEP(5), 0)--` and observe response delays to confirm true/false conditions. Once confirmed, use a tool like SQLMap with `--technique=T` (time-based) to automate data extraction, or boolean-based blind techniques if response content subtly differs (e.g., different status codes or content length).

**S17. You've identified that a company's password reset functionality sends a token via email, but the token appears to be a predictable sequential number. How would you exploit this and what's the impact?**
A: Test by requesting multiple password resets and observing if tokens follow a predictable pattern (sequential, timestamp-based). If predictable, an attacker could guess/brute-force a victim's token, reset their password, and take over the account — a critical account takeover vulnerability.

**S18. While performing a phishing-based social engineering assessment, you successfully harvest a domain user's credentials. The user account doesn't have local admin rights on their machine. What's your next step toward lateral movement?**
A: Use the credentials to authenticate via SMB/WinRM to other hosts (password spraying carefully to avoid lockouts), enumerate shares and accessible resources, check for stored credentials in files/scripts, and use BloodHound to map the user's group memberships and identify any privilege escalation paths (e.g., access to a service account with higher privileges).

**S19. You discover a Git repository (`.git` folder) exposed on a production web server. How would you exploit this?**
A: Use a tool like `git-dumper` or `GitTools` to download the exposed `.git` directory and reconstruct the repository, then review commit history and source code for hardcoded credentials, API keys, internal endpoints, and potentially sensitive business logic.

**S20. During a black-box web app test, you notice that all API responses include detailed stack traces when an error occurs (debug mode enabled). What information might this leak and how would you leverage it?**
A: Stack traces can reveal the underlying framework/version, file paths, database queries, internal variable names, and sometimes even partial source code — all of which help craft more targeted attacks (e.g., framework-specific exploits, SQLi payload tuning) and indicate a broader "security misconfiguration" issue.

**S21. You're testing a thick client application that communicates with a backend over a custom binary protocol. How would you approach intercepting and analyzing this traffic?**
A: Use a tool like Wireshark to capture raw traffic and analyze the protocol structure, or use a proxy like Burp's "Invisible Proxy"/match-and-replace features if it's HTTP-based but obfuscated. For TLS-encrypted thick clients, consider techniques to redirect traffic through a proxy by modifying the hosts file or using tools like `mitmproxy` with certificate pinning bypass (e.g., via reverse engineering/Frida for mobile or patching the binary).

**S22. A client's internal network has SMB signing disabled on several servers. Explain the risk and how an attacker would exploit this in combination with LLMNR poisoning.**
A: With SMB signing disabled, captured NTLM authentication attempts (via Responder/LLMNR poisoning) can be relayed in real-time using `ntlmrelayx` to authenticate to the target server as the victim, potentially executing commands or dumping credentials (e.g., via secretsdump) without ever cracking the password hash.

**S23. You find that an application's "forgot password" feature reveals whether an email address is registered ("Email not found" vs generic message). Separately, you also find the password reset link doesn't expire. How do these combine into a chained risk?**
A: An attacker can first enumerate valid email addresses, then for each valid account, request a password reset and rely on the non-expiring token — if the token is also predictable or can be intercepted (e.g., via email account compromise or referer leakage), the attacker has a long window to take over the account. Recommend generic messaging, time-limited single-use tokens, and secure random token generation.

**S24. During an external pentest, you identify a subdomain pointing to a decommissioned cloud storage bucket (e.g., `assets.client.com` → CNAME to an S3 bucket that doesn't exist). What is this vulnerability called and what's the impact?**
A: This is a "subdomain takeover" via a dangling DNS record. An attacker can register the now-unclaimed cloud resource (S3 bucket, Azure blob, etc.) with the matching name, effectively taking control of content served on `assets.client.com` — useful for phishing, cookie theft (if same parent domain/cookie scope), or hosting malware under a trusted domain.

**S25. You've compromised a low-privilege user on a Windows domain machine and found that the user has "GenericAll" rights over another user object in Active Directory (discovered via BloodHound). How would you exploit this?**
A: GenericAll over a user object allows you to reset that user's password (or perform a "Shadow Credentials" attack by adding alternate authentication material). If the target user has more interesting privileges/group memberships, reset their password (if you can tolerate detection risk) or abuse Kerberos delegation/certificate-based attacks to obtain their TGT and continue the privilege escalation chain toward Domain Admin.

---

## Mini Case Study Scenarios

**C1. The "Forgotten Staging Server"**
*Scenario:* During recon for a client, you discover `staging.client.com` is publicly accessible and running an older version of a CMS with a known unauthenticated RCE vulnerability. The staging environment is not in the signed scope, but it's on the same IP range as in-scope assets and shares the same database credentials (as you later confirm via a config file exposed on the in-scope host).
*Discussion points:* How do you handle the scope question? What's the business risk of "shared credentials" between staging and production? How would you phrase this in your report to convey urgency despite it being technically out-of-scope?

**C2. The "Helpful" Developer Comment**
*Scenario:* While reviewing JavaScript files on a web app, you find a commented-out API endpoint: `// TODO: remove before prod - /api/v1/debug/users?admin_token=true`. Testing this endpoint (in-scope, same application) returns a full dump of user records including hashed passwords and session tokens.
*Discussion points:* What does this say about the SDLC (secure development lifecycle)? What additional tests would you run on `admin_token=true` as a parameter elsewhere in the app? How would you classify severity, and what compensating controls should be recommended beyond "remove the endpoint"?

**C3. The Chained Low-Severity Findings**
*Scenario:* Individually, you find three "low" severity issues: (1) verbose error messages revealing internal server names, (2) an open internal wiki with no authentication on a non-standard port discovered via those server names, and (3) the wiki contains a page with SSH credentials for a "test" server that turns out to be a misconfigured production database backup server.
*Discussion points:* How do individually low-severity findings combine into a critical risk? How should the report reflect "chained" vulnerabilities versus listing them separately? What does this case illustrate about the value of manual testing over automated scanning?

**C4. The Locked-Down Web App, Open Network**
*Scenario:* A client's flagship web application is well-hardened (no common web vulns found after thorough testing), but during the same engagement's internal network test, you find that the build server (Jenkins) has no authentication enabled and contains credentials for the production deployment pipeline, including the web app's database.
*Discussion points:* How does this illustrate the importance of scope covering the full attack surface, not just "the obvious target"? What's the impact of compromising a CI/CD pipeline versus a single application? How would you explain to a non-technical stakeholder why "our main app is secure" doesn't mean "we are secure"?

**C5. The Password Spray That Worked**
*Scenario:* After enumerating ~500 valid usernames from a company's Outlook Web Access (OWA) login page (via username enumeration), you perform a slow password spray (one attempt per account per 30 minutes, common seasonal passwords like `Welcome2024!`) and successfully authenticate as 12 users, three of whom turn out to have no MFA enforced and one of whom is an IT helpdesk account with elevated AD permissions.
*Discussion points:* Why is password spraying effective against large organizations even with account lockout policies in place? What does the helpdesk account compromise represent in terms of business impact? What layered controls (MFA, conditional access, lockout thresholds, monitoring) would have prevented or detected this?

---

## How to Use This for Practice

- For **0–1 years**: Focus on Networking, Web Application Security Q&A, and Beginner Scenarios.
- For **1–3 years**: Add Network Pentesting, Linux Privilege Escalation, Tools & Methodology, and Intermediate Scenarios.
- For **3–5 years**: Focus on Active Directory, chained scenarios, mini case studies, and be ready to discuss reporting, methodology, and business impact in depth.

---

*Feel free to fork, expand, and contribute additional questions via pull requests.*
