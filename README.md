

__Problem 1: For the pipeline below, describe the text that passes through each of the pipes and into the final redirect (`final.txt`).__      cat animals.txt | head -n 5 | tail -n 3 | sort > final.txt

We start with the original list of animals.txt, which is displayed chronologically by using cat. This list is piped, and the top five samples are kept and piped again. At this point those bottom three samples are selected. These final samples are then ordered reverse chronologically with the most recent on top and the oldest on bottom and sent to the final.txt file.

__Problem 2: What other command(s) could be added to this in a pipeline to find out what animals the file contains (without any duplicates in their names)? 

To the original command (cut -d , -f 2 animals.txt) you would add “| sort -n | uniq”

__Problem 3: Assuming your current directory is `data-shell/data/`, write a command with pipes to produce a table that shows the total count of each type of animal in the file__

cut -d , -f 2 animals.txt | sort | uniq -c

__Problem 4: Morgan has a directory full of tree ring measurement files that he inherited from a previous student who was poorly organized. The files are organized by a 7-character ID:__

``
##NOTE: these are codes I have been trying to implement in one way or another. The first line is my most succesful line so far.

wc -l *.txt | sort -n | tail -n 24

| cut -c 1-7 *.tx

cut -d , -f 1 *.txt
``
