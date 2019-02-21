# Security Plus Study Notes

Following along with https://www.professormesser.com/security-plus/sy0-501/

* OSI Model
  * Layer 1 Hub
  * Layer 2 Switch
  * Layer 3 Router
* Ports
## Things to Review More
* VPN Concentrators
* nonrepudiation - can't deny having used a digital signature
* integrity - not altered
* authentication - prove who you are
* UTM - unified threat management
* 2.1 Router, Switch, Proxy, 
* Review list of command line tools:
  - ping
  - netstat
    * http://techgenix.com/determining-you-actively-being-compromised/
    * unrecognized foreign addresses, especially in the ESTABLISHED state
    * LISTENING connections on your local system on odd ports
  - tracert
  - nslookup/dig
  - arp
    * List cached MAC addresses
  - ipconfig/ip/ifconfig
  - tcpdump
    * capture network traffic
  - nmap
    * find devices on the network, OSs, services
  - netcat
    * Read or write data to the network
    * could be a backdoor
* Hardware/firmware security
  - FDE/SED
    * Encrypted disks
  - TPM Trusted Platform Module
    * on-host encryption
  - HSM Hardware Security MOdule
    * key management, crypto-processing
  - UEFI/BIOS
    * Secure BIOS
  - Secure boot and attestation
  - Supply chain
  - Hardware root of trust
  - EMI/EMP Electro-magnetic Interference
## Overview
* Overview
  * Overview
    * [CompTIA Security+ Certification Exam Objectives SYO-501](https://www.comptia.jp/pdf/Security%2B%20SY0-501%20Exam%20Objectives.pdf)
    * 1.0 Threats, Attacks, and Vulnerabilities 21%
    * 2.0 Technologies and Tools 22%
    * 3.0 Architecture and Design 15%
    * 4.0 Identify and Access Management 16%
    * 5.0 Risk Management 14%
    * 6.0 Cryptography and PKI 12%
## Section 1 – Threats, Attacks, and Vulnerabilities
* 1.1 Malware
  * An Overview of Malware (4:00)
  * Viruses and Worms [(5:01)](https://www.professormesser.com/security-plus/sy0-501/viruses-and-worms-3/)
    * Virus needs you to execute a program, may or may not cause problems
    * Virus can be a program, boot sector, script, or macro
    * Worm can self-replicate w/o human intervention over the network
    * Wannacry was a famous Ransomware Worm
  * Ransomware and Crypto-Malware (4:01)
    * Ransomware - Hold your data hostage
    * Crypto-malware - actually encrypts the data
  * Trojans and RATs [(4:27)](https://www.professormesser.com/security-plus/sy0-501/trojans-and-rats/)
    * Trojan - pretends to be something else
    * installs a backdoor
    * RAT - Remote Access Trojan / Remote Administration Tools
    * DarkComet is a RAT
  * Rootkits [(2:54)](https://www.professormesser.com/security-plus/sy0-501/rootkits-3/)
    * Embedded at the lowest level of the OS (kernel level)
    * Can't even stop the process, need a rootkit remover, 
    * UEFI BIOS secure boot can prevent
  * Keyloggers (2:36)
  * Adware and Spyware (3:45)
  * Bots and Botnets (4:22)
  * Logic Bombs [(3:52)](https://www.professormesser.com/security-plus/sy0-501/logic-bombs-3/)
    * Waiting for a time or event
    * Usually made by someone on the inside
* 1.2 Attack Types
  * Sideloading
    * Installing software on a mobile device via non-traditional channels
  * Vishing
    * voice phishing
  * Pass the Hash Attack
    * https://searchsecurity.techtarget.com/definition/pass-the-hash-attack
    * Exploiting the has w/o access to the underlying password
    * Vulnerability associated with Windows SSO / Local Security Authority Subsystem Service / NTLM / LM (LanMan)
  * Phishing
  * Tailgating and Impersonation
  * Dumpster Diving
  * Shoulder Surfing
  * Hoaxes
  * Watering Hole Attacks
  * Principles of Social Engineering
  * Denial of Service
  * MITM Man-in-the-Middle
  * MITB Man-in-the-Browser
    * type of MITM with a compromised browser
  * BUffer Overflows
  * Data Injections
  * Cross-site scripting XSS [(7:02)](https://www.professormesser.com/security-plus/sy0-501/cross-site-scripting-3/)
    * Non-persistent / reflected
    * Happens in the browser
    * Example: Submitting javascript via a form that grabs user session info / cookies
    * Persistent / stored - everyone gets it who goes to the page, untargetted
  * Cross-site Request Forgery XSRF, CSRF [(2:48)](https://www.professormesser.com/security-plus/sy0-501/cross-site-request-forgery/)
    * Web app should prevent it
    * Example: Some link that requests an action, an authenticated user clicking on it unwittingly causes the action
  * DNS Poisoning and Domain Hijacking
    * https://www.professormesser.com/security-plus/sy0-501/dns-poisoning-and-domain-hijacking/
    * Domain Hijacking - points to the bad guy domain server
    * Often involves gaining access to the domain account
  * Zero-Day Attacks
    * https://www.professormesser.com/security-plus/sy0-501/zero-day-attacks-4/
  * Replay Attacks
    * https://www.professormesser.com/security-plus/sy0-501/replay-attacks-2/
    * MITM could be how you got the traffic
    * Original user doesn't need to be on the network
    * Thwarted by encrypted traffic, salted passwords
  * Client Hijacking Attacks [(9:01)](https://www.professormesser.com/security-plus/sy0-501/client-hijacking-attacks/)
    * Redirecting to a different site (mispellings/typosquatting, similar product or brand)
    * click jacking (some invisible website underneath?)
    * Common on mobile devices
    * cookies can be exploited, track user sites, theoretically get session id stuff
    * side-jacking (session hijacking), request + session id
    * get from Wireshark, Kismet, or XSS
    * avoid by encrypted end-to-end (https)
    * alternatively, use a VPN
  * Driver Manipulation
    * https://www.professormesser.com/security-plus/sy0-501/driver-manipulation/
    * shim - in the middle
    * technique, to create a fake shim, eg windows ver w/ reduced security privledges
    * metamorphic malware - refactoring, different each downloaded executable, harder to id w/ antivirus
    * need a layered approach to deal with, e.g., block urls, etc
  * Spoofing
    * https://www.professormesser.com/security-plus/sy0-501/spoofing-2/
    * One device pretends to be something/one it's not
    * Pretending to be a webserver, DNS server, email address, etc
    * ARP (Address Resolution Protocol) Spoofing   
      * https://www.veracode.com/security/arp-spoofing
      * malicious linking of a MAC address w/ a legit IP
      * DoS: link multiple IPs to a single MAC, funneling a traffic overload
      * Session Hijacking and Man-in-the-middle
      * avoid with packet filtering, avoiding trust relationships (e.g., IP-as-authentication), and Transport Layer Security (TLS), Secure Shell (SSH), HTTP Secure (HTTPS)
    * media access control address (MAC address) spoofing
    * spoof mac address hard to detect
    * DNS amplification for distributed denial of service attacks
      * https://www.cloudflare.com/learning/ddos/dns-amplification-ddos-attack/
      * Make a request to an open DNS server
      * the response is a huge and routed to the target
      * do that lots to overwhelm target's bandwith
    * spoofed IP address is easier to detect, can trap at the firewall
  * Wireless Replay Attacks [(3:32)](https://www.professormesser.com/security-plus/sy0-501/wireless-replay-attacks/)
    * Easier to capture the traffic
    * WEP didn't have encryption that prevented this
    * you can crack the password on a 802.11 WEP network with 10k-15k gathered password
  * Rogue Access Points and Evil Twins
    * https://www.professormesser.com/security-plus/sy0-501/rogue-access-points/
    * 802.1x requires authentication for all access
    * Evil Twin more likely on open networks (e.g., Starbucks)
    * mitigate by encrypting your traffic
  * Wireless Jamming
    * https://www.professormesser.com/security-plus/sy0-501/wireless-jamming/
  * WPS Attacks
    * https://www.professormesser.com/security-plus/sy0-501/wps-attacks-2/
    * WPS WiFi Protected Setup
    * 8 digit pin, validated in 4 then 3 (last 1 is checksum)
    * or, just look at it and write it down
    * just disable it
  * Bluejacking and Bluesnarfing
    * https://www.professormesser.com/security-plus/sy0-501/bluejacking-and-bluesnarfing-3/
    * Bluejacking - unsolicated message via Bluetooth
    * could specifically be addressbook related
    * doesn't expose data, more of an annoyance, less of a thing now
    * Blue snarfing someone actually gets your data
  * RFID and NFC Attacks
    * NFC - Near Field Communications, is two way
  * Wireless Disassociation Attacks
    * Management frames aren't encrypted or authenticated
  * Cryptographic Attacks [(9:54)](https://www.professormesser.com/security-plus/sy0-501/cryptographic-attacks/)
    * KPA Known Plaintext Attack - have some plaintext (crib), break it down
    * Rainbow Tables - precalculated hashes, fail on salted input
    * dictionary attack - try common pws
    * brute force attacks work better if you can get the users/hashes offline
    * larger hashes are less likely to have collisions
    * 801.11 WEP and DES are both weak
    * Kerberos puts a timestamp to prevent replay attacks
* 1.3 Threat Actors
* 1.4 Penetration Testing
  * Penetration Testing
    * Starts w/ information gathering / Passive Reconnisaince
    * Active Recon
    * Exploit vulnerabilities
    * initial exploit -> leave a backdoor
    * black box - pentesters don't know anything
    * gray box -
    * white box - they get full info
* 1.5 Vulnerability Scanning
  * Vulnerability Scanning
    * https://www.professormesser.com/security-plus/sy0-501/vulnerability-scanning-5/
    * minimally invasive
 * 1.6 Vulnerability Types
   * Vulnerability Types
     * Race condition
     * End of Life avoid by upgrading
     * Improper Error Handling / verbose error messages with too much info
     * untrained user (physical vulnerability)
     * improperly configured accounts (too many, too much access)
     * cypher suite - protocol (AES, 3DS), length, hash (sha, md5)
     * TLS is a common suite
     * memory leak - memory not deallocated
     
## Section 2 – Technologies and Tools
* 2.1 Security Components
  * Another resource: http://www.pearsonitcertification.com/articles/article.aspx?p=2861453
  * Firewalls [(9:17)](https://www.professormesser.com/security-plus/sy0-501/firewalls-3/)
    * filter at OSI Layer 4 ()
    * OSI Layer 7 - Application filtering option
    * Often used as VPN concentrators
    * does Network Address Translation
    * stateless - doesn't track sessions; just looks at ACLs, allow or disallow, requires return rules
    * stateful - tracks outgoing connections, allows response, mostly this now
    * "application layer gateway" looking at the packet, 
    * host-based?
    * ACLs - (dis)allow traffics
    * Application-based vs. network-based
  * VPN Concentrators [(7:59)](https://www.professormesser.com/security-plus/sy0-501/vpn-concentrators-5/)
    * SSL/TLS is common, runs from a browser, usually allowed, doesn't require special authentication
    * Full Tunnel - all traffic will traverse it (corp network and 3rd party redirected through it)
    * Split Tunnel - only corporate traffic goes through it
    * Site to Site usually use firewalls
    * IPSec - OSI Layer 3, uses IKE (Internet Key Exchange)
    * Has an integrity check to prevent replay
    * standard across manufacturers
    * AH - Authentication Header (type of IPSec), "authentication and integrity"
    * ESP - Encapsulation Security Payload (type of IPSec), adds confidentiality, "authentication, integrity, and confidentiality"
    * Transport Mode - "payload encrypted", data encrypted, use original IP header
      [Original IP Header][IPsec Headers][Data][IPsec Trailers]
    * Tunnel Mode - "entire packet encryption", IP Header and Data are encrypted, uses a different IP header (it's encrypted)
      [New IP Header][IPsec Headers][IP Header][Data][IPsec Trailers]
    * TODO: Review this more
  * Network Intrusion Detection and Prevention [(7:51)](https://www.professormesser.com/security-plus/sy0-501/network-intrusion-detection-and-prevention-3/)
    * IDS - Intrusion Detection System (informs)
    * IPS - Intrusion Protection System (blocks)
    * passive monitoring - gets a copy
    * can send TCP reset "out of band response", doesn't work w/ UDP
    * inline monitoring - passes through IPS
    * signature based - perfect match
    * anaomly - stats
    * behavior
    * heuristics - AI, characterisitcs, rules
    * Can set lots of rules to tell IPS what to do
    * network-based monitor network, host-based look at info originating on machine (unauthorized file mods, user activity)
    * RELISTEN
  * Router and Switch Security [(12:31)](https://www.professormesser.com/security-plus/sy0-501/router-and-switch-security/)
    * Routers can prevent IP spoofing
    * Port security - only specific MAC addresses (or # thereof) are allowed to connect
    * That's only a deterrent; you can spoof MAC addresses, hide hosts behind a small router
    * floodguard - max # of mac addresses to preventDDoS
    * STP Spanning Tree Protocol - prevents network loops, dynamically modify network topology
    * parallel bridges can create looping problems
    * BPDU bridge protocol data units are special messages to prevent loops
    * RPF Reverse Path Forwarding - inbound traffic responds the same way (e.g., don't send outside)
    * NAC Network Access Control (EAP and RADIUS)
  * Proxies [(4:13)](https://www.professormesser.com/security-plus/sy0-501/proxies/)
    * Explicit Proxy - 
    * NAT is a stype of proxy
    * forward proxy - protect users connecting to internet, url filtering
    * reverse proxy - protect server from the internet
    * "open proxy" - third-party, circumvents security
  * Load Balancers (5:43)
  * Access Points (10:25)
  * SIEM [(7:11)](https://www.professormesser.com/security-plus/sy0-501/siem-2/)
    * Security Information and Event Management, logs basically
    * Can correlate data from different vendors
    * NTP / central time keeping is crucial
    * syslog is a standard exchange
    * maybe write to WORM (Write Once Read Many)
  * Data Loss Prevention [(4:59)](https://www.professormesser.com/security-plus/sy0-501/data-loss-prevention-3/)
    * Prevents data leakage e.g. data moving around that shouldn't be (PII)
    * endpoint dlp (cpu) / data in motion (network) / data at rest (dbs) 
  * Network Access Control [(3:56)](https://www.professormesser.com/security-plus/sy0-501/network-access-control-4/)
    * Some sort of agent runs on the devices to see if they are allowed to connect
    * persistent agent - always running software
    * dissolvable agent - health check at initial authentication
    * agentless - e.g., windows AD thing
  * Mail Gateways [(4:00)](https://www.professormesser.com/security-plus/sy0-501/mail-gateways/)
    * Antivirus, DLP, spam prevention
  * Other Security Devices [(6:51)](https://www.professormesser.com/security-plus/sy0-501/other-security-devices/)
    * SSL accelerator - 
    * Media Gateway - telephony to IP phones, need to protect this
    * 
* 2.2 Security Software
  * Software Security Tools [(15:00)](https://www.professormesser.com/security-plus/sy0-501/software-security-tools/)
    * Passive tools - watch network traffic go by
    * active tool - sends data to a device
    * protocol analyzer - network traffic patterns and abnormalities
    * network scanner - what services running on a remote device, OS, 
    * wireless scanners and monitors
    * vulnerability scanners
    * 
  * Command Line Security Tools [(19:39)](https://www.professormesser.com/security-plus/sy0-501/command-line-security-tools/)
    * dig replaces nslookup
    * ARP cache maps device MAC to IP (arp displays this)
    * TCP dump, gets it in PCAP
    * nmap - network mapper, port scan, os scan, service scan
    * 
* 2.3 – Common Security Issues
  * Common Security Issues [(18:16)](https://www.professormesser.com/security-plus/sy0-501/common-security-issues/)
    * 
* 2.4 – Analyzing Security Output
  * Analyzing Security Output (11:42)
* 2.5 – Securing Mobile Devices
  * Mobile Device Connection Methods (6:47)
  * Mobile Device Management (13:17)
  * Mobile Device Enforcement (11:37)
  * Mobile Device Deployment Models (4:04)
* 2.6 – Secure Protocols
  * Secure Protocols [(10:27)](https://www.professormesser.com/security-plus/sy0-501/secure-protocols/)
    * SRTP Secure Real-Time transport proptocol (voice/video), adds AES
    * S/MIME Secure/Multipurpose INternet Mail Extesions, requires PKI
    * SSL/TLS uses assymetric to transfer a symetric key
    * LDAP more secure, do LDAPS, or SASL
    * SNMPv3 - Simple Network Management Protocol v 3, Co/Int/Auth
    * DHCP doesn't have security (threat of rouge DHCP, "DHCP starvation" keep requesting DHCP)

## Section 3 – Architecture and Design
* 3.1 – Security Frameworks
  * Compliance and Frameworks (5:20)
  * Secure Configuration Guides (5:46)
  * Defense-in-Depth (3:24)
* 3.2 – Securing the Network
  * Secure Network Topologies [(6:59)](https://www.professormesser.com/security-plus/sy0-501/secure-network-topologies/)
    * DMZ
    * Extranet, Intranet
    * NAT isn't security
  * Network Segmentation (5:19)
  * VPN Technologies (3:00)
  * Security Technology Placement (11:28)
  * Securing SDN Software Defined Networking [(2:39)](https://www.professormesser.com/security-plus/sy0-501/securing-sdn/)
    * control plane for config, data plane for work
* 3.3 – Secure Systems Design
  * Hardware Security (6:59)
  * Operating System Security (12:16)
  * Peripheral Security (6:31)
* 3.4 – Secure Deployments
  * Secure Deployments (3:43)
* 3.5 – Embedded Systems
  * Embedded Systems [(8:39)](https://www.professormesser.com/security-plus/sy0-501/embedded-systems/)
    * SCADA Supervisory Control and Data Acquisition
    * ICS Industrial Control Systems
    * typically isolated network
    * SOC System on a Chip
    * RTOS Real-Time Operating System - important
    * MFD Multifunction Device - print/scanner
* 3.6 – Secure Application Development
  * Development Life Cycle Models (3:33)
  * Secure DevOps (6:18)
  * Version Control and Change Management (3:22)
  * Provisioning and Deprovisioning (2:56)
  * Secure Coding Techniques (12:35)
  * Code Quality and Testing (7:35)
* 3.7 – Cloud Technologies
  * Virtualization Overview (3:37)
  * Virtualization Security (3:25)
  * Cloud Deployment Models (3:43)
  * Security in the Cloud (5:58)
* 3.8 – Resiliency and Automation
  * Resiliency and Automation (6:25)
  * Redundancy, Fault Tolerance, and High Availability (5:44)
* 3.9 – Physical Security Controls
  * Physical Security Controls (22:09)

## Section 4 – Identity and Access Management
* 4.1 – Identity and Access Management
  * AAA and Authentication [(9:30)](https://www.professormesser.com/security-plus/sy0-501/aaa-and-authentication/)
    * Authentication, Authorization, and Accounting
    * Authentication - who we are (username, password)
    * Authorization - based on who we are, what resources do we have access to?
    * Accounting - Who logged in when for how long?
    * Multi-factor authentication:
      * Something you are
      * Something you know - password, PIN, swipe pattern
      * Somewhere you are - biometrics
      * Something you have - smart card, usb token, mobile phone
      * Something you do - handwriting, typing pattern, 
      * Somewhere you are -
      * Federated Network - authenticate with another count aka OAuth
      * SSO - Single Sign On, single username and password when connecting the network (Kerberos)
* 4.2 – Identity and Access Services
  * Identity and Access Services [(7:39)](https://www.professormesser.com/security-plus/sy0-501/identity-and-access-services/)
    * RADIUS - Remote Authentication Dial-in User Service
      * Centralize authentication, multi-OS
    * TACACS - Terminal Access Controller Access-Control System
      * 
    * LDAP
      * container objects ("Orgs") and leafs ("printers", "comptuers")
      * kerberos replaced LTMN for Windows
      * mutual auth
      * kerberos is ticket based      
  * PAP, CHAP, and MS-CHAP (4:09)
    * non-ethernet authentication (PPTP, PPoE)
    * PAP - Password Authentication Protocol (it's old, no encryption)
    * CHAP - Challenge-Handshake Authentication Protocol, challenge response
    * MS-CHAP - Microsoft version of CHAP, vulnerable from DES use
  * Federated Identities [(4:49)](https://www.professormesser.com/security-plus/sy0-501/federated-identities/)
    * token based - server is stateless, client stores session token locally, client includes it with each request
    * login ->, token sent <-, Request+token ->, Response <-
    * federated often token based
    * SAML - security assertion markup language
* 4.3 – Identity and Access Controls
  * Access Control Models [(6:06)](https://www.professormesser.com/security-plus/sy0-501/access-control-models/)
    * Authorization - 
    * mandatory access control - MAC, set by sys admin
    * Discretionary Access Control - have some controls (e.g., set spreadsheet access)
    * role based access control -
    * attrib8ute-based access control ABAC - IP, time of day
    * rule based access control
    * file system security
  * Access Control Technologies [(6:15)](https://www.professormesser.com/security-plus/sy0-501/access-control-technologies/)
    * FAR - false acceptance rate
    * FRR - False Rejection Rate
    * 
4.4 – Account Management
Account Types (4:01)
Account Management (7:45)
Account Policy Enforcement (4:23)

## Section 5 – Risk Management
* 5.1 – Security Policies
  * Agreement Types [(4:10)](https://www.professormesser.com/security-plus/sy0-501/agreement-types/)
    * SOPs
    * Interoperability agreements
    * SLA
    * BPA - Business Parnters Agreement (manufacturers and resellers)
    * ISA - Interconnection Security Agreement (Feds, defines sec controls)
    * MOU - intent
    * MOA - above an MOU
  * Personnel Management (5:17)
  * Role-based Awareness Training (2:43)
  * General Security Policies [(1:56)](https://www.professormesser.com/security-plus/sy0-501/general-security-policies/)
    * Social media, code of conduct, confidentiality
    * Email use
* 5.2 – Business Impact Analysis
  * Business Impact Analysis [(9:06)](https://www.professormesser.com/security-plus/sy0-501/business-impact-analysis-3/)
    * MTTR - Mean Time To Restore
    * MTTF - Mean Time to Failure
    * MTBF - Mean Time Between Failures
    * RTO - Recovery Time Objectives - at what point you're back up, multiple levels
    * RPO - Recovery Point Objectives - degrees of restoration, degrees of data loss
    * Uptime expressed as availability % ("availability" definition is negotiated)
    * Identify mission essential functions
    * Remove single points of failure: equipment, facilities/utilities, people/locations
    * BIA: Life, Property, Safety, Finance, Reputation
    * Some compliance requires a privacy statement, Privacy Threshold Analysis (PTA)
* 5.3 – Risk Management
  * Risk Assessment [(9:29)](https://www.professormesser.com/security-plus/sy0-501/risk-assessment/)
    * environmental, man-made
    * ARO Annualized Rate of Occurent - how likely per year
    * SLE Single Loss Expectancy - monetary loss if it occurs
    * ALE Annual Loss Expectancy - ARO x SLE
    * quantitative and qualitative (traffic light grid)
    * Business Impact Analysis BIA -
    * Risk avoidance: Transference (insurance), Acceptance, Mitigation (invest in security)
    * Formal change management process is a normal part of minimizing risk
* 5.4 – Incident Response
  * Incident Response Planning (6:08)
Incident Response Process (7:14)
* 5.5 – Forensics
Gathering Forensics Data (8:22)
Using Forensics Data (2:32)
* 5.6 – Disaster Recovery
Disaster Recovery Sites (1:51)
Application Recovery (5:25)
Geographic Considerations (3:18)
Continuity of Operations (4:49)
* 5.7 – Security Controls
Security Controls (3:10)
* 5.8 – Data Security and Privacy
Data Destruction (5:02)
Handling Sensitive Data (2:18)
Data Roles and Retention (3:00)

## Section 6 – Cryptography and PKI
* 6.1 – Cryptography
  * Cryptography Concepts [(7:52)](https://www.professormesser.com/security-plus/sy0-501/cryptography-concepts/)
    * Confidential - secret
    * Authentication and access control
    * non-repudiation
    * integrity - tamper proof
    * ciphertext - encrypted content
    * cipher - encrypt / decrypt
    * cryptanalysis - cracking encryption
    * key - add to cypher to encrypt
    * confusion - data looks different from plain text, nonlinear, no patterns
    * diffusion - one char change in input changes many characters in output
    * ROT13 - shift 13 letters
    * CSP Cryptographic Service Provider - windows crypto api library
  * Symmetric and Asymmetric Encryption (6:07)
  * Hashing and Digital Signatures (7:33)
  * Randomizing Cryptography [(3:35)](https://www.professormesser.com/security-plus/sy0-501/randomizing-cryptography/)
    * nonce - arbitrary number used once, prevents replay attacks
    * IV Initialization Vector - nonce
    * salt - added to password hash, makes them unpredictable
  * Weak Encryption (3:19)
  * Cryptographic Keys (3:47)
  * Steganography (2:34)
  * Stream and Block Ciphers (1:55)
  * States of Data (3:07)
  * PFS Perfect Forward Secrecy [(2:10)](https://www.professormesser.com/security-plus/sy0-501/perfect-forward-secrecy-2/)
    * Don't use the server's private RSA key; every session uses a different key
  * Common Cryptography Use Cases (4:21)
* 6.2 – Cryptography Algorithms
Symmetric Algorithms (4:45)
Block Cipher Modes (5:44)
Asymmetric Algorithms (5:04)
Hashing Algorithms (3:36)
Key Stretching Algorithms (1:32)
Obfuscation (3:53)
* 6.3 – Wireless Security
  * Wireless Cryptographic Protocols [(3:30)](https://www.professormesser.com/security-plus/sy0-501/wireless-cryptographic-protocols/)
    * WPA and WPA2 wifi encryption standards
    * WEP is bad, WPA was a stop-gap replacement
    * WPA WiFi Protected Access (RC4 w/ TKIP), larger IV, 128bit encryption
    * TKIP Temporal Key Integrity Protocol - secret root key w/ IV, sequence counter, 64bit message integrity check, TKIP is vulnerable
    * WPA2 uses AES ecnryption over RC4, CCMP Counter Mode with Cipher Block Chaining replaces TKIP
    * CCMP uses AES, 128bit / 128 bit
    * Use WPA2: condientiality/encription, authentication, and access control
  * Wireless Authentication Protocols [(5:21)](https://www.professormesser.com/security-plus/sy0-501/wireless-authentication-protocols/)
    * EAP Extensible Authetication Protocol: more of a framework
    * EAP-FAST Flexibile Authentication via Secure Tunneling replace LEAP
    * EAP-TLS EAP Transport Layer Security: good, common
    * EAP-TTLS EAP Tunneled Transport Layer Security: use a TLS tunnel to use whatever authentication you want
    * PEAP Proected Extensible Authentication Protocol: EAP+ TLS, PEAPv)/EAP-MSCHAPv2
    * 802.1X - port-based NAC authentication, used w/ RADIUS/LDAP/TACACS+/etc
    * Supplicant <-> Authenticator <-> Authentication Server
    * RADIUS Federation uses 802.1X as authentication method, RADIUS on the backend, EAP to authenticate
  * Wireless Security [(4:46)](https://www.professormesser.com/security-plus/sy0-501/wireless-security-3/)
    * Home use WPA-Personal / WPA-PSK: WPA2, everyone uses the same 256bit key
    * Businesses use WPA-Enterprise / WPA-802.1X: use 802.1X w/ RADIUS
    * Captive Portal: popup w/ login
    * WPS WiFi Protected Setup (originally WiFI Simple Config), "easy" setup, flawed, uses 8 digit PIN but not really, easily brute forced
6.4 – Public Key Infrastructure
PKI Components (8:29)
PKI Concepts (6:18)
Types of Certificates (6:21)
Certificate File Formats (3:21)
