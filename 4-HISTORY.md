# HISTORY

it's a file: ~/.bash_history (not exist on mac?!)

### less

```bash
less <path/to/filename> # open a content with interactive view
```

### history

ctrl + r --> search in history

```bash
history
history | less
!<number of line> # run the command of that line in history

echo $HISTSIZE # size of history stored in memory
```

### cat

```bash
cat <path/to/filename> # concatinate. if you set one input, it just displays the content
cat <file1> <file2> # combine files to show
cat -n # show content with number of lines
```

### tac

```bash
tac <path/to/filename> # concatinate files like cat but in a reverse mode! Just reversing what is printing out # doesn't exist on mac.
```

### rev

```bash
rev <path/to/filename> # reverse every character in a horizontal line! Just reversing what is printing out
```

### head

```bash
head <path/to/filename> # head of the file. Shows first 10 lines
head -n <number> # number of lines
head -<number>
head -c <number> # specific number of bytes
```

### tail

```bash
tail <path/to/filename>
tail -n  <number>
tail -<number>
tail -c <number>
tail -f # interesting (best usage: tail -f syslog --> to monitor last logs immediately)
```

### wc

```bash
wc <path/to/filename> # Word Count. lines, words, bytes
wc -l # lines
wc -w # words
wc -c # bytes
wc -m # chars
```

### sort

```bash
sort <path/to/filename>
sort -r # reverse
sort -u # unique only
sort -n # for numerical values and prevernt to mess fload values
sort -k<number> # sort the kth column of the list
sort -h # human readable sort

sort -k<number>h
```
