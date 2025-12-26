# My-Hacking-Journey
### Host Discovery (Local Network)
Scan active hosts in a subnet using ARP (fastest for LAN)
sudo nmap -sn -PR 192.168.18.0/24

# Flags breakdown:
-sn: Disable port scan (host discovery only)
-PR: Use ARP ping (bypasses OS firewalls in LAN)

### Service & Version Enumeration
Scan a specific target to identify open ports and service versions
sudo nmap -sV [target_ip]

# Flags breakdown:
-sV: Probe open ports to determine service/version info
Standard output: [Port] [State] [Service] [Version]

# Pro Tip: Use -A for aggressive scan (OS detection, version detection, script scanning, and traceroute)
sudo nmap -A [target_ip]

### Bypassing Firewalls & Basic Discovery
# Scan target even if it blocks ping (ICMP)
sudo nmap -Pn [target_ip]

# Flags breakdown:
-Pn: Skip host discovery. Treat all hosts as online. Essential for Windows targets.
-sC: Run default Nmap scripts (NSE) to get more info about the service.

### Port States
Open: Application is listening and responding.
Closed: No application listening, but probe was received.
Filtered: Firewall/Filter is dropping packets (Nmap gets no response).

### Advanced Troubleshooting & Forcing Scans
# Force Nmap to use raw ethernet frames and show why a host is considered down
sudo nmap -Pn -sS -p [port] --send-eth --reason [target_ip]

# Flags break -down:
--send-eth: Bypasses the OS IP stack, sends raw packets (useful for stubborn LAN targets)
--reason: Displays why Nmap determined a port/host is in a certain state
-sS: TCP SYN Scan (Stealth/Half-open scan)

### Advanced Nmap Troubleshooting
Use when target is active but normal scans return "0 hosts up"
sudo nmap -Pn -sS -p [port] --send-eth --reason [target_ip]

# Key Indicators:
syn-ack: Confirms the port is open and responding to handshake.
ttl 128: Common TTL value for Windows-based systems.
--send-eth: Bypasses OS routing/firewall by sending raw Layer 2 frames.
