# Задание 1

## Команда ip a

### Команда используется для просмотра сетевых интерфейсов и их ip.
### В результате отображаются активные интерфейсы и назначенные им адреса.
```
┌──(jetjoyred㉿kali)-[~]
└─$ ip a 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:c7:36:2d brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute eth0
       valid_lft 85719sec preferred_lft 85719sec
    inet6 fd17:625c:f037:2:729d:273e:f1c:2d5/64 scope global temporary dynamic 
       valid_lft 86047sec preferred_lft 14047sec
    inet6 fd17:625c:f037:2:a00:27ff:fec7:362d/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 86047sec preferred_lft 14047sec
    inet6 fe80::a00:27ff:fec7:362d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:4f:de:97 brd ff:ff:ff:ff:ff:ff
```
## Команда ping
### Команда проверяет доступность удаленного узла.
### Успешный ответ означает наличие сетевого соединения
```
┌──(jetjoyred㉿kali)-[~]
└─$ ping -c 4 8.8.8.8  
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=255 time=0.498 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=255 time=0.496 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=255 time=0.435 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=255 time=0.488 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3054ms
rtt min/avg/max/mdev = 0.435/0.479/0.498/0.025 ms
```
## Команда traceroute 
### Команда показывает маршрут прохождения пакетов до узла
### Позволяет определить промежуточные узлы сети
```
┌──(jetjoyred㉿kali)-[~]
└─$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  10.0.2.2 (10.0.2.2)  0.417 ms  0.399 ms  0.392 ms
 2  * * *
 3  * * *
 4  * * *
```
## Команда SS/NETSTAT
### Команда показывает активные сетевые соединения и открытые порты
```
┌──(jetjoyred㉿kali)-[~]
└─$ ss -tuln
Netid       State       Recv-Q       Send-Q             Local Address:Port             Peer Address:Port      
```
## Команда DIG
### Команда используется для проверки DNS записей
### Показывает ip адреса домена и DNS серверы
```
┌──(jetjoyred㉿kali)-[~]
└─$ dig google.com 

; <<>> DiG 9.20.20-1-Debian <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27403
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; MBZ: 0x00e6, udp: 1232
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             230     IN      A       172.217.17.206

;; Query time: 51 msec
;; SERVER: 172.18.0.2#53(172.18.0.2) (UDP)
;; WHEN: Sun Apr 12 15:10:06 EDT 2026
;; MSG SIZE  rcvd: 65
```
