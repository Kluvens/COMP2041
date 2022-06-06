## Linux commands

1. ```pwd``` command: to find out the path of the current working directory you are in. The command will return an aboslute path.
2. ```cd``` command: to navigate through the Linux files and directories (cd means change directory). It requires either the full path or the name of the directory, depending on the current working directory that your are in. ```cd .``` will leave the user in the same directory they are currently in. ```cd``` will always put the user in their home directory. ```cd ..``` will move the user up one directory. 
3. ```ls``` command: to view the contents of a directory. By default, this command will display the contents of your current working directory. ```ls -R``` will list all the files in the sub-directories as well. ```ls -a``` will show the hidden files. ```ls -al``` will list the files and directories with detailed information like the permissions, size, owner, etc. ```ls -l``` can also be used to show more details.
4. ```cat``` command: ```cat``` is short for concatenate, this is one of the most frequently used commands in Linux. It is used to list the contents of a file on the standard output. ```cat file.txt``` is the way we use it. ```cat > filename``` creates a new file. ```cat filename1 filename2 > filename3``` joins two files(1 and 2) and stores the output of them in a new file(3)
5. ```cp``` command: to copy files from the current directory to a different directory. For instance, the command ```cp scenery.jpg /home/username/Pictures``` would create a copy of ```scenery.jpg``` (from your current directory) into the ```Pictures``` directory.
6. ```mv``` command: to move files, although it can also be used to rename files. To move: ```mv file.txt /home/username/Documents``` and to rename: ```mv oldname.ext newname.ext```.
7. ```mkdir``` command: to make a new directory. ```mkdir Music``` is used to create a directory called ```Music```.
8. ```rmdir``` command: to delete empty directories.
9. ```rm``` command: to delete directories and the contents within them. ```rm -r``` means recursively delete, so this is used to delete a directory.
10. ```touch``` command: to create a blank new file through Linux command line.
11. ```locate``` command: search any files containing the following word. ```locate book``` is used to search any files that contain book. 
12. ```find -name notes.txt``` is used to find the path of notes.txt from the current directory.
13. ```grep``` search words in given file. ```grep blue notepad.txt``` will search for the word blue in the notepad file. Lines that contain the searched word will be displayed fully.
14. ```df``` command to get a report on the system's disk space usage, shown in percentage and KSs. If want to see the report in megabytes, then use ```df -m```.
15. ```du``` command to check how much space a file or a directory takes. However, the disk usage summary will show disk block numbers instead of the usual size format. If want to see it in bytes, kilobytes, and megabytes, add the ```-h``` argument to the command line.
16. ```head``` command is used to view the first lines of any test file. By default, it will show the first ten lines, but we can change the number to show. e.g. ```head -n 5 filename.txt.```
17. ```head``` command is used to view the last ten lines of a text file. More change we can do ```tail -n 5 filename.txt```
18. ```diff``` command compares the contents of two files line by line and show the difference of the two files. e.g. ```diff file1.ext file2.ext```
19. ```chmod``` command is a Linux command used to change the read, write and execute permissions of files and directories.
20. ```kill``` command is used to terminate an unresponsive program manually. It will send a certain signal to the misbehaving app and instructs the app to terminate itself.
21. ```ping``` command is used to check the connectivity status to a server.
22. ```uname``` command is short for Unix name and used to print detailed information about your Linux system.
23. ```history``` command is used to review the commands the user has entered before.
24. ```echo``` command is used to move some data into a file.
25. ```man``` command is used to display the user manual of any command that we can run on the terminal.
26. ```zip``` command is used to compress the files into a zip archive, and use the ```unzip``` command to extract the zipped files from a zip archive.
27. ```hostname``` is used to know the name of the host/network. Adding a ```-i``` to the end will display the IP address of network.
28. ```wc``` is word counter to summarize its input as a single line. This is often used as last command in pipeline. ```-c```  print the number of characters. ```-w```  print the number of words. ```-l```  print the number of lines only.
29. ```tr``` command reads chars and writes characters, mapping(replacing) some chars with others in a given file. e.g. ```tr 'abc' '123' < file.txt``` means in the in file.txt, change `a` to `1`, `b` to `2` and `c` to `3`. ```-c``` maps all bytes not occurring in 𝑠𝑜𝑢𝑟𝑐𝑒𝐶ℎ𝑎𝑟𝑠 (complement). ```-s``` squeezes adjacent repeated characters out (only copy the first). ```-d``` deletes all characters in 𝑠𝑜𝑢𝑟𝑐𝑒𝐶ℎ𝑎𝑟𝑠 (no 𝑑𝑒𝑠𝑡𝐶ℎ𝑎𝑟𝑠). e.g. ```tr -d '0-9' < text.txt``` will delete all digits from text.txt.
30. ```cut``` command prints selected parts of input lines. Options include: ```-f``` (list of cols) - prints only the specified fields on output. e.g. ```cut -f2 data.txt``` means print the second column of data.txt. ```-c``` (list of positions) - prints only chars in the specified positions. e.g. ```cut -c1-5 data``` means print the first five chars on each line. ```-d``` - use character c as the field separator. e.g. ```cut -d'|'``` separate with vertical bar(|). And ```cut -d'|' -f1-3 data``` means print the first three columns, if '|'-separated.
31. ```sort``` command copies input to output but ensures that the output is arranged in some particular order of lines. Some options include: ```-r``` - sort in descending order. ```-n``` - sort numerically rather than lexicographically. ```-d``` dictionary order, ignore non-letters and non-digits. ```-tc``` - use character c to separate columns. ```-kn``` - sort on column n.
32. ```uniq``` command removes all but one copy of adjacent identical lines. Some options are ```-c``` - also print number of times each line is duplicated. ```-d``` - only print (one copy of) duplicated lines. ```-u``` - only print lines that occur uniquely (once only).
33. ```sed``` is an editor for streams(pipelines) and ```sed``` is not interactive - editing commands specified on command-line or in a file. Editing commands are ```p``` - print the current line. ```d``` - delete (don't print) the current line. ```s/regex/replace/``` - substitute first occurence of string matching regex by replace string. ```s/regex/replace/g``` - substitute all occurences of string matching regex by replace string. ```q``` - terminate execution of sed. e.g. 
- ```sed 's/unix/linux/' geekfile.txt``` this command replaces the word "unix" with "linux" in the file called geekfile.txt. 
- ```sed 's/unix/linux/2' geekfile.txt``` this command means replace the second occurence of "unix" in the file. 
- ```sed 's/unix/linux/g' geekfile.txt``` this command means replace all the occurences of "unix". 
- ```sed 's/unix/linux/3g' geekfile.txt``` this command means replacing from nth occurence to all occurences. 
- ```sed '3 s/unix/linux/' geekfile.txt``` replacing string on a specific line (3 in this case). 
- ```sed -n 's/unix/linux/p' geekfile.txt``` print only replaced lines.
