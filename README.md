# Linux-Common-Cammands
This is a learning notes to show users the most common used Linux (shell) commands or commbined commands. Using Linux commands is my daily work. I read book \<\<Efficent Linux at the command line\>\> to review all the commands I used before and advance my abilities using other new techniques.

#### Input, Output and Channel
- **ls -l /path/to/folder** cannot show all files if the folder contains tremendous amount of files. However, use combined command **ls -l /path/to/folder | less** can be used to only show one page of content in the terminal screen.
- wc: output the rows, vocabularies and characters in a file. **wc test.txt**. Using options **-l, -w, -c** can output rows, vocabularies and characters independently.
- **ls -l | wc -l** shows us the number of viewable files in a directory.
- **head -n3 test.txt** outputs the first few rows of the text content in a file.
- **grep keyword test.txt** outputs the content that contains the keyword in a specific file.
- **md5sum \*.txt | cut -c1-32 | sort** calculates the checksum for all files and uses cut command to get first 32 characters and finally uses sort to put together duplicated files.
- **cut** command can be used to output one or multiple columns of the file. The definition of columns here: a) if the input consists of string (field), and the string was separated by tab character, we can cut the file using option **-f**. **-f2** means the seconf field of the string. b) another way is to use -c option to cut the string by characters. **-c1-3** outputs the first 3 characters. **-d** to define separator, e.g. **echo {1..5}.jpg | cut -d. -f1** outputs 1 to 5

#### Commands for Generating Text
- **cut -d: f1 /etc/passwd | sort** outputs all usernames being sorted
- **cat \*.txt | wc -l** outputs all rows of the file
- **date** outputs date and time according to the expected format
  - date +%Y-%m-%d
  - date +%H:%M:%S
- **seq** outputs a digital sequence with a range. **seq 1 5** outputs 1 2 3 4 5.
- Usage of brace in shell commands.
  - echo {A..Z} | tr -d ' ' output A to Z and remove space
  - echo {A..Z} | tr ' ' '\n' output A to Z vertically by replacing space with \\n
  - echo {1..1000..100} outputs a sequence of numbers from 1 to 1000 with an interval 100
  - **find** lists all files in a directory
    - **find /etc | head -n10** outputs the first 10 rows of the files in /etc

#### Detach Text
- **grep**
  - **grep -w** output the result with the keyword 100% matched.
  - **grep -i** ignore case sensitive for letters
- **tail** outputs last few rows of a file
  - **head -n6 test.txt | tail -n2** get the first 6 rows of the file and then get the last two rows content of these 6 rows (e.g. log investigation)
- **awk** a general command for text processing
  - **awk '{print $2}' /etc/hosts** get the hostnames from hosts file, awk command uses $ to locate specific column in a file
  - **df /data | awk '{print $3}'** check disk usage and get the third column content

#### Transform Text
- **tr** can transform any characters
  - **echo desk | tr a-z A-Z** transform desk to DESK
  - **echo hello python | tr " " "\\n"** hello python will be output as two rows instead of one
  - **echo hello python | tr -d '\t'** delete tabs and space, -d means delete
- **awk and sed**
  - **echo image.jpg | sed \'s/\\.jpg/.png/\'** replace jpg with png
  - **echo is Python wonderful | awk \'{print $2, $1}\'** swaps 'is' and 'python', the output will be 'Python is wonderful'
  - **seq 1 100 | awk '{s+=$1} END {print s}'** outputs 5050
  - **echo Hello Python | sed "s/python/django/"** nothing happens as the string does not match (case sensitive)
  - **echo Hello Python | sed "s/python/django/i"** replace Python with Django, ignore case sentive by adding option /i
  - **echo Hello Python | sed "s/l/L/"** outputs HeLlo Python, replace first l with L
  - **echo Hello Python | sed "s/l/L/g"** outputs HeLLo Python, replace all l with L
- Limit the width of output string, **fold -w40 test.txt**

#### Processing Text Files
- Find a specific file: **find $HOME -name python-world.txt -print**
- find command is very slow as it searches everything in HOME directories, we can use **find $HOME -print > $HOME/.allfiles** to create a file list with the path in a text file and then use **grep keyword.txt $HOME/.allfiles** to search target file path. grep has better searching performance in a file than using find to search everything in a directory structure (Tree Structure).

#### Others
- shell is just a normal program
- bash is the default shell for most of the Linux systems
- **cd** is not a program but a built-in function of shell
- using **export** to change a **local variable** to a **environment variable**
- **cd dir && touch test.txt** only when the first command being executed successfully then touch will be executed
- **cd dir || mkdir dir** if dir does not exist, then will create one
- **diff /tmp/original-list /tmp/full-list** compare difference between two folders
- **cat package.tar.gz | (mkdir -p /tmp/dir2 && cd /tmp/other && tar xzvf -)** pass the package data to tar command to extract files in another folder
- **shuf /usr/share/dict/words | head -n10** randomly echo 10 words
- **$RANDOM** randomly get a number from 0 ~ 32767
- **pwgen -N5 10** to generate a string with each having 10 characters
- **yes 'shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words | head -n 100 | bash** to iteratively generate 100 files with each having a random name and random words in each file
- **cat /etc/passwd | cut -d: f1 | sort** echo the users listed in passwd file and sort them

