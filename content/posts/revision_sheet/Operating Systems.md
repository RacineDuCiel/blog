---
title: '📝 : Operating System'
date: 2024-01-19
---

### 1. **Basic Concepts & Structure**

#### **Operating System Overview**
- **Definition**: An operating system (OS) is software that manages computer hardware and software resources and provides common services for computer programs.
- **Core Functions**:
  - **Resource Management**: Manages CPU, memory, disk space, and peripheral devices.
  - **File System Management**: Controls the creation, deletion, reading, and writing of files.
  - **Process Management**: Handles process creation, deletion, synchronization, and scheduling.
  - **Security & Access Control**: Protects data and resources from unauthorized access.
  - **User Interface**: Command-line, Graphical (GUI), or Touch-based.

#### **Types of Operating Systems**
- **Batch Operating Systems**: Processes batches of jobs without user interaction. E.g., Early mainframes.
- **Time-Sharing Operating Systems**: Allows multiple users to use the computer simultaneously. E.g., UNIX.
- **Distributed Operating Systems**: Manages a group of independent computers and makes them appear to be a single computer. E.g., Google's GFS (Google File System).
- **Real-Time Operating Systems (RTOS)**: Provides real-time execution. Divided into Hard RTOS (strict time constraints) and Soft RTOS (more lenient).
- **Embedded Operating Systems**: Designed for embedded computer systems. E.g., VxWorks for embedded devices.

#### **System Structure**
- **Monolithic Systems**: Single large program where all OS services reside in a single memory block.
- **Microkernels**: Minimalist approach, only essential core services in kernel; user-space services outside the kernel.
- **Layered Systems**: OS is divided into a series of layers, each built upon the one below.
- **Modules**: Modern approach, combining monolithic system's speed and microkernel's modularity.

#### **Key Concepts**
- **Kernel Mode vs. User Mode**: Kernel mode has full access to all hardware and can execute any CPU instruction. User mode is restricted.
- **System Calls**: Interface between user programs and the OS, e.g., `open()`, `read()`, `write()`, `close()` in file operations.
- **Interrupts and Exceptions**: Mechanisms for the CPU to handle events (interrupts) or errors (exceptions).
- **Bootstrapping (Booting)**: Process of starting the computer and loading the operating system.

#### **Hardware Abstraction Layer (HAL)**
- **Purpose**: Abstracts and hides hardware specifics from the OS kernel and above layers.
- **Functionality**: Includes device drivers and provides a uniform interface to interact with hardware.

#### **OS Services**
- **User Interface**: Shell (CLI) or Desktop Environment (GUI).
- **Program Execution**: Ability to load and run programs, including memory allocation, I/O resource allocation, and cleanup.
- **I/O Operations**: Abstracted access to hardware devices.
- **File System Manipulation**: File creation, deletion, read, write, permissions.
- **Communication**: Processes may exchange information on the same computer or between computers over a network.
- **Error Detection & Response**: Detect hardware and software errors and take appropriate action.

#### **User and Job Management**
- **User Accounts & Authentication**: Ensuring user identity and security.
- **Job Scheduling**: Determining the order in which jobs or processes are given access to system resources.

### 2. **Process Management**

#### **Process Concepts**
- **Definition**: A process is a program in execution, consisting of program code, current activity, and associated resources.
- **Process States**: New, Ready, Running, Waiting, Terminated.
- **Process Control Block (PCB)**: Data structure in the OS kernel containing essential information about each process, like process state, program counter, CPU registers, memory-management information, accounting information, and I/O status information.

#### **Scheduling Algorithms**
- **First-Come, First-Served (FCFS)**: Processes are served in the order they arrive.
- **Shortest Job First (SJF)**: Process with the smallest execution time is selected next.
- **Round Robin (RR)**: Each process gets a small time slice, rotating in a circular queue structure.
- **Priority Scheduling**: Process with the highest priority served first. Can be preemptive or non-preemptive.
- **Multilevel Queue Scheduling**: Queue set with different priorities, e.g., system processes, interactive processes, batch jobs.
- **Multilevel Feedback Queue (MLFQ)**: Allows a process to move between queues based on their behavior and requirements.

#### **Process Synchronization**
- **Critical Section Problem**: Ensuring multiple processes do not access shared data or resources simultaneously.
- **Synchronization Tools**: Semaphores, Mutexes, Monitors.
- **Deadlocks**: System becomes locked because two processes are each waiting for the other to release a resource.

#### **Inter-Process Communication (IPC)**
- **Pipes**: Unidirectional communication channel, typically used between parent and child processes.
- **Message Passing**: Processes communicate with each other without sharing variables.
- **Shared Memory**: Processes share a section of system memory.

#### [**Thread Management**](/posts/revision_sheet/thread-management/)
- **Benefits of Threads**: Less overhead than processes, easier sharing of data, efficient communication.
- **Models of Threads**: User-Level Threads, Kernel-Level Threads.
- **Multithreading Issues**: Synchronization, Deadlocks, CPU Scheduling.

#### Advanced Topics
- **Process Scheduling in Multiprocessor Systems**: Load balancing, affinity scheduling.
- **Real-Time Scheduling**: Meeting specific timing requirements, often found in embedded systems.
- **Virtual Memory Interaction**: How process management works with paging and swapping.

### 3. **Memory Management**

#### **Basic Memory Concepts**
- **Logical vs. Physical Address Space**: Logical (virtual) addresses are generated by the CPU; physical addresses refer to actual physical locations in memory.
- **Contiguous Memory Allocation**: Memory is allocated in contiguous blocks.
- **Dynamic Partitioning**: Memory is divided into partitions as required; suffers from external fragmentation.
- **Fixed-Size Partitioning**: Memory is divided into fixed-size partitions; leads to internal fragmentation.

#### **Paging and Segmentation**
- **Paging**: Divides memory into fixed-size pages. Logical address space is also divided into pages, mapped to physical frames.
  - **Page Table**: Maps logical pages to physical frames.
  - **Fragmentation**: Paging suffers from internal fragmentation.
- **Segmentation**: Divides memory into segments of different sizes, reflecting the nature of the data (code, stack, heap).
  - **Segment Table**: Maps segments to physical memory.
  - **Fragmentation**: Segmentation can suffer from external fragmentation.

#### **Virtual Memory**
- **Concept**: Allows execution of processes that may not be completely in memory.
- **Demand Paging**: Pages are loaded on demand, not in advance.
- **Page Replacement Algorithms**:
  - **FIFO (First In First Out)**
  - **LRU (Least Recently Used)**
  - **Optimal Page Replacement**
- **Thrashing**: Occurs when a process spends more time paging than executing.

#### **Memory Allocation**
- **First-fit, Best-fit, Worst-fit**: Strategies for allocating memory blocks.
- **Garbage Collection**: Automated process of reclaiming memory not in use.

#### **Advanced Memory Management Concepts**
- **Swap Space Management**: Part of a disk used as virtual memory.
- **Memory Compression**: Techniques to reduce the physical memory required to store data.
- **Shared Memory**: Allows multiple processes to access common structures in memory.
- **Copy on Write (COW)**: Optimizes memory usage by allowing multiple processes to share the same pages until they modify them.

### 4. **File Systems**

#### **File System Basics**
- **Definition and Purpose**: Manages how data is stored, retrieved, and updated on a storage disk.
- **File Attributes**: Name, type, location, size, protection, creation and modification times, etc.
- **File Operations**: Open, read, write, close, delete, rename, etc.

#### **Directory Structure**
- **Types of Directory Structures**:
  - **Single-Level Directory**: Simplest, all files in one directory.
  - **Two-Level Directory**: Separate directory for each user.
  - **Tree-Structured Directories**: Hierarchical structure allowing directories within directories.
  - **Acyclic-Graph Directory Structure**: Allows sharing of files and directories.
  - **General Graph Directory Structure**: More complex, allows directories to have multiple parents.

#### **File System Implementation**
- **File Allocation Methods**:
  - **Contiguous Allocation**: Each file occupies a set of contiguous blocks.
  - **Linked Allocation**: Each file is a linked list of disk blocks.
  - **Indexed Allocation**: Each file has its own index block, which is an array of disk-block addresses.
- **Directory Implementation**: Linear list, Hash Table, B+ Trees.

#### **File System Mounting**
- **Process**: Attaching a file system to a directory tree at a designated mount point.

#### **Access Methods**
- **Sequential Access**: Reading/writing data in a sequential manner.
- **Direct (Random) Access**: Randomly accessing data at any location.

#### **File System Protection**
- **Access Control Lists (ACLs)**: Specify which users or system processes can access a file/directory and operations allowed.
- **Encryption**: Protects file data from unauthorized access.

#### **Virtual File Systems (VFS)**
- **Purpose**: Provides an abstraction layer to allow uniform access to different types of file systems.
- **Functionality**: Interface between the kernel and various file systems.

#### **Disk Space Management**
- **Techniques**: Free-space list, bit vector, grouping, counting.
- **Quota Management**: Limiting the amount of disk space a user or group can use.

#### **File System Reliability**
- **Journaling**: Tracking changes not yet committed to the file system.
- **Redundancy**: RAID configurations to protect against data loss.
- **Backup & Recovery**: Techniques for data backup and restoration.

#### **Advanced File System Concepts**
- **Distributed File Systems**: Allows users to access files from multiple hosts.
- **Special-Purpose File Systems**: Optimized for specific data types or usage patterns, e.g., database file systems.

### 5. **I/O Systems**

#### **I/O Hardware Overview**
- **Devices**: Input devices (keyboard, mouse), output devices (monitors, printers), and storage devices (hard drives, USB flash drives).
- **Controllers**: Special-purpose computers that control the operation of the specific device.
- **Device Drivers**: Software modules that directly interact with the device hardware, providing a uniform interface to the OS.

#### **I/O Software Layers**
- **Interrupt Handlers**: Deal with interrupts generated by I/O devices.
- **Device Drivers**: Manage communications with specific types of devices.
- **Device-Independent I/O Software**: Provides uniform interfacing for all devices, abstracting device specifics.
- **User-Space I/O Software**: Libraries and system calls that provide API for application programmers.

#### **I/O Techniques**
- **Programmed I/O**: CPU is fully engaged in the I/O operation, repeatedly checking the device status.
- **Interrupt-Driven I/O**: CPU is interrupted when I/O device is ready, reducing CPU's involvement.
- **Direct Memory Access (DMA)**: Allows devices to transfer data to/from memory without constant CPU intervention.

#### **Disk Management**
- **Disk Structure**: Platters, tracks, sectors, and the disk arm.
- **Disk Scheduling Algorithms**:
  - **FCFS**
  - **SSTF**
  - **SCAN**
  - **C-SCAN**
  - **LOOK**
- **Disk Formatting**: Preparing the disk for use, establishing a file system.
- **Boot Block**: Special sector that contains a bootloader.

#### **File System Integration**
- **File Allocation Table (FAT)**, **NTFS**, **ext3/ext4**, **HFS+**: Examples of how various file systems manage disk I/O.
- **Buffer Cache**: Memory area for buffering data during I/O operations.

#### **Characteristics of I/O Devices**
- **Block Devices vs. Character Devices**: Differences in data access patterns and buffering requirements.
- **Network Devices**: Special considerations for data transfer over networks.

#### **I/O Performance Measurement**
- **Throughput, Latency, and Bandwidth**: Key metrics for assessing I/O system performance.
- **I/O Request Time Breakdown**: Different stages of I/O processing and their impact on overall performance.

#### **Advanced I/O Techniques**
- **RAID (Redundant Array of Independent Disks)**: Enhancing performance and reliability through disk redundancy.
- **I/O Virtualization**: Abstraction of physical I/O resources in a virtual environment.
- **Asynchronous I/O**: Improving efficiency by allowing other processing to occur simultaneously with I/O operations.

### 6. **Secondary Storage Management**

#### **Overview of Secondary Storage**
- **Definition**: Secondary storage refers to non-volatile storage devices, such as hard disk drives (HDDs), solid-state drives (SSDs), and optical disks.
- **Characteristics**: Larger storage capacity than primary memory, non-volatile, slower access speed.

#### **Disk Structure and Operation**
- **Basic Components**: Platters, tracks, sectors, spindle, read/write heads.
- **Access Time Components**: Seek time, rotational latency, transfer time.

#### **Disk Scheduling**
- **Goal**: Minimize the total seek time and improve system performance.
- **Algorithms**:
  - **FCFS (First-Come, First-Served)**: Simple, but can lead to long wait times.
  - **SSTF (Shortest Seek Time First)**: Selects the request closest to the current head position.
  - **SCAN (Elevator Algorithm)**: Moves the head from one end of the disk to the other, servicing requests along the way.
  - **C-SCAN (Circular SCAN)**: Similar to SCAN, but only services in one direction.
  - **LOOK and C-LOOK Variants**: Similar to SCAN and C-SCAN but the head only goes as far as the last request in each direction.

#### **Disk Formatting and Partitioning**
- **Low-Level Formatting**: Defines the physical structure of the disk.
- **Partitioning**: Dividing a disk into separate areas, each treated as an independent disk.
- **High-Level Formatting**: Establishing a file system within a partition.

#### **File Allocation**
- **Contiguous Allocation**: Files are stored in contiguous sectors on the disk.
- **Linked Allocation**: Each file is a list of disk blocks.
- **Indexed Allocation**: Uses an index block to keep track of all the blocks in a file.

#### **Swap-Space Management**
- **Function**: Provides a space on disk where pages can be written to and read from, offering an extension to the physical memory.
- **Swap-Space Location**: Can be a dedicated swap partition or a file within a file system.

#### **RAID Storage**
- **RAID Levels**: Different configurations (RAID 0, 1, 5, 6, 10) offering various trade-offs in performance, redundancy, and storage efficiency.
- **Purpose**: Improve performance and provide fault tolerance.

#### **Disk Reliability and Fault Tolerance**
- **Backup Strategies**: Regular backups to safeguard against data loss.
- **Redundant Arrays of Independent Disks (RAID)**: Using multiple disks for redundancy and performance.
- **Error Detection and Correction**: Techniques such as ECC (Error-Correcting Code) to maintain data integrity.

#### **Storage Virtualization**
- **Concept**: Pooling physical storage from multiple network storage devices into a single storage device managed from a central console.
- **Benefits**: Easier backup, archiving, and recovery.

### 7. **Practical Applications & Case Studies**

#### **Linux Operating System**
- **Kernel Structure**: Monolithic with modules.
- **Process Management**: Use of CFS (Completely Fair Scheduler), support for multi-threading and multi-core processors.
- **Memory Management**: Virtual Memory, Demand Paging, Swap Management.
- **File System**: Ext3/Ext4, support for various file systems through VFS.
- **Case Study**: Deployment in servers, embedded systems, and as a basis for Android OS.

#### **Windows Operating System**
- **Kernel Structure**: Hybrid kernel, combining aspects of microkernels and monolithic kernels.
- **Process and Thread Management**: Windows API for process and thread operations, Scheduler Types.
- **Memory Management**: Virtual Memory using a paging file, Prefetcher and SuperFetch technologies.
- **File System**: NTFS with features like encryption, disk quotas, and shadow copies.
- **Case Study**: Dominance in desktop computing, use in enterprise environments.

#### **macOS Operating System**
- **Kernel Structure**: XNU (a hybrid kernel), combining Mach (microkernel) and parts of FreeBSD (monolithic kernel).
- **Process Management**: Grand Central Dispatch for optimizing multi-core processors.
- **Memory Management**: Advanced Memory Management, including Automatic Reference Counting for Objective-C.
- **File System**: APFS (Apple File System) focusing on encryption and performance.
- **Case Study**: Integration with Apple ecosystem, focus on creative professional usage.

#### **Android OS**
- **Kernel**: Modified Linux kernel.
- **Application Framework**: Activities, Services, Content Providers, Broadcast Receivers.
- **Runtime Environment**: Dalvik Virtual Machine (replaced by Android Runtime, ART).
- **Case Study**: Dominance in mobile device market, application development ecosystem.

#### **iOS**
- **Kernel**: XNU Kernel, derived from macOS.
- **Application Development**: Cocoa Touch framework, Swift and Objective-C programming languages.
- **Security**: Secure Enclave for data protection, strict app review process.
- **Case Study**: Widespread use in mobile devices, emphasis on user privacy and security.

#### **UNIX and Solaris**
- **UNIX**: Foundation for many modern OS, POSIX standards.
- **Solaris**: A UNIX-based OS, known for scalability and robust network capabilities.
- **Case Study**: Use in academic, research, and large-scale enterprise environments.

#### **Real-Time Operating Systems (RTOS)**
- **Examples**: VxWorks, QNX.
- **Applications**: Used in embedded systems, automotive, aerospace, and telecommunications.
- **Case Study**: Mars Rover's use of VxWorks, automotive control systems using QNX.

#### **Distributed Operating Systems**
- **Examples**: Google's GFS, Hadoop's HDFS.
- **Applications**: Big data processing, scalable web services.
- **Case Study**: Implementation in large-scale cloud computing environments.
