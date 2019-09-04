
## HW_2: Pipe Problems  
This homework can be completed by editing this file with your answers.

#### For problems 1-4, use `animals.txt` (in the `data-shell/data` folder)  

__Problem 1: For the pipeline below, describe the text that passes through each of the pipes and into the final redirect (`final.txt`).__

`cat animals.txt | head -n 5 | tail -n 3 | sort > final.txt`

`cat animals.txt` reads the content of the text file and passes it to the `head -n 5` which in turn returns the first 5 lines of the text file. These 5 lines are then passed to the `tail -n 3` which then returns the last 3 lines. These 3 lines are then sorted and appended to a text file called `final.txt`. if this text file is not present, it creates a new file and then writes the 3 lines into it.
Hint: build the pipeline up one command at a time to test your understanding.

__Problem 2: For the file _animals.txt_ from the previous exercise, the command:
`cut -d , -f 2 animals.txt` . 
uses the `-d` flag to separate each line by comma, and the `-f` flag to print the second field in each line, to give the following output:__
```
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```
What other command(s) could be added to this in a pipeline to find out what animals the file contains (without any duplicates in their names)? 

`cut -d , -f 2 animals.txt | sort | uniq`

__Problem 3: Assuming your current directory is `data-shell/data/`, write a command with pipes to produce a table that shows the total count of each type of animal in the file__
 
e.	`cut -d, -f 2 animals.txt | sort | uniq -c`   

### For Remaining Problem, Use HW_2/tree_data  

__Problem 4: Morgan has a directory full of tree ring measurement files that he inherited from a previous student who was poorly organized. The files are organized by a 7-character ID:__

`SSPPTTC.txt`  
S - site number  
P - plot number  
T - tree number  
C - core id (could be A, B or C)  
Ex: 130101A.txt  

Morgan is only interested in the raw data (the tree ring measurement files [`.txt`] noted by the 7-character IDs above: SSPPTTC). In addition, some of the files are too short to use and some files have data that are repeated. 

`wc -l *[ABC].txt | sort `
###still figuring out what to do next

Write a line of code that will create a text file containing a list of the unique tree IDs (no repeats, no extensions) that have at least 5 lines of data. Build it up, one pipe at a time.

### To Submit
1) Fork the repo
2) Clone to your machine
3) Create a new branch
4) Edit this README.md file to add your answers.  Use code blocks for code.
5) Commit changes.
6) Submit a pull request on hessllab/HW_2
