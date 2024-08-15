# Notes

**Multi-programming** increases CPU utilization by organizing jobs (code and data) so that the CPU always has one to execute.

>*No time left unused; assume, one task start; needs to wait; in MP, other task to job; first task wait and then finish after second task stop*

**Time sharing** (or multitasking) is a logical extension of multiprogramming.
In time-sharing systems, the CPU executes multiple jobs by switching among them, but the switching occur so frequently that the users can interact with each program while it is running.

Requires **Interactive** or (hands on) comp sys that provides direct comms btw user and system.
*Response time should be short*

## Key Terms

 1. **Job Scheduling** = many jobs;not enough resource; process of managing all of them
 2. Having several programs in memory at the same time requries some form of **Memory management**
 3. **CPU Scheduling** = Job Scheduling but for CPU jobs
 4. **Swapping** = during process;jobs are swapped;from and to **main memory** and **disk**
 5. **Virtual Memory** = same result as swapping; allows running of program not completely in memory; allows users to run programs larger than physical memory;abstracts main mem block into array of smaller storage;sepearates logical from physcial mem as obs by user; helps dev concerns.

# Linux Terminal
![.\linku.jpg](https://cdn.imgchest.com/files/6yxkcojpjm7.png)

# Types of os???

1. Interrupt driven:
   1. HDware by one of the devices
   2. Software errors; infini loops, errors, waiting on os instructions etc
   3. called *exception* or *trap*

2. Dual Mode Operation
   1. Has 2 modes ; User - Kernel
   2. Additional bit is added to sys to indicate between them; called **MODE bit**
   3. Some instructions are set as privleged and can only be run under Kernel mode
   4. Increases Security
   5. Sys call turns it to Kernel and return call sets it to user

## Dual Mode Operation

### Transition from User to Kernel mode OS

* Process executing, makes system call;
* control shifts to kernel; sets MODE bit 0;
* makes system call when timer hits 0; system call returns MODE bit to 1;
* Control returns to UserProcess;
  
* Assume there is a program
* Program is stuck in loop/taking a lot of resources
* Set timer to kill the program  
* Timer set by internal physical clock
* When timer hit 0; pass control to kernel which kills program; pass control back to User

## Process Management

A process is a program in execution. It is a unit of work within the system. **Program** is a passive
entity, **process** is an active entity.

### Process Management Activities

* Creating and deleting both user and system processes
* Suspending and resuming processes
* Providing mechanisms for process synchronization
* Providing mechanisms for process communication
* Providing mechanisms for deadlock handling

## Memory Management

* To execute a program all of the data of the program must be in the memory
* MM determines what is in the memory and when.

### Memory Management Activities

* Track of memory parts being used and by whom.
* Decidding which processes and data to move in and out of memory.
* Allocating/ Deallocating space to program/process

## Storage Management

### File-Sys Mgmt

* files are organized into directories.
* Access is clearly specified to users and system

### OS Activities Include

* Creating and Deleting files
* Primititves to maniputlate files and directories
* These primitives are usually provided as functions or methods in programming languages or as system calls in operating systems

## Mass Storage Management

* Disks used to store long term useable data
* Mgmt of disks is of critical importance
* Speed relies on efficiency of Disk subsystem

### OS Activities in MSM

* Free-Space Management
* Storage Allocation
* Disk Scheduling

## Performance of various levels of Storage

![Performance](https://cdn.imgchest.com/files/84apcod9dl4.png)

---
>When multiple process share a resource among themselves, on the event that it changes, all the processes must have the most uptodate value of that resource.  

>In cpus with multiple cores,multiple levels of cache exist. This shared memory must be cohearent to all the parties. that means the cache must be cohearent.

>In distributed sys, same copies of data might exist over different nodes or machines in a system. all of these must be kept in check

## IO SUBSYSTEM

Uses:

* Mem management of IO
* Buffering : storing data temporarily while it is being transferred
* Caching : Storing parts of data for higher performance
* Spooling : the overlapping of output of one job with the input of other jobs

## Protection and Security

Protection:

* Control over processes and resources
  
Security:

* Defense against internal and external attacks
* DDOS, Worms, Viruses etc

Systems generally first distinguish among users to determine who can do what.

* User Identities = uids include name and associated number, distinct to one user
* Group Identities = GIDs include group of people, settings distinct to a group

* Privilage Escalation = allows user to gain higher authority by securing an effective ID.

---

# System Calls

>System calls are the interface between a user-level process and the operating system (OS) kernel. They provide a way for applications to request services from the operating system such as creating or terminating processes, reading or writing files, allocating memory, communicating with devices, and more.

User wants to perform function that interacts with system level resources; 
User requires OS level perms;
User application sends system call;
Control is passed over to OS and action is performed;
Control is passed back;

System calls are typically provided by libraries such as C library and Windows API

Examples are read(),write(),fork(),exec()and malloc() etcf

## Types of System Calls

1. Process Control - end,abort; load,execute
2. File Management - create file,delete file; open,close
3. Device Management - request device,release device; read,write,reposition
4. Information maintenance - get time or date, set time or date; get system data, set system data
5. Communications - create ,delete communication network ; send,receive messages

### Example of System call in action

![handling of write](https://cdn.imgchest.com/files/6yxkcojzq97.png)

1. Printf line is read by the compiler
2. control is at user mode, Compiler access the C library
3. C library takes control over to the kernel mode and accesses os level resources such as write().
   That process, is called a system call
4. Control is handed back to the user mode as the value is returned by write()(null in our case).

System programs are a type of software that directly interacts with the operating system 

Categories of System Programs:

1. File management programs - used to create, delete and modify files. Ex: ls, cp , mv and rm subroutines that are file management programs
2. Status information: date, time and other system resource status finder 
3. Programming language support: compilers etc
4. Communications : These programs provide the mechanism for creating virtual connections among processes, users, and computer systems

# OS Structure 

A common approach is to partition the task into small components rather than have one monolithic system. Each of these modules should be a well-defined portion of the system, with carefully
defined inputs, outputs, and functions.

## Simple Structure

* MSDOS wasn't designed with capability in mind.
* It was written to proivde most functionality in the least space
* the interfaces and the levels of functionality are not waell separated.
* More vulnurable to malicious programs
* Due to lack of hardware they were forced to keep base hardware accessable.

## Layered Approach

* OS is divided into number of layers(or levels)
* Bottom layer is the hardware and the highest layer (Layer N), is the user interface
* Main adv: simplicity of construction and debugging.
* Layer are selected so that each users functions or operations and services of only lower level layers
* Data abstraction can be found as higher layers do not need the existance of certain ds ops and hardware.
* But Careful planning is Necessary 


## Microkernels

* **Definition**: Microkernels are a design approach for operating systems where the kernel is kept as small as possible, with minimal functionality implemented as part of the kernel itself.

* **Key Principles**:
  1. **Minimization of Kernel Functionality**: Kernel provides only essential services like memory management and process scheduling.
  2. **Isolation of Components**: Device drivers, file systems, etc., run as separate user-space processes for stability and security.
  3. **Message Passing**: Communication between components and the kernel occurs through message passing mechanisms.
  4. **Flexibility and Extensibility**: New features and services can be added or removed without modifying the kernel itself.
  5. **Fault Isolation and Modularity**: Individual components running in user space enable better fault isolation and modularity.

Microkernels have advantages in terms of flexibility, security, and fault isolation, but they also come with performance considerations that need to be carefully managed.

