## List of important commands

### Stefan Wyder

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
