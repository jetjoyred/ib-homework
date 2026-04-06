# Task 2
## Command

### Базовое сканирование 

```
┌──(jetjoyred㉿kali)-[~]
└─$ nmap b24.reagroup.ru        
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-06 12:10 -0400
Nmap scan report for b24.reagroup.ru (46.149.70.209)
Host is up (0.0042s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 7.83 seconds
```

### Сканирование конркретных портов
```                                                                                                                
┌──(jetjoyred㉿kali)-[~]
└─$ nmap -p 80,443,22 b24.reagroup.ru
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-06 12:10 -0400
Nmap scan report for b24.reagroup.ru (46.149.70.209)
Host is up (0.0016s latency).

PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 2.65 seconds
```
### Сканирование диапазона портов
```                                                                                                                   
┌──(jetjoyred㉿kali)-[~]
└─$ nmap -p 1-1000 b24.reagroup.ru   
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-06 12:11 -0400
Nmap scan report for b24.reagroup.ru (46.149.70.209)
Host is up (0.016s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 34.25 seconds
```
### Определение сервисов и ОС
```                                                                                                                   
┌──(jetjoyred㉿kali)-[~]
└─$ nmap -sV -O b24.reagroup.ru   
Starting Nmap 7.98 ( https://nmap.org ) at 2026-04-06 12:12 -0400
Nmap scan report for b24.reagroup.ru (46.149.70.209)
Host is up (0.0071s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.7 (protocol 2.0)
80/tcp  open  http     nginx
443/tcp open  ssl/http nginx
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: VoIP adapter|bridge|general purpose
Running (JUST GUESSING): AT&T embedded (93%), Oracle Virtualbox (92%), Slirp (92%), QEMU (90%)
OS CPE: cpe:/o:oracle:virtualbox cpe:/a:danny_gasparovski:slirp cpe:/a:qemu:qemu
Aggressive OS guesses: AT&T BGW210 voice gateway (93%), Oracle Virtualbox Slirp NAT bridge (92%), QEMU user mode network gateway (90%)
No exact OS matches for host (test conditions non-ideal).

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 48.37 seconds
```
### Greppable формат
```                                                                                                                
┌──(jetjoyred㉿kali)-[~]
└─$ nmap -p 1-1000 b24.reagroup.ru -oG -
# Nmap 7.98 scan initiated Mon Apr  6 12:24:54 2026 as: /usr/lib/nmap/nmap --privileged -p 1-1000 -oG - b24.reagroup.ru
Host: 46.149.70.209 ()  Status: Up
Host: 46.149.70.209 ()  Ports: 22/open/tcp//ssh///, 80/open/tcp//http///, 443/open/tcp//https///        Ignored State: filtered (997)
# Nmap done at Mon Apr  6 12:25:02 2026 -- 1 IP address (1 host up) scanned in 8.41 seconds
```

