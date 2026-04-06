# Task 2

## Command

```ps -u "$(whoami)" --sort=-%cpu | head -10 | tee top10.txt```

## Output

```
┌──(jetjoyred㉿kali)-[~]
└─$ ps -u "$(whoami)" --sort=-%cpu | head -10 | tee top10.txt
    PID TTY          TIME CMD
   2004 ?        00:00:02 qterminal
   1220 ?        00:00:02 xfwm4
   1339 ?        00:00:01 wrapper-2.0
   1337 ?        00:00:01 wrapper-2.0
   2041 pts/0    00:00:01 zsh
   1148 ?        00:00:01 VBoxClient
   1286 ?        00:00:00 xfdesktop
   1269 ?        00:00:00 xfce4-panel
   1677 ?        00:00:00 blueman-applet
                                                                                                                   
┌──(jetjoyred㉿kali)-[~]
└─$ cat top10.txt                                            
    PID TTY          TIME CMD
   2004 ?        00:00:02 qterminal
   1220 ?        00:00:02 xfwm4
   1339 ?        00:00:01 wrapper-2.0
   1337 ?        00:00:01 wrapper-2.0
   2041 pts/0    00:00:01 zsh
   1148 ?        00:00:01 VBoxClient
   1286 ?        00:00:00 xfdesktop
   1269 ?        00:00:00 xfce4-panel
   1677 ?        00:00:00 blueman-applet
                                                                                                                   
┌──(jetjoyred㉿kali)-[~]
└─$ 
```
