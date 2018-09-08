---
title: "Linux I: Knowing and Using the Terminal"
date: 2018-08-09T21:19:00-03:00
author: "Amintas Victor"
type: "post"
---

For those who are now being introduced to Linux, handling the terminal can at the same time fascinate, give a belly cold. In order to learn the basics about handling this very important tool in the use of any Linux distribution, and of course, if we lose any preconceptions about the command prompt, we will see in this article the **main commands in the Linux terminal**.

<!--more-->

# Working with files and directories

1. To find the current directory, use the ```pwd``` command.
2. If we want to list the files and directories in the current directory, use the command ```ls```.
  1. Similarly, we can list the files and directories in the current directory in detail through the ```ls -l``` command.
  2. In a similar way, we can include in the detailed listing the hidden files: ```ls -la```.
  3. We can list the files and directories in a specific directory with the command ```ls directory```.
3. We can print a message in the terminal through the command ```echo "message"```.
4. We can create and overwrite a file using the command ```echo "message" > file.extension```.
5. If we want to read a file in the directory, showing its contents in the terminal, we can use the command ```cat file.extension```.
6. To clear the screen, we use the ```clear``` command.
7. To obtain the documentation of a particular command, we use the following command: ```man command```. To navigate through the documentation, we use the up and down arrows and ```q``` to exit.
8. To get the username, we use the ```whoami``` command.

# More about redirect and wildcard characters in bash

1. To enter a directory, we use the ```cd path``` command, where the PATH of the directory is relative to the current directory.
  1. We can also use the command ```cd  ~/path```, where the PATH of the directory is relative to the base directory.
  2. We use the same command ```cd home/user/path```, where the PATH of the directory is relative to the root directory.
2. We add a line to a file with the command ```echo "message" >> file.extension```.
3. Return to the current directory using the command ```cd ..```. In the same way we can go to the users directory using the command ```cd```.
4. Some references to directories:
  1. Current directory: ```.```.
  2. Previous directory, or higher: ```..```.
  3. Root directory: ```/```.
  4. User directory: ```/ home```.
5. To create a directory, we use the command: ```mkdir directory_name```.
6. To remove a file, we use the command ```rm file.extension```.
7. To remove a directory without subdirectories, we use the command ```rmdir directory```.
8. To remove a directory and its subdirectories recursively, we use the command ```rm -r directory```.
9. Here are some wildcard characters in bash:
  1. We use ```?``` To represent any character.
  2. We use ```*``` to represent any substring.

# Manipulating, compressing and unzipping files.

1. To make a copy of a file, we use the following command: ```cp original.extension copy.extension```.
2. Rename a file using the following command: ```mv old_name.extension new_name.extension```.
3. We move files using the command ```mv file.extension directory/```. We can also rename the file by moving it using the command ```mv old_name.extension directory/ new_name.extension```.
4. We can list the files of the current directory and subdirectories recursively with the command ```ls *```.
5. We make a copy of a directory with the command ```cp -r original_directory copy_directory```.
6. We can compress a file as zip with the command ```zip compressed_file.zip file.extension```. Likewise, we can "zip" a directory recursively with the command ```zip -r compressed_file.zip directory/```.
7. We can list the inside of a zip file with the command ```unzip -l file.zip```.
8. Uncompress a zip file with the command ```unzip.zip```. We can make the process silent with the command ```unzip -q file.zip```.

Note: We can combine flags, so the command ```zip -r -q compressed_file.zip directory/``` can be written as ```zip -rq compressed_file.zip directory/```.

# Compacting and decompressing tar

1. We can compress using tar from the following command: ```tar -cz directory > file.tar.gz```. By default, this is a recursive, quiet process.
2. We can decompress using tar from the following command: ```tar -xz < file.tar.gz```. This same command can be written as ```tar -x < file.tar.gz```.
3. If we do not want to work with data entry redirects (```<```) and data output (```>```), we can use the following commands:
  1. ```tar -czf file.tar.gz directory/```, to compress using tar.
  2. ```tar -xzf file.tar.gz``` or``` tar -xf file.tar.gz```, to unzip using tar.
  3. ```tar -vczf file.tar.gz directory/```, to compact verbosely using tar.
  4. ```tar -vxzf file.tar.gz``` or``` tar -vxf file.tar.gz```, to unpack verbosely using tar.

Note: In reality, tar only packs data and uses compactors such as gzip (.gz). There are other external compactors like bzip2 (.bz2). To use it in commands, simply replace ```-z``` with``` -j``` and the extension```tar.gz``` with ```.tar.bz2```.

# More on compression and unpacking and terminal commands

1. We can change the date and time of last modification of a file with the command ```touch file.extension```.
2. We can check the current date and time of the system with the command ```date```.
3. We can display current date and time data with the command ```date "+data"```. Use the ```date --help``` command to see what data can be displayed on the terminal.
4. We can access quick help with the ```help command``` command or ```--help command```.
5. We can read the first 10 lines of a file through the command ```head file.extension```. We can read the first x lines of a file through the command ```head -n x file.extension```.
6. We can read the last 10 lines of a file via the command ```tail file.extension```. We can read the last x lines of a file through the command ```tail -n x file.extension```.
7. We can read an entire file using ```less``` reader via the``` less file.extension``` command. To navigate the player, simply use the up and down arrows.

# Editing files with the VI: inclusion, change, deletion, repetition

1. To open a file with the VI we use the command ```vi file.extension```.
2. We move from the **navigation mode and commands**, which is opened by default, to the **insert mode** with ```i``` or``` a```, and vice versa with ```esc```.
3. To make uppercase letters ```Shift + letter```, instead of ```Caps lock```.
4. The most commonly used editing commands in the **navigation mode and commands** are listed below:
  1. ```w```, to save.
  2. ```q```, to exit. We can exit without saving with the command ```q!```.
  3. ```x```, to remove the current character. We can remove n characters with the command ```nx```.
  4. ```i```, to insert in the current character.
  5. ```a```, to enter in the next character.
  6. ```dd```, to remove current row. We can remove n rows with the ```ndd``` command.
  7. ```A```, to enter at the end of the line.
5. The most commonly used navigation commands in the **navigation mode and commands** are listed below:
  1. ```G```, to go to the last line. We can go to the nth line with the command ```nG```.
  2. ```gg```, to go to the beginning of the file.
  3. ```$```, to go to the end of the current line.
  4. ```O```, to go to the beginning of the current line.
  5. ```/word```, to search for a word in the text.
  6. ```n```, to go to the next occurrence.
  7. ```N```, to go to the previous occurrence.
  8. ```yy```, to copy the current line. We can copy 2 lines with the command ```y``` and n lines with``` nyy```.
  9. ```p``` to paste and ```np``` to paste n times.

Note: We can combine commands. For example, to save and exit we use the command ```wq```.
