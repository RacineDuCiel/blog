---
title: '🐧 : find command'
date: 2024-02-15
tags: ["Linux commands"]
ShowToc: false
---


### Introduction:
In the realm of Linux, one command stands out as a powerful tool for searching and locating files and directories with ease: `find`. Whether you're a seasoned system administrator or a novice Linux user, mastering the `find` command can greatly enhance your efficiency and productivity. In this guide, we'll delve into what the `find` command is, its syntax, and various ways to utilize it effectively with practical examples.


The `find` command in Linux is a versatile utility designed to search for files and directories within a specified directory hierarchy based on various criteria. It provides a flexible means of locating specific files by name, size, modification time, permissions, and more.

### Basic Syntax:
```
find [directory] [options] [expression]
```

**Common Options:**
- `-name <pattern>`: Searches for files matching the specified name pattern.
- `-type <type>`: Filters files based on their type (e.g., `f` for regular files, `d` for directories).
- `-size <size>`: Filters files based on their size (e.g., `+10M` for files larger than 10 megabytes).
- `-mtime <days>`: Filters files based on their modification time (e.g., `-7` for files modified within the last 7 days).
- `-perm <mode>`: Matches files based on specific permissions (e.g., `644` for files with permissions set to 644).
- `-exec <command>`: Executes a command on each matched file or directory.

**Additional Options:**
- `-user <username>`: Searches for files owned by a specific user.
- `-group <groupname>`: Searches for files belonging to a specific group.
- `-depth <level>`: Limits the depth of the search.
- `-empty`: Matches empty files and directories.
- `-iname <pattern>`: Case-insensitive version of `-name`.
- `-maxdepth <level>`: Limits the maximum depth of the search.
- `-mindepth <level>`: Specifies the minimum depth of the search.
- `-delete`: Deletes the matched files or directories.
- `-print`: Prints the matched files or directories.

**Common Expressions:**
- `-and`: Combines multiple expressions with the logical AND operator.
- `-or`: Combines multiple expressions with the logical OR operator.
- `-not`: Negates the following expression.
- `-regex <pattern>`: Searches for files matching the specified regular expression.
- `-size +<size>`: Matches files larger than the specified size.
- `-size -<size>`: Matches files smaller than the specified size.
- `-mtime +<days>`: Matches files modified more than the specified number of days ago.
- `-mtime -<days>`: Matches files modified less than the specified number of days ago.
- `-exec <command> {} +`: Executes a command on multiple matched files at once.
- `-exec <command> {} \;`: Executes a command on each matched file individually.


### Practical Examples:
1. Finding Files by Name:
```
find /home/user/documents -name "example.txt"
```
This command searches for a file named "example.txt" within the "/home/user/documents" directory and its subdirectories.

2. Searching for Directories:
```
find /var/www -type d
```
Here, the command searches for directories within the "/var/www" directory.

3. Locating Large Files:
```
find /mnt/data -type f -size +100M
```
This command finds files larger than 100 megabytes within the "/mnt/data" directory.

4. Filtering Files by Modification Time:
```
find /backup -type f -mtime -7
```
This command locates files modified within the last 7 days in the "/backup" directory.

5. Finding Files with Specific Permissions:
```
find /etc -type f -perm 644
```
This command searches for files with permissions set to 644 within the "/etc" directory.
