# Security Plus Study Notes

Following along with https://www.professormesser.com/security-plus/sy0-501/

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
    
    
