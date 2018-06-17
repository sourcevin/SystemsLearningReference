## Reference commands:


### bash history

Use shortcuts for bash history

* `!v`  last command starting with v
* `!$`   last argument
* `!?example` search reverse for example text
* `ctrl + r`  reverse search
* `history`   prints history
* `!30`  execute 30th command in history
* `~/.bash` location of history



### consoles

physical consoles and pseudo consoles

ssh port 22 .  created by Tatu Ylolen

* `ctrl + alt + [f1-f6]`  for consoles
* `tty`   for current terminal
* `who` for all users
* `exit` or `logout` or `ctrl + D`
*  `/dev/pts/x`  limit concurrent logon 
* `/etc/shells` for all shells
* `sudo apt-get install zsh` for installing zsh shell
* `chsh -s /usr/bin/zsh`  for switching shell

### others

* `pwd` print working directory
* `du -sh`  disk usage -s summary -h human readable
* `file file1.txt` to get the type of file


### Text Files

commands cat head tail cat less sort

* `cat file1 file2`   concatenate command reads and prints file
* `tac file1`  reverse reading of file
* `head -n 10 filename`  read 10 lines from top
* `tail -n 10 filename` read 10 lines from bottom
* `tail -f filename`   -f for follow
* `less filename`  open and navigate the file (/search, 16G go to line 16)
* `cut -f1,3 -d ":" filename`  -f is for field, 1 and 3 for columns , -d for delimiter 
* `sort -r filename` -r is for reverse
* `sort -k4 -t "," filename` -k for column and -t for delimiter

file movements . cp rsync tar mv rm ls 

* `cp -i filename1 filename2` copy file , -i interactive ask for overwrite , -f force copy, 
* `cp -R folder folder` -R Recursive copy including hidden files
* `mv filename1 filename2` move file
* `ls -R files/` recursive listing of all files
* `ls -lh file1` human readable format
* `rm file`  remove file 
* `rmdir folder` remove directory
* `rm -rf folder` -r is for recursive and -f is for force
* `ls -l -t -r` -l for long listing -t for timestamp reverse
* `ls -F` -F for file type


### permissions  https://www.guru99.com/file-permissions.html
* `drwxr-xr-x+`   <br>
            d = directory
            r = read permission
            w = write permission
            x = execute permission
            - = no permission
* user types  <br>
            u - Owner  <br>
            g - Group  <br>
            o - Others  <br>
            a - All users  <br>
* r=4 w=2 x=1
* `chmod a+rwx file1`  add permissions to all users
* `chmod a-rwx file2` remove permissions from all users
* `chmod a=rwx file1` set file permissions to all users
* `chmod 740 file1` set file permission 
* `chown user:group file1` change owner and group of the file
* `chown --reference=file1 file2` copy file permissions

```
The setuid/setguid permissions are used to tell the system to run an executable as the owner with the owner\'s permissions.
Be careful using setuid/setgid bits in permissions. If you incorrectly assign permissions to a file owned by root with the setuid/setgid bit set, then you can open your system to intrusion.
You can only assign the setuid/setgid bit by explicitly defining permissions. The character for the setuid/setguid bit is s.
So do set the setuid/setguid bit on file2.sh you would issue the command chmod g+s file2.sh.
```

```
The sticky bit can be very useful in shared environment because when it has been assigned to the permissions on a directory it sets it so only file owner can rename or delete the said file.
You can only assign the sticky bit by explicitly defining permissions. The character for the sticky bit is t.
To set the sticky bit on a directory named dir1 you would issue the command chmod +t dir1.
```



### creating backups

* `tar -cvf etc.tar /etc`  -c create , -v verbose, -f name of file 
* `tar -cvzf etc.tar.gz /etc` -z for zip
* `tar -xvzf etc.tar.gz` -x for expand

### find command

* `find . -name file1` find this directory for file1
* `find /etc/ -name *.conf` searching for files with conf extn
* `find /etc/ -type d -name *conf` searching for directory with name conf
* `find /home/xyzuser/ -name *.doc -atime -1` accessed in last one day
* `find /etc/ -mmin +10` accessed 10 minutes ago
* `find /etc/ -type f -user xyz`  find files by user xyz

From https://www.everythingcli.org/find-exec-vs-find-xargs/

### find \;
* `find . [args] -exec [cmd] {} \;`
{} Is a placeholder for the result found by find
\; Says that for each found result, the command (in this case ‘grep’) is executed once with the found result

* `find . [args] -exec [cmd] {} \+`
{} Is a placeholder for the result found by find
\+ All result lines are concatenated and the command (in this case ‘grep’) is executed only a single time with all found results as a parameter

So in the above example ‘grep’ is executed only once and its parameter are all files found with the specified pattern.

equivalent in find | xargs
* `find . [args] -print0 | xargs -0 [cmd]`
-print0 Tells find to print all results to std, each separated with the ASCII NUL character ‘\000’
-0 Tells xargs that the input will be separated with the ASCII NUL character ‘\000’

You have to use both or neither of them. The advantage is that all results will be handed over to xargs as a single string without newline separation. NUL charater separation is a way to escape files which also contain spaces in their filenames.

All results by find are piped to xargs and you can now execute commands on them.


different in find | xargs
xargs with -n1
* `find .[args] -print0 | xargs -0 -n1 [cmd]`
-n1 Tells xarg to execute the command [cmd] with only one argument (In this case only one file found by find). This is equal to:

`find . -exec [cmd] {} \;`
So in the above example ‘grep’ is executed as many times as a file with the specified pattern has been found:

grep [...] file1
grep [...] file2
...

xargs without -n
* `find .[args] -print0 | xargs -0 [cmd]`
If no -n[int] is specified, xargs uses the default of -n5000 (see man xargs).
This means that xargs uses up to 5000 parameters for the command and executes it once, instead of 5000 times.
This is equal to:

* `find . -exec [cmd] {} +;`  
So in the above example ‘grep’ is executed only once and its parameter are all files found with the specified pattern.

grep [...] file1 file2 ... file5000
grep [...] file5001 file5002 ... 







### grep command

* `grep -i "UNix" geekfile.txt` case insensitive search for unix 
* `grep -r --include "*.txt" texthere .`  recursive search for texthere in present directory for all *.txt
* `find . -name '*bills*' -exec grep -H "put" {} +` exec grep on the search, -H for file name , {} current processing, + combines file name
* `find . -type f -exec mv {} {}.bak ";"`  
* `find . -type f | xargs grep 'test'` search for files and grep it


