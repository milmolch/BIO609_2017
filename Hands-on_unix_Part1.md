# Exercises Linux Tutorial – Part 1


### Stefan Wyder

#### URPP Evolution in Action
![URPP logo](Logo_URPP_kl2.png)
#### University of Zurich

------

## Basic file and directory manipulation

(this exercise is from the von Mering group / IMLS)

The UNIX **filesystem** is laid out as a hierarchical tree structure where a directory can have many child directories, but only one parent directory. The top-level directory is known as the **root** (designated by a slash '**/**').

### Iron ration when working with Files/Directories


**Command** | **Meaning**
----------- | ----------------
ls | List files and directories
ls -a | List all files and directories
cd *directory* | Change to directory
cd | Change to home directory
cd \~ | Change to home directory
cd \~/software | Change to a subfolder of your home directory
mkdir | Make a directory
cp | Copy a file/directory
rm | Delete a file/directory


Once the Terminal is open follow the commands below:

Command | Meaning 
--- | ------
$ **cd**| change directory to your home directory
$ **Cd**| Doesn’t work, Linux commands are case-sensitive!
$ **pwd**| prints the current directory (print working directory)
$ **ls –l**| ls means list, -l means long; this command lists all files and directories in the current directory
$ **mkdir** tmp| make directory; the command creates the directory “tmp” in your home directory  


Here we use a relative path, we would have gotten the same result with the absolute path: mkdir ~/tmp

Command | Meaning
---|------
$ **cd** tmp | brings you to your newly created directory tmp
$ **pwd** | you can see that your current working directory changed|
$ **cd ..** | move one level up|
$ **ls -l** | you should see the newly created tmp directory
$ **nano tmp/poem.txt**|start editing file `tmp/poem.txt` (or creates a new file)|
| copy/paste the poem by Robert Frost below to the `poem.txt` file in your nano editor


(Copyright by Henry Holt and Company, from http://www.poetryfoundation.org/poem/171621)
```


Whose woods these are I think I know.   
His house is in the village though;   
He will not see me stopping here   
To watch his woods fill up with snow.   

My little horse must think it queer   
To stop without a farmhouse near   
Between the woods and frozen lake   
The darkest evening of the year.   

He gives his harness bells a shake   
To ask if there is some mistake.   
The only other sound’s the sweep   
Of easy wind and downy flake.   

The woods are lovely, dark and deep.   
But I have promises to keep,   
And miles to go before I sleep,   
And miles to go before I sleep.
```

Command | Meaning
---|------
**ctrl+x** | press ctrl and then x (Exit) to quit the nano editor, press y to confirm saving and return to the shell
$ **head tmp/poem.txt**|displays first 10 lines of the poem|
$ **tail tmp/poem.txt**|displays last 10 lines of the poem|
$ **man** head|use **man** to get more information about the head command; use the correct parameter to display not only the first 10 lines of the poem but the entire poem
 |Scrolling: press space
 |To quit: q
$ **less** tmp/poem.txt|less is a convenient command for displaying file contents (“less is more”; **more** is another command people used a lot before less was introduced)|
$ **grep** house tmp/poem.txt|if you are searching for something, you can use **grep** *text* to display only lines matching text|
$ **wc** tmp/poem.txt|displays the number of lines in the file|
$ **wc** -w tmp/poem.txt|counts the words in the file|
$ **cp** tmp/p + `TAB`|if you start typing “cp tmp/d" and then press `TAB`, what happens?|
$ **cd** \~/tmp|change current directory to directory tmp  | (On Mac OS X press alt+n for ~) 
$ **cp** poem.txt poem2.txt|cp is used to copy the file data.tab to file data2.tab|
$ **ls** -l|you should see 2 files now|
$ **mv** poem2.txt poem\_v2.txt|Rename the file (also for moving it to another directory)|
$ **cd** ..|go back one level|
$ **cp** -Rp tmp poems|you just made a copy of the entire directory tmp to poems|
$ **ls** -l|you should see both tmp directories|
$ **ls** tmp/\*.txt|you can use the wildcard (\*) to list files and directories that match your expression|
$ **rm** tmp/poem\*.txt|rm removes files and folders|
$ **rmdir** tmp|finally we remove the bio directory|
:collision: Be careful!|rm and mv are potentially very dangerous commands as you can lose your files by deleting or overwriting them without notice! In the shell there is no trash bin, you will not get the files back. In the worst case you can delete all files you ever created in your home directory and subdirectories with the recursive -R options. Better use rm -i , which asks you to confirm the deletion of each file. For deleting directory one can use rmdir that only deletes empty directories.

Of course as long as we are working on single files we can also perform file/directory operations using the Linux or Mac OS graphical interface. But when we log in to a server we do not have a graphical user interface and we need to know how to move around using the shell.


### Absolute vs relative paths

(this exercise is from Stephen Turner)

Let’s say you are here: /home/turnersd/scripts/. If you wanted to go to /home/turnersd/, you could type: `cd /home/turnersd/`. Or you could use a relative path: `cd ..` (two periods) will take you one directory “up” to the parent directory of the current directory.


`.` (a single period) means the current directory  
`..` (two periods) means the parent directory  
`~` means your home directory  

**A few examples** 

Command | Description
---|------
mv myfile .. | moves myfile to the parent directory
cp myfile ../newname | copies myfile to the parent directory and names the copy newname
cp /home/turnersd/scripts/bstrap.pl . | copies bstrap.pl to `.` i.e. to dot, or the current directory you’re in
cp myfile ~/subdir/newname | copies myfile to subdir in your home, naming the copy newname
more ../../../myfile | displays screen by screen the content of myfile, which exists 3 directories “up”


### (optional) Repetition of absolute and relative paths

(this exercise is from Tobias Rausch www.embl.de/\~rausch/primer.pdf‎ )

This exercise is to repeat absolute and relative paths, as experience shows that many beginners initially struggle with the directory structure. If you feel comfortable to move around you can skip it.

The Linux file system is organized as a tree. The root of the tree is simply labeled as `/`. A first level subdirectory of / is, for instance, /home or /user. The home directory contains all user directories, such as /home/garfield or /home/snoopy.


The command that shows the directory you are currently in is **pwd** (stands for print working directory). Let us assume garfield is in its home directory /home/garfield and wants to create two subdirectories work and freetime. The commands to achieve that are

$ **mkdir** work

$ **mkdir** freetime

These commands use so-called relative paths because garfield creates the directories where he is currently in, which is hopefully /home/garfield. Alternatively, garfield can use absolute paths.

$ **mkdir** /home/garfield/work

$ **mkdir** /home/garfield/freetime

An absolute path describes the whole path starting from the root through all subdirectories.

Since our workaholic garfield has no freetime we only create two further subdirectories underneath /home/garfield/work

$ **mkdir** work/sleep       	(does the same as the longer form **mkdir** ./work/sleep )

$ **mkdir** /home/garfield/work/food

The former command uses a relative path whereas the latter command uses an absolute path. The command cd allows you to move through the directory tree.

$ **cd** work/ 		(does the same as the long form **cd** ./work/ )  

$ **pwd**

$ **cd** /home/garfield/freetime

$ **pwd**

$ **cd** ..

$ **pwd**

Whereas a single `.` specifies your current directory a double `..` specifies the parent directory. With these operations one can specify a very complicated command that does absolutely nothing.

$ **cd** ./work/./sleep/../sleep/../../

Finally, there is the ls command that shows the directory content and the rmdir command that removes a directory.

$ **ls**

$ **ls** /home/garfield/work

$ **rmdir** /home/garfield/freetime

$ **ls** /home/garfield

 

### Using the terminal efficiently

All the commands you have used recently are stored in the history and can be retrieved to minimize typing. TAB completion also saves you some typing.

Command | Description
---|------
$ **history**|shows all the commands you have used recently|
arrow keys|Move in history, relaunch command by pressing Enter|
$ **ctrl-r**|Search in history, eg. type "grep" to retrieve your last grep command.
| To keep it in the command line, press the -> arrow key. To look for the second last etc press ctrl-R multiple times|
**TAB completion**|completes program\_path/file\_name by pressing the `TAB` key

If there are multiple options, they will be listed|

- What were the options of your last grep command? wc command?

- Explore the the files and subdirectories of the root directory: ls / + `TAB`

- TAB completion also works with commands: list all commands starting with "g", "gr", "gre"


## Working with text files

Linux has very powerful tools to work with text files. It is no problem to work on your laptop with 10-20Gb files which are sometimes seen in Next-Generation-Sequencing. Some people actually start using the Linux shell because their files are too large to be opened with Excel. Furthermore, working with the shell improves the reproducibility (compared with manual reformatting / selection in Excel) and reduces the error rate.

**First lets prepare the data files**

We use a genome annotation file for the model plant Arabidopsis thaliana – The file is in gtf format which is a standard format to describe genome annotations.

1.  In the terminal: Create a new directory "Arabidopsis_annotation" in your home and move into the directory

2. Download the file TAIR10_GFF3_genes to your harddisk:
   ```
   wget ftp://ftp.arabidopsis.org/home/tair/Genes/TAIR10_genome_release/TAIR10_gff3/TAIR10_GFF3_genes.gff
   ```

3.  Extract the first 100 lines into a new file At.gff:
   ```
   head -100 TAIR10_GFF3_genes.gff > At.gff
   ```

4.  Look at the file, the file is tab-separated with 9 columns/fields:
   ```
   <chromosome> <source> <feature> <start> <end> <score> <strand> <frame> <group>
   ```
   Non-available (unknown) values are denoted with a `.`. You find a detailed format description under [http://genome.ucsc.edu/FAQ/FAQformat.html\#format3](http://genome.ucsc.edu/FAQ/FAQformat.html#format3)

5.  Make a second file `indA.txt` using the nano editor by typing `nano indA.txt`:
  ```
  mRNA
  three_prime_UTR
  ```
  Quit the editor by `Control + x` and `Y`



## Type all commands to find out what they do

### grep – search pattern/text

grep searches are case-sensitive by default.

Command | Description
---|------
$ **grep** "exon" At.gff|The command grep searches each line of a file for a certain pattern and outputs all matching lines.|
$ grep `–v` "exon" At.gff|Shows only lines which do NOT match the search pattern|
$ grep `–f` indA.txt At.gff|Get search patterns from a file, and searches them all|
$ grep `–w` "Chr1" At.gff|Only whole words, would e.g. exclude Chr10|
$ grep `-i` "CHR1" At.gff|Case-insensitive search|
$ grep `--color` "protein" At.gff|Colors the search pattern in the result|
$ grep `-c` "protein" At.gff|counts the number of lines containing "protein"|

### sort 

GNU sort is flexible and very space efficient. Its possible to sort a 20 Gb file with less than 2 Gb memory. It is not trivial to implement so powerful a sort by yourself.

Command | Description
---|------
$ sort At.gff|The command sort can be used to sort a file according to numerical values or dictionary order. Dictionary order is default.|
$ sort −k4,4g At.gff|`-k` indicates the key (column to be sorted), `g` denotes numerical sorting|
$ sort –k4,4 At.gff|For comparison: sort column 4 in dictionary order|
$ sort –k4,4gr At.gff|Sort column 4 as numbers in descending order (`r`:reverse)|
$ sort −k1,1 –k4,4gr At.gff|We can define several sorting keys. Sort column 1 in dictionary order, if identical, sort column 4 as numbers in descending order. This command is often used to sort a genomic file according to chromosome (column 1) and position (column 4).|

### cut – extract columns

Default field separator: single TAB

Command | Description
---|------
$ cut -f 1 At.gff|The command cut can be used to extract columns from a file. Here we extract column 1|
$ cut -f 2 At.gff|Now we extract column 2|
$ cut −f 1,3 At.gff|or columns 1 and 3|
$ cut -f1-3,6,7- At.gff|cut out the 1st, 2nd, 3rd, 5th, 7th and following columns|
$ cut -d" " -f 3 input.txt|Cut out column 3 with columns separated by a single space|


### tr – replace/delete text

**tr** is special as it only reads from standard input (i.e. you can not give it a filename to read from). You can try tr like this
```
echo "hello hello" | tr e a
```
Command | Description
---|------
$ tr|The command tr can be used to replace/delete characters|
$ tr e a|Replaces all "e"s with “a”s|
$ tr `–d` e|Deletes all “e”s|
$ tr `–s` ello i||

### wc – count lines/words

Command | Description
---|------
$ wc At.gff|The wc command shows the line, word and byte count for a file|
$ wc `-l` At.gff|Shows number of lines only|

### uniq – report or filter out repeated lines in a file

Make sure the input of uniq is **sorted**!

Command | Description
---|------
uniq *file*|eliminate duplicate lines|
cut –f 1 At.gff \| sort \| uniq -c |uniq –c counts the number of occurences of **sorted** lines. Here we extract values of column 1, sort them and count them|
uniq -d|shows lines that are repeated in the input (duplicates)|


## Pipes and redirecting input / output

(this exercise is from the von Mering group / ILMS)

The pipe **|** operator is used to create concurrently executing processes that pass data directly to one another:
```
$ command1 | command2 | command3 …
```
The standard output of command1 is redirected (piped) to the standard input of command2, etc.

Pipes are useful for combining system utilities to perform more complex functions. For example (On Mac OS X, press alt+7 for |):
```
$ cd
$ cd poems
$ cat poem.txt | grep "House" | wc
```

creates three processes (corresponding to **cat**, **grep** and **wc**) which execute concurrently. As they execute, the output of the cat process is passed on to the grep process which is in turn passed on to the wc process. wc displays its output on the screen.

Redirecting input and output: The output from programs is usually written to the screen, while their input usually comes from the keyboard (if no file arguments are given). To redirect standard output to a file instead of the screen, we use the **>** operator:

Command | Description
---|------
$ echo hello|displays “hello” on the screen|
$ echo hello > hello.txt|writes “hello” to the file|
$ cat hello.txt|displays contents of file; you should see “hello”|

In this case, the contents of the file data.tab will be overwritten if the file already exists. If instead we want to append the output of the echo command to the file, we can use the **>>** operator:

Command | Description
---|------
$ echo hello >> hello.txt|appends “hello” to the end of the file|
$ cat hello.txt|displays contents of file|

Standard input can also be redirected using the < operator, so that input is read from a file instead of the keyboard:
```
$ wc < hello.txt
```
You can combine input redirection with output redirection, but be careful not to use the same filename in both places. For example:
```
$ wc < hello.txt > hello_counts.txt
```

## Exercise: Piping together text processing commands

In exercise 4 we have learnt to combine multiple commands by using pipes. To check if a command works as expected (and to check intermediary steps) you can pipe the results to less or head like this:
`command | command | less`

Use the complete genome annotation file `TAIR10_GFF3_genes.gff` for Arabidopsis from above.

1.  Count the number of lines in the file

2.  Sort the first 100 lines of the file alphabetically according to feature (CDS, exon, gene, three_prime_UTR, …).

3. Extract all entries for gene `AT1G01270`. Is it a protein coding gene?

4.  How many different chromosomes does the file contain?

5.  How many genes, mRNAs?

6. How many miRNA genes are annotated?  
  Tip: Use multiple grep searches 

7.  Which genes encodes an exon in Chromosome 1 at position 3535383-3538439 ?

8.  Which types of RNAs are annotated? (tip: use multiple `cut` and use `;` as separator)



## More working on text files


### awk

awk is a simple programming language dedicated to text processing. Although you can achieve all its functionality e.g. with all-purpose programming languages like python/perl awk is often simpler and convenient to use in pipes. We will not learn awk now but use it for some handy one-liners.

Command | Description
---|------
awk '{print $1,$2,$4,$5}' At.gff|awk splits a tab- or space-delimited file into variables. $0 contains the full input line, $1 column 1, $2 column 2, and so on.|
awk '{print $4,$2,$3,$1}' At.gff|So to switch column 1 and 4 we simply type.|
awk '{sum=$4+$5;print sum,$0}' At.gff|Print out sum of columns 4 and 5 before the line|
awk '{$2=$4+$5;print}' At.gff|Replace column 2 by the sum of columns 4 and 5|
awk 'BEGIN {OFS="\t"} {print $4,$2,$3,$1}' At.gff|We want to create tab-separated output (default is space-separated output)|
awk 'BEGIN {FS=",";OFS="\t"} {print $4,$2,$3,$1}' input.file|We have to change the input field separator as the input file indB.txt is comma-separated (`,`)|
awk '$4>1000 && $5<6000 {print $0}’ At.gff|Shows all lines for positions between 100 and 200|
awk '{SUM+=$4} END {print SUM}' input.txt|Print out the sum of column 4 over the whole file|
awk '{SUM+=$4} END {print SUM/NR}' At.gff|Print out the mean of column 4|
awk '/gene/ {c++} END {print c}' At.gff|Count lines containing “gene”| 
awk '$4>max {max=$4; maxline=$0} END {print maxline}' At.gff|Print the maximum value of column 4 observed in the file|
awk 'BEGIN {FS="\t"} {print NF}' At.gff \| sort \| uniq -c|Handy to check proper formatting – same number of columns over all lines.|

### Even more useful commands

Explore using the man command and google searches

Command | Description
---|------
sort -u|Make unique (keep only of each kind)|
comm|Compare files, can be used to identify shared and unique elements (for Venn diagrams)|
paste|Merge corresponding or subsequent lines of files|
join|Join files on common fields|
diff|Compare files line by line. See also diff3|

### Advanced: More examples

Command | Description
---|------
awk 'BEGIN {while((getline<"file1.txt")>0) lin[$1]=$0} $1 in lin {print $0"\t"lin[$1]}' file2.txt > output.txt|join two files on column 1|
awk 'BEGIN {OFS="\t"} {print NF}' indA.txt | sort | uniq -c|Handy to check proper formatting of a tab-delimited file (e.g. before importing it into R) – same number of columns over all lines.|
sort -k2.3n input.txt|sort starting from the 3rd character at column 2, as numbers|
(echo hello; echo world; cat file1.txt) > output.txt|Use brackets to redirect multiple files together|


## (Advanced) Exercises

Use the complete genome annotation file `TAIR10_GFF3_genes.gff` for Arabidopsis from above.

2. How many genes are encoded in the Arabidopis genome?

3. How many genes are encoded in the Arabidopis genome? **The safe way** 

3. How many genes are encoded by each chromosome?

4. Find the gene with the highest number of exons.

5. How many genes are not spliced?

6. Extract exons encoded on Chromosome 3 on positions 10000 – 30000

7. How many genes are encoded by the region?



## Solutions

1.  Count the number of lines in the file
  ```
wc -l TAIR10_GFF3_genes.gff
  590264 TAIR10_GFF3_genes.gff
wc TAIR10_GFF3_genes.gff 
  590264 5312376 44139005 TAIR10_GFF3_genes.gff
```
`wc` returns number of lines, words and bytes. Here we only want the lines `wc -l TAIR10_GFF3_genes.gff`.
  

2. Sort the first 100 lines of the file alphabetically according to feature (CDS, exon, gene, three_prime_UTR, …).
  ```
head -100 TAIR10_GFF3_genes.gff | sort -k3,3
```

3. Extract all entries for gene `AT1G01270`. Is it a protein coding gene?
  ```
grep AT1G01270 TAIR10_GFF3_genes.gff 
\#or grep "AT1G01270" TAIR10_GFF3_genes.gff  
Chr1	TAIR10	gene	111890	111961	.	-	.	ID=AT1G01270;Note=tRNA;Name=AT1G01270
Chr1	TAIR10	tRNA	111890	111961	.	-	.	ID=AT1G01270.1;Parent=AT1G01270;Name=AT1G01270.1;Index=1
Chr1	TAIR10	exon	111890	111961	.	-	.	Parent=AT1G01270.1
```
AT1G01270 is a tRNA gene.
  
  
4.  How many different chromosomes does the file contain?  
  A first option using `grep`: 
  ```
grep chromosome TAIR10_GFF3_genes.gff 
Chr1	TAIR10	chromosome	1	30427671	.	.	.	ID=Chr1;Name=Chr1
Chr2	TAIR10	chromosome	1	19698289	.	.	.	ID=Chr2;Name=Chr2
Chr3	TAIR10	chromosome	1	23459830	.	.	.	ID=Chr3;Name=Chr3
Chr4	TAIR10	chromosome	1	18585056	.	.	.	ID=Chr4;Name=Chr4
Chr5	TAIR10	chromosome	1	26975502	.	.	.	ID=Chr5;Name=Chr5
ChrC	TAIR10	chromosome	1	154478	.	.	.	ID=ChrC;Name=ChrC
ChrM	TAIR10	chromosome	1	366924	.	.	.	ID=ChrM;Name=ChrM
```
  Chr1-5 and the chloroplast and mitochondrial genomes
  

  Another option using `cut`:
  ```
cut -f1 TAIR10_GFF3_genes.gff | sort -u
Chr1
Chr2
Chr3
Chr4
Chr5
ChrC
ChrM
```


5.  How many genes, mRNAs?
  ```
grep -c -w gene TAIR10_GFF3_genes.gff 
28775
grep -c -w mRNA TAIR10_GFF3_genes.gff 
35386
```
  Or we could also pipe the grep result into wc: `grep -w gene TAIR10_GFF3_genes.gff | wc -l`
  With the `-w` parameter we count only lines where "gene" occurs as a separate word. If we use grep without the `-w` parameter lines containing `protein_coding_gene` will also be counted. See further below for a safe solution using `awk`. 


6. How many miRNA genes are encoded in the genome?  
  Tip: Use multiple grep searches 
  ```
  grep "miRNA" TAIR10_GFF3_genes.gff | grep -w "gene" | wc -l
     177
```

7. Which genes encodes an exon in Chromosome 1 at position 3535383-3538439 ?
  ```
grep -w Chr1 TAIR10_GFF3_genes.gff | grep -w 3535383 | grep -w 3538439 | grep -w gene
Chr1	TAIR10	gene	3535383	3538439	.	+	.	ID=AT1G10670;Note=protein_coding_gene;Name=AT1G10670
```

8. (Advanced) Which types of RNAs are annotated? 
  Tip: use multiple cut and finally use ";" as separator
  ```
grep -w gene TAIR10_GFF3_genes.gff | cut -f9 | cut -d";" -f2 | sort -u
Note=miRNA
Note=other_RNA
Note=protein_coding_gene
Note=rRNA
Note=snRNA
Note=snoRNA
Note=tRNA
```


## Solutions for Advanced Exercises


1. How many genes are encoded in the Arabidopis genome?
  ```
grep -c -w gene TAIR10_GFF3_genes.gff
   28775
\# Or piping the results of grep into wc
grep -w gene TAIR10_GFF3_genes.gff | wc -l
   28775
```
With the `-w` parameter we count only lines where "gene" occurs as a separate word. If we use grep without the `-w` parameter lines containing `protein_coding_gene` will also be counted. See the next exercise for a safe solution. 

  **The same the safe way**
  Note that the previous `grep` searches were a bit risky, e.g. in exercise 2 we were assuming that "gene" never occurs as a word in any other column. From looking at the file it seems so but can we be sure?  
  The easiest solution is to only look for "gene" in column 3:
  ```
awk '$3=="gene" {print}' TAIR10_GFF3_genes.gff | wc -l
   28775
```


2. How many genes are encoded by chromosome?
  ```
grep -w gene TAIR10_GFF3_genes.gff | cut -f1 | sort | uniq -c 
7509 Chr1
4470 Chr2
5650 Chr3
4308 Chr4
6559 Chr5
 133 ChrC
 146 ChrM 
```
We grep all the gene lines and extract the chromsome their are encoded on (the first column). Now we count how many times each chromosome occurs. As `uniq -c` works on a sorted input we sort the chromosome list before piping it into `uniq -c` (Here not necessary as TAIR10_GFF3_genes is already sorted by chromosome, but it's always a good idea not to assume that the input file is sorted). 


3. Find the gene with the highest number of exons (79)
  ```
grep -w exon TAIR10_GFF3_genes.gff | cut -f9 | sort | uniq -c | sort -k1,1nr | head
  79 Parent=AT3G48190.1
  75 Parent=AT1G67120.1
  67 Parent=AT1G48090.1
  66 Parent=AT4G17140.1
  65 Parent=AT4G17140.2
  65 Parent=AT4G17140.3
  61 Parent=AT1G64790.2
  60 Parent=AT1G64790.1
  56 Parent=AT1G50030.1
  56 Parent=AT1G50030.2
```

4. How many genes are not spliced?
  ```
grep -w exon TAIR10_GFF3_genes.gff | cut -f9 | sort | uniq -c | awk '$1==1 {print }' | wc -l
   10740
```   
      
5. Extract exons encoded on Chromosome 3 on positions 10000 – 30000  
  45 exons
  ```
awk '$1=="Chr3" && $3=="exon" && $4>=10000 && $5<=30000 {print }' TAIR10_GFF3_genes.gff | head
Chr3	TAIR10	exon	10106	10161	.	+	.	Parent=AT3G01040.1
Chr3	TAIR10	exon	10265	10423	.	+	.	Parent=AT3G01040.1
Chr3	TAIR10	exon	10507	11097	.	+	.	Parent=AT3G01040.1
Chr3	TAIR10	exon	11302	11604	.	+	.	Parent=AT3G01040.1
Chr3	TAIR10	exon	11698	12444	.	+	.	Parent=AT3G01040.1
Chr3	TAIR10	exon	10106	10161	.	+	.	Parent=AT3G01040.2
...
``` 

6.  How many genes are encoded by the region?
  ```
awk '$1=="Chr3" && $3=="gene" && $4>=10000 && $5<=30000 {print }' TAIR10_GFF3_genes.gff | wc -l
       4
``` 


## List of important commands

a more complete list is available [here](ImportantShellCommands.md)


**File and folder manipulation, compression**

Command | Description
---|------
**pwd**|display current folder|
**ls -l** *path*|list files and folders|
**cd** *path*|change folder to path|
**cd** \~|change folder to home folder|
**mkdir** *name*|make folder|
**rmdir** *name*|remove folder|
**cp** *source* *dest*|copy file/folder and all its contents|
**less** *filename*|display file content|
**wc** *filename*|count number of lines in file|**head**  *filename*|shows first few lines of file|
**tail** *filename*|shows last few lines of file|


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
