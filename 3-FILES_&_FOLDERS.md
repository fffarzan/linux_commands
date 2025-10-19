# FILES & FOLDERS

### touch

```bash
touch <path/to/filename> # 1- create file. It doesn't care about extension. 2- update modification and access time of a file (:/)
touch ../<filename>
touch ~/<filename>
```

### file

```bash
file <path/to/filename> # show the basic type of the file
```

### mkdir

```bash
mkdir <path/to/filename>
mkdir -p <path/to/dir> # for nested directories
```

### nano

in an opened file with nano:

- ^A: start of line
- ^E: end of line
- ^P: prev line
- ^N: next line
- ^Y: prev page
- ^V: next page
- ^I: insert a tab
- ^W: search
- wrapping lines in nano (nano softwrap): ???

Note: nano is different in some shortcuts on mac and linux

```bash
nano <path/to/filename> # if the file doesn't exist, it'll create it.
```

### rm

```bash
rm <path/to/filename> # remove the file
rm -d
rmdir <path/to/dir> # remove empty directortes
rm -r # remove directories and all their contents recursively
rm -R # remove directories and all their contents recursively
rm -i # remove like interactive mode to make sure what you wanna delete
```

### mv

```bash
mv <path/to/source> <path/to/destination> # remove
mv <path/to/source> . # move to current folder
mv source1 source2 ... destination # just one destination
mv <current file/dir name> <new file/dir name> # change file or folders namec
```

cp

```bash
cp <path/to/source> <path/to/destination> # copy. can have multiple sources
cp -r # copy dirs with its contents
cp -v # with verbose output
```
