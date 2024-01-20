---
title: '🐧 : dd command'
date: 2024-01-14
tags: ["Linux commands"]
---
--  


The `dd` command in Linux is a versatile and powerful utility designed for low-level copying and conversion of data.  

Standing for "data duplicator", dd is commonly used for tasks such as creating disk images, copying data between devices, and converting file formats. It operates at the block level, allowing users to manipulate data at a more granular level than many other file-oriented commands. The dd command is often employed for tasks like backup and recovery, disk cloning, and the creation of bootable USB drives.  

Its flexibility and ability to interact with data at a fundamental level make it an essential tool for system administrators and advanced users working with storage devices and data manipulation on Linux systems.  

--

### The basic syntax of the `dd` command :

```bash
dd [options] [if] [of] [bf]
```

- `[options]`: Optional flags or parameters that modify the
behavior of the `dd` command.
- `[if]`: Input file or block input (device-file). This is the
source from where data will be read.
- `[of]`: Output file or block output (device-file). This is
the destination where data will be written.
- `[bf]`: Block size or bswap file endianess. The block size
specifies how much data will be transferred at a time, and it
can help improve performance by reducing the number of I/O
operations.



**Common options :**

- `count=<number>`: Copy a specified number of blocks. A block
is defined as the given block size.
- `conv=<conversion>`: Perform data conversions as specified by
the conversion parameter.
- `status=progress`: Show progress during the copy process.

--
# Examples


### 1. Copying a file with progress indication :
```bash
dd if=input.file of=output.file bs=1M status=progress
```
This will copy the data from the input file "input.file" to the
output file "output.file" in 1 megabyte blocks, and display the
progress during the process.

--

### 2. Creating an ISO image from a USB drive :

```bash
dd if=/dev/sdX of=/path/to/destination/image.iso bs=4M
```
This command reads data from the USB drive (/dev/sdX) as a block input and writes it to the "output.iso" file in 2 megabyte blocks, performing synchronous reading and writing with no error correction. This will create an ISO image of the DVD.

--

### 3. Cloning a disk or partition to another one :
```bash
dd if=/dev/sdb of=/dev/sda bs=4M status=progress conv=noerror,notrunc
```
This command copies the contents from one block device `(/dev/sdb)` to another block device `(/dev/sda)`. The `conv=noerror,notrunc` option indicates that the command should continue copying data even if errors are encountered in the source file, replacing the erroneous data with null bytes. Additionally, it ensures that the destination file is not truncated to the size of the source file if it is smaller.

--

### 4. Erasing a disk :
```bash
dd if=/dev/zero of=/dev/sdX bs=4M status=progress
```

The provided dd command is used to erase the contents of a USB drive `(/dev/sdX)` by overwriting it with zeros. The `if=/dev/zero` specifies that the input source is a stream of null bytes (zeros), and the `of=/dev/sdX` designates the USB drive as the output file.
