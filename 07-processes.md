# §7: Processes

---

- Each process has its unique Process ID (PID).

- `pidof {name}` (e.g. `pidof bash`) finds PIDs by name.

---

## ps: process info 📝

| Command      | Action                          |
|--------------|---------------------------------|
| `ps`         | list current processes          |
| `ps -e`      | list all processes              |
| `ps -C bash` | processes with command `bash`   |
| `ps -U root` | processes run by `root` user    |
| `pstree`     | process tree (package `procps`) |

---

## Monitoring processes 👁

- `apt install procps`
- `top`

```
top - 19:57:02 up  4:24,  0 users,  load average: 3.86, 1.34, 0.61
Tasks: 120 total,   1 running, 118 sleeping,   1 stopped,   0 zombie
%Cpu(s): 70.3 us, 11.7 sy,  0.0 ni,  6.4 id,  0.8 wa,  0.0 hi,  0.1 si, 10.8 st
MiB Mem :   6603.6 total,   6592.3 free,      5.1 used,      6.2 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   6598.5 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND           
20995 abeshen+  20   0 7894004   2.2g 297812 S 305.7  34.0   2:44.67 java              
21501 abeshen+  20   0 2475216  55784  26788 S  23.0   0.8   0:00.69 java              
21495 abeshen+  20   0 2475216  52100  26660 S  22.0   0.8   0:00.66 java              
  499 abeshen+  20   0   72268  28936   8140 S   1.7   0.4   2:16.51 ld-linux-x86-64   
  459 abeshen+  20   0   36864   5728   1748 S   0.3   0.1   1:21.33 ld-linux-x86-64   
21319 abeshen+  20   0   10088   3752   3128 R   0.3   0.1   0:00.02 top               
    1 root      20   0  165600   5936   3520 S   0.0   0.1   0:01.14 systemd           
   60 root      20   0   48328   5228   4068 S   0.0   0.1   0:02.18 systemd-journal   
   67 root      20   0   20796   4176   2124 S   0.0   0.1   0:00.24 systemd-udevd     
  104 root      20   0   99824   4392   3064 S   0.0   0.1   0:00.05 dhclient          
  137 avahi     20   0    7284   3040   2688 S   0.0   0.0   0:00.18 avahi-daemon      
  138 message+  20   0    8532   4236   3560 S   0.0   0.1   0:00.83 dbus-daemon       
  140 root      20   0  234420   6424   5104 S   0.0   0.1   0:00.67 polkitd           
```

---

## kill 🔪

| Command                   | Action             |
|---------------------------|--------------------|
| `kill {pid}`              | sends `SIGTERM`    |
| `killall {name}`          | sends `SIGTERM`    |
| `kill -KILL {pid}`        | sends `SIGKILL`    |
| `killall -KILL {name}`    | sends `SIGKILL`    |

- `SIGTERM` asks process politely to terminate.
- `SIGKILL` kills the process (e.g. when not responding)

---

## Example 🔪

- Run `less /etc/passwd`.
- Press `C-z`.
- Check `top`.
- Try `killall less`.
- Check `top` again.
- Try `killall -KILL less`.
