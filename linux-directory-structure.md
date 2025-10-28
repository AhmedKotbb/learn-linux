In Linux, everything is treated as a file even if it is a normal file, a directory, or even a device such as a printer or keyboard. All the directories and files are stored under one root directory which is represented by a forward slash ( / ).

- The Linux directory layout follows the Filesystem Hierarchy Standard (FHS).
- This standard defines how directories are organized and what types of files should be stored in each.
- Since Linux is based on UNIX, it inherits many of UNIX’s filesystem conventions.
- Similar directory structures are also found in other UNIX-like operating systems such as BSD and macOS.

## Types of files in the Linux system

1. General Files - It is also called ordinary files. It may be an image, video, program, or simple text file. These types of files can be in ASCII or Binary format. It is the most commonly used file in the Linux system.
2. Directory Files - These types of files are a warehouse for other file types. It may be a directory file within a directory (subdirectory).
3. Device Files - In a Windows-like operating system, devices like CD-ROM and hard drives are represented as drive letters like F: G: H, whereas in the Linux system, devices are represented as files. As for example, /dev/sda1, /dev/sda2, and so on.

We know that in a Windows-like operating system, files are stored in different folders on different data drives like C: D: E:, whereas in the Linux/Unix operating system, files are stored in a tree-like structure starting with the root directory,

This tree represents a **standard Linux filesystem layout** based on the **Filesystem Hierarchy Standard**

/
├── bin/ → Essential command binaries
├── boot/ → Boot loader files (e.g., kernel, GRUB)
├── dev/ → Device files
├── etc/ → System configuration files
├── home/ → User home directories
│ ├── user1/
│ └── user2/
├── lib/ → Shared libraries for essential binaries
├── lib64/ → 64-bit libraries (on 64-bit systems)
├── media/ → Mount point for removable media (USB, CD-ROM)
├── mnt/ → Temporary mount point for manual mounts
├── opt/ → Optional software packages
├── proc/ → Virtual filesystem for process and kernel info
├── root/ → Home directory for root (administrator)
├── run/ → Runtime data since last boot
├── sbin/ → System binaries (used by root/admin)
├── srv/ → Data for system services (e.g., web/ftp servers)
├── sys/ → Virtual filesystem for system and hardware info
├── tmp/ → Temporary files
├── usr/ → User programs, libraries, documentation
│ ├── bin/ → Non-essential user command binaries
│ ├── lib/ → Libraries for user programs
│ ├── local/ → Locally installed software
│ ├── share/ → Shared data (man pages, docs)
│ └── sbin/ → Non-essential system binaries
└── var/ → Variable files (logs, mail, cache, spool)
├── log/ → Log files
├── mail/ → User mailbox files
├── cache/ → Application cache data
└── spool/ → Queued tasks (e.g., print jobs, mail)

### System Configuration Files

A collection of essential configuration files in the `/etc` directory that define system behavior, user access, boot settings, network rules, and service management in Linux.

| File               | Description                                                                             |
| ------------------ | --------------------------------------------------------------------------------------- |
| `/etc/passwd`      | Stores user account information (username, UID, home directory, shell).                 |
| `/etc/shadow`      | Contains encrypted user passwords and password expiration info (readable only by root). |
| `/etc/group`       | Defines user groups.                                                                    |
| `/etc/gshadow`     | Secure group account information.                                                       |
| `/etc/fstab`       | Lists disk partitions and their mount points.                                           |
| `/etc/hostname`    | Contains the system’s hostname.                                                         |
| `/etc/hosts`       | Maps hostnames to IP addresses (local name resolution).                                 |
| `/etc/resolv.conf` | Specifies DNS servers for name resolution.                                              |
| `/etc/issue`       | Message or banner displayed before login prompt.                                        |
| `/etc/motd`        | “Message of the day” shown after successful login.                                      |
| `/etc/profile`     | Global initialization script for login shells (sets environment variables).             |
| `/etc/bash.bashrc` | Global configuration for interactive bash shells.                                       |
| `/etc/sudoers`     | Defines permissions for `sudo` command (edit safely with `visudo`).                     |
| `/etc/crontab`     | Defines system-wide scheduled tasks (cron jobs).                                        |
| `/etc/rc.local`    | Script executed at the end of boot (optional in modern systems).                        |

### User Related Files

These directories under `/usr` contain essential user-space programs, libraries, headers, and shared data used by both regular users and administrators.

### **Major Subdirectories of `/usr`**

| Directory       | Description                                                                                                                                                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/usr/bin/`     | **Primary directory for user commands and applications.** Contains most of the executable programs that are not required for system booting (e.g., `cp`, `grep`, `gcc`, `vim`, `python3`). Regular users can run these. |
| `/usr/sbin/`    | **System administration binaries** used for managing the system after boot (e.g., `apache2`, `sshd`, `useradd`). Usually restricted to the root user.                                                                   |
| `/usr/lib/`     | **Shared libraries** used by programs in `/usr/bin` and `/usr/sbin`. Similar to `/lib`, but for non-essential software.                                                                                                 |
| `/usr/lib64/`   | **64-bit library directory** (on 64-bit systems).                                                                                                                                                                       |
| `/usr/include/` | **Header files** for developing C/C++ programs (e.g., `stdio.h`, `stdlib.h`). Used when compiling software.                                                                                                             |
| `/usr/share/`   | **Architecture-independent shared data**, such as icons, documentation, localization files, and manual pages (e.g., `/usr/share/man`, `/usr/share/doc`).                                                                |
| `/usr/local/`   | **Locally installed software** — not managed by the system’s package manager. For example, custom-compiled programs go here. It mirrors `/usr` (contains `bin`, `lib`, `share`, etc.).                                  |
| `/usr/src/`     | **Source code** for the kernel and installed packages. For example, `/usr/src/linux` often contains kernel source files.                                                                                                |
| `/usr/games/`   | Older directory for game binaries. Rarely used on modern systems.                                                                                                                                                       |
| `/usr/libexec/` | **Helper programs** not meant to be run directly by users but used internally by applications or services.                                                                                                              |

### System Log Directory

This directory stores **most of the operating system’s and application’s log files**.
Here’s what you typically find inside:

| File / Directory                          | Description                                                                                        |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `/var/log/syslog`                         | Main system log (Ubuntu/Debian). Contains general messages from the kernel and user-space daemons. |
| `/var/log/messages`                       | Equivalent to `/var/log/syslog` on Red Hat, CentOS, and Fedora. General system activity logs.      |
| `/var/log/auth.log`                       | Authentication logs — tracks logins, sudo usage, and authentication attempts.                      |
| `/var/log/secure`                         | Same as `auth.log` on RHEL-based systems.                                                          |
| `/var/log/kern.log`                       | Kernel messages, including hardware and driver information.                                        |
| `/var/log/dmesg`                          | Boot-time kernel ring buffer messages.                                                             |
| `/var/log/boot.log`                       | Logs from system startup (services that start at boot).                                            |
| `/var/log/faillog`                        | Records failed login attempts.                                                                     |
| `/var/log/lastlog`                        | Contains timestamps of the last user logins.                                                       |
| `/var/log/wtmp`                           | Binary log of all logins and logouts. View with `last` command.                                    |
| `/var/log/btmp`                           | Binary log of failed login attempts. View with `lastb` command.                                    |
| `/var/log/cron`                           | Logs from cron jobs (scheduled tasks).                                                             |
| `/var/log/maillog` or `/var/log/mail.log` | Email-related logs from mail servers (Postfix, Sendmail).                                          |
| `/var/log/httpd/` or `/var/log/apache2/`  | Web server logs (Apache access and error logs).                                                    |
| `/var/log/nginx/`                         | Nginx web server logs.                                                                             |
| `/var/log/mysql/` or `/var/log/mariadb/`  | Database logs.                                                                                     |
| `/var/log/Xorg.0.log`                     | X Window System (GUI) logs — useful for graphics troubleshooting.                                  |
| `/var/log/journal/`                       | Systemd journal logs (binary format). Use `journalctl` to read them.                               |
| `/var/log/apt/`                           | Logs from package management operations (Ubuntu/Debian).                                           |
