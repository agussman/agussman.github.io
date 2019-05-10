# Linux Admin Notes

Users can increase the soft-limit up to the (root controlled) hard limit.

View user limits:
```
$ ulimit -a
```

Common flags:
```
 -n The maximum number of open file descriptors
 -u The  maximum  number  of  processes available to a single user (nproc)
```

`sysctl` is a tool for examing and changing kernel parameters at runtime
-p: Load sysctl settings from the file specified or /etc/sysctl.conf if none is given.
-a: Displays all variables.
-w: Enables writing of a value to a variable.


`systemctl` is a `systemd` command for starting, stopping, or enabling services

`firewall-cmd --permanent --add-port=100/tcp`
(was `iptables`)

`ip addr` will show IP addresses on network interfaces (was `ifconfig`)

`ss` to show processes/ports (was `netstat`)

`nmap` to see what's on the network

# DNS

  * A record - Address record, points a domain to an IP address
  * CNAME - Canonical Name, points to another domain name
  * MX Entry - Mail, points to a domain name
  * TTL - how long to remember the record
  * negative TTL - how long to remember you don't have the record
  * DNS zone - portion of domain name space it's managing
  * SOA - Start of Authority, administrative info about the zone

# Routing
 * OSPF - Open Shortest Path First


# Linux Boot Process

Boot and Startup

Boot: power to kernel is initialized and systemd is launched

Startup: takes over, get to operational state

Boot:
 * Power on
 * POST (Power On Self Test), part of BIOS (Basic Input Output System)
 * checks basic operability of the hardware
 * locates boot sectors on attached bootable devices, loads into RAM
 * Master Boot Record (MBR) has file partitions and boot loader 
 * boot loader could be GRUB2 (GRand Unified Bootloader 2), older LILO
 * GRUB2 can provide a choice of OS, kernel to load
 * Kernel loads and uncompresses, loads systemd

Startup:
 * mounts filesystems from `/etc/fstab`
 * gets target to boot to from `/etc/systemd/system/default.target`
   * multi-user.target for a server
   * graphical for a desktop workstation
 * goes to interim `sysinit.target` (mounting fs, swap, udev, random seed)
 * next goes to `basic.target` (communication sockets)


# What happens when

Keyboard:
 * Brown tactile switches, 45g of actuation
 * Completes an electrical circuit
 * Stored keycode in keyboard's endpoint
 * polled by USB controller
 * passed to the keyboard driver, passed to the OS abstraction layer

X Server:
 * `X server` acquires the keypress from an event driver `evdev`
 * Sends it to the windows manager, which sends it to the focused window


Browser:
 * Attempt to autocomplete
 * Search or URL?
 * Encode invalid URL characters
 * Check HTTP Strict Transport Security (HTST) list

DNS Lookup:
 * Maps a domain name to an IP address
 * Browser checks its local cache
 * If no, then OS-level `gethostname` checks local hosts file, then will try to resolve via DNS
 * <ARP stuff goes here>
 * Opens a port 53 UDP request to a DNS server
 * If local DNS doesn't have it, recursive search until SOA is found

ARP process:
 * Maps a Layer 3 (Transport, IP) address to a Layer 2 (Data link, MAC) address
 * Check internal ARP cache
 * Need to get the MAC of the default gateway (presuming destination IP not on the local network)
 * Broadcast an ARP reqeust
 * Intended target will respond
 * Can use `ip` command to flush the arp cache

Socket:
 * Requests a TCP socket stream from the system library
 * Craft the TCP segment (Transport Layer) including destination port and source port chosen from kernel's dynamic port range
 * Add the IP header (Network Layer) of destination and source
 * Add the MAC address of gateway and client (Data Link layer)

TCP Handshake:


TSL handshake:







