<!--markdownlint-disable MD033-->
<!--markdownlint-disable MD001-->
# Input Output Organization

## Dealing With IO Devices

1. Memory Mapped I/O
2. I/O Mapped I/O

### Memory Mapped I/O

- Memory and io devices share a common address-space
- any data transfer instruction can be used
- eg: *Move DATAIN,R0*. here *DATAIN* is the input buffer of the keyboard

### IO Mapped I/O

- Memory and I/O address spaces are different
- *IN* and *OUT* are used for data transfer
- adv: i/o deal with less address lines

I/O interface for an input device:

1. Address Decoder : allows the device to recognise its Address when its requested on address line
2. Status Register: contains info regarding status
3. Data register: holds data to be sent to processor (Two Types : DATAIN *input buffer* and DATAOUT *output buffer*)

![IO interface](https://cdn.imgchest.com/files/6yxkco2nrk7.png)

# Mechanisms Used for interfacing IO Devices

1. Program Controlled IO
   - Processor repeatedly checks status of io to check for sync btw io and proccessor
   - disadvantage: time is wasted

2. Interrupt IO
   - I/O device sends a INTR or *Interrupt Request* to the processor when ready to send information
   - Hence time is saved by processor

3. Direct Memory Access (DMA)
   - Device to memory direct data transfer without involvment from processor
   - DMA is a technique for high speed IO use
  
### Program that reads one line at a time from the keyboard, loads it to memory buffer and then relays it to the dispaly

![Program](https://cdn.imgchest.com/files/l4necnnr9x4.png)

# Interrupts

- Interrupt signal is sent by the **Interrupt-Request** Line
- **Interrupt Service Routine** or ISR is run in response to an interrupt
- Processor acknowledges the ISR and responds with a INTA **Interrupt Acknowledge**

## Example using COMPUTE and PRINT

![Print and Compute](https://cdn.imgchest.com/files/6yxkco2ng87.png)

1. I is executed
2. Interrupt Arrives as INTR
3. Contents of PC and Status is saved
4. INTA is sent to acknowledge
5. ISR points to address of Interrupt Request Instruction
6. ISR and the Instruction are executed
7. Control returns to Program1
8. PC and Status are restored from save
9. Execution Continues from i+1

Interrupt Latency is a delay between when INTR is received and start of the execution of ISR

Difference between Subroutines and ISRs

|Subroutine|ISR|
|:----------:|:---|
|executes a func requried by the program from where its called|ISR need not have anything in common with the program being executed|
|is just a linkage of 2 or more functions|is a mechanism for coordinating IO transfers|

## Interrupt Hardware

![Multiple Interrupts](https://cdn.imgchest.com/files/pyq9cn6zln4.png)

- single interrupt line may be used to serve multiple io devices
- all IR *Interrupt Request* lines are connected via switches in the io devices to the ground
- the voltage at regular time is set to V<sub>dd</sub>
- during interrupt, one of the switches closes setting IR voltage to 0
- The inverse gate returns a signal of 1 signalling INTR

## Enabling and  Disabling Interrupts

- Having multiple interrups may cause an infinite loop
- To prevent this
  - Processor should ignore interrupts until the ISR is done executing
  - Processor should automatically disable interrupts at the start of the ISR
  - Processor has a special Interrupt handling circuit INTR line
    - Circuit only responds to leading edge of signal
  
Sequence of events involded in handling an IRequest

- INTR is raised
- Proc boi alters the value of the control bits in the process status register disabling interrupts
- The INTA signal is sent and the request from the io device is closed
- The ISR is executed
- The program that was interrupted is resumed

## Handling Multiple Devices

Issues concerning handling multiple devices

1. Recognition of device that sent INTR
2. Finding the appropriate starting address of the respective ISR
3. Dealing with interrupts while another ISR is ongoing execution
4. Dealing with 2 or more simultaneous interrupts

### Vectored Interrupts

1. The device requesting an interrupt sends a code over bus
2. The code contains the starting address of the respective ISR
3. This starting address is called the **Interrupt Vector**
4. Proc boi loads IV into PC and executes respective ISR

Notes

1. When proc boi ready to receive IV, it sends out an INTA signal
2. In response, IO device shuts down INTR and sends IV via bus

### Interrupt Nesting

- Use multiple priority scheme
- Each device has its own INTR and INTA lines assiged a perticular priority level
- During Execution of ISR the processor takes the priority level of the ISR
- Proc boi only accepts interrupts of priority level greater than its own
  
Privleged Instructions

- Processor's priority is encoded in a few bits of Processor-Status word
- Those bits can be changed by Privileged Instructions
- This can be changed only in *Supervisor mode*
- Proc can be in Supervisor mode only when execuing OS subroutines

![Nesting](https://cdn.imgchest.com/files/pyq9cn6apd4.png)

### Simultaneous Requests

- Device closest to processor has priority
- INTR is common to all devices
- INTA is arranged in a daisy chain fashion

On the event that INTR is activated by multiple devices

- INTA signal is set to one which reaches device 1
- If device 1 does not have an active INTR signal, it forwards the signal to device 2
- If it has raised the signal, it blocks the INTA line and sends the interrupt code via the data bus
- After execution, the INTA line is forwarded to the second device and repeated

---

## Direct Memory Access (DMA)

- The transfer or share of memory between main memory and an external device without the use of the processor is called DMA

DMA Controller is

- a control circuit that performs DMA Transfer
- is a part of the I/O device interface
- Performs the functions that would normally be carried out by the procesor

While a DMA transfer is taking place, the processor could be executing a task

![DMA](https://cdn.imgchest.com/files/p7bwcobjre7.png)
![Typical registers](https://cdn.imgchest.com/files/l7lxc263m87.png)

DMA interface has 3 registers

- For storing starting address
- For storing word count
- For containing status and control flags

![DMA](https://cdn.imgchest.com/files/p7bwcob3ja7.png)

## Bus Arbitration

- Only one device can access the bus at a time
- That device is called the **Bus Master**
- Bus Arbitration is the process of deciding which device become the bus master and the process of transferring.

There are two ways

1. Centralized - A single designated Bus Arbiter
2. De-Centralized - All devices help in deciding bus master

Centralized

- Usually Processor is the bus master
- Processor might grant the BusMasterShip to one of the DMA controllers
- A DMA controller indicates it needs BusMasterShip by activating the BR line
- Then, processor activates BG1 signal indicating to DMA controllers to use bus when it becomes free
- If DMA controller-1 is requesting the bus,Then, DMA controller-1 blocks propagation of grant-signal to other devices. Otherwise, DMA controller-1 passes the grant downstream by asserting BG
- Current bus-master indicates to all devices that it is using bus by activating BBSY li
- Arbiter ensures that only 1 request is granted at any given time according to a priority scheme

![Centralized Arbitration](https://cdn.imgchest.com/files/w7w6cor6zmy.png)

Distributed Arbitration

- All devices participate in arbitration
- Devices have a 4 bit id
- They send out a `Start Arbitration` signal
- They release their 4 bit ids upon the 4 arbitration lines
- the interaction between the 4 arbitration lines happens
- the ID that is the highest after the interactions is selelcted as the bus arbitar

![Dist Arbitration](https://cdn.imgchest.com/files/6yxkcolnpl7.png)

# Memory System

Maximum size of memory that can be used in any computer is determined by addressing mode

![Conection of memory to the processor](https://cdn.imgchest.com/files/3yrgcaad2g4.png)

- If MemoryAddressRegister is k bits long : mem may contain upto 2<sup>k</sup> addressable locations
- if MDR is n bits long: word length is n bits

- Processor Bus:
  - Address line
  - Data line
  - Control line ( read-write,mem func completed)
- Control line is used for coordinating data transfer

The process of reading data goes as follows

1. Processor loads the address of required mem into MAR
   1. this sets the R/W line to 1
2. Memory responds with placing the data from the addressed loc to the data lines and confirms by setting MFC signal
3. Upon MFC,proc loads data from data line to MDR

Writing data goes as follows

1. Loads the address of the loc into MAR
2. Sets the R/W line to 0
3. Data is loaded from the MDR into the Data line
4. Memory receives the MDR and loads it into the address of the MAR
5. Sends MFC to confirm data transfer

![SRAMDRAm](https://cdn.imgchest.com/files/p7bwceeqr67.png)

![Cache](https://cdn.imgchest.com/files/84jdc33pd24.png)

## Mapping Functions

### Direct Mapping

- This is the simplest wway
- Main memory block (indicated as M) 0, 128,256 and so on are loaded onto cache memory block (indicated as c)
- M1,M129,M257 are loaded into C1 and so on
- Since more than one block is being stored on a C block contensions might arrive
  - to counter this the next block that is needed is overwritten

![DirectMapping](https://cdn.imgchest.com/files/345xcq2a6m7.png)

