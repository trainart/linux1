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


`df -h`  չափերը լինեն մարդու համար ընթեռնելի k-Kb, M-Mb, G-Gb 

`df -T`  ցույց տալ ֆայլային համակարգի տեսակը

`df -hT -x tmpfs -x devtmpfs` ցույց չտալ `tmpfs` և `devtmpfs` ֆայլային համակարգերը

## File Search - Ֆայլերի որոնում

**find** - որոնում Ֆայլերի տարբեր հատկանիշներով


```bash
find /etc -name "passwd*" 2> /dev/null
```

```bash
find ~ -name "f*“
```

```bash
find ~ -type l 2> /dev/null
```
> _-type_  կարող է լինել <br>
>   **d**    directory <br>
>   **f**    regular file <br>
>   **l**    symbolic link <br>

```bash
find ~ -name "f*" -type l 2> /dev/null
```

```bash
find /bin -size +20000k
```

```bash
find /usr/sbin -size 2M -name "t*" -exec ls -l {} \;
```

```bash
find /usr/sbin -size +100k -name "t*" -ok cp {} /tmp \;
```


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


![img.png](img.png)


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

### Login / Logout

Global Login Config Files:
* `/etc/profile`
* `/etc/bash.bashrc`

Per-User Login Config Files:
* `~/.bash_profile` 
  * հաճախ ընդգրկում է `~/.bashrc`
* `~/.bash_login`   
* `~/.profile`
Կատարվելու է այս 3-ից մեկը

Մեջբերում `man bash`-ի `INVOCATION` հատվածից

> When bash is invoked as an **interactive login shell** ...
> it first reads and executes commands from the file `/etc/profile`, if that file exists.  
> After reading that file, it looks for
>    `~/.bash_profile`,  `~/.bash_login`,  and `~/.profile`, **in that order**, 
> and reads and executes commands from the FIRST ONE that exists and is readable.  


Logout

*   `~/.bash_logout`


### Shell Scripting Basics

> First line of Shell script should look like: 
* `#!/bin/bash`
* `#!/bin/sh`

After 2 special characters **#!**, 
it should contain the path to the interpreter - program that will try to interpret the text line by line and do what is required.

In case script don't have such first line, it will still work, but it will be interpreted by current shell and chances are, there will be some errors. 

<br><br>

*Simple script example*

```bash
cat  > ~/s1  << "EOF1"
#!/bin/bash
ls -l /usr/bin/
EOF1
chmod +x ~/s1

```

Try running this simple script:

`./s1`

Let's now understand what was done above.

We used method called _Here document_ to create the script and made it executable with `chmod`.
The script itself is a single `ls` command, that outputs detailed (-l) contents of directory _/usr/bin/_

Check the contents of the script you created:

```bash
cat ~/s1
```

<br><br>

## Positional Parameters

During running, shell scripts have access to special data from the environment:

* **$0** or **{$0}** - The name of the script
* **$1** or **{$1}** - The first argument sent to the script 
* **$2** or **{$2}** - The second argument sent to the script
...
* **$*** - all arguments as one
* **$#** - count/number of arguments

This enables to pass some data to the script by means of positional parameters.

> Example of positional parameters

```bash
cat  > ~/s2  << "EOF1"
#!/bin/bash
# Here we get the first positional parameter and provide it to "ls" command
ls -l ${1}
EOF1
chmod +x ~/s2

```

Now try running this simple script without any parameter:

```bash
./s2
```

> QUESTION: What directory did `ls` command list ?  Why ?

Now try providing one positional parameter

```bash
./s2 /tmp
```

```bash
./s2 /usr/sbin
```

As you see we pass the data to the script, which changes how `ls` command works.


Let's now pass more data. 
We will provide options to `ls` via first positional parameter, 
the directory to show via second and pattern to filter lines via third.

```bash
cat  > ~/s3  << "EOF1"
#!/bin/bash
ls ${1} ${2} | grep ${3}
EOF1
chmod +x ~/s3

```

First try running this script without parameters:

```bash
./s3
```

> EXPLAIN THE OUTPUT


Now try providing all 3 positional parameters

```bash
./s3 -lh /bin log
```

```bash
./s3 -r / l
```


## Conditionals - if

Very frequently there is need to make decisions based on certain conditions. 
Conditions are expressions that after being evaluated return "yes" or "no" 
(i.e. true or false).

Most used is **if** conditional

Shell script to check whether a number is positive or negative

```bash
#!/bin/bash
echo "Enter a Number"
read num

if [ $num -lt 0 ]
then
    echo "$num is Negative"
elif [ $num -gt 0 ]
then
    echo "$num is Positive"
else
    echo "$num is ZERO"
fi

```

### Task 
Modify script to get number from 1st positional parameter

## Loops

Example of `for` loop


```bash
cat  > ~/loop2  << "END5"
#!/bin/bash
echo "How do you like it:"
for (( i=1; i<=5; i++ ))
do
    for (( j=1; j<=i;  j++ ))
    do
     echo -n "$i"
    done
    echo ""
done
END5
chmod +x ~/loop2

```

#### Task

Modify the above script to get first positional parameter and to output numbers until that.
