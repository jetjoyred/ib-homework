# Task 1

## Command

Корректная команда:
```bash
ps aux --sort=-%cpu > task1_processes.txt 2>/dev/null
```

Команда с ошибкой:
```bash
pss aux --sort=-%cpu > task1_bad.txt 2> task1_error.log
```

task1_error:

```bash
┌──(jetjoyred㉿kali)-[~]
└─$ cat task1_error.log    
Command 'pss' not found, but there are 19 similar ones.
```

task1_bad(stdout):

```bash
┌──(jetjoyred㉿kali)-[~]
└─$ cat task1_bad.txt      
                                                                                                                   
┌──(jetjoyred㉿kali)-[~]
└─$ 
```
task1_processes:

```bash
┌──(jetjoyred㉿kali)-[~]
└─$ cat task1_processes.txt | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           2  0.0  0.0      0     0 ?        S    11:24   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    11:24   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/R-netns]
root           9  0.0  0.0      0     0 ?        I    11:24   0:00 [kworker/0:0-events]
root          10  0.0  0.0      0     0 ?        I<   11:24   0:00 [kworker/0:0H-events_highpri]
```
