#🐧 Day 1, PM practical - More advanced shell

### **<u>1. Using Core utilities </u>**

> A. grep: globally search a regular expression and print

- `man grep`

- `grep ’EAS’ sequences.fa`
- `grep ’Contig’ sequences.fa`
- `grep ’contig’ sequences.fa`

- grep -i : grep,case insensitive
`grep -i ’contig’ sequences.fa`

- grep -r: recursive grep
`grep -r ’Contig’ ./`

- You may also combine options, e.g.:

- grep -A: show lines after the grep hit
`grep -i -A 1 ’contig’ sequences.fa` Useful if the sequences are in one line. 􏰀

	- Also try:  
		- `grep -B 10 '<searchterm>' <filename>` (10 lines Before)􏰀
		- `grep -C 5 '<searchterm>' <filename>` (5 lines of Context)
		- Combinations are possible: `grep -A 1 -B 2 '<searchterm>' <filename>` (1 line After, 2 lines Before the hit)

> 	B. Output redirection: > (write to file)

- `grep ’Contig’ sequences.fa >> selection.fa`

> 	C. sed: stream editor

- Add taxa name to end of all header lines:

	`sed 's/>.*/& Escherichia coli/' sequences.fa > outfile_sed.fa`

	D. awk: 'awk' stands for the names of its authors “Aho, Weinberger, and Kernighan”
	
- Clean up a fasta file so only first column of the header is outputted:

	`awk '{print $1}' sequences.fa > output_awk.fa`

### **<u>2. Working with FASTA files</u>**

>	A. wc: count number of lines, words, characters

- Mnemonic: wc → word count. `-l ` (for counting lines) is the most commonly used option. More information: `man wc`.

- **Exercise: sequence count**

	- Find a way to output the number of Sequences in a FASTA file.
You may use ‘temporary’ files.

		- **Possible solutions: sequence count**

			`grep ’>’ sequences.fa > tempfile.txt`
`wc -l tempfile.txt`

> B. Output redirection: | (pipe)
‘Pipes’ the output of  `ls -1` into the input of `wc -l`. 􏰀 Prints out the number of items in this directory.

- `grep ’>’ | less`
 
	- Displayed using  less:

- **Exercise: filter;**

	- Possible solution: 

- **Exercise: one specific line;**
Output line number 19 of a given file.
	- Possible solution: 

	- Possible solution: 
`grep ’>’ sequences.fa | head -n 3 > newfile.fa` or

#**<u>3. Managing Files</u>**

> A. tar: tape archive

`tar -cvf new_tar_archive.tar <list>`

-  `c`: create new archive

Show the content of a tar archive:

Unpack a tar archive:

> B. gzip: compress files

- `gzip sequences.fa`
Mnemonic: `d` → decompress􏰀 

# **<u>4. Transfer a file to /pool/genomics</u>**
> A. scp: secure copy

`scp [options] <username1>@source_host:/directory1/filename1 <username2>@distination_host:/directory2/filename2`

- Name of the account on the host computer (username1)
- [options] 

	- `-p` for preserve time info (can be very helpful to keep track of what is what)
	- `-r` copy directory
- Hostname of the computer on which the source file resides (source_host = hydra-login01)
- Name of the directory containing the source file (directory1)
- Filename of the source file (filename1)
- The location to which the source file will be copied is specified by username2@destination_host:directory2/filename2, which includes the:
	- Name of the account on the destination computer (username2)
	- Hostname of the computer to which the source file will be copied (destination_host)
	- Name of the directory to which the source file will be copied (directory2)
	- Filename of the copy (filename2)

- For more information: `man scp`

- **Exercise: compress and transfer to your local computer**	
	- In hydra-3: `gzip sequences.fa` 
	- In local terminal: `scp -p <username>@hydra-login01:/pool/cluster0/workshop/<username>/Day1/data/sequences.fa.gz ./`

	

 
