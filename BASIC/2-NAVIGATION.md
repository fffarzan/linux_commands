# NAVIGATION

- root dir: "/"
- home dir : "~"

Important Directories:

- bin: bunch of built-in executable programs like pwd
- etc: configuration files and scripts
- var: related to logging and log files, caches
- usr: executable files of programs that we installed

Paths:

- relative path: relative to current directory
- absolute path: starts with "/", from root directory

Here is most useful commands and their options:

### open

```bash
open / # opens root dir
open ~ # opens home dir
```

### pwd

```bash
pwd # Print Working Dir
```

### ls

```bash
ls
ls <dirname or path/to/file>
ls -l # long listing format (with more data about the files and dirs).
ls -a # all. includes hidden ones
ls -la
ls -h # human readable (specially as -lh)
ls --sort=WORD # (NOT ON MAC) time, size, none, version, extension -->
ls -t # sort by time modified
ls -1 # remove first line (first line shows the total number)
```

### cd

```bash
cd <dirname or path/to/file> # Change Dir
cd . # current dir
cd .. # parent dir
cd ~ # changes to home
cd / # changes to root
```
