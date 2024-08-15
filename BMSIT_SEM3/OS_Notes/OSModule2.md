# Process Management

* Process Concept - A process includes a program counter, a stack and a data seciton
* Process Scheduling
* Operation on Processes
* Cooperating Processes
* Interprocess Communication

## Process State

* New - newly created
* Running - Program is executing
* Waiting - Program is waiting for some event to occur.
* Ready - Program is ready for the processor
* terminated - program finished executing

![Process State](https://cdn.imgchest.com/files/e4gdcrvngx4.png)

### Process Control Block

PCB contains the following information:

* Process state
* Program counter
* CPU registers
* CPU scheduling info
* mem management
* Accounting info
* IO status

![PCB design](https://cdn.imgchest.com/files/pyvdcob6lzy.png)

### Context Switch

Context switch is the process of saving the registers, process counter etc of a current process and loading in the values of another process.
During this process, no useful computation is done. It is time dependent on the hardware.

### CPU Context Switch

![ProcessSwitch](https://cdn.imgchest.com/files/d7ogcn8vzmy.png)

* At first P0 is being executed
* It is stopped and its save state is saved to PCB0
* Then P1's Save state(PCB1) is loaded into memory/processor
* P1 is then executed
* P1 is unloaded and PCB0 is brought back into memory
* and P0 execution begins again.

## Process Scheduling

![Representation of Process Scheduling](https://cdn.imgchest.com/files/l7lxc2gd9p7.png)

## Scheduling Algorithms

### FCFS Scheduling
