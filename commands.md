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
11. ```locate``` command: search any files containing the following word. ```locate book``` is used to search any files that contain book. ```find -name notes.txt``` is used to find the path of notes.txt from the current directory.
12. ```grep``` search words in given file. ```grep blue notepad.txt``` will search for the word blue in the notepad file. Lines that contain the searched word will be displayed fully.
