---
title: 'Linux fundamentals'
date: 2024-04-21
tags: ["linux"]
TocOpen: true
---


## Introduction
 
- Unix 1970 release by Ken Thompson and Dennis Ritchie
	
- Berkeley Software Distribution 1977 (copy of unix)
	
- Richard stallman started the GNU project in 1983
	- Create a free Unix-like OS 
	
- Linux was a personal project started in 1991 by Linus Torvalds
	- Create a free OS kernel
	
- Today there is more than 600 distributions of linux

### Philosophy

| **Principle**                                                 | **Description**                                                                                                                                                |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Everything is a file`                                        | All configuration files for the various services running on the Linux operating system are stored in one or more text files.                                   |
| `Small, single-purpose programs`                              | Linux offers many different tools that we will work with, which can be combined to work together.                                                              |
| `Ability to chain programs together to perform complex tasks` | The integration and combination of different tools enable us to carry out many large and complex tasks, such as processing or filtering specific data results. |
| `Avoid captive user interfaces`                               | Linux is designed to work mainly with the shell (or terminal), which gives the user greater control over the operating system.                                 |
| `Configuration data stored in a text file`                    | An example of such a file is the `/etc/passwd` file, which stores all users registered on the system.                                                          |

### Components

| **Component**     | **Description**                                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Bootloader`      | A piece of code that runs to guide the booting process to start the operating system.                                                                                                                                                                                                                                                           |
| `OS Kernel`       | The kernel is the main component of an operating system. It manages the resources for system's I/O devices at the hardware level.                                                                                                                                                                                                               |
| `Daemons`         | A daemon is a background process that runs continuously on Unix-like operating systems such as Linux. They typically start automatically when the system boots up and continue to run until shutdown. Daemons operate silently, providing essential system functionality without direct user interface.                                         |
| `OS Shell`        | The operating system shell or the command language interpreter (also known as the command line) is the interface between the OS and the user. This interface allows the user to tell the OS what to do. The most commonly used shells are Bash, Tcsh/Csh, Ksh, Zsh, and Fish.                                                                   |
| `Graphics server` | This provides a graphical sub-system (server) called "X" or "X-server" that allows graphical programs to run locally or remotely on the X-windowing system.                                                                                                                                                                                     |
| `Window Manager`  | Also known as a graphical user interface (GUI). There are many options, including GNOME, KDE, MATE, Unity, and Cinnamon. A desktop environment usually has several applications, including file and web browsers. These allow the user to access and manage the essential and frequently accessed features and services of an operating system. |
| `Utilities`       | Applications or utilities are programs that perform particular functions for the user or another program.                                                                                                                                                                                                                                       |

### Linux Architecture

The Linux operating system can be broken down into layers:

| **Layer**        | **Description**                                                                                                                                                                                                                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Hardware`       | Peripheral devices such as the system's RAM, hard drive, CPU, and others.                                                                                                                                                                                                                          |
| `Kernel`         | The core of the Linux operating system whose function is to virtualize and control common computer hardware resources like CPU, allocated memory, accessed data, and others. The kernel gives each process its own virtual resources and prevents/mitigates conflicts between different processes. |
| `Shell`          | A command-line interpreter (**CLI**), also known as a shell that a user can enter commands into to execute the kernel's functions.                                                                                                                                                                 |
| `System Utility` | Makes available to the user all of the operating system's functionality.                                                                                                                                                                                                                           |

| **Path** | **Description**                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/`      | The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root. |
| `/bin`   | Contains essential command binaries.                                                                                                                                                                                                                                                                                              |
| `/boot`  | Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.                                                                                                                                                                                                                                    |
| `/dev`   | Contains device files to facilitate access to every hardware device attached to the system.                                                                                                                                                                                                                                       |
| `/etc`   | Local system configuration files. Configuration files for installed applications may be saved here as well.                                                                                                                                                                                                                       |
| `/home`  | Each user on the system has a subdirectory here for storage.                                                                                                                                                                                                                                                                      |
| `/lib`   | Shared library files that are required for system boot.                                                                                                                                                                                                                                                                           |
| `/media` | External removable media devices such as USB drives are mounted here.                                                                                                                                                                                                                                                             |
| `/mnt`   | Temporary mount point for regular filesystems.                                                                                                                                                                                                                                                                                    |
| `/opt`   | Optional files such as third-party tools can be saved here.                                                                                                                                                                                                                                                                       |
| `/root`  | The home directory for the root user.                                                                                                                                                                                                                                                                                             |
| `/sbin`  | This directory contains executables used for system administration (binary system files).                                                                                                                                                                                                                                         |
| `/tmp`   | The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.                                                                                                                                   |
| `/usr`   | Contains executables, libraries, man files, etc.                                                                                                                                                                                                                                                                                  |
| `/var`   | This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.                                                                                                                                                                                               |

## Filter content 

1. **more**:
   - Display output one screen at a time.
   - Press spacebar to move forward, 'q' to quit.

2. **less**:
   - Similar to more but allows scrolling backward and forward.
   - Use arrow keys or page up/down for navigation.

3. **head**:
   - Display the first few lines of a file.
   - Syntax: `head [options] [file]`.

4. **tail**:
   - Display the last few lines of a file.
   - Useful for monitoring log files.
   - Syntax: `tail [options] [file]`.

5. **sort**:
   - Sort lines of text files.
   - Options include alphabetical, numerical, and reverse sorting.

6. **grep**:
   - Search for patterns in files.
   - Supports regular expressions.
   - Syntax: `grep [options] [pattern] [file]`.

7. **cut**:
   - Extract sections from each line of files.
   - Useful for splitting lines by delimiter.
   - Syntax: `cut [options] [file]`.

8. **tr**:
   - Translate or delete characters.
   - Syntax: `tr [options] [set1] [set2]`.

9. **column -t**:
   - Format input into multiple columns.
   - Useful for aligning output.
   - Syntax: `column -t [file]`.

10. **awk**:
    - A powerful pattern scanning and processing language.
    - Useful for data extraction and reporting.
    - Syntax: `awk '[pattern] {action}' [file]`.

11. **sed**:
    - Stream editor for filtering and transforming text.
    - Supports regular expressions and substitution.
    - Syntax: `sed [options] '[script]' [file]`.

12. **wc -l**:
    - Count the number of lines in a file.
    - Syntax: `wc -l [file]`.


**--- EXAMPLES ---**

1. **more**:
   - Example: View the contents of a text file named "example.txt" using more:
     ```
     more example.txt
     ```

2. **less**:
   - Example: Scroll through the contents of a log file named "logfile.log" using less:
     ```
     less logfile.log
     ```

3. **head**:
   - Example: Display the first 10 lines of a file named "data.csv" using head:
     ```
     head data.csv
     ```

4. **tail**:
   - Example: Monitor the last 100 lines of a log file named "access.log" using tail:
     ```
     tail -n 100 access.log
     ```

5. **sort**:
   - Example: Sort the lines of a file named "unsorted.txt" alphabetically and display the result:
     ```
     sort unsorted.txt
     ```

6. **grep**:
   - Example: Search for lines containing the word "error" in a file named "log.txt" using grep:
     ```
     grep "error" log.txt
     ```

7. **cut**:
   - Example: Extract the second field (delimited by ':') from a file named "data.txt":
     ```
     cut -d ':' -f 2 data.txt
     ```

8. **tr**:
   - Example: Convert all lowercase letters to uppercase in a file named "text.txt":
     ```
     tr '[:lower:]' '[:upper:]' < text.txt
     ```

9. **column -t**:
   - Example: Format the contents of a CSV file named "table.csv" into aligned columns:
     ```
     column -t -s ',' table.csv
     ```

10. **awk**:
    - Example: Print the first and third columns of a space-separated file named "data.txt":
      ```
      awk '{print $1, $3}' data.txt
      ```

11. **sed**:
    - Example: Replace all occurrences of "old" with "new" in a file named "text.txt":
      ```
      sed 's/old/new/g' text.txt
      ```

12. **wc -l**:
    - Example: Count the number of lines in a file named "poem.txt":
      ```
      wc -l poem.txt
      ```


**Tips:**
- Combine commands using pipes (`|`) for complex operations.
- Utilize redirection (`>`, `>>`, `<`) to manage input and output.
- Refer to man pages (`man [command]`) for detailed usage and options.


## Obtain information on a function

man
apropos
--help 
## System information

| **Command** | **Description**                                                                                                                    |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `whoami`    | Displays current username.                                                                                                         |
| `id`        | Returns users identity and groups in which the current user is                                                                     |
| `hostname`  | Sets or prints the name of current host system.                                                                                    |
| `uname`     | Prints basic information about the operating system name and system hardware.                                                      |
| `pwd`       | Returns working directory name.                                                                                                    |
| `ifconfig`  | The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters. |
| `ip`        | Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.                                            |
| `netstat`   | Shows network status.                                                                                                              |
| `ss`        | Another utility to investigate sockets.                                                                                            |
| `ps`        | Shows process status.                                                                                                              |
| `who`       | Displays who is logged in.                                                                                                         |
| `env`       | Prints environment or sets and executes command.                                                                                   |
| `lsblk`     | Lists block devices.                                                                                                               |
| `lsusb`     | Lists USB devices                                                                                                                  |
| `lsof`      | Lists opened files.                                                                                                                |
| `lspci`     | Lists PCI devices.                                                                                                                 |




## Find files and directories

1. **find**:
   - Search for files and directories in a directory hierarchy.
   - Syntax: `find [directory] [options] [expression]`.

   - Example: Find all files with a .txt extension in the current directory and its subdirectories:
```
find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 2>/dev/null
```

1. **which**:
   - Locate the executable file associated with a given command in the user's PATH.
   - Syntax: `which [command]`.

   - Example: Find the location of the ls command:
     ```
     which ls
     ```

3. **locate**:
   - Quickly find files by name using a prebuilt database.
   - Syntax: `locate [pattern]`.

   - Example: Locate all files and directories with "example" in their name:
     ```
     locate example
     ```

**Tips:**
- Use wildcards (*) and regular expressions for flexible searching.
- Combine commands with other utilities for more advanced search operations.
- Keep in mind that 'locate' may not always return the most up-to-date results since it relies on a prebuilt database. Use 'updatedb' to update the database if needed.



## File Descriptors and Redirections 

**File Descriptor:**

- In Unix-like operating systems, everything is treated as a file, including input/output streams, devices, and regular files. File descriptors are integer identifiers used to represent these files within a process.
- There are three standard file descriptors:
    1. **stdin (Standard Input)**: File descriptor 0. Default input source, typically keyboard input.
    2. **stdout (Standard Output)**: File descriptor 1. Default output destination, typically terminal output.
    3. **stderr (Standard Error)**: File descriptor 2. Default error output, used for error messages.

**Redirection:**

- Redirection is a feature in Unix-like operating systems that allows changing where input comes from and where output goes to.
- Redirection operators:
    1. **>**: Redirects standard output to a file, overwriting the file if it exists.
    2. **>>**: Redirects standard output to a file, appending to the end of the file if it exists.
    3. **<**: Redirects standard input from a file.
    4. **2>**: Redirects standard error to a file, overwriting the file if it exists.
    5. **2>>**: Redirects standard error to a file, appending to the end of the file if it exists.
    6. **&>**: Redirects both standard output and standard error to a file, overwriting the file if it exists.
    7. **&>>**: Redirects both standard output and standard error to a file, appending to the end of the file if it exists.

## Regular expressions

**1. Anchors:**
   - **^**: Start of a line.
   - **$**: End of a line.

**2. Quantifiers:**
   - **\***: Zero or more occurrences.
   - **+**: One or more occurrences.
   - **?**: Zero or one occurrence.
   - **{n}**: Exactly n occurrences.
   - **{n,}**: At least n occurrences.
   - **{n,m}**: Between n and m occurrences.

**3. Character Classes:**
   - **.**: Any character except newline.
   - **[ ]**: Any single character listed inside.
   - **[^ ]**: Any single character not listed inside.
   - **\d**: Any digit (equivalent to [0-9]).
   - **\D**: Any non-digit.
   - **\w**: Any word character (alphanumeric + underscore).
   - **\W**: Any non-word character.
   - **\s**: Any whitespace character.
   - **\S**: Any non-whitespace character.

**4. Grouping and Capturing:**
   - **( )**: Grouping. Captures matched text.
   - **(?: )**: Grouping without capturing.
   - **\n**: Back-reference to captured group n.

**5. Alternation:**
   - **|**: Alternation (OR operator).

**6. Assertions:**
   - **\b**: Word boundary.
   - **\B**: Not a word boundary.
   - **(?= )**: Positive lookahead.
   - **(?! )**: Negative lookahead.
   - **(?<= )**: Positive lookbehind.
   - **(?<! )**: Negative lookbehind.

**7. Escaped Characters:**
   - **\\**: Escapes a special character.

**8. Flags:**
   - **g**: Global match (find all matches).
   - **i**: Case-insensitive match.
   - **m**: Multiline match.

**Examples:**
- **Match Email Addresses:**
  ```
  \b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b
  ```

- **Extract Phone Numbers:**
  ```
  \(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}
  ```

- **Find HTML Tags:**
  ```
  <[^>]*>
  ```

## Permissions management

These permissions are shown utilizing the `octal` or Base 8 (0-7) numbering system. They are used to apply the `read`, `write`, and `execute` attributes to the contexts of `User owner`, `Group owner`, and `Others` on a file. These are represented as:

|**Attribute**|**Octal Value**|
|---|---|
|(`r`) - Read|`Octal value of 4`|
|(`w`) - Write|`Octal value of 2`|
|(`x`) - Execute|`Octal value of 1`|

- **chmod**: Change file permissions.
    - Example: `chmod 777 <file>`
- **chown**: Change file ownership.
    - Example: `sudo chown <new_user> <file>`
	- Example: `sudo chown <new_user>:<new_group> <file>`

### Special permissions

#### SUID (Set User ID):

- When a file has the SUID bit set, it will be executed with the privileges of the file's owner, rather than the user who is executing it.
- For example, if an executable file belongs to the user "root" and has the SUID bit set, when another user executes this file, it will be run with the privileges of the "root" user.
- This can be useful to allow ordinary users to execute programs with specific privileges without granting direct access to those privileges.

#### SGID (Set Group ID):

- When a file has the SGID bit set, it is executed with the privileges of the file's group owner, instead of the executing user's primary group.
- This allows a file to be executed with the same privileges as the owning group, regardless of the user's primary group.


The letter **`s`** is used instead of an **`x`**. When executing such a program, the SUID/SGID of the file owner is used.

#### Sticky bits

 **Files:** 
	For files, the sticky bit doesn't have a specific meaning. Its usage is primarily reserved for directories.

**Directories:**
	- When the sticky bit is set on a directory, it means that only the file owner, the directory owner, or the root user can delete or rename files within that directory.
	- 
	- This provides an additional layer of security in shared directories where multiple users have write permissions. Without the sticky bit, any user with write permissions could delete or rename any file in the directory.
	- 
	- With the sticky bit enabled, only authorized users can modify or delete files, thus ensuring data integrity and protecting important files from accidental deletions.


The letter **`t`** or **`T`** is used instead of an **`x`**. 

- **"t"**: Other users have permission to execute (access) the directory and its files.
- **"T"**: Other users do not have permission to execute (access) the directory, but the properties of the sticky bit for file deletion and renaming remain in place.

## User management

| **Command** | **Description**                                                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sudo`      | Execute command as a different user.                                                                                                                       |
| `su`        | The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed. |
| `useradd`   | Creates a new user or update default new user information.                                                                                                 |
| `userdel`   | Deletes a user account and related files.                                                                                                                  |
| `usermod`   | Modifies a user account.                                                                                                                                   |
| `addgroup`  | Adds a group to the system.                                                                                                                                |
| `delgroup`  | Removes a group from the system.                                                                                                                           |
| `passwd`    | Changes user password.                                                                                                                                     |

## Package management

| **Command** | **Description**                                                                                                                                                                                                                                                                                                                                         |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `dpkg`      | The `dpkg` is a tool to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is aptitude.                                                                                                                                                                                                        |
| `apt`       | Apt provides a high-level command-line interface for the package management system.                                                                                                                                                                                                                                                                     |
| `aptitude`  | Aptitude is an alternative to apt and is a high-level interface to the package manager.                                                                                                                                                                                                                                                                 |
| `snap`      | Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things.                                                                                                                                                              |
| `gem`       | Gem is the front-end to RubyGems, the standard package manager for Ruby.                                                                                                                                                                                                                                                                                |
| `pip`       | Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation. |
| `git`       | Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.                                                                                                                                                                                  |

## Service and Process Management


- **Types of Services**:
    
    - Internal services: Essential tasks required at system startup, often hardware-related.
    - User-installed services: Includes server services, run in the background without user interaction, also known as daemons.
- **Identifying Daemons**:
    
    - Daemons are recognized by the letter 'd' at the end of their program names, e.g., sshd or systemd.
- **Systemd**:
    
    - Most Linux distributions now use systemd as the init process, with PID 1.
    - Responsible for orderly starting and stopping of services, monitoring other processes.
- **Process Management**:
    
    - Each process has a unique Process ID (PID), visible under /proc/.
    - Processes may have a Parent Process ID (PPID), indicating their relationship to other processes.
- **Service Management Tools**:
    
    - `systemctl`: Main command-line utility for managing services with systemd.
    - `update-rc.d`: Tool for managing SysV init script links, offering similar functionality to systemctl for older init systems.


- We can use journalctl to view the log if a service do not start due to an error

**Kill a process**

1. **kill**: Sends signals to processes, typically used to terminate them. Syntax: `kill [options] PID`.
    
2. **pkill**: Searches and kills processes based on their names or attributes. Syntax: `pkill [options] pattern`.
    
3. **pgrep**: Searches for processes based on their names or attributes and prints their PIDs. Syntax: `pgrep [options] pattern`.
    
4. **killall**: Terminates processes by their names. Syntax: `killall [options] process_name`.


The most commonly used signals are (signals are sent to the kernel):

| **Signal** | **Description**                                                                                                          |
| ---------- | ------------------------------------------------------------------------------------------------------------------------ |
| `1`        | `SIGHUP` - This is sent to a process when the terminal that controls it is closed.                                       |
| `2`        | `SIGINT` - Sent when a user presses `[Ctrl] + C` in the controlling terminal to interrupt a process.                     |
| `3`        | `SIGQUIT` - Sent when a user presses `[Ctrl] + D` to quit.                                                               |
| `9`        | `SIGKILL` - Immediately kill a process with no clean-up operations.                                                      |
| `15`       | `SIGTERM` - Program termination.                                                                                         |
| `19`       | `SIGSTOP` - Stop the program. It cannot be handled anymore.                                                              |
| `20`       | `SIGTSTP` - Sent when a user presses `[Ctrl] + Z` to request for a service to suspend. The user can handle it afterward. |

**Background a Process:**

- To suspend a process and put it in the background, use `[Ctrl + Z]`.
- View background processes with `jobs`.
- Resume a suspended process in the background with `bg`.
- Alternatively, append `&` to a command to automatically run it in the background.

**Foreground a Process:**

- View background processes with `jobs`.
- Bring a background process to the foreground with `fg <ID>`.

**Execute Multiple Commands:**

- Use semicolon `;` to separate commands, executing them sequentially.
- Double ampersand `&&` executes commands sequentially, stopping if an error occurs.
- Pipes `|` execute commands based on previous processes' results.


## Task scheduling

**Systemd:**

1. **Create a Timer:**
    
    - Make a directory for the timer script.
    - Create a timer script with "Unit", "Timer", and "Install" options.
    - Specify timing settings in the timer script.
2. **Create a Service:**
    
    - Set a description and specify the script's full path in the service script.
    - Define the target for installation.
3. **Reload Systemd:**
    
    - Use `sudo systemctl daemon-reload` to apply changes.
4. **Start the Timer & Service:**
    
    - Manually start the service with `sudo systemctl start <service_name>`.
    - Enable autostart with `sudo systemctl enable <service_name>`.

**Cron:**

1. **Create a Cron File:**
    - Use `crontab -e` to edit the cron table.
    - Define tasks using time frames for minutes, hours, days of the month, months, and days of the week.

**Example Cron File:**

```txt
# System Update
* */6 * * * /path/to/update_software.sh

# Execute scripts
0 0 1 * * /path/to/scripts/run_scripts.sh

# Cleanup DB
0 0 * * 0 /path/to/scripts/clean_database.sh

# Backups
0 0 * * 7 /path/to/scripts/backup.sh
```

**Systemd vs. Cron:**

- **Systemd:** Requires timer and service scripts; offers precise control over timing and execution.
- **Cron:** Uses cron table for task scheduling; simpler syntax but less flexible than systemd.

## Network Services

**SSH (Secure Shell):**

- **Description:** Securely transmit data and commands over a network.
- **Check Status:** `systemctl status ssh`
- **Login Command:** `ssh username@hostname`

**NFS (Network File System):**

- **Description:** NFS is a distributed file system protocol that allows users to access files and directories stored on remote systems over a network as if they were local.

- **Share Creation:** Edit the `/etc/exports` file to define which directories should be shared and specify access rights for users and systems. Each line in this file represents a shared directory and its associated settings.

- **Mounting a Share:** To access a shared directory from a remote system, use the `mount` command followed by the IP address of the server and the path to the shared directory. For example, `mount <server_ip>:/path/to/share /mount/point`.

| **Permissions**  | **Description**                                                                                                                                            |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rw`             | Gives users and systems read and write permissions to the shared directory.                                                                                |
| `ro`             | Gives users and systems read-only access to the shared directory.                                                                                          |
| `no_root_squash` | Prevents the root user on the client from being restricted to the rights of a normal user.                                                                 |
| `root_squash`    | Restricts the rights of the root user on the client to the rights of a normal user.                                                                        |
| `sync`           | Synchronizes the transfer of data to ensure that changes are only transferred after they have been saved on the file system.                               |
| `async`          | Transfers data asynchronously, which makes the transfer faster, but may cause inconsistencies in the file system if changes have not been fully committed. |

Example : 

```shell-session
cry0l1t3@htb:~$ mkdir nfs_sharing
cry0l1t3@htb:~$ echo '/home/cry0l1t3/nfs_sharing  hostname(rw,sync,no_root_squash)' >> /etc/exports
```


```shell-session
cry0l1t3@htb:~$ mkdir ~/target_nfs
cry0l1t3@htb:~$ mount 10.129.12.17:/home/john/dev_scripts ~/target_nfs
```



**Web Server (Apache & Python):**

- **Description:** Web servers like Apache and Python's built-in HTTP server facilitate hosting websites and web applications over the internet. Apache is a widely-used web server with extensive features, while Python's HTTP server is lightweight and suitable for simple tasks.
- **Check Status:** Use `systemctl status apache2` to verify if Apache is running. This command provides information about the status of the Apache service.
- **Configuration File:** Apache's main configuration file is located at `/etc/apache2/apache2.conf`. Here, you can customize settings such as directory access permissions, virtual hosts, and modules.
- **Python Web Server:** Python's built-in HTTP server can be started using `python3 -m http.server`. This starts a simple web server serving files from the current directory. Python Web Server will be started on the `TCP/8000` port.
- **Python Web Server with Directory:** To specify a directory for Python's HTTP server, use `python3 -m http.server --directory /path/to/directory`. This serves files from the specified directory.


**VPN (Virtual Private Network - OpenVPN):**

- **Description:** VPNs provide secure communication over public networks by creating encrypted tunnels between the client and server, allowing users to access resources securely.
- **Server Configuration:** OpenVPN server configuration is done through the `/etc/openvpn/server.conf` file. Here, you can specify settings such as encryption, tunneling, and network routing.
- **Client Connection:** To connect to an OpenVPN server, use `sudo openvpn --config client.ovpn`, where "client.ovpn" is the configuration file provided by the server. This initiates the VPN connection from the client to the server.



## Working with web service 


**cURL**

- **Usage**: `curl [URL]`
- **Functionality**: Transfer files over various protocols like HTTP, HTTPS, FTP, SFTP, FTPS, or SCP.
- **Importance**: Facilitates remote website control and testing. Often pre-installed on Linux systems.

**wget**

- **Usage**: `wget [URL]`
- **Functionality**: Download files from FTP or HTTP servers directly to the terminal.
- **Difference from cURL**: Content is downloaded and stored locally.



## Backup and Restore


- **Rsync**:
  - Open-source tool for quick and secure backup of files and folders.
  - Efficient for transferring large data over networks, transmitting only changes.
- **Deja Dup**:
  - Graphical backup tool simplifying the backup process with a user-friendly interface.
  - Uses Rsync as a backend and supports encryption.
- **Duplicity**:
  - Comprehensive backup tool utilizing Rsync backend.
  - Offers encryption options and supports storing backups on remote storage.


**Basic Rsync Commands**

- **Backup a Directory**:
  ```
  rsync -av /path/to/source user@backup_server:/path/to/destination
  ```

  - `-z`: Enable compression for faster transfers.
  - `--backup --backup-dir=/path/to/backup/folder --delete`: Create incremental backups and delete files not present in the source.

**Restoring Data from Backup**

  ```
  rsync -av user@backup_server:/path/to/backup/directory /path/to/destination
  ```

**Secure Transfer with Rsync**

  ```
  rsync -avz -e ssh /path/to/source user@backup_server:/path/to/destination
  ```
- Utilizes SSH encryption for secure transfer.

**Auto-Synchronization with Cron and Rsync**
- **Create Script**:
  - Create a script (e.g., `RSYNC_Backup.sh`) containing the rsync command.
  - Ensure script execution permissions: `chmod +x RSYNC_Backup.sh`
- **Configure Cron Job**:
  - Edit crontab to run the script at desired intervals.
  - Example crontab entry: `0 * * * * /path/to/RSYNC_Backup.sh`



## File system management 


- **ext2:** Basic file system management.
- **ext3:** Journaling file system, improves reliability.
- **ext4:** Successor to ext3 with improved performance and features.
- **XFS:** High-performance file system suitable for large storage.
- **Btrfs:** Modern file system with features like snapshots and data integrity.
- **NTFS:** Compatibility with Windows systems.

**Components of Linux File System:**

- **Inode Table:** Contains metadata about files and directories.
- **Regular Files:** Common files stored in the root directory.
- **Directories:** Containers for collections of files.
- **Symbolic Links:** References to other files or directories.

**Disk Management Tools:**

- **fdisk:** Create, delete, and manage partitions on drives.
- **gpart:** Another tool for partition management.
- **GParted:** GUI-based partition editor.

**Mounting File Systems:**

- **mount:** Attach a drive to a directory.
- **/etc/fstab:** Defines default file systems mounted at boot time.
- **mount** command alone displays currently mounted file systems.

**Mounting Examples:**

- `sudo mount /dev/sdb1 /mnt/usb`: Mount USB drive to directory.
- `sudo umount /mnt/usb`: Unmount a file system.
- Ensure permissions and no running processes before unmounting.

**Swap Space Management:**

- Used for memory management when physical memory is depleted.
- Created with `mkswap` and activated with `swapon`.
- Size depends on system memory and usage.
- Place on dedicated partition or file separate from the rest of the file system.
- Can be encrypted for security.
- Used for hibernation to save and restore system state.

**Example /etc/fstab Entry:**

The `/etc/fstab` file contains information about all the file systems that are mounted on the system, including the options for automatic mounting at boot time and other mount options. To unmount a file system automatically at shutdown, we need to add the `noauto` option to the entry in the `/etc/fstab` file for that file system. This would look like, for example, the following:

```
/dev/sda1 / ext4 defaults 0 0
/dev/sda2 /home ext4 defaults 0 0
/dev/sdb1 /mnt/usb ext4 rw,noauto,user 0 0
192.168.1.100:/nfs /mnt/nfs nfs defaults 0 0
```


## Containerization

**Overview:**
- Containerization is the process of packaging and running applications in isolated environments
- Key technologies: Docker, Docker Compose, Linux Containers.

**Container Security:**
- Containers offer secure environments by isolating applications from the host system and other containers.
- Lightweight nature enhances security, making them harder to compromise compared to traditional virtual machines.

**Docker:**
- Open-source platform automating application deployment using containers.
- Utilizes layered filesystem and resource isolation for flexibility and portability.
- Docker Hub: Repository for Docker images, public and private areas available.
- Dockerfile: Contains instructions for building Docker images.
- Docker Build: Command for building Docker images.
- Docker Run: Command for starting containers from Docker images.

**Docker Management:**
- Docker provides tools for listing, starting, stopping, and managing containers efficiently.
- Key commands: docker ps, docker stop/start/restart, docker rm/rmi, docker logs.

**Linux Containers (LXC):**
- Virtualization technology allowing multiple isolated Linux systems on a single host.
- Uses features like cgroups and namespaces for resource isolation.
- Combined with Docker for a comprehensive containerization experience.
- LXC installation: Use package manager (e.g., apt-get).

**Managing LXC Containers:**
- Tasks include creating, configuring, starting, stopping, and monitoring containers.
- Command-line tools: lxc-ls, lxc-stop/start/restart, lxc-config, lxc-attach.

**Securing LXC:**
- Implement measures like restricting access, limiting resources, isolating containers, enforcing access control, and keeping containers updated.
- Use cgroups to limit CPU and memory usage for containers.
- Leverage namespaces for isolation of processes, network interfaces, and file systems.

**Additional Tips:**
- Containers are useful for testing software or systems with specific dependencies or configurations.
- Use containers to test exploits or malware safely in controlled environments.
- Always configure container security to prevent unauthorized access or malicious activities.
- Namespaces provide isolation for processes, network interfaces, and file systems, enhancing security.



## Network configuration

- **Tools:** ifconfig, ip command (preferred nowadays).
  
- **Commands:**
  - `ifconfig`: View and configure network interfaces (deprecated).
  - `ip addr`: View and configure network interfaces (modern approach).
  
- **Activation:**
  - `sudo ifconfig eth0 up` or `sudo ip link set eth0 up`: Activate network interface `eth0`.

- **Assigning IP Address:**
  - `sudo ifconfig eth0 <IP_Address>`

- **Setting Netmask:**
  - `sudo ifconfig eth0 netmask <Netmask>`

- **Assigning Default Gateway:**
  - `sudo route add default gw <Gateway_IP> eth0`

**Editing DNS Settings:**

- **File:** `/etc/resolv.conf`

- **Example:**
  ```
  nameserver 8.8.8.8
  nameserver 8.8.4.4
  ```

- **Edit Command:** `sudo vim /etc/resolv.conf`


**Saving Configuration Changes:**

- **File:** `/etc/network/interfaces`

- **Example:**
  ```
  auto eth0
  iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
  ```

- **Edit Command:** `sudo vim /etc/network/interfaces`

- **Restart Networking Service:** `sudo systemctl restart networking`

### Access Control

**Discretionary Access Control (DAC):**

- **Overview:** DAC is one of the most common access control models, allowing users to control access to their resources. It grants users discretion over who can access their files, folders, or resources, and what actions they can perform on them.
- **User Control:** Owners of resources decide who can access their resources and what permissions they have.
- **Flexibility:** Offers flexibility as users can grant permissions to other users or groups based on their preferences.
- **Example:** In a DAC system, a file owner can specify that only certain users or groups have permission to read or modify the file.

**Mandatory Access Control (MAC):**

- **Overview:** MAC provides a more rigid access control mechanism than DAC. It is typically used in high-security environments such as government or military systems.
- **Rule-Based:** Access decisions are based on predefined rules or policies rather than the discretion of resource owners.
- **Labeling:** Resources and users are assigned security labels or levels, and access is granted based on these labels.
- **Enforcement:** The system enforces access controls based on the security labels, ensuring that users can only access resources with compatible labels.
- **Example:** In a MAC system, a user with a "Top Secret" clearance can only access files labeled as "Top Secret" or lower.

**Role-Based Access Control (RBAC):**

- **Overview:** RBAC assigns permissions to users based on their roles within an organization or system.
- **Roles:** Users are assigned roles based on their job responsibilities, and each role is associated with a set of permissions.
- **Simplicity:** Simplifies access control management by organizing permissions based on roles rather than individual users.
- **Granularity:** Provides a finer level of access control compared to DAC but may not be as strict as MAC.
- **Example:** In an RBAC system, a network administrator role might have permissions to configure network devices, while a guest user role might only have permissions to access public resources.

**Network Access Control (NAC) vs. Basic Linux Permissions:**

- **Basic Linux Permissions:** Control access to files and resources locally on a system based on user permissions.
    
- **NAC Systems:** Extend control to network access, offering several advantages:
    
    1. **Granular Control:** Define policies for network access based on user identity, device type, location, and security posture.
        
    2. **Dynamic Access:** Adjust access privileges in real-time based on changes in the network environment.
        
    3. **Integration:** Work with other security tools like IDS/IPS, firewalls, and SIEM systems to enhance security.
        
    4. **Compliance Enforcement:** Ensure compliance with organizational policies and regulatory requirements.
        
    5. **Visibility:** Provide visibility into devices and users accessing the network, aiding in monitoring and auditing.
        
    6. **Quarantine and Remediation:** Automatically quarantine compromised devices and initiate remediation actions in case of security incidents or policy violations.
        
- **Overall:** While Linux permissions control local access, NAC systems enhance security, compliance, and visibility across the entire network infrastructure.

**Hardening**
  - SELinux
  - AppArmor
  - TCP wrappers


## Remote desktop protocols in Linux

1. **Introduction to Remote Desktop Protocols:**
    
    - Remote desktop protocols enable graphical remote access to systems.
    - Used for troubleshooting, system upgrading, and remote administration.
2. **XServer (X11):**
    
    - XServer is part of the X Window System for Unix/Linux.
    - Facilitates communication between graphical user interface and OS.
    - Utilizes TCP/IP or Unix sockets for network transparency.
    - Ports typically range from TCP/6001-6009.
    - Can be accessed remotely without additional protocols on Unix/Linux systems.
    - X11 communication is unencrypted, posing security risks.
    - Vulnerabilities in XServer (e.g., CVE-2017-2624) can lead to unauthorized access.
    - SSH tunneling can secure X11 communication by enabling X11 forwarding.
3. **XDMCP (X Display Manager Control Protocol):**
    
    - Facilitates remote X Window sessions on Unix/Linux machines.
    - Communicates over UDP port 177.
    - Vulnerable to man-in-the-middle attacks and should not be used in high-security environments.
4. **VNC (Virtual Network Computing):**
    
    - Allows remote desktop sharing based on the RFB protocol.
    - Offers secure remote access and screen sharing.
    - Servers traditionally listen on TCP port 5900.
    - Common tools: TigerVNC, TightVNC, RealVNC, UltraVNC.
    - SSH tunneling can enhance security when connecting via VNC.
5. **Setting Up TigerVNC Server:**
    
    - Install necessary packages (e.g., xfce4, tigervnc-standalone-server).
    - Create password for VNC connection.
    - Configure xstartup and config files for session setup.
    - Start VNC server and list sessions.
    - Optionally, set up an SSH tunnel for secure connection.
6. **Connecting to VNC Server:**
    
    - Connect using appropriate VNC viewer (e.g., xtightvncviewer).
    - Authenticate with VNC server password.
    - Enjoy remote desktop access securely.


## Linux security 

- Keeping System Updated
- Firewall Configuration
- Disable password login and root SSH access:
	PasswordAuthentication no 
	PermitRootLogin no`
- Implement least privilege principle for user access.
- Use sudoers configuration for specific root commands.
- Utilize fail2ban for preventing brute-force attacks.
- Implement auditing tools like Lynis for system checks.
- Enable SELinux/AppArmor for granular access controls.
- Define policies to control user and application access.
- Remove unnecessary services and software.
- Enable NTP and ensure Syslog is running.
- Enforce strong passwords and password aging policies.

**TCP Wrappers:**
- Control access to services based on hostname/IP:
	- `/etc/hosts.allow`: Allow specific hosts/services.
	- `/etc/hosts.deny`: Deny specific hosts/services.

**Important Considerations:**
	- Order of rules in configuration files matters.
	- TCP wrappers complement firewall but don't replace it.

## Firewall Setup 

**1. Introduction to Firewalls:**
   - Purpose: Control and monitor network traffic.
   - Protects from unauthorized access and security threats.
   - Linux offers built-in firewall capabilities.

**2. History of Linux Firewalls:**
   - Example: iptables replaces ipchains and ipfwadm.
   - Introduced in Linux 2.4 kernel in 2000.
   - iptables became standard for Linux firewall solutions.

**3. Iptables:**
   - Provides rules for filtering network traffic.
   - Other solutions: nftables, UFW, FirewallD.
   - iptables: Flexible command-line interface.

**4. Components of iptables:**
   - Tables: Organize firewall rules.
   - Chains: Group rules for specific traffic.
   - Rules: Define filtering criteria and actions.
   - Matches: Criteria for filtering network traffic.
   - Targets: Specify actions for matched packets.

**5. Tables in iptables:**
   - Filter: IP addresses, ports, protocols.
   - Nat: Modify source/destination IP addresses.
   - Mangle: Modify header fields of packets.
   - Raw: Special packet processing options.

**6. Chains in iptables:**
   - Built-in: Pre-defined for different tasks.
   - User-defined: Group rules based on criteria.

**7. Rules and Targets:**
   - Define criteria for filtering network traffic.
   - Targets specify actions for matched packets.
   - Common targets: ACCEPT, DROP, REJECT, LOG, SNAT, DNAT, MASQUERADE, REDIRECT, MARK.

**8. Example Rule in iptables:**
   - Allow incoming TCP traffic on port 22 (SSH):
     ```
     sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
     ```

**9. Matches in iptables:**
   - Specify criteria for applying firewall rules.
   - Examples: Protocol, source/destination IP address, port, state, multiport, string, limit, conntrack, mark, MAC address, IP range.

**10. Example iptables Rule with Matches:**
   - Allow incoming TCP traffic on port 80 (HTTP):
     ```
     sudo iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
     ```

## System log

**1. Introduction to System Logs:**
   - Importance: Monitoring and troubleshooting system activities.
   - Provide insights into system behavior, application activity, and security events.
   - Valuable for identifying security weaknesses and vulnerabilities.

**2. Types of System Logs on Linux:**
   - Kernel Logs
   - System Logs
   - Authentication Logs
   - Application Logs
   - Security Logs

**3. Kernel Logs:**
   - Location: /var/log/kern.log
   - Information about the system's kernel, hardware drivers, and kernel events.
   - Helps identify vulnerabilities, system crashes, and suspicious activities.

**4. System Logs:**
   - Location: /var/log/syslog
   - Records system-level events like service starts/stops, login attempts, and system reboots.
   - Essential for detecting access attempts, abnormal activities, and system issues.

**5. Authentication Logs:**
   - Location: /var/log/auth.log
   - Focuses on user authentication attempts (successful and failed).
   - Crucial for identifying unauthorized access and security threats.

**6. Application Logs:**
   - Location: Varies based on the application (e.g., /var/log/apache2/error.log for Apache).
   - Contains information about specific application activities.
   - Helpful for identifying vulnerabilities, misconfigurations, and suspicious activities.

**7. Access and Audit Logs:**
   - Critical for tracking user and process activities.
   - Access logs record user/process actions like login attempts and file accesses.
   - Audit logs record security-relevant events such as system file modifications.
   - Essential for identifying security breaches and enforcing compliance.

**8. Security Logs:**
   - Location: Varies based on security application/tool (e.g., /var/log/fail2ban.log for Fail2ban).
   - Records security-related events like failed login attempts, firewall activity, and system file changes.
   - Important for detecting security issues and potential attack vectors.

**9. Log Analysis Tools:**
   - Utilize log file viewers in Linux desktop environments.
   - Command-line tools: tail, grep, sed for log analysis.
   - Proper analysis helps troubleshoot system issues and detect security breaches.

**10. Best Practices:**
   - Configure log levels appropriately.
   - Implement log rotation to manage log file sizes.
   - Regularly review and analyze logs for security risks.
   - Protect log files from unauthorized access.


## Solaris 

**1. Introduction to Solaris:**
   - Unix-based OS developed by Sun Microsystems, later acquired by Oracle.
   - Known for robustness, scalability, and support for high-end hardware/software.
   - Widely used in enterprise environments for mission-critical tasks like database management, cloud computing, and virtualization.

**2. Solaris Features:**
   - Built-in hypervisor (Oracle VM Server for SPARC) for virtualization.
   - High availability, fault tolerance, and system management features.
   - Used in banking, finance, government sectors, data centers, and cloud environments.

**3. Solaris vs Linux Distributions:**
   - Solaris: Proprietary, source code not publicly available.
   - Linux: Open-source, commonly uses ZFS file system.
   - Solaris: Uses Service Management Facility (SMF) for service management.

**4. Solaris Directory Structure:**
   - /: Root directory
   - /bin, /boot, /dev, /etc, /home, /kernel, /lib, /lost+found, /mnt, /opt, /proc, /sbin, /tmp, /usr, /var

**5. Solaris Unique Features:**
   - High-end hardware/software support.
   - Image Packaging System (IPS) for package management.
   - Advanced security features like Role-Based Access Control (RBAC).

**6. System Information:**
   - uname: Display basic system info in Linux.
   - showrev: Display detailed system info in Solaris.

**7. Installing Packages:**
   - Ubuntu: Uses apt-get for package installation.
   - Solaris: Uses pkgadd for package installation.

**8. Permission Management:**
   - Linux: Uses chmod to change file permissions.
   - Solaris: Similar command, find / -perm -4000 to find files with specific permissions.

**9. NFS in Solaris:**
   - Configuration using share command.
   - Mounting NFS file systems using mount command.
   - Configuration stored in /etc/dfs/dfstab file.

**10. Process Mapping:**
   - Ubuntu: Uses lsof to list files opened by a process.
   - Solaris: Uses pfiles for similar functionality.

**11. Executable Access:**
   - Ubuntu: Uses strace for tracing system calls.
   - Solaris: Uses truss for similar functionality.

## Tips

`systemctl list-units` 
	 Displays the systemd units currently loaded and running on the system. Units can be services, filesystem mounts, devices, etc. 
`systemctl list-unit-files`
	Lists the systemd unit files available on the system. These unit files, usually located in directories such as `/lib/systemd/system/` and `/etc/systemd/system/`, 
`systemctl show ≤nom du service>`
	Display all the information about an unit

```netcat -z 127.0.0.1 1-65535 ```
	Scan all port from 1 to 65535 on the machine and show which one is active

**To check battery capacity :**

```upower -e```
	Enumerate objects paths for devices
```upower -i /org/freedesktop/UPower/devices/battery_BAT0```
	Show information about object path

































