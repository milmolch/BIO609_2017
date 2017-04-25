# Exercises Linux Tutorial - Part 2


## Stefan Wyder

### URPP Evolution in Action
![URPP logo](Logo_URPP_kl2.png)
### University of Zurich

---------------

Many thanks to Gregor Roth (von Mering group / IMLS, UZH) who agreed to share some exercises.


 
## Compressing/Decompressing files

### File compression and decompression

There are 2 different frequently used methods to compress files, in order to save space: `gzip` and `zip`. The `.gz` gzip format is the 
most frequently used format in the Linux world. Gzip is used in combination with `tar` to archive all the files into a single
tarball before compression (format `.tar.gz`).     
  
Zip and unzip are compatible with Windows and Mac OS compression software.
  

**Command** | **Meaning** |
---|----
**gzip** *filename* | compress file with gzip (adds .gz extension) |
**gunzip** *filename.gz* | decompress file with gzip (removes .gz extension) |
**zmore** *filename.gz* | display file content of a gzip compressed file
**zless** *filename.gz* | display file content of a gzip compressed file
**tar xfz** *filename.tar.gz* | extract/decompress files from tar.gz archive
**tar** **zcvf** *archive.tar.gz folder\_to\_compress* | creates archive.tar.gz
**unzip** *filename.zip* | unzip archive
**zgrep** *pattern* filename.gz | search text/pattern in a compressed file


### Exercise
Use the program **wget** to download the human protein sequence from ensembl

`wget ftp://ftp.ensembl.org/pub/release-84/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz`

1. When downloaded, look at the file using **zmore** or **zless**

2. **gunzip** the file. Then count how many proteins are in the file.

3. Now **gzip** again the file and try to count the number of proteins without using **gunzip** directly from the compressed file (Tip: use zgrep).


## Software installation

There are several options how to install software on a Linux system. The easiest way is to use the package manager. Even though the Ubuntu package management contains a lot of software, we sometimes have to install a software "manually". We will first use the package manager and later install the latest version of bwa manually

### Try out your package manager

The Linux package management systems are comprehensive (for Ubuntu > 35'000 software packages), powerful and still easy to use – one of the advantages of the Linux world. You can often save time and nerves using the package manager as compiling software from source can be painful and time-consuming (due to dependencies). The package manager helps you to install, upgrade and remove software.
 
It also checks automatically for software updates and your system will propose you from time to time to upgrade your system.

The drawback is that the repositories are lagging a bit behind and they often do not install the latest versions. This is not a problem for most applications but it can be problematic in the fast-moving genomics field.

You can interact with the package manager using a graphical user interface or the command line. There is a sort of App Store called "Ubuntu Software Center" which includes software reviews. To run it, click on topmost icon in the dock on the left and type "Ubuntu Software Center" in the search field.

### Exercise

The "Ubuntu Software Center" comprises many software frequently used in bioinformatics/genomics.   
1. Open the "Ubuntu Software Center" and look for "muscle". Click on "More Info" to learn more about it.  
2. Try to find out what "emboss" is using the "Ubuntu Software Center"  


### Compile from source

Let us install the latest version of the short-read mapper [bwa](https://github.com/lh3/bwa). An increasing number of programs are available on github.

Go to the `~/software folder`, download and build the software like this:
```
git clone https://github.com/lh3/bwa
cd bwa && make
```

Run the binary: `./bwa` 

## Connecting to a remote host, transferring files

**Command** | **Task**
-- | ---
ssh -X *user*@*hostname* | Connect to server
scp <what> <towhere> | Transfer file from/to server
sftp *user*@*hostname* | Transfer file from/to server (interactive)


`ssh` ("secure shell") is a secure protocol for remote login and also for executing commands in a remote machine. To connect to a remote machine 
using `ssh`, simply type:

$ **ssh** username@130.60.201.40

inside your local computer shell. You will be asked for the password and after you successfully login, you can work with the remote machine 
in the same way as you work on your local machine. (You are dropped at your home directory /home/username). Unfortunately `ssh` can’t transfer files, for that you can 
use another program called `sftp`. Disconnect before you go on to the next step (Ctrl+d).

$ **sftp** username@130.60.201.40

After you are connected, you can use “cd”, “mkdir”, “rm” to navigate around and manipulate files on the remote computer. To upload a file from 
your local computer to the remote computer, simply use `put *filename*`. Filename here refers to a file on your local computer that will be uploaded 
to the remote computer.

### Exercise
1. Create a new file with **nano** on your local computer. Save a few lines of text to the file. 
2. Connect to the remote server using **sftp** and upload the file using the **put** command inside the sftp session.
3. Login to the remote server and inspect the file content using `more`.


## Writing and executing a perl script

Many scripts in bioinformatics are written in perl. You have used the **nano** editor from the first exercise in part 1 of the Tutorial. Try to 
copy/paste the below simple perl program into a file and execute it. The hello world perl script:
```
\#!/usr/bin/perl
print "Hello World.\\n";
```
Copy the above 2 lines and save them to the file `hello.pl`. The first line tells the Unix shell to interpret the program with **perl**. In order to run the program you can either start it with:
```
$ perl hello.pl
```
The output on the screen should be `Hello World`.

Optionally you can make your file executable by typing:
```
$ chmod +x hello.pl
```
And now you can simply type:
```
$ ./hello.pl
```
Note the `./` at the start of the command. This tells the system that we want to run hello.pl which is located in the current directory.
It is necessary because the directory where we stored `hello.pl` is not in the system variable `$PATH`.

### Exercise
Check the file's permissions using `ls -l`. Remove the permission to execute it and check the permissions again.


## Exercise: Write a simple bash script

Often you would like to run the same command with different parameters. As an exercise, write a short bash script that outputs numbers
from 1 to 100. Use a **for** loop.

```
\#!/bin/bash
for i in {1..100}
do
  echo $i
done
```

Save the above code to a file (e.g. PrintNumbers.sh), make the file executable (+x flag) and run it.


## Exercise: Iterating over files

By using the same concept from the previous exercise (**for** loop), you can iterate over all files in a directory, print their name 
and the length of each file.

`for filename in *.fasta`
  
  
1. Use **wc** to count the sequence length in each file. Make sure not to include the sequence header  
2. Count the number of Methionines (M) in each sequence (use grep -o)  


## Appendix




## Getting help

Command | Description
---|------
**man** *command*|display manual page of command|
*command* **-h**|display shorter manual page of command (only GNUtools, not in Mac OS X)|
*Program* **--help**|display help / usage information for software/scripts|
*Program* **-h**|display help / usage information for software/scripts|


## List of important commands

**File and folder manipulation**

Command | Description
---|------
**pwd**|display current folder|
**ls -l** *path*|list files and folders|
**cd** *path*|change folder to path|
**cd** \~|change folder to home folder|
**mkdir** *dir\_name*|make folder|
**rmdir** *dir\_name*|remove folder|
**cp** *source* *dest*|copy file/folder and all its contents|

**File compression and decompression**

Command | Description
---|------
**gzip** *filename*|compress file with gzip (adds .gz extension)|
**gunzip** *filename.gz*|decompress fildecompress file with gzip (removes .gz extension)|
**zmore** *filename.gz* | |
**zless** *filename.gz*|file decompress display file content of a gzip compressed file|
**tar xfz** *filename.tar.gz*|extract/decompress files from tar.gz archive|
**tar** **zcvf** *archive.tar.gz folder\_to\_compress*|creates archive.tar.gz|
**unzip** *filename.zip*|unzip archive|
**zgrep** *pattern* *filename.gz*|search text/pattern in a compressed file|


**Text processing**

Command | Description
---|------
**grep** *pattern* *filename*|search text/pattern|
**cut**|extract column|
**tr**|substitute/delete text/pattern|
**less**|display file content|
**wc**|count number of lines in file|
**sort**|sort lines|
**uniq**|remove lines occurring more than once|
**comm** *file1* *file2*|compares files (intersection,union,difference)|

**Network and file transfer**

Command | Description
---|------
**wget** URL|download file (also html page) and save to current folder|
**ssh** –X *username@host*|remote login to host with username
| disconnect by Ctrl+d|
**sftp** username@host|remote login to host with username and transfer files|
**scp** source target|copy files from/to host
scp username@host:\~/path/*file* .|
scp *file* username@host:\~/path*/file*| 

**Permissions and Ownership**

These commands also work on directories

Command | Description
---|------
**chmod** ug+rx *filename*|Set write and execute permissions to user and group|
**chown** user *filename*|changes user ownership|
**chgrp** group *filename*|changes group ownership|
**chown** user:group *filename*|changes user & group ownership|

**System information & processes**

Command | Description
---|------
**uname -a**|display system information|
**df -h**|list mounted disks with available space|
**du -h** *path*|show space usage|
**top**|display running processes|
**kill** *pid*|kill process|


“**vi” editor**

Command | Description
---|------
**$ vi** *filename*|start editing file with vi|
**i**|switch to “insert” mode|
**ESC**|switch to “command” mode|
**:w**|save|
**:q**|quit|
**:x**|save and quit|
**/\<pattern\>**|search for pattern, \<n\> gives you the next match|
**:q!**|quit without saving changes|
