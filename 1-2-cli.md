# Linux Essentials (level 1) <br> Լինուքսի Հիմունքներ (փուլ 1)

## Linux Terminal (Լինուքսի հրամանների տողը)

> Ներածական հարցեր թեմայի վերաբերյալ 
* Ծանո՞թ եք տերմինալի միջոցով Linux-ում աշխատելուն
* Եթե այո ի՞նչ ծրագրի միջոցով
* Ծանո՞թ եք SSH-ով միանալուն
  * ssh (Windows-ի հրամանային միջավայրում)
  * Putty
  * Xshell
  * MobaXterm
* Ծանո՞թ եք Windows Subsystem for Linux (WSL) in Windows 10/11
  

Լինուքս համակարգ մուտքագրվելու հիմնական ձևն է՝
անուն (username) և գաղտնաբառ (password) մուտքագրելը

SSH-ով միանալու պարագայում գաղտնաբառի փոխարեն հնարավոր է մուտքը զույգ-բանալիներով (Public/Private Keys)

<br><br>

## Linux VM remote access

* **Oracle VM VirtualBox** միջավայրում միացրեք վիրտուալ մեքենան

### Local login
* մուտք գործեք
  * **student** անունով
  * **123456** գաղտնաբառով

### Remote login
* Նկատեք `IP address`-ը:
* Windows-ում բացեք հրամանների միջավայրը (`cmd`)
* միացեք SSH-ով `student` անունով ու IP-հասցեյով (password - `123456`)

`ssh student@<ip-address>`


## CLI vs GUI

Լինուքս համակարգում հնարավոր է աշխատել հետևյալ տարբերակներից մեկով. 
* Graphical User Interface (**GUI**)
* Command Line Interface (**CLI**) / Terminal

Այս դասընթացի ընթացքում մենք հիմնականում կաշխատենք երկրորդ (**CLI / Terminal**) տարբերակով, քանի որ դա Լինուքս համակարգի սերվերային տարբերակի 
հիմնական տարբերակն է: 
Լինուքսի համար կան նաև շատ գրաֆիկական միջավայրեր (**GUI**), բայց սերվերային տարբերակներում դրանք սովորաբար նույնիսկ չեն տեղադրվում 
և դրանց իմաստն էլ չկա, քանի որ նման համակարգերում չկան նույնիսկ մոնիտորներ:
Գրաֆիկական միջավայրերը ավելի շատ օգտագործվում են Linux-ի Desktop տարբերակներում:

Ինչպես ասացինք, գրաֆիկական միջավայրը լրացուցիչ է և տեքստայինից դրան անցում կարելի է անել, 
միայն եթե տեղադրվածեն համապատասխան փաթեթներ։

Ընթացիկ ռեժիմը կարող ենք իմանալ հետևյալ հրամանով.
```bash
systemctl get-default
```
* **graphical.target** → գրաֆիկական միջավայր (**GUI**)
* **multi-user.target** → տեքստայինից միջավայր (**CLI / Terminal**)


Միացնել գրաֆիկական միջավայրը կարելի է հետևյալ հրամանով.
```bash
systemctl isolate graphical.target
```
Սակայն դա չի պահպանվի համակարգը համակարգը անջատել-միացնելուց հետո

> ✅ ԿԱՐԵՎՈՐ Է <br>
> Գրաֆիկական միջավայրը աշխատում է տեքստայինի «վրայից» (**GUI** on top of **CLI**) <br>
> Կարելի է միշտ անցում կատարել դեպի «տակի» տեքստային տերմինալներ, որոնք սովորաբար մի քանիսն են <br>
> Անցում դեպի տեքստային տերմինալ՝  **Ctrl + Alt + (F1 – F12)** <br>
> Վերադարձ/տեղափոխում տերմինալների միջև՝  **Alt + (F1 – F12)** <br>


Միացնել տեքստային միջավայրը կարելի է հետևյալ հրամանով.
```bash
systemctl isolate multi-user.target
```


## Linux Terminal, CLI Basics

> Ինչ է Terminal-ը

Ծրագիր, որի ներսում գոծում է հրամանի տող (Command Line): 
Հնարավոր է դա լինի հեռակա միացումով (remote connection/access):
Այսինքն աշխատանքը իրականացվի ցանցով կապված մեկ այլ հեռակա համակարգի վրա:

> Ինչ է Command Line Interface/Interpreter (CLI) / Shell 

Ծրագիր, որը իրականացնում է հրամանի տողի աշխատանքը, 
վերլուծում է (interpret) տողը ու կատարում հրամանը կամ հայտնում սխալի մասին:

Հրամանները վերլուծվում են տող առ տող, այդ պատճառով ամեն մի հրամանը պետք է ավարտվի **[Enter]**-ով:
** [Enter]**-ից հետո հրամանը այլևս հնարավոր չէ փոխել:

> **#**  նշանը և դրանից հետո ամեն ինչը համարվում է comment և չի վերլուծվում:  

CLI այլ կերպ նաև անվանվում է Shell: Լինում են տարբեր տեսակներ, ամենատարածվածը` **Bash**

CLI / Shell / Bash աշխատում է ինտերակտիվ եղանակով, որը նաև անվանում են REPL 

**Read** -> **Evaluate** -> **Print** -> **Loop**  

## LiNuX iS CaSe SeNsItIvE

Լինուքսի առանձնահատկություններից մեկը այն է, որ այս համակարգում տարբերություն կա **մեծատառերի** և **փոքրատառերի** միջև։

  * Հրամանների և ծրագրերի անվանման մեջ 
    * `command`
    * `Command` 
    * `COMMAND` 
    
  * Ֆայլերի և դիրեկտորիաների/ֆոլդերների անվանման մեջ
    * `file`
    * `File`
    * `FILE`
    
  * Օգտագործողների և խմբերի անվանման մեջ
    * `user`
    * `User`
    * `USER`


### Command Prompt

Հարաման մուտքագրելու հրավեր:

Օրինակներ.

**$** - User Prompt

**#** - ROOT Prompt

Այս հրավերի տեսքը հնարավոր է փոխել, սակայն հաճախ նշված նշանները պահպանվում են և ավելանում է լրացուցիչ տեղեկություն, 
օրինակ՝ սերվերի, օգտագործողի, տվյալ դիրեկտորիայի անունները:

`student@server:/usr/bin$`

<br><br>

#### Movement in command line

Տեղաշարժ հրամանային տողում. 
*  **Աջ/ձախ սլաքներ**
* `Ctrl-A` – տեղափոխել տողի սկիզբ
* `Ctrl-E` – տեղափոխել տողի վերջ


#### Command structure

Հրամանների կառուցվածք

<pre>
┌──────────────┬────────────┬─────────────┐
│    Command   │   Option   │   Argument  │
├──────────────┼────────────┼─────────────┤
│    հրաման    │ ընտրանքներ │ արգումենտներ│
├──────────────┼────────────┼─────────────┤
│              │            │             │
│      cal     │     -m     │     2025    │
│              │            │             │
└──────────────┴────────────┴─────────────┘

</pre>


💡 Հիմնական կանոններ.

1. Յուրաքանչյուր հատված բաժանվում է միմյանցից բացատներով /**SPACE**/ <br>
Դա շատ կարևոր է, քանի որ հրամանները վերլուծող համակարգը չունի բանականություն և չի կարող հասկանալ միասին գրվածը 

```bash
cal-m2025
```

```bash
cal -m2025
```

```bash
cal-m 2025
```


2. հաջորդականությունը կարևոր է. <br>
    «**հրաման [ընտրանքներ] [արգումենտներ]**»<br>

3. **Ընտրանքները** (**Options**) փոխում են աշխատաձևը (**-m** = սկսել երկուշաբթիից)<br>
3.1 Ընտրանքները լինում են.<br><br>
        - կարճ : `-a` (մեկ գծիկ, մեկ տառ)<br><br>
        - երկար: `--all` (երկու գծիկ, բազմատառ)<br><br>
3.2 կարճ ընտրանքները կարելի է միավորել<br><br>
`ls -l -a -h /home/student`  =  `ls -lah /home/student`<br>

4. **Արգումենտները** (**Arguments**) տվյալներ են տրամադրում (**2025** = տարի, **/home/student** = դիրեկտորիա)


<pre>
[հրաման] [աշխատաձև] [մուտքի տվյալներ]
   cal      -m          2025
</pre>



### Command examples

Հրամանների օրինակներ

* **cal** - display calendar 

```bash
cal
```

```bash
cal 2025
```

```bash
cal -m 2025
```


* **echo** - display a line of text 
```bash
echo We learn Linux # this is a comment 
```
```bash
# echo We learn Linux # this is a comment
```

```bash
echo "$USER" learns Linux OS
```
```bash
echo My Shell is: "$SHELL"
```

* **sleep** - delay for a specified time 

```bash
echo ; echo -n "Be patient " ; sleep 2 ; echo -n "to learn " ; sleep 2 ; echo "LINUX Operating System" ; sleep 2 ; echo 

```

* **id** - display user information

```bash
id
```

```bash
id -n -u
```

```bash
id --help
```

* **date** - display date

```bash
date
```

```bash
date --help
```

```bash
date +"%d-%m-%Y"
```

### Command Manuals (man)

Գրեթե յուրաքանչյուր հրամանի վերաբերյալ հնարավոր է ստանալ մանրամասն բացատրող տեղեկատվություններ:<br> <br>
Դա կարելի է անել հրամանային տողում հրամանի դեմը գրելով `man`: Ելքը - `q` 

```bash
man cal
```

```bash
man echo
```

```bash
man sleep
```

```bash
man id
```

```bash
man date
```

Հրամանի `--help` կամ `-h` ընտրանքները (options) նույնպես տեղեկատվություն են տրամադրում, բայց այն հակիրճ է:


### Command History 

Նախորդ հրամանները հիշվում են, որ նորից նույնը չհավաքենք:

* Վերևի սլաքը (Up Arrow) նախորդ հրամանները
* `history` հրամանը ցույց է տալիս բոլոր նախորդ հրամանները (հիմնականում պահվում են վերջին 500, 1000 կամ 2000 հրամանները)
* Որոնում նախորդ հրամաններում `Ctrl-R`
  * մուտքագրեք հրամանի սկիզբը
  * Կրկնելով `Ctrl-R` հնարավոր է փնտրել նախորդ տարբերակները
    * Օրինակ - սեղմեք `Ctrl-R` և հավաքեք `da`
    * Կրկնեք `Ctrl-R` հաջորդ տարբերակը գտնելու համար
  

### Filename/Command completion 	

Հնարավոր է ամբողջությամբ չլրացնել հրամանի/ֆայլի անունը՝ համակարգը կարող է ամբողջացնել անունը

* `[Tab]`	հրամանի/ֆայլի լրացում, եթե դա միակ տարբերակն է
  * Օրինակ - հավաքեք `sle` և `[Tab]`

<br><br>
* `[Tab] [Tab]` եթե մեկից ավել տարբերակ կա, ապա ցուցադրվում են բոլոր տարբերակները
  * Օրինակ - հավաքեք `sl` և `[Tab] [Tab]`
  
**Հրամանների որոնումը կատարվում է նախապես սահմանված դիրեկտորիաների ցանկում։** <br>
**Այն սահմանվում է $PATH փոփոխականում**

```bash
echo $PATH
```

<br><br>

## File Management

> Ֆայլերի անվանումը
* Windows
  * `C:\Program Files\Oracle\VirtualBox\VirtualBox.exe`

* Linux/UNIX

  * `/home/student/docs/letter.txt`
  * `/bin/ls`


### Linux Filesystem structure

Ծանոթացում Լինուքսի ֆայլային համակարգի կառուցվածքին

* Տվյալները Լինուքսում պահպանվում են`
  * կոշտ սկավառակի կամ այլ կրիչների վրա 
  * Ֆայլերի տեսքով, որոնք ներկայացվում են օգտագործողին ծառաձև դիրեկտորիաների կառուցվածքով 

* **Filesystem**/**Ֆայլային համակարգ**՝ որոշակի ստանդարտին համապատասխանող տվյալները սկավառակի/կրիչի վրա պահպանելու կառուցվածք
  * Նպատակն է հեշտ հասանելի դարձնել տվյալները

* Լինուքսը "հասկանում" է ֆայլային համակարգերի բազմաթիվ ստանդարտներ, օրինակ.
    * ext2, ext3, ext4, xfs, zfs, jfs, btrfs
    * FAT16, FAT32, NTFS, ISO9660, UDF


* Դիրեկտորիաների կառուցվածքը 
  * կազմում է հիերարխիկ ֆայլային համակարգ 
  * Լինուքսի յուրահատկությունը՝ 
    * Միասնական ծառ, ոչ թե  **C:**  **D:**  **E:** դիսկեր 
    
### Linux Filesystem Hierarchy Standard (FHS)

<pre>
🌳 C:\ (System Drive)
├── 📁 Windows           # OS core files
│   ├── 📁 System32      # Critical system binaries
│   └── 📁 Temp          # Temporary files
├── 📁 Program Files     # 64-bit applications
├── 📁 Program Files (x86) # 32-bit applications
└── 📁 Users            # User profiles
    └── 📁 User         # User documents
        ├── 📁 Desktop
        └── 📁 Documents

🌳 D:\ (User Data)
├── 📁 Projects
├── 📁 Media
│   ├── 📁 Music
│   └── 📁 Videos
└── 📁 Backups

🌳 E:\ (Photo Archive)
└── 📁 Photos

🌳 F:\ (Video Archive)
├── 📁 Clips
└── 📁 Videos

🌳 Z:\ (USB Stick)
├── 📁 Pictures
└── 📁 Images

</pre>

<br> <br>

<pre>
🌳 /
├── 📁 bin                 # Essential user command binaries
├── 📁 boot                # Boot loader files (kernel, initramfs)
├── 📁 dev                 # Device files (hardware interfaces)
├── 📁 etc                 # System-wide configuration
│   ├── 📄 passwd          # User accounts
│   └── 📄 shadow          # Encrypted passwords
├── 📁 home                # User personal directories
│   ├── 📁 student         # Student's files
│   └── 📁 student2        # Student2's files
├── 📁 lib                 # Essential shared libraries
├── 📁 media               # Removable media mount points
│   ├── 📁 usb             # USB drives
│   └── 📁 cdrom           # Optical drives
├── 📁 mnt                 # Temporary manual mounts
├── 📁 opt                 # Optional software packages
├── 📁 proc                # Virtual process filesystem
├── 📁 root                # Root user's home
├── 📁 run                 # Runtime variable data
├── 📁 sbin                # System administration binaries
├── 📁 srv                 # Service data
├── 📁 sys                 # Virtual kernel objects
├── 📁 tmp                 # Temporary files
├── 📁 usr                 # Secondary hierarchy
│   ├── 📁 bin             # Non-essential binaries
│   ├── 📁 sbin            # Non-essential admin tools
│   ├── 📁 lib             # Libraries
│   └── 📁 local           # Locally installed software
└── 📁 var                 # Variable data
    ├── 📁 log             # System logs
    ├── 📁 cache           # Application cache
    └── 📁 lib             # Dynamic libraries
</pre>



### Linux Partition Mounting (հատվածների կցում)

* Partition հատվածները որպես առանձնացված տառերով դիսկեր ներկայացնելու փոխարեն, Լինուքսում կա 
  * գլխավոր հատված՝ **Root partition**
  * մյուս հատվածները կցվում են (**mount**) գլխավորի որևէ կետին - դիրեկտորիային
* Յուրաքանչյուր Partition հատվածում տվյալներ պահպանելու համար այն պետք է ունենա որոշակի ստանդարտի ֆայլային համակարգ (format-արած լինի այդ ստանդարտով):


Windows example

<pre>
🖴 Physical Storage Devices
├── Disk 1 (500GB)
│   ├── Partition 1 (200GB,ntfs) → C:\   Windows OS
│   ├── Partition 2 (150GB,ntfs) → D:\   User Data
│   └── Partition 3 (50GB,ntfs)  → E:\   Photo Archive
│
├── Disk 2 (1TB)  
│   └── Partition 1 (1TB,ntfs)   → F:\   Video Archive
│
└── USB Stick (32GB)
    └── Partition 1 (32GB,vfat)  → Z:\   Image Archive
</pre>


Linux example

<pre>
🖴 Physical Storage Devices
├── Disk 1 (500GB)
│   ├── Partition 1 (200GB,ext4) → / (Root Filesystem)
│   ├── Partition 2 (150GB,ext4) → /home
│   └── Partition 3 (50GB,ext4)  → /tmp
│
├── Disk 2 (1TB)  
│   └── Partition 1 (1TB,xfs)    → /usr
│
└── USB Stick (32GB)
    └── Partition 1 (32GB,vfat)  → /media/usb
</pre>

<br><br>

<pre>
🌳 /            → Root Filesystem - Disk 1,Partition 1 (ext4)
├── 📁 bin       
│   └── ls
├── 📁 etc       
├── 📁 home     → mounted from Disk 1,Partition 2 (ext4)
│   └── 📁 student
│       └── userinfo.txt 
├── 📁 tmp      → mounted from Disk 1,Partition 3 (ext4)
│   └── tmpfile
├── 📁 usr      → mounted from Disk 2,Partition 1 (xfs) 
│   ├── 📁 bin   
│   └── 📁 lib   
│       └── systemlib
└── 📁 media
    └── 📁 usb  → mounted from USB stick,Partition 1 (vfat)
        └── 📁 docs
            └── info.doc
</pre>


<br><br>

* Որտե՞ղ (ո՞ր partition-ում) է ֆիզիկապես գտնվում հետևյալ ֆայլը.
  * `/bin/ls`
  * `/home/student/userinfo.txt`
  * `/tmp/tmpfile`
  * `/usr/lib/systemlib`
  * `/media/usb/docs/info.doc`


<hr>

### File path
ճանապարհը դեպի ֆայլը նշելու տաբերակներ.

* Ցանկացած տեղից
  * `/home/student/userinfo.txt`
  
* Եթե գտնվում ենք `/home/student`-ում
  * `userinfo.txt`
  * `./userinfo.txt`
  * `../student/userinfo.txt`

* Եթե գտնվում ենք `/usr/lib`-ում
  * `../../home/student/userinfo.txt`

  
### PRACTICE

Երբ մուտքագրվում եք (բացվում է Terminal-ը), հայտնվում եք ֆայլային համակարգի ընթացիկ դիրեկտորիայում: 
Սովորաբար դա տվյալ օգտագործողի անձնական դիրեկտորիան է (Home Directory):

> Հիմնական հրամաններ
* `pwd` - ընթացիկ դիրեկտորիան
* `cd` - փոխել ընթացիկ դիրեկտորիան
  * Օրինակ - հավաքեք `cd /h` և `[Tab]` հետո ևս մեկ `[Tab]`
  * Օրինակ - հավաքեք `cd /u` և `[Tab]` հետո `lo` և `[Tab]` հետո `b` և `[Tab]`


* `ls` - ֆայլերի ցուցակ
<hr>

`ls [options] <directory/file>`

* `-l`  ընդլայնված ցուցակ
* `-a`  ցույց տալ բոլոր ֆալերը  (նեռարյալ .-ով սկսվող ֆալերը )
* `-S`  դասավորել ֆայլերը ըստ չափի (`–lS`)
* `-r`  Հակադարձ դասավորման կարգով (`–lSr`)
* `-h`  Մարդու համար ավելի ընթեռնելի (ֆայլերի չափը k, M, G-ով)


<hr> 

> ՕԳՏԱԿԱՐ ԿԱՅՔ՝ 
> https://explainshell.com/
> հրամանների մանրամասն բացատրություն: 
> Բացեք կայքը և մուտքագրեք հրաման, օրինակ

```bash
id -n -u
```

կամ

```**bash**
echo -n "Be patient " ; sleep 2 ; echo -n "to learn LINUX" ; sleep 2
```
<hr> 

> Հատուկ անվանումներ
* `/`    Գլխավոր դիրեկտորիան, դիրեկտորիաների միջև տարանջատիչ
* `.`    Տվյալ դիրեկտորիան
* `..`   Նախորդ (վերևի) դիրեկտորիան
* `~`    Օգտագործողի անձնական դիրեկտորիան
* `.`-ով սկսվող ֆայլերը սովորաբար օգտագործվում են անհատական կարգավորումները պահելու համար:
  (կետը տվյալ դեպքում ֆայլի անվանման մասն է)


Օրինակներ.

`./a`        նույնն է ինչ   `a`

> ՈՉ ՄԻՇՏ՝ քանի որ հրամանների /ոչ թե սովորական ֆայլերի/ դեպքում գոյություն ունի `$PATH` փոփոխականը, որը որոշում է թե որտեղ է փնտրվելու հրամանը 

```bash
echo $PATH
```

<br><br>

`../home/student`  մեկ մակարդակ վերև և home/student

`.`-ով սկսվող ֆայլերի օրինակ `~/.bash_history` - նախորդ հրամանները պահվում են այստեղ:

```bash
ls -la ~/.bash_history
```

Կան նաև այլ նման ֆայլեր

```bash
ls -la ~/.bash*
```

<hr>

> Հիմնական հրամաններ
* `touch`                    Ստեղծել դատարկ ֆայլ
* `cp <fromfile> <tofile>`   	Պատճենել ֆայլը
* `mv <fromfile> <tofile>`	Տեղափոխել / վերանվանել ֆայլը
* `rm <file>`  			Հեռացնել ֆայլ/դիրեկտորիա
* `mkdir <newdir>`		 Ստեղծել դիրեկտորիա 
* `alias <alias> <command>` Ստեղծել հրամանի կրճատում 

> Հրամանների օրինակներ

```bash 
cd /home ; pwd ; ls -la
```

```bash 
cd ; ls -la /home
```

```bash 
mkdir d1 ; cd d1 ; pwd ; touch f1 ; ls f*
```

```bash 
cp f1 f2 ; ls f*
```

```bash 
mv f2 f3 ; ls f*
```

```bash 
alias del="rm -i" ;\
alias

```

Հետևյալ կերպ մենք պահպանում ենք `alias`-ը, որպեսզի այն աշխատի նաև հաջորդ մուտքագրումից հետո

```bash
echo 'alias del="rm -i"' >> ~/.bash_aliases

```

```bash 
del f*
```

```bash 
cd ~ ; rm -r d1
```

<hr>

```bash 
cp -r /etc ~
```

```bash 
mkdir ~/TEST
```

```bash 
mv  ~/etc  ~/TEST
```

```bash 
rm -r ~/TEST
```

#### PRACTICE

* `clear` հրամանը մաքրում է էկրանը
  * ստեղծել `c` անունով `alias`, որ մաքրում է էկրանը
  * պահպանել `alias`-ը, որ այն գործի մյուս մուտքագրվելիս նույնպես

* ստեղծել երկու հրամանից բաղկացած `goup` անունով `alias`, որը
  * կտեղափոխի վերեվի դիրեկտորիա 
  * և կտպի ներկայիս գտնվելու վայրը 
  * պահպանել `alias`-ը, որ այն գործի մյուս մուտքագրվելիս նույնպես


### Variables

Փոփոխականներ

Shell/Bash փոփոխականները - ժամանակավորապես պահպանում են տեղեկատվությունը

Bash-ը փոփոխականների տեսակներ չունի։

Փոփոխականները կարող են պահել տոեքստ (string) կամ ամբողջ թվեր (integer).

Փոփոխականների անունները պայմանականորեն ՄԵԾԱՏԱՐ են, բայց կարող են օգտագործվել նաև փոքրատառեր և այլ նշաններ:

Կառուցվածք - **VARNAME=VALUE**

> 
> ✅ ԿԱՐԵՎՈՐ է <br>
> Փոփոխականի **անունը** (**VARNAME**) և **արժեքը** (**VALUE**) պետք է կպած լինեն `=` նշանին: <br>
> Այսինքն `=` նշանի կողքերը չպետք է լինեն բացատներ (space):


Օրինակ.

Նշանակենք `LIST` փոփոխականին `/usr/bin` արժեքը

Փոփոխականի դեմը գրելով `$` ստանում ենք դրա արժեքը

```bash
LIST="/usr/bin/" ; ls -l $LIST
```

<br><br>

### File Permissions


<pre>
- rwx r-x r--  1 student student   size date filename
│└─┬─┴─┬─┴─┬─┘     │        │        
│  │   │   │       │        └── Group
│  │   │   │       └─── Owner
│  │   │   └── Others (r--) - թույլտվություններ մյուսների համար  
│  │   └── Group (r-x) - թույլտվություններ խմբի անդամների համար
│  └── Owner (rwx) - թույլտվություններ տիրոջ համար
└── Ֆայլի տեսակը
</pre>

- **Ֆայլի տեսակներ.** <br>
  **-** 	ֆայլ <br>
  **d** 	դիրեկտորիա <br> 
  **l** 	սիմվոլիկ հղում (shortcut) <br>

<br><br>
<img src=https://github.com/trainart/linux1/blob/main/img/permissions2.png  width=70% height=70% >
<br><br>
<img src=https://github.com/trainart/linux1/blob/main/img/permissions3.png  width=70% height=70% >
<br><br>
<img src=https://github.com/trainart/linux1/blob/main/img/permissions4.png  width=70% height=70% >
<br><br>
<img src=https://github.com/trainart/linux1/blob/main/img/chmod.png  width=70% height=70% >
<br><br>

> ✅ ԿԱՐԵՎՈՐ է<br>
> Որևէ ֆայլը **հասանելի է** եթե բոլոր դիրեկտորիաները, որոնց մեջ նա հաջորդաբար գտնվում է ունեն **x** թույլտվությունը:

<br>

> ✅ ԿԱՐԵՎՈՐ է<br>
> Որևէ ֆայլը **փոփոխելու համար** բավական է ունենալ այդ ֆայլի **w** թույլտվությունը:<br>
> Կարիք չկա, որ բոլոր դիրեկտորիաները, 
> որոնց մեջ նա հաջորդաբար գտնվում է ունեն **w** թույլտվությունը: 



#### PRACTICE

Create file `f1.txt`

Set permissions to `rw-r-----` using octal notation

Check: `stat -c "%a %n" file2` should show "640"

<hr>

### Midnight Commander (mc) - visual file manager

* Տեղադրում

```bash
yum -y install mc
```

կամ

```bash
dnf -y install mc
```

#### PRACTICE
> ❓ ՀԱՐՑ.
> Դեպի ուր է հղում `dnf` և `yum`: Նույն ֆա՞յլն է

<br><br>

* Հիմնական հրամաններ
  - **TAB** - Փոխել վահանակները (ձախ/աջ)  
  - **Esc + Enter** - Ֆայլի անունը գրել ներքևի հրամանների տողում  
  - **Esc + A** - Ֆայլի ճանապարհը գրել ներքևի հրամանների տողում
  - **Esc + H** - Հրամանների պատմություն (տարբերվում է Bash-ի պատմությունից)
  - **Esc + P** - Նախորդ հրաման  
  - **Ctrl + O** - Ցույց տալ/թաքցնել տերմինալը  
  - **F10** կամ **Esc + O** - ելք mc-ից  

* Վերևի մենյու - ֆայլի գործողություններ
  - **Esc + 9 → File → Chmod** - Փոխել ֆայլի թույլտվությունները  
  - **Esc + 9 → File → Advanced Chown** - տիրոջ/խումբը  


<hr>

### Umask

<img src=https://github.com/trainart/linux1/blob/main/img/umask.png  width=70% height=70% >


#### PRACTICE

> ❓ ՀԱՐՑ. umask-ի որ արժեքի դեպքում նորաստեղծ դիրեկտորիան կունենա `rwx --x --x`  իրավունքները:

* Փոփոխեք umask-ը և ստեղծեք մի քանի ֆայլեր և դիրեկտորիաներ

<hr>

### Additional Attributes

Լրացուցիչ Ատրիբուտներ

* Sticky bit (`t`)  
  * ֆայլեր - հնացած է 
  * դիրեկտորիաներ - յուրաքանչյուրը իրավունք ունի ջնջել և փոփոխել միայն իր ֆայլերը
    (հիմնականում օգտագործվում է `/tmp`-ի նման դիրեկտորիաների դեպքում)

* SUID (`s` in `u` category)
  * ֆայլեր - սահմանել UID (EUID), ըստ ֆայլի տիրոջ 
  * դիրեկտորիաներ - ժառանգել նորաստեղծ ֆայլի UID ըստ տվյալ դիրեկտորիայի տիրոջ

* SGID (`s` in `g` category)
  * ֆայլեր - սահմանել GID (EGID), ըստ ֆայլի խմնբի 
  * դիրեկտորիանե - ժառանգել նորաստեղծ ֆայլի GID ըստ տվյալ դիրեկտորիայի խմնբի

<hr>

## Links (Hard,Symbolic/Soft)

Հղումները (links) թույլ են տալիս ֆայլերի և դիրեկտորիաների համար մեկից ավելի անուն ունենալ:

Ֆայլային համակարգի տարբեր վայրերում կարելի է ներկայացնել նույն ֆայլը կամ դիրեկտորիան առանց տվյալները պատճենելու: 

* Հղումները լինում են 2 տեսակի 
  
  * Symbolic/Soft link (Shortcut)
    * կարող է ստեղծվել դիրեկտորիաների համար
    * կարող է գործել մեկ partition-ից մյուս partition
    * սիմվոլիկ հղումը ջնջելիս օրիգինալ ֆայլը պահպանվում է
    * օրիգինալ ֆայլը ջնջելիս սիմվոլիկ հղումը պահպանվում է
  
  * ~~Hardlink~~ 
      * խուսափեք օգտագործել, բայց իմացեք դրանց մասին, քանի որ Լինուքսի ֆայլային համակարգի դիրեկտորիաների կառուցվածքը հիմնված է դրա վրա
    
  
Հղումները ստեղծվում են **ln** հրամանով

**`ln [options] <original> [<link>]`**

### Symbolic/Soft link (Shortcut)

Սիմվոլիկ հղումը ստեղծվում է, եթե առկա է `-s` ընտրանքը 

**`ln -s <original> [<link>]`**


Սիմվոլիկ հղումը հղումների հիմնական օգտագործվող ձևն է: Այն ակտիվորեն օգտագործվում է հենց Լինուկս համակարգում:

Օրինակներ.

```bash
ls -l /etc/alternatives
```

```bash
ls -l /etc/ssl
```

<hr>

#### Example: relative path symlink
* Օրինակ. ՀԱՐԱԲԵՐԱԿԱՆ ճանապարհով հղում

Ստեղծեք `~/linkdemo` դիրեկտորիա և դրանում `origfile` ֆայլ 

```bash
mkdir -p ~/linkdemo && cd ~/linkdemo
echo "Original file for soft link with RELATIVE path"  > origfile
```

Ստեղծեք symlink հղում ՀԱՐԱԲԵՐԱԿԱՆ ճանախարհով
```bash
ln -s origfile link_rel
```

Ստուգեք, որ գործում է, դիտելով պարունակությունը
```bash
cat link_rel
```

Տեղափոխեք հղումը
```bash
mkdir /tmp/other_link_dir
mv link_rel /tmp/other_link_dir/
```

Ստուգեք, արդյո՞ք գործում է

```bash
cat  /tmp/other_link_dir/link_rel  
```

```bash
ls -la  /tmp/other_link_dir/link_rel 
```

> ❓ ՀԱՐՑ. Ինչո՞ւ չի գործում:

<hr>

#### Example: absolute path symlink
* Օրինակ. ԱՄԲՈՂՋԱԿԱՆ ճանապարհով հղում

Ստեղծեք `origfile2` ֆայլ 

```bash
echo "Original file for soft link with ABSOLUTE path" > ~/linkdemo/origfile2
```

Ստեղծեք symlink հղում ԱՄԲՈՂՋԱԿԱՆ ճանախարհով
```bash
cd ~/linkdemo
ln -s ~/linkdemo/origfile2 link_abs
```

Ստուգեք, որ գործում է, դիտելով պարունակությունը
```bash
cat link_abs
```

Տեղափոխեք հղումը
```bash
mv link_abs /tmp/other_link_dir/
```

Ստուգեք, արդյո՞ք գործում է

```bash
cat  /tmp/other_link_dir/link_abs  
```

```bash
ls -la  /tmp/other_link_dir/link*  
```

> ❓ ՀԱՐՑ. Ինչո՞ւ է գործում:

<hr>

#### Example: Original file move
* Օրինակ. Օրիգինալ ֆայլի տեղափոխում

Սակայն եթե տեղափոխեք կամ վերանվանենք օրիգինալ ֆայլը, հղումը այլևս չի գորցի

```bash
mv ~/linkdemo/origfile2 ~ 
```

```bash
ls -la  /tmp/other_link_dir/link*  
```

> ❓ ՀԱՐՑ. Ինչո՞ւ այլևս չի գործում:

<hr>

#### Example: Directory symlink
* Օրինակ. Սիմվոլիկ հղում դիրեկտորիաների համար

```bash
ln -s ~/linkdemo ~/symlink2linkdemo
```

```bash
ls -l ~/symlink2linkdemo
```


✅ ՀԱՐԱԲԵՐԱԿԱՆ ճանապարհով սիմվոլիկ հղումները ավելի կարճ են և փոխադրելի, բայց չեն գորցի, եթե հղումը տեղափոխվի։

✅ ԱՄԲՈՂՋԱԿԱՆ ճանապարհով սիմվոլիկ հղումմները միշտ գործում են, քանի դեռ օրիգիինալ ֆայլը մնում է տեղում:

<hr>

### ~~Hardlink~~ 

Hardlink-երը ստեղծվում են նույն `ln` հրամանով, սակայն ցանկալի է խուսափել դրանց օգտագորցումից:

#### ~~Hardlink~~ limitations

Hardlink-երի սահմանափակումները

Hardlink-երը ունեն մի քանի կարևոր սահմանափակումներ, որոնք դրանք դարձնում են պակաս ճկուն՝ սիմվոլիկ հղումմների (symlink-երի) հետ համեմատած.

* Չեն աշխատում տարբեր ֆայլային համակարգերի միջև (մեկ partition-ից մյուս partition)
  * Hardlink-երը կարող են միայն ցույց տալ նույն ֆայլային համակարգում գտնվող ֆայլերին (inode-ի միջոցով):
      Օրինակ, եթե `/home/student/dir1/file1`-ը և `/tmp/dir2/file2`-ը տարբեր partition-ում են, հնարավոր չէ hardlink ստեղծել դրանց միջև:

* Չեն աշխատում դիրեկտորիաների համար 
  * Միայն ֆայլերին կարելի է hardlink ստեղծել, ոչ թե դիրեկտորիաներին 
  (բացառություն `.` և `..`, որոնք արդեն hardlink-եր են, քանի որ Լինուքսի ֆայլային համակարգի դիրեկտորիաների կառուցվածքի կապը հիմնված է դրա վրա):

* Շփոթեցնող է 
  * Քանի որ hardlink-ը նոր անուն է ստեղծում այդ (տվյալ inode-ի տակ պահված) տվյալների համար, 
  եթե մի քանի անուն /hardlink/ ունեցող ֆայլը ջնջվի սկզբում ստեղծված անունով, 
  ապա այն կշարունակի պահել տվյալները մյուս անվան /անունների/ տակ։ 
  Սա կարող է հանգեցնել խառնաշփոթի:

#### ~~Hardlink~~ examples

* Օրինակներ. 

`ls` հևամանի  `-i` ընտրանքը ցույց է տալիս ֆահլի կամ դիրեկտորիայի inode-ը, այսինքն ID-համարը, որով այն գրանցվել է տվյալ partition-ում:


```bash
echo "Hello, World!" > hltest-1.txt

```

```bash
ln hltest-1.txt hltest-2.txt

```

```bash
ls -i hltest-*

```


```bash
ls -li hltest-*

```


```bash
rm hltest-1.txt
ls -li hltest-*

```


```bash
ln hltest-2.txt hltest-3.txt
ls -li hltest-*

```

#### ~~Hardlink~~ for directories

Լինուքսի ֆայլային համակարգի դիրեկտորիաների կառուցվածքի կապը հիմնված է hardlink-երի վրա
Ամեն մի դիրեկտորիայում կա `.` և `..` անուն: 

```bash
mkdir -p ~/hl_dirtest/hl_subdir
ls -lai ~/hl_dirtest
ls -lai ~/hl_dirtest/hl_subdir
```

Նկատեք, որ թվերն են համընկնում:

> ❓ ՀԱՐՑ. Քանի՞ անուն ունի ցանկացած նորաստեղծ դիրեկտորիան

```bash
ls -laid /usr/lib
```

> ❓ ՀԱՐՑ. Ի՞նչ է ասում այս դիրեկտորիայի անունների քանակը


### Symlink vs ~~Hardlink~~ 

* Եզրակացություն
  * Symlink → Միշտ փորձել օգտագործել այս տարբերակը, եթե պահանջվում է ստեղծել **հղում** ֆայլին կամ դիրեկտորիային, քանի որ այս մեթոդը ճկուն է և ապահով:
  * ~~Hardlink~~ → Չօգտագործել


  


## Access to files (view,parse)

Տեքստային ֆայլերը մեծ դեր ունեն Լինուքսում: Դրանք հանդիպում են բազմաթիվ վայրերում, 
և անհրաժեշտ է կարողանալ դիտել և մշակել դրանք։

Տեքստային ֆայլերի պարունակությունը դիտելու համար կան մի քանի գործիքներ։

<hr>

### less
> **less** - view/browse text file page-by-page

* **Enter/DOWNARROW**	– մեկ տող ներքև
* **SPACE/PgDn**		– մեկ էկրան ներքև
* **PgUp/b**			– մեկ էկրան վերև
* **UPARROW**			– մեկ տող վերև
* **/**					– որոնում
* **Home**				– անցնել տեքստի սկիզբը
* **End**				– անցնել տեքստի վերջը
* **q**					– ելք

> Օրինակներ
 
```bash
less /etc/services
```

```bash
ls /usr/bin | sort -r | less
```

<hr>

### cat

> **cat** - output whole file to STDOUT (default - terminal)

> Օրինակներ

```bash
cat /etc/services
```

```bash
cat /etc/services | sort -r
```

```bash
cat /etc/services | sort -r | less
```

<hr>

### head

> **head** - output some first lines (default 10) of file STDOUT (default - terminal)

> Օրինակներ
 
```bash
head /etc/services
```

```bash
head -1 /etc/services
```

```bash
head -1 /etc/services > /tmp/h1
```

```bash
head -1 /etc/services >> /tmp/h1
```
 
<hr>

### tail

> **tail** - output some last lines (default 10) of file STDOUT (default - terminal)

> Օրինակներ
 
```bash
tail /etc/services
```

```bash
tail -1 /etc/services
```

```bash
tail -1 /etc/services > /tmp/s1
```

```bash
tail -1 /etc/services >> /tmp/s1
```

<hr>

### grep - filter lines based on pattern

> **grep** - Ֆիլտրել նմուշին համապատասխանող տողերը - **հորիզոնական** ֆիլտրում

> Օրինակներ
 
```bash
cat /etc/services | grep http
```

```bash
ls /usr/bin | grep log
```

Նախորդ հրամանների պատմության մեջ որոնում

```bash
history | grep ls
```


#### Regular expressions 

* **^**	- beginning of the line
* **$**	- end of the line
* **.**	- any single symbol
* \* - repetition of previous wildcard 0 or more times. 
    Thus **.*** expression means - "any amount of any symbols"
* \	- treat next symbol as a literal character. 
  * \\$ means $ (dollar sign)
  * \\\\$ means \ (backslash) at the end of line


Հրամանի կատարման արդյունքի ֆիլտրում

```bash
ls /usr/bin | grep ^log
```

```bash
ls /usr/bin | grep log$
```

```bash
ls /usr/sbin | grep ^a.*s$
```

Ֆայլի միջից տողերի ֆիլտրում

```bash
cat /etc/services | grep ^http.*80
```

```bash
cat /etc/passwd | grep -E ^'(b|sy)' 
```


<hr>

### wc

> **wc** - count number of **lines**, words, characters 

> Օրինակներ
 
```bash
wc -l /etc/passwd
```

```bash
wc  -l < /etc/group
```

> **cut** - extract sections/fields from each line (of files)

-f  field number

-d  delimiter symbol

Օրինակ

Select 1-st and 3-rd fields from /etc/passwd  separated by “:”

```bash
cut -f1,3 -d":" /etc/passwd
```

<hr>

## I/O Redirection

Linux I/O Redirection


* Normal I/O
<pre>
┌──────────┐       ┌──────────┐  STDOUT   ┌──────────┐
│          │ STDIN │          │  ---->  > │  Screen  │
│ Keyboard │ ----> │  Process │  ----> 2> │          │
│          │       │          │  STDERR   └──────────┘
└──────────┘       └──────────┘    
</pre>

- STDIN (FD0)  — input from keyboard  (`<`)
- STDOUT (FD1) — normal output  (`>` `>>`)
  - `>`  - Creates or **OVERWRITES** file
  - `>>` - Creates or **APPENDS** to file
- STDERR (FD2) — error messages (`2>` `2>>`)
  - `2>`  - Creates or **OVERWRITES** file
  - `2>>` - Creates or **APPENDS** to file


* Redirect Only Standard Output (`>`)

<pre>
┌──────────┐       ┌─────────┐           ┌────────┐
│          │ STDIN │         │ STDERR 2> │ Screen │
│ Keyboard │ ----> │ Process │ ---->     │        │
│          │       │         │           └────────┘
└──────────┘       └─────────┘           ┌────────┐
                    └── STDOUT ---->   > │  FILE  │
                                         └────────┘
</pre>

Օրինակներ.

```bash
ls /a /home > ~/stdout
cat ~/stdout
```


```bash
echo "Hi" > ~/stdout
echo "Hi again" > ~/stdout
echo "Hi again and again" > ~/stdout
cat ~/stdout
```

```bash
echo "Hi" >> ~/stdout2
echo "Hi again" >> ~/stdout2
echo "Hi again and again" >> ~/stdout2
cat ~/stdout2
```


* Redirect Only Standard Error (`2>`)

<pre>
┌──────────┐       ┌─────────┐          ┌────────┐
│          │ STDIN │         │ STDOUT > │ Screen │
│ Keyboard │ ----> │ Process │ ---->    │        │
│          │       │         │          └────────┘
└──────────┘       └─────────┘          ┌────────┐
                    └── STDERR ----> 2> │  FILE  │
                                        └────────┘
</pre>

Օրինակներ.

```bash
ls /e > ~/stdout
cat ~/stdout
```

```bash
ls /a > ~/stdout 2> ~/stderr
ls /b > ~/stdout 2> ~/stderr
ls /c > ~/stdout 2> ~/stderr
```

```bash
cat ~/stdout
```

```bash
cat ~/stderr
```

> ❓ ՀԱՐՑ. Ի՞նչ կա **~/stdout** և **~/stderr** ֆայլերում և ինչու


```bash
ls /a > ~/stdout 2>> ~/stderr
ls /b > ~/stdout 2>> ~/stderr
ls /c > ~/stdout 2>> ~/stderr
```

```bash
cat ~/stdout
```

```bash
cat ~/stderr
```

> ❓ ՀԱՐՑ. Ի՞նչ կա **~/stdout** և **~/stderr** ֆայլերում և ինչու


<br><br>
**/dev/null** - "black hole" (դեն է նետում իրեն ուղարկված ամեն ինչ)


```bash
ls /e > ~/stdout 2> /dev/null
cat ~/stdout
```


* Redirect Both Standard Output and Error Together (`&>`)

<pre>
┌──────────┐       ┌─────────┐        ┌────────┐
│          │ STDIN │         │        │        │
│ Keyboard │ ----> │ Process │        │        │
│          │       │         │        └────────┘
└──────────┘       └─────────┘        ┌────────┐
                    └─ STDOUT ---> &> │  FILE  │
                    └─ STDERR --->    └────────┘ 
</pre>


Օրինակներ.

```bash
ls /home /ho &> ~/stdall
cat ~/stdall
```

```bash
ls /home /ho &> /dev/null 
```

### PRACTICE

* Գրեք հրամանների հերթականության, որի արդյունքում `/etc/group` ֆայլի տողերի քանակը կգրվի `~/grpln` ֆայլի մեջ:
Ֆայլում պետք է լինի ՄԻԱՅՆ տողերի քանակի թիվը:

* Հետևյալ հրամանով ստեղծել `~/largefile` ֆայլը
```bash
seq 1 10000 > ~/largefile
```
* `~/largefile` ֆայլի համար ցուցադրել էկրանին
  * միայն **առաջին 8** տողերը
  * միայն **վերջին 5** տողերը
  * միայն այն տողերը, որոնց մեջ կա **777** թիվը
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
      * ՀՈՒՇՈՒՄ grep-ը ունի հատուկ option դրա համար, բայց կարելի է նաև լրացուցիչ հրաման օգտագործել 
  * միայն այն տողերը, որոնց մեջ կա **77** թիվը հենց **տողի սկզբում**
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնց մեջ կա **77** թիվը **տողի վերջում**
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնց **տողի սկզբում** կա **33** թիվը, իսկ տողի **վերջում 9** թիվը 
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * **վերևից 7-րդ** տողը
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 

* Հետևյալ հրամանով ստեղծել `~/shakespeare` ֆայլը
```bash
yes $'To be\nor not\nto be\nthat is the\nquestion\n' | head -30 > shakespeare
```
* `~/shakespeare` ֆայլի համար ցուցադրել էկրանին
  * միայն այն տողերը, որոնք սկսվում են `t` տառով
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնք սկսվում են `t` կամ `T` տառով
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնք ավարտվում են `e` տառով
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնք ավարտվում են `be` տառերով
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 
  * միայն այն տողերը, որոնք սկսվում են `t` կամ `T` տառով և ավարտվում են `e` տառով
    * փոփոխել/լրացնել հրամանը, այնպես որ այդ տողերի փոխարեն, ստանանք դրանց քանակը 


### STDIN

STDIN - Standard input 		  < 

```bash
sort -r < ~/stdout
```

```bash
sort -r < ~/stdout > ~/stdouts
```

```bash
wc -l < /etc/services
```


<hr>

## Pipes

Pipeline - Մեկ հրամանի STDOUT-ը ուղարկել այլ հրամանի STDIN-ին

<pre>
┌──────────────────────────┬───────────────────────────┐
│        PIPE    |         │     REDIRECTION    >      │
├──────────────────────────┼───────────────────────────┤
│        Connects          │         Connects          │
│    commands/processes    │  command/process to file  │
│   ┌──────┐    ┌──────┐   │     ┌──────┐              │
│   │Proc.1├--->│Proc.2│   │     │Proc.1├---> FILE     │
│   └──────┘    └──────┘   │     └──────┘              │
│                          │                           │
│    STDOUT ---> STDIN     │      STDOUT ---> FILE     │
└──────────────────────────┴───────────────────────────┘
</pre>

<br><br>

<pre>
┌──────┐              ┌──────┐              ┌──────┐         ┌────────┐
│Proc.1│STDOUT-->STDIN│Proc.2│STDOUT-->STDIN│Proc.3│STDOUT-->│        │
└───┬──┘              └──┬───┘              └──┬───┘         │        │
    │                    │                     └STDERR------>│ Screen │    
    │                    └STDERR---------------------------->│        │ 
    └STDERR------------------------------------------------->│        │
                                                             └────────┘
</pre>

<br><br>

> Օրինակ

```bash
ls /usr/bin | sort -r | wc -l
```
Նույնը չէ, ինչ հաջորդաբար կատարումը `;`-ով

```bash
ls /usr/bin ; sort -r ; wc -l
```

<br><br>
## Հրամանների համակցում

Հրամանները կարելի է համակցել հետևյալ կերպ՝

* `;` ➡️Պարզապես կատարել հրամանները՝ մեկը մյուսի հետևից

* `|`	➡️Փոխանցել առաջին հրամանի ելքի տվյալները (STDOUT) 
    երկրորդ հրամանի մուտքին (STDIN)

* `&&` ➡️	Logical AND 
    եթե առաջին հրամանի ելքի կոդը (exit code) 0 է, կատարել երկրորդը

* `||` ➡️	Logical OR
    եթե առաջին հրամանի ելքի կոդը (exit code) 0 չէ, կատարել երկրորդը

_( `echo $?`  - ցույց է տալիս վերջին հրամանի ելքի կոդը (exit code) 0=OK)_


> Օրինակներ

* `cd /home && pwd`
* `cd /hh && pwd`
  * ❓ ՀԱՐՑ. ինչպե՞ս ազատվել `cd: /hh: No such file or directory` հաղորդագրությունից
* `cd /home || echo "Wrong directory"`
  * փոխեք `/home`-ը `/hh`-ով և նորից աշխատացրեք
* ```bash
  DD=/bin ; [ -d $DD ] ; echo "Exit code is: $?"
  ```
* ```bash
  DD=/bn ; [ -d $DD ] ; echo "Exit code is: $?"
  ```
  

<hr>

## Text Editors (խմբագրիչներ)

* **nano**		Standard Linux editor - նորեկների համար - առկա է Linux-ի տարբերակների մեծ մասում
* **vi /vim**	Standard UNIX editor - փորձառու օգտատերերի համար - առկա է UNIX/Linux տարբերակների մեծ մասում

Կան նաև այլ խմբագրիչներ, օրինակ - **mcedit** կամ **joe**<br>
բայց դրանք հիմնականում ի սկզբանե տեղադրված չեն լինում

<hr>

### Nano editor basics

`nano` հեշտ օգտագործվող տեքստային խմբագրիչ է Linux օպերացիոն համակարգերի համար:

Այն ներառում է տեքստային խմբագրիչի բոլոր հիմնական գործառույթները։

Հիմնական հրամանները ցուցադրվում են տակի հատվածում։

Հրամանների մեծ մասը սկսվում է `^`-ով, ինչը նշանակում է `Ctrl`<br> 
*  `^G` նշանակում է `Ctrl`+`g`  (ոչ մեծատառ `G`)

<hr>

### Vi (Visual Editor) / Vim (Vi IMproved)

`vim`/`vi` շատ հզոր UNIX/Linux տեքստային խմբագրիչ է։

`vi` հիմունքներն իմանալու նպատակն այն է, որ այն հիմնականում առկա է գրեթե ցանկացած UNIX/Linux համակարգում:

Նույնիսկ եթե որևէ այլ խմբագրիչ առկա չէ, Vi/Vim-ը առկա կլինի, որ դրանով ֆայլեր խմբագրեք:

Այսօր հիմնականում `vi` հղում է դեպի `vim`

#### PRACTICE

> ❓ ՀԱՐՑ.
> Դեպի ուր է հղում `vi` և `vim`: Նույն ֆա՞յլն է

#### Vim modes

Vim ռեժիմներ

* **Command**	- Սկզբնական ռեժիմ 
  * **i**  - անցում դեպի խմբագրման հիմնական ռեժիմ (Insert/Input)
  * **ZZ** - ելք, պահպանելով փոփոխությունները
  * **u**  - չեղարկել վերջին խմբագրումը

* **Insert/Input**	- Խմբագրման հիմնական ռեժիմ 
  * տեքստի խմբագրում

* **Execute**	- Հրամանների ռեժիմ (հիմնականում ելքի համար)
  * **:wq**  - պահպանել փոփոխությունները և դուրս գալ  (փոխարենը օգտագործեք ZZ)
  * **:q!**  - դուրս գալ առանց պահպանելու
  
<pre>
  ZZ - պահպանել փոփոխությունները        u - չեղարկել վերջին խմբագրումը
       և դուրս գալ             
                         [Command Mode]   
                         ↙ ↗  Esc  ↖ ↘  
                       ↙ ↗            ↖ ↘  
                 i  ↙ ↗                 ↖ ↘  : 
         [Insert/Input Mode]         [Execute Mode]   
                                     :wq  - պահպանել և դուրս գալ  (փոխարենը օգտագործեք ZZ)
                                     :q!  - դուրս գալ առանց պահպանելու
</pre>

>  ✅ ԿԱՐԵՎՈՐ Է<br> 
> Եթե շփոթվեք, թե որ ռեժիմում եք գտնվում, պարզապես **մի քանի անգամ սեղմեք `ESC`** <br>
> Այդպես վստահ կլինեք, որ սկզբնական **Command** ռեժիմում եք

<br><br>

#### PRACTICE

* Ստեղծեք նոր `testfile1` ֆայլ `vi` խմբագրիչի օգնությամբ 
  * մուտքագրեք որոշ տեքստ ֆայլում
  * պահպանեք և դուրս եկեք

* Կրկին բացեք այդ ֆայլը
  * ավելացրեք որոշ տեքստ
  * պահպանեք և դուրս եկեք

* Կրկին բացեք այդ ֆայլը 
  * ջնջեք որոշ տեքստ
  * չեղարկեք վերջին խմբագրումը
  * պահպանեք և դուրս եկեք


<hr>

## SU - Switch Users

**su** - Switch user accounts (change UID). 

su հրամանը թույլ է տալիս օգտագործողին մուտք գործել որպես այլ օգտագործող (օրինակ՝ **root**), մուտքագրելով **տվյալ օգտագործողի** գաղտնաբառը:
Քանի որ ադրդյունքում ստեղծվում է նոր ենթա-սեսիա, աավարտելիս պետք է հավաքել `exit`, նախորդ սեսիային վերադառնալու համար:

**su - [ <username> ]** 

> Նկատի ունենեցեք՝ **root**-ը որևէ գաղտնաբառ մուտքագրելու կարիք չունի, մեկ այլ օգտագործեղի անունից աշխատելու համար: 

Օրինակներ

```bash
id
su -
id 
```

## SUDO - Run single command as another user

**sudo** - Run single command as another user. 

sudo հրամանը թույլ է տալիս օգտագործողին root-ի «անունից» կոնկրետ հրաման կատարել մուտքագրելով **իր գաղտնաբառը**:
(օգտագործողին դա նախապես պետք է թայլատրված լինի)

Կարելի է որպես հրաման նշելով `su -`, դառնալ root մուտքագրելով ոչ թե root գաղտնաբառը, այլ ձեր սեփական գաղտնաբառը:
Քանի որ այս դեպքում էլ ստեղծվում է նոր ենթա-սեսիա, աավարտելիս պետք է հավաքել `exit`, նախորդ սեսիային վերադառնալու համար:

```bash
sudo su -  
```

Օրինակներ
```bash
id
sudo su -
id 
```

Կարելի է կատարել նաև առանձին հրաման

```bash
sudo id
```


## Chown

* chown թույլ է տալիս ադմինիստրատորին փոխել ֆայլի տիրոջը (և խումբը) (**CHange OWNer**)

`chown [options] username[:groupname] file/foldername`

```bash
touch file4root
sudo chown -R root:root file4root
```

```bash
mkdir dir4root
touch dir4root/file4root2
touch dir4root/file4root3
sudo chown -R root:root dir4root
ls -l dir4root
```


* chgrp թույլ է տալիս ադմինիստրատորին փոխել ֆայլի խումբը (**CHange GRouP**)

`chgrp [options] groupname file/foldername`

```bash
touch file_for_rootgrp
sudo chgrp root file_for_rootgrp
```

> Հիմնականում այս հրամանի կարիքը չի լինում, քանի որ շատ հազվադեպ է պատահում, 
> որ կարիք լինի փոխել միայն խումբը։ 
> Հիմնակաում պետք է լինում փոխել և տիրոջը և խումբը միասին, ինչն էլ անում է `chown`-ը 


