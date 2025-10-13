## 📂 Navigation & directory commands

| Command | Description                                                              | Common Options / Examples                                                                                                                              |
| ------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `pwd`   | Print Working Directory — shows the full path of your current directory. | `pwd` → e.g. `/home/username/projects`                                                                                                                 |
| `ls`    | List files and directories in a directory                                | `ls` (simple list)  <br>`ls -l` (detailed list with permissions, size, owner)  <br>`ls -a` (include hidden files)  <br>`ls -lh` (human-readable sizes) |
| `cd`    | Change Directory — move between directories                              | `cd /path/to/dir`  <br>`cd ..` (go up one level)  <br>`cd ~` (go to home directory)  <br>`cd -` (go to previous directory)                             |
## 🗃️ File & directory management

| Command         | Description                                                      | Common Options / Examples                                                                                                                     |
| --------------- | ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `mkdir`         | Make Directory — create a new directory                          | `mkdir newfolder`  <br>`mkdir -p parent/child` (makes parent if needed)                                                                       |
| `rm`            | Remove (delete) files or directories                             | `rm file.txt`  <br>`rm -r dir_name` (recursive delete directory)  <br>`rm -rf dir_name` (force delete without asking) — **Use with caution!** |
| `cp`            | Copy files or directories                                        | `cp source.txt dest.txt`  <br>`cp -r dir1 dir2` (copy directory recursively)                                                                  |
| `mv`            | Move or rename files/directories                                 | `mv oldname newname` (rename)  <br>`mv file.txt /other/path/` (move file)                                                                     |
| `touch`         | Create an empty file or update the timestamp of an existing file | `touch newfile.txt`                                                                                                                           |
| `cat`           | Concatenate and display file contents                            | `cat file.txt`  <br>`cat file1 file2`                                                                                                         |
| `less` / `more` | View file contents page by page (for larger files)               | `less bigfile.log`  <br>`more file.txt`                                                                                                       |
|                 |                                                                  |                                                                                                                                               |
## 🔍 Searching, viewing, and info

| Command  | Description                                                      | Common Options / Examples                                                            |
| -------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| `grep`   | Search within files for lines matching a pattern                 | `grep "error" logfile.txt`  <br>`grep -r "TODO" .` (recursive search in current dir) |
| `man`    | Display the manual (help) page for another command               | `man ls`  <br>`man grep`                                                             |
| `echo`   | Display a line of text (or values of variables)                  | `echo "Hello, World!"`  <br>`echo $HOME`                                             |
| `uname`  | Show system information, like kernel name, version, architecture | `uname -a`                                                                           |
| `whoami` | Display the current user name                                    | `whoami`                                                                             |
## ⚙️ Permissions, ownership, & system commands

| Command        | Description                                              | Common Options / Examples                                                     |
| -------------- | -------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `chmod`        | Change file/directory permissions (read, write, execute) | `chmod u+x script.sh` (give execute permission to user)  <br>`chmod 755 file` |
| `chown`        | Change owner and/or group of a file/directory            | `chown user:group file.txt`                                                   |
| `sudo`         | Run a command with superuser (root) privileges           | `sudo apt update` (on Debian/Ubuntu)                                          |
| `df`           | Show disk space usage of file systems                    | `df -h` (human-readable sizes)                                                |
| `du`           | Show disk usage of files and directories                 | `du -sh .` (size of current folder)                                           |
| `top` / `htop` | Show real-time process and system resource usage         | `top`  <br>If installed, `htop` gives a nicer UI                              |
| `ps`           | Show current processes                                   | `ps aux`                                                                      |
| `kill`         | Terminate processes by PID                               | `kill 1234`  <br>`kill -9 1234` (force kill)                                  |

## 🗜️ Archiving & compression

| Command         | Description                                           | Common Options / Examples                                                                                |
| --------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `tar`           | Create or extract archive files (possibly compressed) | `tar -czvf archive.tar.gz folder/` (create compressed archive)  <br>`tar -xzvf archive.tar.gz` (extract) |
| `zip` / `unzip` | Create and extract ZIP format archives                | `zip archive.zip files`  <br>`unzip archive.zip`                                                         |
Note: Not all commands in Linux have their own separate **`man`** pages. This is especially common for **shell built-in commands**, aliases, or commands implemented inside the shell (bash, zsh, etc.)
Commands built into the shell (called _builtins_) are implemented as part of the shell program. Their documentation is included in the shell’s manual (e.g. `man bash`) rather than in separate pages.