## BIO609 Introduction to UNIX/Linux and Bash Scripting 

## May 3 + 9, 2017


### University of Zurich
### URPP Evolution in Action
![URPP logo](Logo_URPP_kl2.png)

Stefan Wyder & Heidi Tschanz-Lischer

stefan.wyder@uzh.ch  
heidi.lischer@ieu.uzh.ch


## Table of Content


&nbsp;   | &nbsp; | &nbsp;
-------- | --- | --- 
9.30 - 9.40 | **Welcome & Introduction** | SW&HTL
9.40 - 12.30 | **Introduction to the command line** <br /> Working with files, working with text, pipes <br /> [Presentation](LinuxBash.pdf)  \| [Demo](demo_filesystem.md) \| [Hands-on 1](Hands-on_unix_Part1.md) \| [Hands-on 2](Hands-on_unix_Part2.md) | SW
 | |
13.30 - 14.30 | Working with text files | SW
14.30 - 17.30 | **Bash scripting** <br /> [Presentation](BashScripting.pdf) \| [Hands-on](Exercises_BashScripting.pdf) | HTL


[Etherpad](https://public.etherpad-mozilla.org/p/BIO609_2016)


## Installation Instructions for the Virtual Machine (VM)

- Download the virtual machine manager VirtualBox, from [virtualbox.org](https://www.virtualbox.org/). Make sure you pick the right operation system for your laptop. 
- Install VirtualBox on your machine
- Download the VM image (~7 GB) from dropfiles.uzh. Use the download link you got by email. Note that it is a large download, use an Ethernet connection if possible.
- Run VirtualBox and do `File | Import Appliance` from the menu. Choose the VM image you just downloaded (file with extension .OVA). This will trigger a menu where you can change the Appliance settings. We recommend giving the VM as much memory as you can (about 2/3 of the total memory, but between 2-4 GB). Start the import process.

Now you can start the VM by selecting it in the list and clicking on the Start button. Login with the VM password. 

### Copy/paste doesn't work in the command window

To copy, select text and click the title bar and go to Edit->Copy. You can use Edit->Paste to paste.  
  
  
The usual shortcuts for copy/paste don't work in the virtual machine. For Macs use ctrl+shift+C for copying and ctrl+shift+v for pasting.  
  
You can also setup shared folders between the VM and the host system. See below or ask us how to do it.

### Adding Shared Folders

It is possible to share data (read/write/copy files) between Virtual Machine and your host operating system (e.g. Mac OS or Windows). By default no access is granted, we have to configure it: 

1. Share a folder in your operating system  
   With a running VM go to the menu of the VirtualBox software `Devices | Shared Folder Settings…` and add 1 or multiple folders
2. In Ubuntu VM, go to the terminal and type:  
`usermod -aG vboxsf student`           
 (student is our username)
3. Reboot the VM

On Ubuntu the shared folder is located in the path `/media`

## Recommended books (Practical Computing Skills)

- [Haddock & Dunn. Practical Computing for Biologists. Sinauer Associates 2011.](http://practicalcomputing.org)  
  A good book that covers the shell/command line, programming in python & bash, databases, regular expressions. 
  Suitable for self-study and as a reference book.

- [Vince Buffalo. Bioinformatics Data Skills. O'reilly 2015](http://shop.oreilly.com/product/0636920030157.do)  
  This practical book teaches the skills that scientists need for turning large sequencing datasets into reproducible and robust biological findings.
  Also covers methods on Sequence and Alignment Data. 
  More advanced than Haddock & Dunn and progresses with faster pace.


## Recommended websites

**General**  
- <http://software-carpentry.org/lessons> and <http://www.datacarpentry.org/lessons>
  Scientific Computing Resources for learning bash shell, programming in python, R, …]  
- [BioStars](https://www.biostars.org/) for questions about biocomputing and scripting for biologists  
- [stackoverflow](http://stackoverflow.com/) for questions related to coding

**Linux/Shell**  
- Software Carpentry tutorial - [The Unix shell](http://swcarpentry.github.io/shell-novice)   
- Data-Carpentry - [shell-genomics](http://github.com/datacarpentry/shell-genomics/tree/gh-pages/lessons) 
- [Interactive course](http://www.learnshell.org/)  
- [Cheatsheet](https://github.com/swcarpentry/boot-camps/blob/master/shell/shell_cheatsheet.md)  
- [SIB e-learning: UNIX fundamentals](http://edu.isb-sib.ch/pluginfile.php/2878/mod_resource/content/3/couselab-html/content.html)  
- [Explain shell commands](http://explainshell.com/)   
- [Tips & Tricks for using the shell on Mac OS](http://furbo.org/2014/09/03/the-terminal/)  
- [Safe Bash scripting](http://robertmuth.blogspot.ch/2012/08/better-bash-scripting-in-15-minutes.html)

**Intermediate level**  
- [Cheatsheet intermediate](http://www.cheatography.com/davechild/cheat-sheets/linux-command-line/pdf/)  
- [Important Commands & Glossary](http://swcarpentry.github.io/shell-novice/reference.html)  
- [Linux commands listed](http://www.gnu.org/software/coreutils/manual/coreutils.html)  
- [Advanced handy command line examples](http://www.commandlinefu.com/)  
