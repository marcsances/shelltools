# shelltools

This folder will contain some shell tools / scripts that I find useful to work with terminals.

## Installation

Copy the scripts to your PATH, for example copy all to /usr/local/bin. Make sure the files are executable.

## The tools

### drag / drop

Literally can drag files and then drop them somewhere else, as you would do in your favorite graphic file manager, useful for dealing with long paths.

Example:

```bash
user@host:/home/folder1 $ drag *
user@host:/home/folder1 $ cd /home/folder2
user@host:/home/folder2 $ drop
user@host:/home/folder2 $ ls
file1 file2 file3 folder1
```

Use ``drop -m`` to move instead of copying the files. That's all it can do!

### goodreadlink

Copied from https://stackoverflow.com/questions/1055671/how-can-i-get-the-behavior-of-gnus-readlink-f-on-a-mac to give a quick solution to the problem that readlink -f doesn't get cannonical names in macOS.

No warranties whatsoever. It is required to make drag/drop commands work in macOS.

### notes

It allows you to make quick notes from the terminal, inspired by the game Hacknet.

It has three commands: addNote, rmNote and notes. Notes are stored at ~/.notes.

```bash
# add notes
$ ./addNote Hello
$ ./addNote Some test
$ ./addNote Goodbye
# display notes
$ ./notes
     1	2019-03-26 11:38:52: Hello
     2	2019-03-26 11:38:56: Some test
     3	2019-03-26 11:38:59: Goodbye
# remove a certain note
$ ./rmNote 2
$ ./notes
     1	2019-03-26 11:38:52: Hello
     2	2019-03-26 11:38:59: Goodbye
# remove all notes
$ ./notes -c
$ ./notes
Nothing here!
```
