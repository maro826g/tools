# nmap (Network Mapper)

## Host Discovery
nmap -sn 192.168.1.0/24
nmap -sn 192.168.1.0/24 --exclude 192.168.1.1
nmap -sn 192.168.1.1-254
nmap -iL targets.txt -sn
nmap -PS 192.168.1.1
nmap -PA 192.168.1.1
nmap -PU 192.168.1.1
nmap -PE 192.168.1.1
nmap -PR 192.168.1.0/24

## Basic Port Scanning
nmap 192.168.1.1
nmap 192.168.1.1-254
nmap 192.168.1.0/24
nmap -p 80 192.168.1.1
nmap -p 80,443,8080 192.168.1.1
nmap -p 1-65535 192.168.1.1
nmap -p- 192.168.1.1
nmap --top-ports 100 192.168.1.1
nmap --top-ports 1000 192.168.1.1
nmap -F 192.168.1.1

## Scan Types
nmap -sS 192.168.1.1
nmap -sT 192.168.1.1
nmap -sU 192.168.1.1
nmap -sA 192.168.1.1
nmap -sW 192.168.1.1
nmap -sN 192.168.1.1
nmap -sF 192.168.1.1
nmap -sX 192.168.1.1
nmap -sM 192.168.1.1
nmap -sI <zombie_host> 192.168.1.1

## Service and Version Detection
nmap -sV 192.168.1.1
nmap -sV --version-intensity 9 192.168.1.1
nmap -sV --version-all 192.168.1.1
nmap -sV --version-light 192.168.1.1
nmap -A 192.168.1.1
nmap -sV -p 22,80,443 192.168.1.1

## OS Detection
nmap -O 192.168.1.1
nmap -O --osscan-guess 192.168.1.1
nmap -O --osscan-limit 192.168.1.1
nmap -A 192.168.1.1
nmap -O --max-os-tries 3 192.168.1.1

## NSE Script Engine
nmap --script=default 192.168.1.1
nmap --script=vuln 192.168.1.1
nmap --script=safe 192.168.1.1
nmap --script=exploit 192.168.1.1
nmap --script=auth 192.168.1.1
nmap --script=brute 192.168.1.1
nmap --script=discovery 192.168.1.1
nmap --script=intrusive 192.168.1.1
nmap --script=malware 192.168.1.1
nmap -p 80 --script=http-enum 192.168.1.1
nmap -p 80 --script=http-title 192.168.1.1
nmap -p 80 --script=http-headers 192.168.1.1
nmap -p 80 --script=http-methods 192.168.1.1
nmap -p 80 --script=http-shellshock 192.168.1.1
nmap -p 80 --script=http-sql-injection 192.168.1.1
nmap -p 80 --script=http-wordpress-enum 192.168.1.1
nmap -p 443 --script=ssl-enum-ciphers 192.168.1.1
nmap -p 443 --script=ssl-heartbleed 192.168.1.1
nmap -p 443 --script=ssl-poodle 192.168.1.1
nmap -p 21 --script=ftp-anon 192.168.1.1
nmap -p 21 --script=ftp-brute 192.168.1.1
nmap -p 22 --script=ssh-brute 192.168.1.1
nmap -p 22 --script=ssh-auth-methods 192.168.1.1
nmap -p 23 --script=telnet-brute 192.168.1.1
nmap -p 25 --script=smtp-enum-users 192.168.1.1
nmap -p 25 --script=smtp-open-relay 192.168.1.1
nmap -p 53 --script=dns-zone-transfer 192.168.1.1
nmap -p 139,445 --script=smb-vuln-ms17-010 192.168.1.1
nmap -p 139,445 --script=smb-enum-shares 192.168.1.1
nmap -p 139,445 --script=smb-enum-users 192.168.1.1
nmap -p 139,445 --script=smb-brute 192.168.1.1
nmap -p 1433 --script=ms-sql-info 192.168.1.1
nmap -p 3306 --script=mysql-enum 192.168.1.1
nmap -p 3306 --script=mysql-brute 192.168.1.1
nmap -p 5432 --script=pgsql-brute 192.168.1.1
nmap -p 6379 --script=redis-info 192.168.1.1
nmap -p 27017 --script=mongodb-info 192.168.1.1
nmap --script=vuln -p 1-65535 192.168.1.1
nmap --script "not intrusive" 192.168.1.1
nmap --script=default,vuln 192.168.1.1
nmap --script=smb-vuln-* -p 139,445 192.168.1.1
nmap --script-args=user=admin,pass=admin -p 80 --script=http-brute 192.168.1.1
nmap --script-updatedb

## Firewall and IDS Evasion
nmap -f 192.168.1.1
nmap --mtu 24 192.168.1.1
nmap -D RND:10 192.168.1.1
nmap -D 192.168.1.5,192.168.1.6,ME 192.168.1.1
nmap -S 192.168.1.100 192.168.1.1
nmap -g 53 192.168.1.1
nmap --source-port 53 192.168.1.1
nmap --spoof-mac 0 192.168.1.1
nmap --spoof-mac Apple 192.168.1.1
nmap --data-length 25 192.168.1.1
nmap --badsum 192.168.1.1
nmap --randomize-hosts 192.168.1.0/24
nmap -T0 192.168.1.1
nmap -T1 192.168.1.1
nmap --scan-delay 5s 192.168.1.1
nmap --max-retries 1 192.168.1.1
nmap -sI <zombie_ip> 192.168.1.1
nmap -sN 192.168.1.1
nmap -sF 192.168.1.1
nmap -sX 192.168.1.1
nmap --proxies socks4://127.0.0.1:1080 192.168.1.1

## Timing and Performance
nmap -T0 192.168.1.1
nmap -T1 192.168.1.1
nmap -T2 192.168.1.1
nmap -T3 192.168.1.1
nmap -T4 192.168.1.1
nmap -T5 192.168.1.1
nmap --min-rate 1000 192.168.1.1
nmap --max-rate 500 192.168.1.1
nmap --min-parallelism 10 192.168.1.1
nmap --max-parallelism 100 192.168.1.1
nmap --min-hostgroup 64 192.168.1.0/24
nmap --host-timeout 30m 192.168.1.0/24

## Output Formats
nmap -oN output.txt 192.168.1.1
nmap -oX output.xml 192.168.1.1
nmap -oG output.gnmap 192.168.1.1
nmap -oA output 192.168.1.1
nmap -oS output.txt 192.168.1.1
nmap -v 192.168.1.1
nmap -vv 192.168.1.1
nmap -d 192.168.1.1
nmap --reason 192.168.1.1
nmap --open 192.168.1.1
nmap --packet-trace 192.168.1.1

## Full Enumeration One-Liners
nmap -sC -sV -oA full_scan 192.168.1.1
nmap -p- -T4 -A -v 192.168.1.1
nmap -sS -sU -T4 -A -p- 192.168.1.1
nmap -sV -sC -p- --min-rate 5000 -oA output 192.168.1.1
nmap -Pn -sV -sC -p 21,22,23,25,53,80,110,139,143,443,445,3306,3389 192.168.1.1
nmap --script=vuln -sV -p- -T4 -oN vuln_scan.txt 192.168.1.1
nmap -sn 192.168.1.0/24 | grep "Nmap scan report" | awk '{print $5}' > live_hosts.txt

## Common Flags
- `-sS` - SYN (stealth) scan; sends SYN packets and never completes the TCP handshake; requires root
- `-sT` - TCP connect scan; completes full handshake; slower but works without root privileges
- `-sU` - UDP scan; slower than TCP scans; useful for finding DNS, SNMP, DHCP services
- `-sN` - TCP Null scan; sends packets with no flags set; used for firewall evasion
- `-sF` - FIN scan; sends packets with only the FIN flag; used for firewall evasion
- `-sX` - Xmas scan; sets FIN, PSH, and URG flags; used for firewall evasion
- `-sA` - ACK scan; used to map firewall rulesets, not to detect open ports
- `-sI` - Idle/zombie scan; uses a third-party host to spoof the source IP completely
- `-sn` - Ping scan only; disables port scanning, used purely for host discovery
- `-Pn` - Skip host discovery; treat all hosts as online; useful when ICMP is blocked
- `-p` - Specify port(s) to scan; accepts single ports, ranges, and comma-separated lists
- `-p-` - Scan all 65535 ports
- `-F` - Fast scan; scans only the top 100 most common ports
- `--top-ports` - Scan the N most commonly used ports
- `-sV` - Probe open ports to detect service name and version
- `--version-intensity` - Set version detection intensity from 0 (light) to 9 (all probes)
- `-O` - Enable OS detection
- `--osscan-guess` - Aggressively guess OS when detection is not definitive
- `-A` - Aggressive scan; enables OS detection, version detection, script scanning, and traceroute
- `-sC` - Run default NSE scripts; equivalent to `--script=default`
- `--script` - Specify NSE scripts or categories to run against targets
- `--script-args` - Pass arguments to NSE scripts (e.g. credentials, paths)
- `-f` - Fragment packets to evade packet filters and IDS
- `--mtu` - Set custom MTU size for packet fragmentation (must be a multiple of 8)
- `-D` - Decoy scan; send packets from spoofed IPs alongside your real IP to obscure origin
- `-S` - Spoof source IP address (requires `-e` and `-Pn` in most cases)
- `-g` / `--source-port` - Use a specific source port number to bypass port-based firewall rules
- `--spoof-mac` - Spoof MAC address; use 0 for a random MAC or specify a vendor name
- `--data-length` - Append random data to packets to alter their size and evade signature detection
- `--randomize-hosts` - Randomize the order of target hosts to reduce scan detection likelihood
- `-T` - Timing template from T0 (paranoid/slowest) to T5 (insane/fastest); T3 is default
- `--min-rate` - Send packets no slower than this many per second
- `--max-rate` - Send packets no faster than this many per second
- `--scan-delay` - Enforce a minimum delay between probes to evade IDS rate detection
- `--max-retries` - Cap the number of port scan probe retransmissions
- `--host-timeout` - Abandon a target host after this much time
- `-iL` - Read target hosts from a file (one host/range per line)
- `-v` / `-vv` - Increase verbosity level of output
- `-d` - Enable debug mode output
- `--reason` - Display the reason each port is in its detected state
- `--open` - Only show open ports in results; suppress filtered and closed
- `--packet-trace` - Show all packets sent and received during the scan
- `-oN` - Save output in normal human-readable format to a file
- `-oX` - Save output in XML format; useful for importing into other tools
- `-oG` - Save output in greppable format; easy to parse with grep and awk
- `-oA` - Save output in all three major formats simultaneously (normal, XML, greppable)
- `--proxies` - Route TCP connections through a chain of HTTP/SOCKS4 proxies
