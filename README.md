# Linux-Common-Cammands
This is a learning notes to show users the most common used Linux commands or commbined commands. Using Linux commands is my daily work. I read book <<Efficent Linux at the command line>> to review all the commands I used before and advance my abilities using other new techniques.


#### Input, Output and Channel
- **ls -l /path/to/folder** cannot show all files if the folder contains tremendous amount of files. However, use combined command **ls -l /path/to/folder | less** can be used to only show one page of content in the terminal screen.
- wc: output the rows, vocabularies and characters in a file. **wc test.txt**. Using options **-l, -w, -c** can output rows, vocabularies and characters independently.
- **ls -l | wc -l** shows us the number of viewable files in a directory.
- **head -n3 test.txt** outputs the first few rows of the text content in a file.
- **grep keyword test.txt** outputs the content that contains the keyword in a specific file.
- **md5sum \*.txt | cut -c1-32 | sort** calculates the checksum for all files and uses cut command to get first 32 characters and finally uses sort to put together duplicated files.
- **cut** command can be used to output one or multiple columns of the file. The definition of columns here: a) if the input consists of string (field), and the string was separated by tab character, we can cut the file using option **-f**. **-f2** means the seconf field of the string. b) another way is to use -c option to cut the string by characters. **-c1-3** outputs the first 3 characters.


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
  - **echo image.jpg | sed 's/\\.jpg/.png/' replace jpg with png
  - **echo is Python wonderful | awk '{print $2, $1}' swap is and python, the output will be Python is wonderful
  

