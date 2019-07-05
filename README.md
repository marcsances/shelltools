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

### git-branchnote

If you are a dev who has to keep track of several Git branches simultaneously as me, you will find out the _notes_ command useful. You can `addNote myBranch: does whatever my branch shoudl do`, so if you have to checkout back to such branch, you know something else than the name. If your branch names are not very descriptive because of project requirements (us2811, v2.3.4), keeping notes will help you out.

git-branchnote is just a small script that automatically creates a branch with checkout with the first parameter as name, and adds a note with the arguments as addNote would.

The usage, therefore, is: `git branchnote myNewBranch does things that a new branch should`. As simple as it looks. 

### here/there

In a similar fashion than drag/drop, here/there allows you to export the current directory and change to it from another terminal (or do some other stuff). However, due to the problem that commands are run in a subshell, "there" will only output the path, and you have to manually cd there:

```bash
# from terminal A in directory X
me@pc X $ here
# from terminal B in directory Y
me@pc Y $ there
/home/me/X
me@pc Y $ cd $(there)
me@pc X $
```

### bookmark

Allows you to have bookmarks in the terminal, either directories or files, for later use.

```bash
# bookmark the current location
me@pc directoryA $ bookmark -s
# list bookmarks
me@pc directoryZ $ bookmark
    1 /home/test/directoryA
# cd to bookmark
me@pc directoryZ $ cd $(bookmark 1)
me@pc directoryA $
# remove a bookmark
me@pc directoryZ $ bookmark -r 1
me@pc directoryZ $ bookmark
me@pc directoryZ $
# add a file to bookmarks
me@pc directoryX $ ls
fileA
me@pc directoryX $ bookmark fileA
me@pc directoryX $ bookmark
    1 /home/test/directoryX/fileA
me@pc directoryZ $ cp $(bookmark 1) .
me@pc directoryZ $ ls
fileA
# remove all bookmarks
me@pc directoryZ $ bookmark -c
```

