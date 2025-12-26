# My-Hacking-Journey
### Host Discovery (Local Network)
# Scan active hosts in a subnet using ARP (fastest for LAN)
sudo nmap -sn -PR 192.168.18.0/24

# Flags breakdown:
# -sn: Disable port scan (host discovery only)
# -PR: Use ARP ping (bypasses OS firewalls in LAN)

### Service & Version Enumeration
# Scan a specific target to identify open ports and service versions
sudo nmap -sV [target_ip]

# Flags breakdown:
# -sV: Probe open ports to determine service/version info
# Standard output: [Port] [State] [Service] [Version]

# Pro Tip: Use -A for aggressive scan (OS detection, version detection, script scanning, and traceroute)
# sudo nmap -A [target_ip]
