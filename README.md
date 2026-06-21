# OVERTHEWIREBANDITCTF
This repository contains thorough solutions of "OVERTHEWIREBANDIT" levels 1-14, a popular game used to practice essential linux commands. It also showcases common mistakes and the reasons you thought for them.
Some things to know-Have practice over commands and the password section would look blank even if you are writing password.
###Level 0-1
*Goal-* TO ENTER THE GAME
*Solution-* Open your terminal and write- "ssh bandit0@bandit.labs.overthewire.org -p 2220"
That remains common for almost every level but change the number eg. bandit1@ for bandit level 1.
Password for first level is bandit0 --which leads into game
type ls - you get a file called readme
cat readme and you get your password

###Level1-2
*Goal-* To take password from a file named '-'
*Solution-* We know '-' is already used in linux.So to make computer understand we write
'cat ./-' instead of 'cat -' because in cat ./- 
cat-concatenate or open file
. means current directory and
/means located in
Also don't use this in next levels if file is not in current directory.Use cd to change directory if you wish to.
We get password

###Level2-3
*Goal-* To find password from "spaces in this filename"
*Solution-* If you would write 'cat ./spaces in this filename' linux would get confused thinking there are four files but
we know 'spaces in this filename' is a single file so we write
'cat "./spaces in this filename" to let linux know we are searching for a single file.
We get password

###Level3-4
*Goal-* To find password from hidden file in inhere directory
*Solution-* First we change directory by typing
'cd /home/bandit3/inhere' and then we type
ls -la where
ls-list the files
ls -la -list the hidden files
Once you get hidden file name
cat ./hiddenfile to get password

###Level4-5
*Goal-* To find readable file in inhere directory
*Solution-* cd to inhere and type ls to get
10 files.Instead of manually checking each we write
file ./* where asterik searches for all files and 
file tells you of filetype.We get that a file has ASCII TEXT which means
it is readable.Open the file using cat and
you get your password

###Level5-6
*Goal-* To find file in inhere which satisfies
(human-readable
1033 bytes in size
not executable)
*Solution-* cd to inhere and for 1033 bytes we directly search
'find -size 1033c'
you get one of the files you searched after typing ls
cat to open the file and
We get the password

###Level6-7
*Goal-* To find password somewhere on server satisfying 
owned by user bandit7
owned by group bandit6
33 bytes in size
*Solution-* We are going to use direct command which is
'find / -userbandit7 -groupbandit6 size33c 2>/dev/null'
which means-find these from root(whole server) and then we mention qualities of file and
2>/dev/null helps removing permission denied messages
We get a gibberish file and 
cat the file to find password

###Level7-8


