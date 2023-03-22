# Linux-Common-Cammands
This is a repository to show users the most common used Linux commands or commbined commands. Using Linux commands is my daily work. I read book <<Efficent Linux at the command line>> to review all the commands I used before and advance my abilities using other new techniques.


#### Input, Output and Channel
- **ls -l /path/to/folder** cannot show all files if the folder contains tremendous amount of files. However, use combined command **ls -l /path/to/folder | less** can be used to only show one page of content in the terminal screen.
- wc: output the rows, vocabularies and characters in a file. **wc test.txt**. Using options **-l, -w, -c** can output rows, vocabularies and characters independently.
- **ls -l | wc -l** shows us the number of viewable files in a directory.
- **head -n3 test.txt** outputs the first few rows of the text content in a file.
- **grep keyword test.txt** outputs the content that contains the keyword in a specific file.
- **md5sum *.txt | cut -c1-32 | sort** calculates the checksum for all files and uses cut command to get first 32 characters and finally uses sort to put together duplicated files.

