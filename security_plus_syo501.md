# Security Plus Study Notes

Following along with https://www.professormesser.com/security-plus/sy0-501/

* OSI Model
* Ports
* 1.2 Attack Types
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
  * Client Hijacking Attacks
    * https://www.professormesser.com/security-plus/sy0-501/client-hijacking-attacks/
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
  * Wireless Replay Attacks
    * https://www.professormesser.com/security-plus/sy0-501/wireless-replay-attacks/
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
    * 
  * Wireless Disassociation Attacks
    * Management frames aren't encrypted or authenticated
    * 
  * Cryptographic Attacks
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
    *
 * Vulnerability Types
   * Vulnerability Types
     * Race condition
     * End of Life avoid by upgrading
     * Improper Error Handling / verbose error messages with too much info
     * untrained user (physical vulnerability)
     * improperly configured accounts (too many, too much access)
     * cypher suite - protocol (AES, 3DS), length, hash (sha, md5)
     * TLS is a common suite
     * memory leak - memory not deallocated
     * 
    
