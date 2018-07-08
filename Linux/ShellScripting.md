### Shell Programming 

* To indicate what type of shell to use

```
#!/bin/bash          
echo Hello World 
```
* references http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-1.html

* `ls -l > ls-l.txt` stdout to file

* `grep da * 2> grep-errors.txt` stderr to file

* `grep * 2>&1` stderr to stdout

* `rm -f $(find / -name core) > /dev/null 2>&1 `  all output to null

* `history | grep testcommand` pipe commands

* `OF=/var/my-backup-$(date +%Y%m%d).tgz` command in brackets execute first

* local variable
```
#!/bin/bash
HELLO=Hello 
function hello {
        local HELLO=World
        echo $HELLO
}
echo $HELLO
hello
echo $HELLO
```
