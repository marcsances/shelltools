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
