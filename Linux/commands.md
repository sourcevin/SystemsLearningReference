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

### rights

* `chmod +x test.sh`  add rights to execute the file

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
*

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











