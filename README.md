

## HW_2: Pipe Problems  
Zack Grzywacz

__Problem 1: For the pipeline below, describe the text that passes through each of the pipes and into the final redirect (`final.txt`).__

`cat animals.txt | head -n 5 | tail -n 3 | sort > final.txt`

## Answer:
```
cat animals.txt #prints the entire animals.txt file, which consists of two columns
| head -n 5 #prints the first five entries in animals.txt
| tail -n 3 #takes the five entries produced from "head" and reduces it to the final 3 entries in that set
| sort > final.txt # sorts the three entries in alphabetical order and prints them in a new file named final.txt
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

## Answer:
```
cut -d, -f 2 animals.txt | sort | uniq #Sort puts the animals in alphabetical order so that animals of the  
same name are adjacent. Then uniq removes the duplicates
```

__Problem 3: Assuming your current directory is `data-shell/data/`, write a command with pipes to produce a table that shows the total count of each type of animal in the file__

## Answer:
e.	`cut -d, -f 2 animals.txt | sort | uniq -c`  

```
cut -d, -f 2 animals.txt | sort | uniq -c #the tag -c for uniq prefixes each line with the number of  
occurences. This produces the total count of each type of animal in the file
```

__Problem 4: Morgan has a directory full of tree ring measurement files that he inherited from a previous student who was poorly organized. The files are organized by a 7-character ID:__

`SSPPTTC.txt`  
S - site number  
P - plot number  
T - tree number  
C - core id (could be A, B or C)  
Ex: 130101A.txt  

Morgan is only interested in the raw data (the tree ring measurement files [`.txt`] noted by the 7-character IDs above: SSPPTTC). In addition, some of the files are too short to use and some files have data that are repeated. 

Write a line of code that will create a text file containing a list of the unique tree IDs (no repeats, no extensions) that have at least 5 lines of data. Build it up, one pipe at a time.

## Answer:

```
wc -l *[ABC].txt | sort | tail -n 25 | head -n 24 | cut -c 7-17 | sort | uniq > unique_ID.txt
# First, all files in the correct title format are listed along with the number of lines they   
contain. Then, they are sorted by the number of lines they contain. Tail and head are used to   
remove the files that contain fewer than 5 lines of data, as well as the "total" at the bottom of   
the list. cut is used to remove the number of lines from the file names. Sort is used so that uniq  
can remove any identical titles, as duplicates would be adjacent. The final list is then written to   
unique_ID.txt
#Note: On my windows machine, sort does not require -n to sort a list numerically. In fact, using -n   
gives an error. You may need to add -n to sort a list numerically
```
