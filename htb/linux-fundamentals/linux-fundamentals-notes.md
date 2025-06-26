# 🌧 HTB Academy – Linux Fundamentals Notes

> Notes from the Linux module on Hack The Box Academy
> ✅ Completed up to: Filter Contents + Bandit Level 20

---

## 📁 Introduction

### 🧱 Linux Structure

* Everything is a file (even devices and processes).
* Filesystem hierarchy starts at `/` (root).
* Key directories:

  * `/etc` – Config files
  * `/bin`, `/sbin` – Essential binaries
  * `/home` – User directories
  * `/var` – Logs and variable data
  * `/dev` – Device files
  * `/proc` – Runtime system info

### 🿶 Linux Distributions

* Same kernel, different packaging/tools.
* Package managers:

  * Debian/Ubuntu: `apt`
  * RedHat/CentOS: `yum`, `dnf`
  * Arch: `pacman`

### 💳 Intro to the Shell

* Interprets user input (bash, zsh, etc.).
* Command format: `command [options] [arguments]`
* Commands are case-sensitive.

---

## 💻 The Shell

### ➔ Prompt Description

* Format: `user@host:~/path$`

### ❓ Getting Help

* `man <command>` – manual pages
* `<command> --help` – quick syntax help
* `whatis <cmd>` – one-line description
* `apropos <keyword>` – search man pages

### 🧠 System Info

* `uname -a` – full system info
* `hostname` – computer name
* `uptime` – how long system has been on
* `whoami` – current user
* `top` or `htop` – live system monitor
* `free -h` – memory usage
* `df -h` – disk usage
* `du -sh *` – size of directories
* `id` – user and group info
* `env` – environment variables

---

## 🛠️ Workflow

### 📂 Navigation

* `pwd` – show current path
* `cd` – change dir

  * `cd ~` = home, `cd ..` = up one
  * `cd -` – switch to previous directory
* `ls -la` – list all with details
* `tree` – show directory tree (may need install)

### 📁 Files & Dirs

* `touch <file>` – create file
* `mkdir <dir>` – create folder
* `rm file` / `rm -r folder` – delete
* `cp src dst` – copy file/dir
* `mv old new` – move/rename
* `stat <file>` – detailed metadata
* `file <name>` – identify file type

### ✍️ Editing

* `nano` – beginner-friendly editor
* `vim` – powerful, efficient once learned
* `cat`, `less`, `more` – read file contents
* `echo "text" > file` – write to file
* `echo "text" >> file` – append
* `head` – show first 10 lines (default)
* `tail` – show last 10 lines (default)
* `cut`, `awk`, `sed`, `tr`, `column` – advanced manipulation and formatting
* `tee` – write to file while also displaying output
* `sort` – sort lines alphabetically or numerically
* `wc -l` – count lines

### 🔍 Finding

* `find / -name "*.txt" 2>/dev/null`
* `find . -type f -size +10M`
* `find . -type f -exec grep 'password' {} \;`
* `locate <file>` – requires updatedb
* `grep`, `egrep`, `zgrep` – search content

  * `grep -v` – exclude matches
* `strings <binary>` – extract readable strings
* `diff file1 file2` – compare files

### 📄 Redirection, Pipes, Logic

* `>` – overwrite
* `>>` – append
* `2>` – stderr
* `&>` – all output
* `<` – file as input
* `|` – pipe
* `&&` – run if previous succeeded
* `||` – run if previous failed

Example:

```bash
cat file.txt | grep "admin" | sort | uniq
ls && echo "Success" || echo "Failed"
```

### 🔢 Flags & Tricks

* `cut -d":" -f1 /etc/passwd` – show usernames
* `awk '{print $1}' file` – show first word of each line
* `awk '{print $1, $NF}'` – show first and last field
* `sed 's/old/new/g'` – replace globally
* `basename /path/to/file`
* `dirname /path/to/file`
* `tr ':' ' '` – replace characters (e.g., colon with space)
* `column -t` – display tabular output

---

## 🔐 Permissions & Ownership

### `chmod` Table

* `7` = read + write + execute (rwx)
* `6` = read + write (rw-)
* `5` = read + execute (r-x)
* `4` = read only (r--)
* `0` = none (---)

Octal permissions (user/group/other):

```bash
chmod 755 script.sh  # u=rwx, g=rx, o=rx
chmod 700 key.pem     # private
chmod +x file.sh      # add exec
```

### `chown`

* `chown user:group file`
* `chown -R user folder/` – recursively

### `umask`

* Default permission subtraction mask

---

## 🌐 Networking & Data Transfer

### Essentials

* `ping <host>` – check connectivity
* `curl <url>` – API, file download
* `wget <url>` – robust downloader
* `scp -i ~/.ssh/key.pem file.txt user@ip:/path/`
* `nc -lvnp 4444` – listener
* `telnet host port` – test connection

### Private Keys & SSH

* `chmod 600 id_rsa`
* `ssh -i id_rsa user@ip`
* `ssh user@localhost` – connect to local service
* `scp` for upload/download files

---

## 🧪 Bandit Takeaways (Up to Level 20)

* Use `ls -la` in every folder — flags are often hidden.
* Watch for file types (`file`, `xxd`, `base64`, `gzip`, etc.)
* Check for symlinks, special characters, or spaces in file names (use quotes or escape `\`).
* Use `cat`, `less`, or `xxd` to explore unknown content.
* Combine tools: `grep`, `cut`, `awk`, `strings`, `sort`, `uniq`, `tr`, `rev`, `base64`, `xxd`
* Watch `/etc/passwd`, `/etc/shadow`, `/tmp`, `/var/backups`, `/proc`, `/dev`
* Use `find`, `stat`, `du`, `md5sum`, `sha256sum`, and `diff` to analyze
* Learn `nc` and piping (ex: `cat file | nc localhost port`)
* Watch `.bashrc`/`.profile` — sometimes auto-logout
* Handle tricky permissions with `chmod`, `chown`, `scp`, SSH keys

---

## 🧠 Extras & Tricks

### Background & Process Control

* `sleep 10 &` – run in background
* `jobs`, `fg`, `bg` – control jobs
* `kill -9 PID` – force kill
* `ps aux | grep process` – list processes
* `lsof -i` – open ports

### Command Recall

* `!!` – repeat last
* `!ls` – repeat last starting with ls
* `history | grep ssh`
* `Ctrl + R` – reverse search

### Bash Aliases & Scripting

```bash
alias ll='ls -la'
alias cls='clear'
```

* `#!/bin/bash` – shebang line
* Use `chmod +x script.sh`

### Output Tricks

* `tac` – reverse `cat`
* `rev` – reverse lines
* `sort`, `uniq`, `cut` – output formatting
* `tee file.txt` – write and display
* `tr -d '\r'` – clean line endings
* `head -c 100 file` – show 100 chars

### Encodings

* `base64 -d` – decode
* `xxd -r` – reverse hex dump
* `gzip -d` or `gunzip` – decompress (remember to make file .gz)
* `tar -xvf file.tar` – extract tar

---
