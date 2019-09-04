
## HW_2: Pipe Problems  
This homework can be completed by editing this file with your answers.

#### For problems 1-4, use `animals.txt` (in the `data-shell/data` folder)  

__Problem 1: For the pipeline below, describe the text that passes through each of the pipes and into the final redirect (`final.txt`).__

`cat animals.txt | head -n 5 | tail -n 3 | sort > final.txt`

Hint: build the pipeline up one command at a time to test your understanding.

__Answers__  
`cat animals.txt` will show all the content of animals.txt.  
```
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-06,fox,4
2012-11-07,rabbit,16
2012-11-07,bear,1
```  
`head -n 5` will show the first five lines of the text file.  
```
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
```  
`tail -n 3` will show the last 3 lines of the result of previous command. This means line 3, 4, and 5 of animals.txt.   
```
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
```  
`sort > final.txt` will align the first column of the file in descending order and export the data into a text file, which is named as final.txt. The resulting file will have lines 3-5 of animals.txt sorted by date (newest first).   
```
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-05,raccoon,7
```  


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

__Answer__  
`|sort | uniq`  
#`sort` will align duplicated data, that are scattering in the file, adjacent to each other. And `uniq` will delete these adjacent duplications.


__Problem 3: Assuming your current directory is `data-shell/data/`, write a command with pipes to produce a table that shows the total count of each type of animal in the file__

a.	`grep {deer, rabbit, raccoon, deer, fox, bear} animals.txt | wc -l`  
b.	`sort animals.txt | uniq -c`  
c.	`sort -t, -k2,2 animals.txt | uniq -c`  
d.	`cut -d, -f 2 animals.txt | uniq -c`  
e.	`cut -d, -f 2 animals.txt | sort | uniq -c`  
f.	`cut -d, -f 2 animals.txt | sort | uniq -c | wc -l`  

__Answer__  
e. `cut -d, -f 2 animals.txt | sort | uniq -c`  
#`cut -d, -f 2 animals.txt` will extract the second column of animals.txt, and `sort` will align these animals' name alphabetically. Then, `uniq -c` will count the number of duplicated occurrences of the data file.  


### For Remaining Problem, Use HW_2/tree_data  

__Problem 4: Morgan has a directory full of tree ring measurement files that he inherited from a previous student who was poorly organized. The files are organized by a 7-character ID:__

`SSPPTTC.txt`  
S - site number  
P - plot number  
T - tree number  
C - core id (could be A, B or C)  
Ex: 130101A.txt  

Morgan is only interested in the raw data (the tree ring measurement files [`.txt`] noted by the 7-character IDs above: SSPPTTC). In addition, some of the files are too short to use and some files have data that are repeated. 

Write a line of code that will create a text file containing a list of the unique tree IDs (no repeats, no extensions) that have at least 5 lines of data. Build it up, one pipe at a time.

__Answer__  
`wc -l *.txt | sort -r | head -n 25 | tail -n 24 | cut -c 7-13 > tree_ID.txt`  
 

### To Submit
1) Fork the repo
2) Clone to your machine
3) Create a new branch
4) Edit this README.md file to add your answers.  Use code blocks for code.
5) Commit changes.
6) Submit a pull request on hessllab/HW_2
