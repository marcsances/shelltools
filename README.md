# cps, mvs
copy and move files to the previous directory of the directory stack

This is a dead simple script that makes terminal file management a little easier.

It copies whatever arguments it's given to the top of the directory stack (i.e. the last folder pushed using ``pushd``), so you don't have to mess around typing in long paths.

For the rest, it works exactly like cp.

## Installation

Just ``sudo make install`` to get the scripts in your ``/usr/local/bin`` folder.

Then ``source ~/.bashrc`` to add cps and mvs aliases.

## Examples

I want to get a file that is in some folder far away...

```bash
user@host:/home/my/very/long/directory $ pushd /home/
/home/ /home/my/very/long/directory
user@host:/home $ cd another/long/directory
user@host:/home/another/long/directory $ ls
some_file_which_name_i_dont_remember.c
user@host:/home/another/long/directory $ cps some_file_which_name_i_dont_remember.c
cp some_file_which_name_i_dont_remember.c /home/my/very/long/directory/
user@host:/home/another/long/directory $ popd
/home/my/very/long/directory
user@host:/home/my/very/long/directory $ ls
some_file_which_name_i_dont_remember.c
```

Or maybe I want to move all files from a directory:

```bash
user@host:/home/my/very/long/directory $ pushd /home/
/home/ /home/my/very/long/directory
user@host:/home $ cd folder/with/many/subfolders
user@host:/home/folder/with/many/subfolders $ ls
folder1/ folder2/ file
user@host:/home/folder/with/many/subfolders $ mvs -R *
cp -R * /home/my/very/long/directory/
user@host:/home/folder/with/many/subfolders $ popd
/home/my/very/long/directory
user@host:/home/my/very/long/directory $ ls
folder1/ folder2/ file
```

## Even kiddos can make this!

I wrote it for me, and keeping here for handyness, nothing else.

## What is that apparam.sh thing?

Things turned a bit trickier than expected when writing this script.

Initially I was gonna make a script that would invoke cp using the directory stack, well, that doesn't work because the directory stack is gone after you start a script.

Then I thought on making an alias, as I can call ``$(dirs -p +1)`` to get the last pushed directory from the stack. Problem is that ``alias`` command will prepend that directory (which will make cp think it's the source directory instead of the destination).

So my workaround has been making a small script that just stores the first argument, shifts and calls the rest of the arguments with the first argument at the end.

So it basically appends the first parameter to the end of the argument list then invokes such argument list.

I install that script for simplicity, but you can come with simpler solutions.

## Known issue

Directories with spaces are not working yet. This was a quick dirty script to save some time, not to waste it on thinking how to make spaces work lol.

If I come up with a viable solution for making these work, I will upload it.
