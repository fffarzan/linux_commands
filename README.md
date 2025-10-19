# SAMPLE COMMANDS

command -options arguments

```bash
clear

date # today date and time
date -u # returns universal
date --universal # returns universal (doesn'r work on mac)

ncal # returns current day as cakendar
ncal 1995 # returns the whole year  in calendar
ncal jul 1995 # return the target month of the year
ncal -j # returns day of the year
ncal -h # returns the current month without current day highlight
ncal -M # we don't have it on mac
ncal -3 # returns the three month that the middle month is the curremt month
ncal -A 1 # one month after than current month
ncal -A1
ncal -B 2 # two months before the current month
ncal -B2
ncal -A1 -B2
ncal -w # the number of the week below each week column.

cal # horizontal calendar

echo "fffarzan" # returns fffarzsn
echo fffarzan # returns fffarzsn

rm <filename>
```

# SHORTCUTS

clear --> ctrl + l
jump to start of a line --> ctrl + a
jump to end of a line --> ctrl + e
delete text from current cursor to end of line --> ctrl + k
delete whole line --> ctrl + u
delete the char under the cursor --> ctrl + d
delete from the current cursor to beginning of the current word --> ctrl + w
revive killed text --> ctrl + y

# STREAM

```bash
<command> > <filename> # redirect standard output
date > today.txt # ex: write output of date inside of today.txt file c
<command> >> <filename> # append to the end of the file
<command> < <filename> # redirect standard input
cat < <filename> # provide an input for cat command by passing content! like: cat <filename>
sort < <filename>
<command> < <filename> > <filename> # combo!
<command> < <filename> >> <filename> # another conbo
<command> 2> <filename> # redirect error to a file
<command> 2>> <filename> # append error to the end of a file

cat bees.txt ants.txt > insects.txt 2>> error.txt # example
```

standard input: 0 --> "0<"
standard output: 1 --> "date > now.txt" or "date 1> now.txt" / "1>>"
standard error: 2 --> "2>" / "2>>"

Fancy shortcut: ls docs > "output.txt 2> output.txt" === "ls docs > output.txt 2>&1"
Fancy shortcut: input and output together: "ls docs &> output.txt" / "ls docs &>> output.txt "

# PIPE

connect two commands. Ex: we can't write this: "rev date" but we can write "date | rev". output of first command will be applied to the second command.

- character classes: digit / lower / upper / alpha / blank / punc / space

```bash
ls -l <filename > | less

cat <filename> | tr a-z A-Z # capitalize all chars
cat <filename> | tr -d s # delete every s chars
cat <filename> | tr -d [:alpha:] # delete every aphabetic char

cat -n <filename> | head -m | tail -p # give us the exact line that we want!
ls -lh /usr/bin | sort -k5h | tail -3

du -ha <path> # size of folder and files in a human readable shape

<command> | tee <filename> | <command> # tee stores the result of first command in specific file and the output of first command is also passing to the second
```

# EXPANSION

wildcard chars (glob patterns):

- "\*": expansion to every single directory that is matched
- "?": exactly one char
- "~": expanding to my home directory
- "[]": Range of something
- "^": not starting with something
- "{}": to generate arbitrary strngs
- "$((+ - \* /\ \*\* %))": arithmatic
- "$": find the variable with the following name
- "\": escape meta-chars

regex:

- "\*": repeat prev expression
- "[\^abc]": matches any char NOT in set
- "^": start with an expression
- "$": matches end of line
- ".": matches any single char
- "[]": Range of something
- "?": match zero or one expression
- "a{3}": three "a"s. number of repeated. can accept range: {2,4}

```bash
ls -l *.js

ls -l app?.css

ls -l app[132].css
ls -l app[1-3].css

echo [a-h]*[ps]

ls [^hf]*

echo ~/Desktop

touch a{1,2,3}.txt
echo Dec_{Mon,Tue,Wed,Thu,Fri}_{AM,PM}_planner.txt
echo {2..10..2} # prints from 2 till 10 every even number
echo {Z..A}
mkdir -p {Mon,Tue,Wed,The,Fri,Sat,Sun}/{Breakfast,Lunch,Dinner}
echo {x,y{1..5},z} # nested expansion

echo $((10+3))

echo hello        world # prints: hello world
echo "hello        world"
echo hello        world{1,2,3} # prints: hello world1 world2 world3
echo "hello        world{1,2,3}"  # prints: hello        world{1,2,3}

echo "holy $hit" # prints: holy
echo "holy \$hit" # prints: holy $hit
echo 'holy $hit' # prints: holy $hit

echo "$(<command>)" # this called command substitution
echo "today is ($date)"
echo "hello there $(whoami)"
echo "hello there `whoami`"
`whoami` # prints: zsh: command not found: farzan
```

# FINDING

These are for many commands

- mtime: last modification time
- ctime: mtime and when we rename file, move it or alter permissions
- atime: when file is read

logical operators:

- -and
- -or
- -not

- NOTE: grep takes regex not glob patterns! glob patterns are for dirs and filenames but regex related to contents.

```bash
locate <string> # find any indexed file that is indexed inside of locate db
locate frontend
locate /bin/less
locate -i # ignore casing
locate -l<number> # limite option
locate -e # update the db before return the matched data

find <directories> # slower than locate. locate looks at a just single file. listing all files and folder names
find <filename> -type f # files
find <dirname> -type d # directories
find . -type f
find Todos -type d
find ~/Desktop -name "*.png" # find by naem inside special dir
find -size +1G # files with size more than 1 GB
find <dirname> -size -50M # files with size more less 50 MB
find -user # find by owner
find -empty # find any files or dirs
find . -mmin +30
find . -amin +10 # find dirs that is accessed more that 10 minutes ago
find . -mtime -10 # in 24 hours period (atime / mtime / ctime)
find . -type f -not -name "*.txt"
find . -type d -iname "*.js" -or -iname "*.css"
find -exec command ??
xarg ??

ls -c
ls -m
ls -lu # for -atime!!

grep <pattern> <filename> # search within files. inside of files.
grep -w # returns just words with w not other fragments
grep -r <pattern> # search recursively every file inside the directory that you are already inside of it
grep -r <pattern> <dirname> # # search recursively every file inside the targret dir
grep -i # case insensitive
grep -ri "parm[ae]san" <dirname> # with regex
grep -c # count number of matches
grep -A<number> # specific lines after the word
grep -B<number> # specific lines before the word
grep -C<number> # specific lines before and after the word
grep -i "tomat[oe]" -C1
grep -n # number of lines
gerp -m<number> # limit to first times that the pattern repeated
grep -E # extended regex syntax / for {} and ? usage of regex
grep -iE "tomat[o|es]s?" shoppingList.txt
grep -l # shows the file names

ps # return the processes of current user
ps aux # all processes

ps aux | grep <pattern>
ps aux | grep sound -i
man grep | grep count -i1C
ls -l /bin | grep date -w

find . -name "*.txt" ! -empty -type f -exec grep -i "tomat[oe]" '{}' ';' # awesome! (shows the exact texts!)
find . -name "*.txt" ! -empty -type f -exec grep -il "tomat[oe]" '{}' ';' # awesome too! (just shows file names)
```

# PERMISSIONS

10 digits to show accesses:

- first col: file type:

  - "-" file
  - "d" dir
  - "c" char special file
  - "l" symbolic link (shortcut)
  - "b" block special files

- first three cols (ignoring first col) --> owener
- second three cols --> group
- thirst three cols --> world

  - first letter: "r" or "-": file: read / dir: contents can be listed
  - second letter: "w" or "-": file: modifying / dir: creating file, renaming files or dirs but only if x is set for third letter
  - third letter: "x" or "-": file: can be treated as a program to be executed / dir: allows a dir to be entered or "cd"ed (cd is best test for seeing access to a dir or not!)

for changing permissions:

- u: owner of the file
- g: group memeber
- o: other people
- a: all of them
- -: removing permission
- +: grants permission
- =: set a permission and remove others

octal numbers:

- 0 (octal) --> 000 (binary) --> --- (access)
- 1 (octal) --> 001 (binary) --> --x (access)
- 2 (octal) --> 010 (binary) --> -w- (access)
- 3 (octal) --> 011 (binary) --> -wx (access)
- 4 (octal) --> 100 (binary) --> r-- (access)
- 5 (octal) --> 101 (binary) --> r-x (access)
- 6 (octal) --> 110 (binary) --> rw- (access)
- 7 (octal) --> 111 (binary) --> rwx (access)

```bash
chmod mod <filename>
chmod u+wx shoppingList.txt
chomd <octal> <filename>
chmod 755 shoppingList.txt

su - <username> # substitute user
su - farzan # go to farzan user. after doing your work, you can come back with "exit"
su --login <username>
su farzan # won't change the current directory and things of current user. we can check the current user and path with pwd

sudo -l

chown <user> <filename>
sudo chown root a3.txt # change user
sudo chown :wheel a3.txt # change group
sudo chown root:wheel a3.txt # change user and group

groups # shows all groups that the current user is inside of
groups <username> # shows all groups that the user is inside of
sudo addgroup <groupname> # create new group (on linux)
adduser <username> <groupname> # (on linux)
sudo dscl . -create /Groups/developers
sudo dscl . -append /Groups/developers GroupMembership farzan
dscl . -read /Groups/developers # shows the members
```

# ENV

shell session maintains these info: home dir / working dir / name of the shell / name of the user logged in

"$": let the shell detect the word as a variable

- PS1: controlling variables for bash
- PROMPT: controlling variables for zsh. We change it here: "~/.zshrc" --> We can see PS1 here!

In PS1:

- "%n": username
- "%m": hostname
- "%<number>~": current working dir from $HOME. number is the amount of dirs that'ss gonna be shown.
- "%d": current working dir
- "%B%{}%b": bold
- "%F{}%f": foreground color
- "%K{}%k": background color

PATH variable: shell looks for executable command the we entered in the list of dirs stored in the PATH

```bash
printenv # view shell vars

echo $USER
echo $HOME
echo $PWD
echo $OLDPWD

animal=lion # creating variables. only on current shell session

bash # create a new shell session in the current window for bash users
zsh # like above comamnd for zsh

export animal=lion # put the val into shell vars and we can see it in printenv (for current session)

echo $PROMPT

alias ll='ls -la'
alias ..='cd ..'
typeof .. # returns: .. is an alias for cd .. / only exists on current shell session! for having it permanently, we should add it to zshrc or bashrc
```

we can run bash scripts like this: we should add path of our bash to PATH.

Shebang: `#!/bin/bash` (for bash) --> this tells to shell that you should use this excutable path to execute this file! (no need to use `bash <something>` or `python3 <something>` or anything other before filename to run the file if you would have added the path to PATH)

```bash
bash <path/to/filename>

export PATH="$PATH:our/path/to/file" # adding new path to $PATH var
```
