# Linux Essentials (level 1) <br> Լինուքսի Հիմունքներ (փուլ 1)

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
