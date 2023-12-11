# Linux Essentials (level 1) Linux-ի Հիմունքներ (փուլ 1)

## Disk/file space usage (du)

* **du** - "_disk usage_" - Ցույց տալ դիրեկտորիայի չափը


`du -h`	- չափերը լինեն մարդու համար ընթեռնելի k-Kb, M-Mb, G-Gb 

`du -d1` - միայն 1 մակարդակ ներս (հին տարբերակներում `--max-depth`)

`du -s` - Ցույց տալ ընդհանուր չափը (նույնն է ինչ `-d 0` )


Ցույց տալ /var/log-ի ընդհանուր չափը, սխալների հաղորդագրությունները ուղարկել /dev/null
```bash
du -hs /var/log 2>/dev/null
```

Ցույց տալ /var-ի յուրաքանչյուր դիրեկտորիայի  չափը
```bash
du -hd1 /var
```

Այլ տարբերակ
```bash
du -sh /var/*
```

#### PRACTICE

Գրել հրամանների հաջորդականություն, որը ցույց կտա /etc-ի յուրաքանչյուր դիրեկտորիայի չափը
* արդյունքը դասավորել ըստ չափերի՝ փոքրից մեծ /թվային/
* չափերը լինեն մարդու համար ընթեռնելի՝ Mb,Gb-ով
* սխալների հաղորդագրությունները ուղարկել /dev/null


## Disk/file space usage (df)

* **df** - "disk free" - ցույց տալ միացված partition-ները ֆայլային համակարգերը 
և զբաղեցրած/ազատ չափը


՝df -h՝  չափերը լինեն մարդու համար ընթեռնելի k-Kb, M-Mb, G-Gb 

՝df -T՝  ցույց տալ ֆայլային համակարգի տեսակը


## Processes  Պրոցեսներ

**Պրոցես** = **աշխատող ծրագիր**


* Պրոցեսի պարամետրեր՝
* Եզակի համար 	Process ID (**PID**)
* Ծնողի համար  	Parent Process ID (**PPID**)
* Վիճակ 		State
* Տերմինալ 		**TTY** (`daemon` պրոցեսները չունեն TTY)
* Իրական օգտագործողի համար  Real user ID (**RUID**)
* Գործող օգտագործողի համար Effective user ID (**EUID**)
* Իրական խմբի համար Real group ID (**RGID**)
* Գործող խմբի համար Effective group ID (**EGID**)

### Պրոցեսների վիճակներ

* Running / Runnable (**R**)
* Sleeping 
  * Interruptable (**S**)
  * Uninterruptible (**D**)
* Stopped (**T**)
* Defunct / Zombie (**Z**)


Գործիքներ`

* ps
* pstree
* top
* htop
* gnome-system-monitor



Օրինակներ`

```bash
ps
```
```bash
ps l
```

```bash
ps -o pid,ppid,user,cmd
```

```bash
ps aux 
```

```bash
ps -eo pid,ppid,user,cmd 
```

```bash
pstree 
```

```bash
pstree -u –p
```

```bash
top
```

#### PRACTICE

Բացեք 3 տերմինալ, երկու պատուհանում տվեք `cat` հրամանը,
3-րդ տերմինալում տվեք հետևյալ հրամանը
`ps aux | grep cat`



Պրոցեսի կառավարում՝


* kill 
* kill -l 
* kill [-signnum] <PID> 
* pkill <process_name>
* pgrep -l bash
* pidof <process_name>
* killall [-signum] <process_name> 

![img.png](img/signals.png)

### Background processes Ետին պլանի պրոցեներ

Հրամաններից հետո `&` նշան դնելիս ուղարկում ենք ետին պլան (background) 

`command &`

Գործիքներ`

 `jobs`     - List  the  active  jobs
 `kill %n` - Kill the foreground  job 
 `fg [#n]` - Resume job in the foreground, 
                 and make it the current  job. 

#### PRACTICE

* Տվեք `man ls` հրամանը, սեղմեք `Ctrl-Z`
* Տվեք `top` հրամանը, սեղմեք `Ctrl-Z`
* Տվեք `jobs` հրամանը

> [1]-  Stopped                 man ls <br> 
> [2]+  Stopped                 top

* Տվեք `fg 1` հրամանը

Հարց՝ ինչպե՞ս լրիվ անջատել այդ ցրագրերը:






