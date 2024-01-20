---
title: '🔖  : Operating System'
date: 2024-01-19
---

## 1 : Introduction to Operating Systems

### 1.1 What is an Operating System?

An operating system (OS) is essential software that acts as an intermediary between the computer hardware and the software applications. It is the backbone of a computer system, responsible for managing both hardware resources (like CPU, memory, and disk drives) and providing an environment for software applications to run.

The primary functions of an operating system include:

- **Process Management**: An OS handles the creation, scheduling, and termination of processes.

- **Memory Management**: The OS is responsible for managing the system's memory. It allocates memory to processes when they need it and deallocates it when they are done. It also manages virtual memory, allowing systems to use more memory than what is physically available.

- **File System Management**: Operating systems manage files on computers, providing a way to store data, retrieve it, and manage it. This includes managing directories (or folders) and handling the access permissions for files and directories.

- **Device Management**: The OS manages device communication via their respective drivers. This includes internal components like the CPU and RAM, and external devices like printers and scanners.

- **Security and Access Control**: The OS is responsible for system security, ensuring that unauthorized users do not access the system. It manages user accounts, passwords, and various permissions to safeguard the data and resources.

- **User Interface**: Operating systems provide interfaces for user interaction. This can be a graphical user interface (GUI) like in Windows or MacOS or a command-line interface (CLI) like in Unix or Linux.

### 1.2 The Role of Operating Systems

- **User Interface (UI)**: The UI is how users interact with the computer. Most modern OSes provide a GUI, which allows users to interact with the system using graphical elements like windows, icons, and menus. Command-line interfaces, though less intuitive, offer powerful scripting capabilities and are widely used in server environments.

- **Resource Allocation**: The OS decides how to allocate resources to various programs and processes. For instance, it determines which process gets CPU time, how much memory is allocated to processes, and the order in which processes access storage devices.

- **Managing Hardware and Software Resources**: The OS acts as a mediator between the hardware and the application software. Without the OS, application programs would need to understand the specifics of every piece of hardware, which is impractical. The OS abstracts this complexity, providing a standard interface for applications to interact with the hardware.

### 1.3 Types of Operating Systems

- **Batch Operating Systems**: These were among the first operating systems. They do not allow for user interaction with the computer. Jobs are collected, batched, and executed one after another.

- **Time-Sharing Systems**: These systems allow multiple users to access the computer simultaneously by rapidly switching between users, giving the illusion of direct access to each user.

- **Distributed Operating Systems**: These systems manage a group of distinct computers and make them appear as a single coherent system to the user. They are used in environments where multiple computers need to work on a single task.

- **Real-Time Operating Systems (RTOS)**: These are used in environments where time constraints are stringent, like in embedded systems, medical equipment, or spacecraft. They are designed to process data as it comes in, typically without buffering delays.

### 1.4 History and Evolution of Operating Systems

- **Early Systems**: The earliest operating systems were developed in the 1950s. They were primitive by today's standards, often providing basic batch processing without any interactive interface.

- **The Evolution of OS Design**: Over time, operating systems have evolved to meet the growing complexity of computer hardware and the needs of more sophisticated applications. This evolution brought forth concepts like multitasking, graphical user interfaces, networking capabilities, and enhanced security features.

- **Influential Operating Systems**: Some key milestones in OS development include:
    - **UNIX**: Developed in the 1970s, UNIX was significant for its portability, multi-user capability, and powerful command-line interface. It has influenced many operating systems, including Linux.
    - **MS-DOS**: Microsoft's Disk Operating System, was the predominant OS for IBM-compatible PCs during the 1980s.
    - **Windows**: Microsoft Windows brought a graphical user interface and broadened the personal computing market.
    - **Linux**: An open-source OS modeled on UNIX, Linux is renowned for its robustness and is extensively used in servers, desktops, and embedded systems.
    - **MacOS**: Known for its user-friendly interface and sleek design, MacOS is the operating system for Apple's Mac computers.

### 1.5 Operating System Components

- **Kernel**: This is the heart of the operating system. It manages the system's resources and communicates directly with the hardware. It is responsible for low-level tasks like disk management, memory management, task scheduling, and handling system calls.

- **Shell**: This is the outermost layer of an OS. It interprets user commands and executes the appropriate programs or functions in the kernel. In Unix and Linux, the shell is often a command-line interface, though graphical shells (like GNOME or KDE) are also common.

- **System Utilities**: These are the programs that provide the user with the capabilities to manage and tune the system. They include disk management tools, file editors, network configuration tools, and system monitoring tools.

---

## 2 : OS Architecture and Design

### 2.1 Kernel Types

- **Monolithic Kernel**: A monolithic kernel is a single large process running entirely in a single address space. It is very efficient due to the minimal amount of context switching required. The Linux kernel is an example. All the essential parts of the OS, like process management, file system, device drivers, are integrated into one piece of software.

- **Microkernel**: In a microkernel, only the most fundamental components like IPC (Inter-process communication) and basic scheduling are included in the kernel. Other services like file systems, device drivers, etc., are run in user space. This structure enhances security and stability but can reduce performance due to more system calls and context switches. An example is the Minix OS.

- **Hybrid Kernel**: A hybrid kernel tries to balance the simplicity and robustness of a microkernel with the performance of a monolithic kernel. It includes more services in the kernel than a microkernel but is still modular. Windows NT and later versions use a hybrid kernel.

### 2.2 Process and Threads Management

#### Process Management

- **Definition and Role**: A process is an instance of a program in execution, characterized by its code, current activity, and allocated system resources. Process management is crucial for the efficient and fair allocation of these resources.

- **Process Lifecycle**:
  - **Creation**: Initiated by system calls such as `fork()` or `exec()`. Involves assigning a unique process identifier (PID), allocating memory, and setting up the process control block (PCB).
  - **Execution**: The processor executes the process instructions. This stage alternates between running (using the CPU) and waiting (for I/O or other resources).
  - **Blocking**: A process is blocked and relinquishes the CPU when it cannot proceed until some external condition is met, such as the completion of an I/O operation.
  - **Termination**: Occurs when a process finishes its execution or is killed. Resources are reclaimed, and the PCB is updated.

- **Process Control Block (PCB)**: Contains important process information such as the process state, program counter, CPU registers, memory limits, list of open files, and process ID.

- **Scheduling**:
  - **Objective**: Allocate CPU time among processes in a manner that meets system objectives, such as responsiveness, throughput, and processor efficiency.
  - **Scheduling Algorithms**: Include First-Come, First-Served (FCFS), Shortest Job First (SJF), Priority Scheduling, Round Robin (RR), and Multilevel Queue Scheduling.

- **Context Switching**: Involves switching the CPU from one process or thread to another. Includes saving the state of the current process and loading the saved state of the next process.

#### Thread Management

- **Thread Concept**: A thread is the smallest unit of processing that can be scheduled by an OS. Threads within the same process share resources like memory and file handles but have their own stack and program counter.

- **Multithreading Models**:
  - **One-to-One Model**: Each user-level thread maps to a kernel thread. Provides concurrency and less overhead but has limitations on the number of threads due to system resources.
  - **Many-to-One Model**: Maps many user-level threads to one kernel thread. Efficient but one thread blocking causes the entire process to block.
  - **Many-to-Many Model**: Combines both models, allowing many user-level threads to be mapped to many kernel threads.


- **Thread Lifecycle**:
  - **Creation**: Initiated through APIs provided by the OS or threading libraries.
  - **Execution**: The scheduler allocates CPU time to threads similarly to processes.
  - **Waiting**: Threads may wait for resources or for other threads to complete.
  - **Termination**: A thread can terminate itself, or it can be terminated by another thread or the process.


#### Process and Thread Scheduling

- **Preemptive vs. Non-Preemptive Scheduling**:
  - **Preemptive**: The OS decides when a process or thread should be interrupted and replaced by another. It is essential for ensuring responsiveness in time-sharing systems.
  - **Non-Preemptive**: A process or thread relinquishes control of the CPU voluntarily, usually after completing its current task.

- **Real-Time Scheduling**: Critical for systems where time constraints must be met. Includes algorithms like Rate-Monotonic Scheduling (RMS) and Earliest Deadline First (EDF).

#### Advanced Topics

- **Thread Pools**: Creating a number of threads at process start-up and reusing them for different tasks can significantly reduce the overhead of creating and destroying threads.

- **Symmetric Multiprocessing (SMP)**: Involves multiple processors managing processes and threads concurrently, requiring sophisticated synchronization and scheduling strategies.

- **Green Threads and Fibers**: User-level thread libraries, like green threads in Java Virtual Machine, which are managed without kernel support. Fibers are lightweight threads that don't require preemption.

### 2.3 Memory Management

#### Basics of Memory Management
- **Role and Importance**: Memory management is vital for optimizing the use of the main memory (RAM), providing a way to dynamically allocate memory to programs during execution, and ensuring the efficient use of memory resources.
- **Memory Manager**: A subsystem within the OS responsible for managing memory. It keeps track of each byte in the computer's memory and whether it is free or in use, and allocates and deallocates memory spaces as needed by programs.

#### Memory Allocation
- **Fixed Partitioning**:
    - **Concept**: The earliest and simplest form of memory management, dividing memory into fixed-size blocks.
    - **Limitations**: Leads to internal fragmentation (wasted space within partitions) and limits the size of the process to the size of a partition.
- **Dynamic Partitioning**:
    - **Concept**: Partitions are created dynamically, so each process gets exactly as much memory as it needs.
    - **Types of Dynamic Partitioning**: Includes first-fit (allocating the first hole that's big enough), best-fit (allocating the smallest hole that's big enough), and worst-fit (allocating the largest hole).
    - **External Fragmentation**: A major drawback, where total memory space exists to satisfy a request, but it is not contiguous.

#### Paging
- **Concept**: Divides memory into fixed-size units called pages, which are mapped onto frames in physical memory.
- **Page Table**: Used to keep track of the mapping between virtual pages and physical frames. Each process has its own page table.
- **Advantages**: Eliminates external fragmentation and reduces internal fragmentation.
- **Page Replacement Algorithms**: When a page needs to be swapped in and the memory is full, the OS must decide which page to swap out. Common algorithms include FIFO (First-In, First-Out), LRU (Least Recently Used), and Optimal Page Replacement.

#### Segmentation
- **Concept**: Memory management scheme that supports user view of memory. A program is a collection of segments, where a segment can be a function, an array, etc.
- **Segment Table**: Maps two-dimensional logical addresses into one-dimensional physical addresses. Each table entry has a base (starting address of the segment in physical memory) and a limit (the length of the segment).
- **Advantages**: Supports modular programming and allows programs to be altered and recompiled independently.

#### Virtual Memory
- **Definition**: A technique that provides an "idealized abstraction of the storage resources that are actually available on a given machine," creating the illusion to users of a very large memory.
- **Implementation**: Typically involves paging and a page table, with some parts of the memory stored on the disk (swap space).
- **Demand Paging**: Pages are loaded into memory on demand. The OS guesses which pages will be used next and preloads them, reducing access time.
- **Thrashing**: Occurs when the OS spends more time swapping pages in and out of memory than executing instructions. It's a signal that the system is over-committed.

#### Memory Protection and Sharing
- **Protection**: Ensures that each process in the system has its own separate memory space and cannot access the memory space of another process unless explicitly allowed.
- **Sharing**: Allows multiple processes to access the same memory space. This is crucial for inter-process communication and for allowing multiple instances of a program to access the same data.

#### Advanced Memory Management Techniques
- **Garbage Collection**: In languages like Java, the system automatically reclaims memory that a program no longer needs. This involves identifying which objects are no longer in use and freeing up the associated memory.
- **Memory-Mapped Files**: A segment of virtual memory is assigned a direct byte-for-byte correlation with some portion of a file or file-like resource. This allows file I/O to be treated as routine memory access, simplifying the code.
- **Non-Uniform Memory Access (NUMA)**: In multi-processor systems, this approach optimizes memory access by allowing a processor to access its local memory faster than non-local memory.

#### Memory Management in Modern Operating Systems
- **Linux**: Uses a combination of paging and segmentation. Implements advanced features like the Out-of-Memory (OOM) killer.
- **Windows**: Employs a virtual memory manager that uses a demand paging system with a modified page replacement algorithm.
- **MacOS**: Similar to Linux, it uses advanced features of virtual memory, demand paging, and efficient memory compression techniques.

### 2.3 File Systems

- **File System Structure**: File systems organize and store files and directories. It includes a mechanism for naming, storing, organizing, and retrieving files. Different file systems (like NTFS, ext4, FAT32) have different structures and features.
- **File Access Methods**: The OS provides several ways to access files, including sequential access, direct access, and indexed access. The choice depends on the use case and the type of data being accessed.
- **File System Management**: The OS handles the creation, deletion, allocation, and management of space for files and directories. This also includes managing permissions and attributes of files.

### 2.4 I/O Systems and Device Management

- **I/O System Management**: The OS manages I/O devices and operations, abstracting the complexity of hardware devices and providing a standardized interface for software applications.
- **Device Drivers**: Device drivers are specific software modules that allow the OS to communicate with hardware devices. They act as a translator between the hardware and the OS.

---


## 3 : Concurrency and Synchronization


### 3.1 Concurrency in Operating Systems

#### Understanding Concurrency
- **Definition**: Concurrency in an operating system allows multiple processes or threads to be executed in overlapping time periods. It's not necessarily simultaneous execution, but rather interleaved.
- **Importance in Modern Systems**: With multi-core processors becoming the norm, effective concurrency is essential for harnessing the full power of the hardware.

#### Challenges of Concurrency
- **Race Conditions**: When multiple threads try to access and modify shared data concurrently, the final outcome depends on the order of access, leading to unpredictable results.
- **Deadlocks**: Situations where two or more threads are unable to proceed because each is waiting for the other to release resources.
- **Starvation**: A situation where a thread is perpetually denied the necessary resources to process its work due to scheduling algorithms favoring other threads.

### 3.2 Synchronization Mechanisms

#### Critical Section Problem
- **Concept**: A critical section is a part of the code where shared resources are accessed. Ensuring that only one process or thread accesses the critical section at a time is crucial for data integrity.

#### Mutexes and Semaphores
- **Mutexes**: A mutex (mutual exclusion object) is a synchronization tool used to prevent multiple threads from accessing the critical section simultaneously. It's a locking mechanism: a thread must acquire the lock before entering a critical section and release the lock upon exiting.
- **Semaphores**: A semaphore is a more general synchronization tool that can be used to control access to a resource pool. It uses a counter to control access: a semaphore count greater than zero indicates the number of available resources, while a count of zero means no available resources.

#### Monitors and Condition Variables
- **Monitors**: Monitors are high-level abstractions that encapsulate both the data and the procedures that operate on the data. They automatically provide mutual exclusion and condition synchronization (using condition variables).
- **Condition Variables**: Used within monitors, they allow threads to wait for certain conditions within the monitor to be true.

#### Deadlock Detection and Prevention
- **Deadlock Prevention**: Involves designing a system in such a way that the possibility of deadlock is excluded. Techniques include ensuring that at least one of the necessary conditions for deadlock cannot hold.
- **Deadlock Avoidance**: Unlike prevention, where the focus is on structuring the system to exclude deadlocks, avoidance allows more flexibility. It involves making dynamic checks before resource allocation to ensure that the system remains in a safe state.

### 3.3 Inter-Process Communication (IPC)

#### Pipes
- **Unidirectional Pipes**: Allow one-way communication between processes. Data written by one process can be read by another.
- **Bidirectional Pipes**: Enable two-way communication, allowing processes to read and write data in both directions.

#### Message Queues
- **Concept**: Message queues are a form of IPC that allow messages to be exchanged between processes. They are particularly useful for asynchronous communication.
- **Usage**: Processes can enqueue messages onto a queue and dequeue them later. This decouples the sender and receiver processes.

#### Shared Memory
- **Mechanism**: A segment of memory is designated as shared, and multiple processes can read and write to this segment. It's one of the fastest forms of IPC since data doesn't need to be copied between the client and the server.
- **Synchronization**: Access to shared memory must be synchronized (using mutexes or semaphores) to prevent race conditions.

#### Remote Procedure Calls (RPCs)
- **Functionality**: Allow a program to call procedures in another address space (commonly on another computer on a network) as if they were local calls.
- **Process**: The calling process sends a request to the remote system to execute a designated procedure with supplied arguments, and the result is returned to the caller.

### 3.4 Multithreading

#### Benefits of Multithreading
- **Responsiveness**: Multithreading can allow an application to remain responsive to user input while performing other tasks in the background.
- **Resource Sharing**: Threads share the resources of their parent process, leading to efficient resource utilization.
- **Scalability**: Multithreaded applications can take advantage of multi-core architectures for parallel processing and improved performance.

#### Thread Synchronization
- **Importance**: Necessary to ensure that shared resources are not accessed simultaneously by multiple threads, which can lead to data inconsistency.
- **Mechanisms**: Similar to process synchronization but involves synchronization within the same process, like using mutexes and semaphores.

#### Thread Libraries and Models
- **POSIX Threads (Pthreads)**: A standard threading library in Unix-like systems, providing API for creating and managing threads.
- **Windows Threads**: The native threading library in Windows environments.
- **Java Threads**: In Java, threads are managed by the Java Virtual Machine (JVM), not the underlying operating system.
- **Threading Models**: Understanding the one-to-one (each user-level thread maps to a kernel thread), many-to-one (many user-level threads map to one kernel thread), and many-to-many (many user-level threads map to an equal or smaller number of kernel threads) models.

### 3.5 Scheduling and Deadlock

#### CPU Scheduling Algorithms
- **Round-Robin**: Each process gets a small unit of CPU time (time quantum), after which it is moved to the end of a ready queue.
- **Priority Scheduling**: Processes are scheduled according to their priority. Higher priority processes are executed before lower priority ones.
- **Multilevel Queue Scheduling**: This involves multiple ready queues, each with a different priority. Processes are permanently assigned to a queue based on their priority or other criteria.

#### Deadlock Handling
- **Deadlock Avoidance**: The system dynamically examines the resource-allocation state to ensure that a circular wait condition can never exist.
- **Deadlock Detection and Recovery**: Involves detecting deadlocks and then taking action (like terminating a process or rolling back to a safe state) to resolve them.

### 3.6 Advanced Topics in Concurrency

#### Real-Time Scheduling
- **Considerations**: Real-time operating systems (RTOS) have strict requirements for timing and reliability. Scheduling in such systems often needs to be deterministic.
- **Types of Real-Time Systems**: Hard real-time systems, where missing a deadline is a system failure, and soft real-time systems, where meeting deadlines is important but not critical.

#### Lock-Free and Wait-Free Algorithms
- **Definition**: Lock-free programming provides a form of concurrency that doesn't use traditional locking mechanisms. Wait-free implies that every thread will continue to make progress in a finite number of steps.
- **Advantages**: Can reduce overhead and improve performance, especially in high-concurrency scenarios.


---

## 4 : I/O Systems and Device Management

### 4.1 Overview of I/O Systems
- **Purpose and Functionality**: I/O systems in an operating system manage the way data and commands are exchanged between the computer and external devices like hard drives, printers, and keyboards. These systems abstract the details of the hardware devices and provide a standardized interface for the rest of the system.
- **Components**: Typically include I/O ports, buses, controllers, and the actual I/O devices. The OS interacts with these components through drivers.

### 4.2 I/O Hardware
- **I/O Ports**: Interface points used for connecting external devices to the computer. They can be serial (transferring data one bit at a time) or parallel (multiple bits simultaneously).
- **Buses**: Physical electrical pathways that carry data within the computer and to external devices. Examples include USB, SATA, and PCI.
- **Controllers and Interfaces**: Specialized hardware that controls the data exchange between the main memory and the I/O device. They interpret the device-specific protocols and present a uniform interface to the device.

### 4.3 I/O Software
- **Goals of I/O Software**: Ease of use, efficiency, ability to share devices, and device independence.
- **Device Drivers**: Software modules that directly interact with the hardware. They encapsulate hardware-specific behavior and present a uniform interface to the OS.
- **Device-Independent I/O Software**: Provides a high-level interface to the I/O devices, abstracting away the details of the specific hardware.
- **Interrupt Handlers**: Part of the I/O software that handles interrupts generated by I/O devices. They play a crucial role in the responsiveness of the system to I/O requests.

### 4.4 I/O Techniques
- **Programmed I/O**: The CPU is responsible for managing all I/O operations. While straightforward, it can be inefficient as it involves busy waiting.
- **Interrupt-Driven I/O**: When the device is ready for I/O, it generates an interrupt that temporarily halts the CPU operations and allows the I/O operation to proceed.
- **Direct Memory Access (DMA)**: A technique where an I/O device can directly read from or write to the system memory without the continuous involvement of the CPU, improving I/O performance.

### 4.5 Buffering
- **Purpose**: Buffering is used to accommodate the speed difference between the CPU and I/O devices. It involves storing data temporarily in a buffer (a memory area) while it is being transferred between two locations.
- **Types of Buffering**:
    - **Single Buffering**: Using one buffer to hold data for a single I/O operation.
    - **Double Buffering**: Using two buffers so the CPU can process one buffer while the other is being filled or emptied.
    - **Circular Buffering**: A more advanced form, where multiple buffers are used in a circular manner to continuously stream data.

### 4.6 Virtual I/O Devices
- **Concept**: Virtual I/O devices are not physical devices but software emulations of physical devices. They allow applications to interact with them as though they are real devices.
- **Usage**: Common examples include virtual drives, virtual network interfaces, and virtual printers.

### 4.7 Security and I/O
- **Access Control**: Ensuring that only authorized processes or users can access certain devices.
- **Audit Trails**: Keeping logs of device access can be crucial for security, especially in environments with sensitive data.

---

## 5 : Case Studies and Practical Exploration

### 5.1 Linux/Unix
- **Linux Kernel Architecture**:
  - **Monolithic Kernel**: Linux's kernel is monolithic, meaning most of its functionality (like device drivers, file system management, network stack) is directly included in the kernel space. However, its ability to load modules dynamically allows it to extend or reduce its capabilities at runtime.
  - **Process Management**: Linux implements efficient process management through techniques like Copy-On-Write (COW) during process creation (`fork`). The Completely Fair Scheduler (CFS) is used for CPU scheduling, ensuring fair distribution of CPU time.
  - **File System**: The ext4 file system, a successor to ext3, offers robust journaling features which ensure filesystem integrity in the event of unexpected shutdowns. It supports large file sizes and has efficient allocation algorithms.


### 5.2 Windows

- **Windows Architecture**:
  - **Hybrid Kernel**: Windows NT uses a hybrid kernel design. It runs some services in kernel mode for performance while keeping others in user mode for better security and stability.
  - **Win32 API**: This API layer is crucial for application development in Windows, providing necessary interfaces for system resources, window management, and graphics.
  - **File System**: NTFS, the primary file system used by Windows, offers features like metadata journaling, disk quotas, and file-level encryption. It supports large volumes and has built-in mechanisms for data recovery.


### 5.3 MacOS  

- **MacOS Architecture**:
  - **XNU Kernel**: The XNU kernel combines elements from the Mach microkernel (handling low-level functions like process and memory management) and components from FreeBSD (like the networking stack and file system).
  - **Application Ecosystem**: MacOS is tightly integrated with Apple’s ecosystem. Applications are predominantly developed in Swift and Objective-C, offering seamless integration with MacOS features and an optimized user experience.
  - **File System**: Apple File System (APFS) is optimized for SSDs and offers strong encryption, space sharing, and snapshots for data recovery and system versioning.

### 5.4 Android

- **Core Architecture**:
  - **Linux Kernel**: Android OS is built on a modified Linux kernel, adding components for mobile device functionalities like touchscreens and cellular radios.
  - **Runtime Environment**: Uses Android Runtime (ART) with ahead-of-time (AOT) compilation for performance optimization.
  - **Application Framework**: Developers use Java or Kotlin to build applications that run within the Android application framework.
