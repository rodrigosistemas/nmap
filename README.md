# Netdiscover & Nmap Commands

<img src="https://github.com/rodrigosistemas/nmap/blob/main/img/nmap.jpeg" alt="nmap" width="500"/>

## List GCC version & devices

* Show GCC version:

  ```bash
  gcc -v
  ```
* List devices on the PC:

  ```bash
  lsusb
  ```

---

## Netdiscover

### Description

Netdiscover is a network discovery tool.

### Basic commands

* Help:

  ```bash
  netdiscover -help
  ```

### Discover devices

* Run netdiscover to find devices in an IP range:

  ```bash
  sudo netdiscover -r 192.168.1.1/24
  ```

  * `-r` : Sets the IP range
  * `192.168.1.1/24` : Specifies the IP range to scan

* Using a specific interface:

  ```bash
  netdiscover -i eth0 -r 192.168.43.0/24
  ```

  * `-i` : Sets the network interface (e.g. eth0)

---

## Nmap

### Description

Nmap is an open-source utility for network discovery, security auditing, and port scanning.

### Basic commands

* Help:

  ```bash
  nmap --help
  ```
* Device discovery (Ping scan):

  ```bash
  sudo nmap -sn <target_IP>
  ```
* Port scan (IP mapping):

  ```bash
  sudo nmap <target_IP>
  ```

### Scan specific ports

* Example scanning ports 80, 135, 2000, 18080 on a specific host:

  ```bash
  sudo nmap -p 80,135,2000,18080 192.168.1.13
  ```

### OS detection

* Detect the operating system of a target:

  ```bash
  sudo nmap -O <target_IP>
  ```

### Firewall evasion (Stealth Scans)

* `-sX` (Xmas Tree Scan): Sends packets with FIN, URG, and PUSH flags set.

  ```bash
  sudo nmap -sX <target_IP>
  ```
* `-sN` (Null Scan): Sends packets with no flags set.

  ```bash
  sudo nmap -sN <target_IP>
  ```
* `-sF` (FIN Scan): Uses packets with the FIN flag set.

  ```bash
  sudo nmap -sF <target_IP>
  ```
* `-P0` : Do not ping the target before scanning (skip host discovery).

  ```bash
  sudo nmap -P0 <target_IP>
  ```

### Firewall evasion (continued)

* Fragment packets (`-f`): Sends small fragments (8 bytes).

  ```bash
  sudo nmap -f <target_IP>
  ```
* MTU (`--mtu`): Specify an MTU size.

  ```bash
  sudo nmap --mtu 16 <target_IP>
  ```
* Decoy scan (`-D`): Use decoy hosts to obscure the scan origin.

  ```bash
  sudo nmap -D RND:10 <target_IP>
  ```

### Export scan results

* Export to `.txt` or `.xml`:

  ```bash
  sudo nmap -sV 192.168.1.1 -oN Desktop/test.txt
  sudo nmap -sV 192.168.1.1 -oX Desktop/test.xml
  ```

### Scan first 1000 ports

* Quick scan of the first 1000 ports:

  ```bash
  sudo nmap -p 1-1000 <ip_address>
  ```

### TCP and UDP scans

* TCP port scan:

  ```bash
  sudo nmap -sT <target_IP>
  ```
* UDP port scan:

  ```bash
  sudo nmap -sU <target_IP>
  ```

---

## ARP Spoofing

* Install `arpspoof` (part of dsniff):

  ```bash
  sudo apt install dsniff
  ```
* Run arpspoof:

  ```bash
  sudo arpspoof -i wlan0 -t 192.168.1.9 192.168.1.1
  ```
