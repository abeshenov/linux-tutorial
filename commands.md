# Some useful GNU/Linux commands

This summary focuses on Debian and Debian-based distributions.


## Bash console

| Command   | Action                         |
|-----------|--------------------------------|
| `clear`   | clear screen                   |
| `exit`    | exit the shell (builtin)       |
| `history` | command history (builtin)      |
| `logout`  | log out of the shell (builtin) |
| `reset`   | reset console                  |


## Bash keys

| Key         | Action                                         |
|-------------|------------------------------------------------|
| `Tab`       | completion                                     |
| `C-a`/`C-e` | cursor to line start/end                       |
| `M-b`/`M-f` | previous/next word (back/forward)              |
| `C-k`       | delete everything till line end ("kill")       |
| `C-w`       | delete previous word                           |
| `C-y`       | paste what we cut ("yank")                     |
| `C-r`       | reverse history search (`C-r` for more)        |
| `C-c`       | send `SIGINT` to the running process           |
| `C-d`       | send end-of-file symbol to console             |
| `C-z`       | stop running process (use `fg`/`bg` to resume) |


## APT

| Command                 | Action                              |
|-------------------------|-------------------------------------|
| `apt list`              | list available packages             |
| `apt list --installed`  | list installed packages             |
| `apt update`            | download list of available packages |
| `apt upgrade`           | install upgrades                    |
| `apt search <package>`  | package lookup                      |
| `apt info <package>`    | package info                        |
| `apt install <package>` | install a package                   |
| `apt remove <package>`  | remove a package                    |
| `apt autoremove`        | remove no longer needed             |


## Getting help

| Command             | Action                             |
|---------------------|------------------------------------|
| `apropos <keyword>` | search for keyword in descriptions |
| `man <page>`        | manual page                        |
| `whatis <page>`     | short summary                      |

See also https://manpages.debian.org/


## Files

###`cd` : change directory (builtin)

```shell
cd <dir>
```

### `cp` : copy

```shell
cp <source> <destination>
```

Some useful options:
* `-R`, `-r`, `--recursive` : copy directories recursively

### `df` : "disk free"

```shell
df -h
 ```

Some useful options:
* `-h`, `--human-readable`

### `du` : "disk usage"

This prints the actual directory size
```shell
du -sh <directory>
```

Some useful options:
* `-h`, `--human-readable`
* `-s`, `--summarize` : display only a total

### `find` : find files

See `man find`; here's a recursive search by pattern:
```shell
find -name '*.java'
```

### `head` : view first lines
```shell
head foo.txt
 ```

### `less` : view contents interactively
```shell
less foo.txt
 ```

Some useful options:
* `+/<pattern>`, `--pattern=<pattern>` : highlight occurrences of `<pattern>`

### `ln` : link; to create a symlink:
```shell
ln -s <source> <target>
```

### `ls` : list files

Some useful options:
* `-1` : one file per line
* `-a`, `--all` : show hidden files
* `-h`, `--human-readable` : human-readable file size
* `-l` : long listing format
* `-t` : sort by time, newest first
* `-r`, `--reverse` : reverse sort order

### `mkdir` : make directory

```shell
mkdir <directory>
```

Some useful options:
* `-p`, `--parents` : make parent directories as needed

### `mv` : move file

```shell
mv <source> <destination>
```
 
### `pwd` : print working directory (builtin)

```shell
pwd
```

### `rm` : remove

```shell
rm <file>
```

Some useful options:
* `-f`, `--force` : ignore  nonexistent  files
* `-r`, `-R`, `--recursive` : remove directories recursively

### `stat` : file stats

```shell
stat <file>
```

### `tail` : view last lines

```shell
tail foo.txt
```

Some useful options:
* `-f`, `--follow` : output appended data as the file grows (e.g. for logs)

### `touch` : change modification time or create file

```shell
touch foo.txt
```

### `tree` : prints file tree

This command is available from the package `tree`.


## Archives

### Create (`-c`, `--create`):

```shell
tar -czvf files.tar.gz files
zip -r files.zip files/
```

### Extract (`-x`, `--extract`):

```shell
tar -xvf files.tar.bz2
unzip files.zip -d /path/to/unzip
```

### List contents (`-t`, `--list`):

```shell
tar -tvf files.tar.bz2
unzip -l files.zip
```

Some `tar` options:
* `-c`, `--create`
* `-f`, `--file`
* `-t`, `--list`
* `-v`, `--verbose`
* `-x`, `--extract`

Common compression methods for `-c`:
* `-z`, `--gzip`
* `-j`, `--bzip2`
* `-J`, `--xz`
* `--lzip`


## Working with text

### `cat` : concatenate

```shell
cat file1.txt [file2.txt ...]
```

### `diff` : compare

```shell
diff foo1.txt foo2.txt
  ```

### `grep` : look inside files

Read `man grep`.

Example of recursive search, ignoring the case:
```shell
grep -r -i 'foobar' .
```

A few useful options:
* `-i`, `--ignore-case`
* `-r`, `--recursive`

### `sed` : "stream editor"

E.g. for a basic regex substitution:
```shell
sed s/foo/bar/g text.txt
 ```

### `sort`

```shell
sort foo.txt
```

Some useful options:
* `-f`, `--ignore-case`
* `-R`, `--random-sort`
* `-r`, `--reverse`
* `-u`, `--unique`

##`wc` : "word count"

```shell
wc -l foo.txt
```

Some useful options:
* `-c`, `--bytes`
* `-m`, `--chars`
* `-l`, `--lines`
* `-w`, `--words`


## Users and groups

### `su`, `sudo` : "substitute user"

This is to run commands as another user. As `root` by default:

```shell
su
sudo <command>
```

As another user:

```shell
su <user>
sudo -u <user> <command>
 ```

### `whoami` : current user

```shell
whoami
```


### `id` : user and group IDs

```shell
id <user>
```

### `passwd` : manage passwords

```shell
passwd
passwd <login>
 ```
 
Some useful options:
* `-d`, `--delete`
* `-e`, `--expire`
* `-l`, `--lock`
* `-u`, `--unlock`

###`userad` : add user

```shell
useradd --create-home --shell /bin/bash <username>
```

Some useful options:
* `-m`, `--create-home`
* `-s`, `--shell <shell>`
* `-G`, `--groups` `<group1>,<group2>,...`

### `usermod` : modify user

E.g. to add to a group:

```shell
usermod -aG <group> <user>
  ```
Some useful options:
* `-a`, `--append`
* `-d`, `--home` <homedir>`
* `-G`, `--groups` `<group1>,<group2>,...`
* `-l`, `--login` `<new-login>`
* `-s`, `--shell` `<shell>`
* `-L`, `--lock`
* `-U`, `--unlock`

### `userdel` : delete user

```shell
userdel <user>
```

Some useful options:
* `--remove` : remove home directory


## Managing permissions

| Number | Permissions |
|--------|-------------|
| `0`    | `---`       |
| `1`    | `--x`       |
| `2`    | `-w-`       |
| `3`    | `-wx`       |
| `4`    | `r--`       |
| `5`    | `r-x`       |
| `6`    | `rw-`       |
| `7`    | `rwx`       |

### `chmod` / `chown` / `chgrp` : change permissions, owner, groupp

```shell
chmod 644 <file>
chmod +x <file>
chmod -x <file>
chown <owner> <file>
chgrp <group> <file>
```

Useful option: `-R`, `--recursive`


## Processes

Install `procps` package.

### `pidof` : process ID of...

```shell
pidof java
```

### `ps` : processes

Some useful options:
* `-e` : list all processes
* `-C bash` : e.g. processes with command `bash`
 * `-U root` : e.g. processes run by `root`

### `pstree` : process tree

```shell
pstree
```

### `kill`, `killall` : kill process

Despite its name, `kill` and `killall` send any signal.

- `kill <pid>`, `killall <name>` : sends `SIGTERM` by default.
- With option `-KILL` : sends `SIGKILL`.

### `top` : interactive process monitor

```shell
top
```


## Network

### `curl`

Some useful options:
* `-i`, `--include` : include response headers
* `-v`, `--verbose` : verbose mode
* `-H`, `--header` `'Accept: application/json'` : send custom header

Example of sending a file via PUT:
```shell
curl -v -H 'Content-Type: application/json' -X PUT --data @"file.json" http://foo.org/bar
```

### `wget`

Some useful options:
* `-O`, `--output-document` : specifies output file
* `-c`, `--continue` : continue with a partially downloaded file

### `tcpdump`

Some useful options:
* `-D`, `--list-interfaces`
* `-i eth0`, `--interface=eth0` : look only for `eth0`
* `-c <num>` : exit after receiving `<num>` packets
* `-s <len>`, `--snapshot-length=<len>` : length of packet in bytes to capture
* `-A` : ASCII output of contents
* `-X` : HEX output of contents

E.g. to capture `10` TCP packets from `eth0` and show their hex contents:
```shell
sudo tcpdump -i eth0 -c 10 -X tcp
```
