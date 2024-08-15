<!--markdownlint-disable MD056-->
<!--markdownlint-disable MD004-->
<!--markdownlint-disable MD007-->
# Module 4

## Name two differences between logical and physical addresses

|Logical|Physical|
|---|---|
|Address generated by the CPU|An address seen by the Memory Unit|
|Compile time and load time address binding methods generate identical logical and physical addresses|
|Execution time address scheme results in differing logical and physical addresses|
|set of all logical add is generated by the program|set of all physical add corresponds to the logical addresses|
|The run time mapping from virtual to physical add is done by a device knows as the memory managemtn unit (MMU)|

## Illustrate with an example the internal and external fragmentation problem encountered in continuous memory allocation

As processes are loaded in and out of memory, the free memory is broken into small peices. this is called fragmentation

Types of Fragmentation:

- External Fragmentation
- Internal Fragmentation
  
**External Fragmenation**:

- Ext Frag is when in the main memory there is enough space for a process but it isn't contigious
- the memory is in a large count of small spaces
- the problem might be extreme where every other space could be a small free space
- We could've run more processes if this were one large space instead

Solution:

- Shuffle the memory contents so as to place all the memory together in one large block

**Internal Fragmentation**:

- This happens when the processes are actually smaller than the memory spaces
- this causes partial use of the memory and causes a lot of unused memory to be left over

## Describe the following allocation algorithms

**First Fit**:

- is the simplest algorithm
- it scans the linked list and when it finds the first big enough hole, it stops the search and fits the process in it
- this causes 2 partitions, one with the process in it and another with a hole in it

**Best fit**:

- The best fit algo tries to find out the smalles hole possible in the list that can accommodate the size requirement of the process
- once found, the memory is split into two parts where one is allocated to the process and one is a hole

**Worst Fit**:

- In this allocation technique, the process traverses the whole memory and always search for the largest hole/partition, and then the process is placed in that hole/partition. It is a slow process because it has to traverse the entire memory to search the largest hole

## System Calls

A system call is a mechanism that allows a user program to request services from the OS 's kernel.
It acts as a bridge between the user's limited capabilities and the kernel's powerful functionalities

This is how OPEN System call works

1. **UserProgram Initiates**: User begins opening a file
2. **System call trap**: The program triggers a system call instruction called OPEN. This instruction causes the program to switch from user mode to kernel mode
3. **Context Switch**: Hte cpu switches context from the user program to the kernel. this involves saving the program's state and loading the kernel's state
4. **Sys call handler**: THe os inentifies the specific system call and the kernel then locates and executes the appropriate system call handler routine
5. **Call Handling**:
   1. checks if the file exists
   2. locates file on disk
   3. hands it over to memory
   4. opens file
6. **Return To user**: The sys call handler returns a system call return val. this val could be a file discriptor or an errorcode
7. **U.P receives response**:  THe U.P regains control and receives the system call return value from the kernel . if successful , theprogram can now use the file for reading, writing or other operations

## Types of system calls

## Types of System Calls

System calls are the mechanism through which user programs (running in user mode) request services from the operating system's kernel (running in privileged kernel mode). They act as a bridge between the limited environment of a user program and the powerful functionalities of the kernel.

**1. Process Control:**

* These system calls deal with creating and managing processes. Examples include:
    * `fork`: Creates a new process (child) that is a copy of the calling process (parent).
    * `exec`: Replaces the current process with a new program.
    * `wait`: Allows a parent process to wait for the completion of a child process.
    * `exit`: Terminates the calling process.

**2. File Management:**

* These system calls handle file manipulation such as creating, reading, writing, and deleting files. Examples include:
    * `open`: Opens a file and returns a file descriptor for further operations.
    * `read`: Reads data from an open file into a buffer in memory.
    * `write`: Writes data from a buffer in memory to an open file.
    * `close`: Closes an open file and releases the associated resources.

**3. Device Management:**

* These system calls interact with various devices connected to the system. Examples include:
    * `read`: Reads data from a device (like a disk or network interface)
    * `write`: Writes data to a device.
    * `ioctl`: Performs device-specific control operations.

**4. Memory Management:**

* These system calls manage memory allocation and deallocation for user programs. Examples include:
    * `malloc`: Allocates a block of memory from the heap.
    * `free`: Releases a previously allocated memory block.

# TO BE COMPLETED 

- MultiThreading
- MultiProcessing
- MessagePassing
- Semaphores
- Deadlocks
- 