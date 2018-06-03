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


permissions
* drwxr-xr-x+ 
            d = directory
            r = read permission
            w = write permission
            x = execute permission
            - = no permission
* user types
            u - Owner
            g - Group
            o - Others
            a - All users
* 







