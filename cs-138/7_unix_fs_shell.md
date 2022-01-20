# Filesystem and Bash Shell

### Filesystem

Pretty much all OS's have a filesystem.
* For small OS's, it's sometime a flat space.
* In general, it's a tree-like hierarchy.

Generally, conventions which files go where. For example:

* `bin/`: Compiled binaries go here
* `user/`: Each user gets a folder here
* `user/trevor/home`: Where each user's personal files go (shorthand: `~`)
* And more!

### UNIX Shell

Lots of different types, we use Bash.

```
pwd     <-- Prints working directory
cd      <-- Takes you to home
cd -    <-- Takes you to prev directory
cd ..   <-- Takes you to parent of durr dir
cd .    <-- . is the current directory
```
```
$ pwd
/user/trevor

$ cd temp
$ pwd
/user/trevor/temp

$ ls
balloon.cc folder/

$ g++ balloon.cc
$ ./a.out
Inflating...
Inflating...
Inflating...
BANG!

$ cd folder
$ pwd
/user/trevor/temp/folder

$ ls
readme.txt

$ cat readme.txt
Hi! Thanks for reading me!
cat prints the text out of a file.
```

### PATH

An environment variable that specifies which folders to search for commands in.

```
e.g. /usr/bin, /bin, /usr/local/bin, $HOME/bin
```