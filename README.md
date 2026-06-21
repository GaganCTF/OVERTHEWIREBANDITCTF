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
*Goal-* To get password from a file 'data.txt' which has password next to the word millionth
*Soluion-* A common mistake which like me you could have made was by opening file by
cat ./data.txt which leads you to a output which seems like infinite progression of data
To Solve this we need to use grep tool
'grep "millionth" data.txt'
This prints the whole line with millionth in it and you find password

###Level8-9
*Goal-* To get password from a file 'data.txt' which has password in a line of text that occurs only once
*Solution-* We are going to get password by typing
Bash- 'sort data.txt | uniq -u' which means
SORT the file 'data.txt' either alphabetically or numerically and then 
show all UNIQue lines with -u to make sure we only get lines which were repeated 0 times
which in turn leads to password

###Level9-10
*Goal-* To find password from a file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters
*Solution-*Just use direct command
Bash- 'strings data.txt' which shows you readable data from files
Although you get 2-3 password which are preceded by '=' characters but use pattern to see that the
password would look gibberish like the other ones.

###Level10-11
*Goal-* To find password from a file data.txt, which contains base64 encoded data
*Solution-* Use direct command 
Bash- 'cat data.txt | base64 -d'
There was a command which I used earlier
Bash- 'echo text | base64 -d'
This will do same thing if you could cat the file earlier and then paste base64 message instead of text.

###Level11-12
*Goal-* To find password from a file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
*Solution-* We want to translate letters or rotate them by 13
Bash- 'cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
Explanation-tr is used to translate letters or rotate them 
Also the next text represents this
[A-N,Z-M,a-n,z-m] - The transformed list shows this pattern.
Also you can see both texts have same 1-2-2......-1 pattern
The file was designed in such a way that it said 
The password is ..........
Copy it for next part

###Level12-13
*Goal-*To find password from a file data.txt, which is a hexdump of a file that has been repeatedly compressed.
*Solution-* This part is lengthy one so we would need to solve it in steps.
The order we are going to follow is making a new directory mkdir as advised in ques
then we are going to copy material inside data.txt into the directory we made.
Then we would uncover it by first reversing hexdump and unzipping using gunzip or bzip2 as the filedata would suggest and 
finally we use tar -xf datafile to finally open posix tar archive file to get password.
I have uploaded a pic of bash on terminal for reference.

###Level14-15
*Goal-* The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.Find password
*Solution-* First open bandit13 and see ls(list) and cat the file.You see a private key file which is big in lines.
Now put bash- ssh -i sshkey.private bandit14@localhost -p 2220
Now open file by bash- cat /etc/bandit_pass/bandit14
Get password.




