---
title: '📝 : Operating System'
date: 2024-01-19
---

# 1. Basic Concepts & Structure

## Operating System Overview

An Operating System (OS) is a critical piece of software responsible for managing both the hardware and software resources of a computer. It acts as an intermediary between computer programs and the computer hardware. The core functions of an operating system include resource management—overseeing CPU, memory, disk space, and peripheral devices—along with file system management, which involves the creation, deletion, reading, and writing of files. Additionally, operating systems handle process management tasks such as the creation, deletion, synchronization, and scheduling of processes. They also ensure security and access control to protect data and resources from unauthorized access, and provide various user interfaces such as command-line interfaces, graphical interfaces, or touch-based interfaces.

## Types of Operating Systems

Operating systems can be categorized based on their design and application. Batch operating systems process groups of jobs with minimal user interaction, typical of early mainframes. Time-sharing operating systems allow multiple users to interact with the computer simultaneously, with UNIX being a prime example. Distributed operating systems manage a network of independent computers, making them appear as a single cohesive system, like Google's GFS. Real-Time Operating Systems (RTOS) offer timely execution for applications with strict timing constraints and are divided into Hard and Soft RTOS depending on the severity of these constraints. Embedded operating systems are designed specifically for embedded computing environments, such as VxWorks for embedded devices.

## System Structure

The structure of an operating system defines how its components are organized and interact. Monolithic systems consist of a single large program with all OS services residing in one memory block, offering speed but potentially at the cost of complexity. Microkernels adopt a minimalist approach, keeping only essential services in the kernel and running other services in user space. Layered systems organize the OS into a hierarchy of layers, each built upon the one below it. Modern systems often use a modular approach, which combines the efficiency of monolithic systems with the modularity and flexibility of microkernels.

## Key Concepts

Key concepts in operating system design include the distinction between kernel mode and user mode, where kernel mode has full access to all hardware and can execute any CPU instruction, while user mode is restricted to prevent unauthorized access to hardware. System calls provide a controlled interface for user programs to request services from the OS. Operating systems also handle interrupts and exceptions to manage events and errors, and the bootstrapping process involves starting the computer and loading the operating system.

## Hardware Abstraction Layer (HAL)

The Hardware Abstraction Layer (HAL) plays a crucial role in abstracting the specifics of hardware from the OS kernel and above layers, offering a uniform interface to interact with hardware components through device drivers.

## OS Services

Operating systems offer a range of services including user interfaces (shell for CLI or desktop environments for GUI), program execution capabilities, I/O operations, file system manipulation, communication services for processes, and error detection and response mechanisms to handle hardware and software errors effectively.

## User and Job Management

To manage users and their jobs efficiently, operating systems incorporate user accounts and authentication mechanisms to ensure security. They also employ various job scheduling techniques to optimize the use of system resources.

# 2. Process Management

## Process Concepts

A process is defined as a program in execution, encompassing the program code, current activity, and associated resources. The life cycle of a process includes several states: New, Ready, Running, Waiting, and Terminated. The Process Control Block (PCB) is a key data structure that contains essential information about each process, facilitating efficient process management.

## Scheduling Algorithms

Operating systems use various scheduling algorithms to manage processes efficiently. First-Come, First-Served (FCFS) serves processes in the order they arrive, while Shortest Job First (SJF) prioritizes processes with the shortest execution time. Round Robin (RR) allocates a small time slice to each process in a circular queue, ensuring fairness. Priority Scheduling serves processes based on their priority, and can be either preemptive or non-preemptive. Multilevel Queue Scheduling organizes processes into different queues based on priority, and Multilevel Feedback Queue (MLFQ) allows processes to move between queues based on their behavior and requirements.

## Process Synchronization

Process synchronization is essential in a multitasking environment to ensure that multiple processes do not access shared data or resources simultaneously. Synchronization tools such as semaphores, mutexes, and monitors are used to manage access to shared resources, preventing deadlocks where two or more processes wait indefinitely for resources held by each other.

## Inter-Process Communication (IPC)

IPC mechanisms enable processes to communicate and synchronize their actions without sharing the same address space. Pipes provide a unidirectional communication channel typically used between parent and child processes, message passing allows processes to communicate without sharing variables, and shared memory enables processes to access a common section of system memory for faster communication.

## Thread Management

Threads offer a way to improve application performance through parallelism. They have less overhead than processes and allow for

 easier sharing of data and more efficient communication between threads within the same process. Operating systems support various models of threads, including user-level and kernel-level threads, each with its synchronization, deadlocks, and CPU scheduling challenges.

## Advanced Topics

Advanced process management topics include process scheduling in multiprocessor systems, real-time scheduling for applications with specific timing requirements, and the interaction between process management and virtual memory systems, including paging and swapping.

# 3. Memory Management

## Basic Memory Concepts

Memory management in operating systems involves distinguishing between logical (virtual) and physical address spaces, where logical addresses are generated by the CPU, and physical addresses correspond to actual memory locations. Contiguous memory allocation assigns memory blocks contiguously, whereas dynamic partitioning divides memory into partitions as needed, potentially leading to external fragmentation. Fixed-size partitioning divides memory into fixed-size partitions, which can result in internal fragmentation.

## Paging and Segmentation

Paging is a memory management scheme that eliminates the need for contiguous allocation by dividing memory into fixed-size pages and mapping them to physical frames, potentially causing internal fragmentation. Segmentation divides memory into segments of varying sizes to more naturally reflect the structure of the data, such as code, stack, and heap segments, but can lead to external fragmentation.

## Virtual Memory

Virtual memory allows for the execution of processes that may not be completely in memory, using techniques like demand paging, where pages are loaded as needed rather than in advance. Various page replacement algorithms, including FIFO, LRU, and Optimal Page Replacement, are used to manage the limited physical memory efficiently. Thrashing occurs when a process spends more time paging than executing, significantly degrading performance.

## Memory Allocation and Advanced Concepts

Memory allocation strategies such as first-fit, best-fit, and worst-fit are used to allocate memory blocks efficiently. Garbage collection automates the process of reclaiming memory not currently in use. Advanced memory management concepts include swap space management for virtual memory, memory compression techniques to reduce the physical memory required, shared memory for efficient inter-process communication, and Copy on Write (COW) to optimize memory usage by allowing processes to share the same pages until modifications are made.

# 4. File Systems

## File System Basics

The file system manages how data is stored, retrieved, and updated on a storage disk, handling file attributes such as name, type, location, size, and protection, along with basic file operations like open, read, write, close, delete, and rename.

## Directory Structure and File System Implementation

Directory structures can range from single-level directories to complex general graph structures, allowing for various degrees of file organization and sharing. File system implementation methods include contiguous, linked, and indexed allocation, each with its advantages and challenges. Directory implementations may use linear lists, hash tables, or B+ trees for efficient file and directory management.

## File System Mounting and Access Methods

Mounting a file system involves attaching it to a directory tree at a designated mount point, allowing for access to its files and directories. Access methods include sequential and direct (random) access, catering to different application requirements.

## File System Protection and Virtual File Systems (VFS)

File system protection is crucial for data security, utilizing access control lists (ACLs) and encryption to restrict access and protect file data. The Virtual File System (VFS) provides an abstraction layer for uniform access to various file systems, facilitating a flexible and extensible file system architecture.

## Disk Space Management and File System Reliability

Disk space management techniques, such as free-space lists and bit vectors, are employed to track and allocate disk space efficiently. Quota management restricts the amount of disk space that users or groups can use. File system reliability is enhanced through journaling, redundancy (e.g., RAID configurations), and backup and recovery techniques to protect against data loss and ensure data integrity.

## Advanced File System Concepts

Advanced concepts include distributed file systems for accessing files across multiple hosts and special-purpose file systems optimized for specific data types or usage patterns, such as database file systems, providing specialized functionality and performance optimizations.

# 5. I/O Systems

## I/O Hardware Overview and Software Layers

I/O systems encompass a wide range of devices, including input, output, and storage devices, each controlled by specialized controllers and device drivers that provide a uniform interface to the operating system. The I/O software stack includes interrupt handlers, device drivers, device-independent I/O software, and user-space I/O software, offering a layered approach to I/O management that abstracts hardware specifics and provides a rich API for application developers.

## I/O Techniques and Disk Management

I/O techniques such as programmed I/O, interrupt-driven I/O, and Direct Memory Access (DMA) optimize the efficiency and performance of I/O operations. Disk management involves organizing the disk structure into platters, tracks, and sectors, and employing disk scheduling algorithms like FCFS, SSTF, SCAN, C-SCAN, LOOK, and their variants to improve access time and overall system performance. Disk formatting and partitioning prepare the disk for use and

 establish the file system, while the boot block contains essential code for system startup.

## File System Integration and I/O Device Characteristics

File systems such as FAT, NTFS, ext3/ext4, and HFS+ manage disk I/O, leveraging buffer caches for efficient data transfer. The characteristics of I/O devices, including the distinction between block devices and character devices and considerations for network devices, influence I/O system design and performance.

## I/O Performance Measurement and Advanced Techniques

I/O performance is measured in terms of throughput, latency, and bandwidth, with a detailed breakdown of I/O request time providing insights into performance bottlenecks. Advanced I/O techniques, including RAID for redundancy and performance enhancement, I/O virtualization for flexible resource management, and asynchronous I/O for improved efficiency, address the evolving needs of modern computing environments.

# 6. Secondary Storage Management

## Overview of Secondary Storage

Secondary storage refers to non-volatile storage devices such as HDDs, SSDs, and optical disks, characterized by their large storage capacity, non-volatile nature, and slower access speed compared to primary memory.

## Disk Structure, Operation, and Scheduling

The disk structure includes basic components like platters, tracks, sectors, and read/write heads, with access time components comprising seek time, rotational latency, and transfer time. Disk scheduling algorithms aim to minimize total seek time and enhance system performance, employing strategies like FCFS, SSTF, SCAN, C-SCAN, LOOK, and C-LOOK to efficiently service disk requests.

## Disk Formatting, Partitioning, and File Allocation

Low-level formatting defines the physical structure of the disk, while partitioning divides the disk into separate areas for independent management. High-level formatting establishes the file system within a partition. File allocation methods, including contiguous, linked, and indexed allocation, determine how files are stored on the disk.

## Swap-Space Management and RAID Storage

Swap-space management extends physical memory onto the disk, improving memory utilization and process management. RAID storage uses multiple disks in various configurations to balance performance, redundancy, and storage efficiency, enhancing fault tolerance and system reliability.

## Disk Reliability, Fault Tolerance, and Storage Virtualization

Ensuring disk reliability and fault tolerance involves strategies like regular backups, the use of RAID for redundancy, and error detection and correction techniques. Storage virtualization pools physical storage from multiple devices into a single managed entity, simplifying backup, archiving, and recovery processes.

# 7. Practical Applications & Case Studies

## Linux Operating System

The Linux operating system features a monolithic kernel with modular capabilities, supporting a wide range of applications from servers and embedded systems to the foundation for the Android OS. Its process management utilizes the Completely Fair Scheduler (CFS) to support multitasking and multi-core processors efficiently. Linux's memory management includes virtual memory, demand paging, and swap management, with the ext3/ext4 file systems and support for various file systems through the Virtual File System (VFS).

## Windows Operating System

Windows employs a hybrid kernel that merges aspects of microkernels and monolithic kernels, offering a comprehensive Windows API for process and thread management. Its memory management system uses virtual memory with a paging file and features like Prefetcher and SuperFetch to enhance performance. The NTFS file system provides advanced features such as encryption, disk quotas, and shadow copies, making Windows a dominant force in desktop computing and enterprise environments.

## macOS Operating System

macOS uses the XNU kernel, a hybrid that combines the Mach microkernel with parts of FreeBSD's monolithic kernel. It features advanced process management with Grand Central Dispatch for optimizing multi-core processor use and memory management techniques including Automatic Reference Counting. The APFS file system is designed for high performance and encryption, with macOS being integral to the Apple ecosystem, particularly for creative professional applications.

## Android OS

Android is based on a modified Linux kernel, offering a comprehensive application framework and a runtime environment initially based on the Dalvik Virtual Machine, later replaced by the Android Runtime (ART). Its widespread adoption in the mobile device market and the rich application development ecosystem demonstrate its versatility and impact on modern mobile computing.

## iOS

iOS utilizes the XNU kernel derived from macOS, offering a robust platform for application development with the Cocoa Touch framework and programming languages like Swift and Objective-C. It emphasizes user privacy and security, featuring technologies like the Secure Enclave and a strict app review process, ensuring a trusted environment for mobile devices.

## UNIX and Solaris

UNIX has laid the foundation for many modern operating systems, adhering to POSIX standards and influencing a wide range of systems including Solaris, known for its scalability and robust network capabilities. These systems have found extensive use in academic, research, and large-scale enterprise environments, demonstrating their reliability and versatility.

## Real-Time Operating Systems (RTOS)

RTOS examples like VxWorks and QNX illustrate the critical role of real-time operating systems in embedded systems, automotive, aerospace, and telecommunications. Their applications, such as the Mars Rover's use of VxWorks and automotive control systems using QNX, highlight

 their importance in mission-critical environments where timing and reliability are paramount.

## Distributed Operating Systems

Distributed operating systems, including Google's GFS and Hadoop's HDFS, cater to the needs of big data processing and scalable web services. Their implementation in large-scale cloud computing environments showcases the evolution of operating systems to address the challenges of distributed computing and data management in the modern era.
