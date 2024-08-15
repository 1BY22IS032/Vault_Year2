<!-- markdownlint-disable MD033-->
<!--markdownlint-disable MD025-->
# Basic Structure Of Computers

## Introduction

### Functional Units

**5 main parts** in a computer

- Input
- Memory
- Arithmetic Logical Unit **ALU**
- Output
- Control Units

![BasicFunctionUnits](https://cdn.imgchest.com/files/6yxkcooodw7.png)

### Input

- Comps accept info through coded units
- most common device is keyboard
- Kepress leads to the respective key being translated into binaray code and sent to the processor

### Memory unit

- stores programs and data
- Two types primary and secondary
  - Primary: main memory, very fast memory operating at electronic speeds
  - Secondary: Less expensive, permanent memory, able to store large amounts of data

### Output Unit

- Counterpart of InputUnit
- Sends Processed results to the outer world.
- ex: printer

### Control unit

- Mem,AL,IO units store and process info.
- Control units coordinate the passage of data and the operations

## Basic Operational Concepts

Ok so this is how it basically works

`ADD LOCa, R0`

1. Fetch the instruction from the main memory into the processor
2. Fetch the operand from the specified location and load it.
3. Add the memory operand to the operand present at the memory register R0
4. Store the result in R0

This can be simplified as

`Load LOCa,R1`

`Add R1,R0`

1. Here we load the value of operand at a into R1
2. We then add the value of R1 to R0
3. Store the result in R0

## Main parts of the processor

Some information:

- The processor contains ALU, control circuitry, and many registers.
- has n registers from R<sub>0</sub> to R<sub>n-1</sub>
- The *IR* or Instruction Register holds current instruction
- *Control unit* generate timing signals to sync the system to
- Program Counter contains the memory address of the next instruction
- MAR (*Memory Address Register*) stores the address in main mem of where the processor wants to dump info
- MDR (*Memory Data Register*) stores the data temporarily to dump into the address pointed by the MAR

### Steps to Execute a function

1. Address of instruction to be executed is loaded into PC
2. PC sends signal to MAR. MDR stores the instruction at add of MAR
3. MDR returns instruction to IR, instruction is decoded and executed
4. To fetch an operand, its add is stored in MAR, MDR stores value at MAR
5. Data is passed to ALU
6. ALU does the computation
7. Result is stored in MDR, MAR is given the address to store
8. MDR stores the value at specified location and write cycle is initiated
9. at some point PC increments to the next instruction

## Bus Structure

- Grp of lines that serve as a connecting path
- may be lines or wires
- carry data, signals or addresses
- Two types of bus structure 1. Single bus structure 2. Multiple Bus structure
  
Single Bus structure:

- only 2 units can activly use the bus at one point in time
- Only one transfer at a time
- Advantages
  - Low cast
  - Flexibility for attaching peripheral devices

Multiple Bus structure:

- Contain multiple buses & achieve more concurrency in operations
- Two or more transfer can be carried out at the same time
- Advantages: Better Performance
- Disadvantages: Increased Cost

Buffer Registers

- are included with the devices to hold the information during transfers
- prevernt high speed processor from being locked to a slow io device during data transfers

## Performance

- At the start of execution, all program instructions are stored in the main-memory
- As instructions are loaded into the processor, a copy is placed into the cache
- if the instruction needs to be loaded again, it can be retrieved from the cache

### Processor clock

- The processor divides the action to be performed into a sequence of basic steps
- Each step should take one clock cycle

- Clock Rate (R) = 1 / clock length(P)
- R is measured in cycles per second
- Cycles per second = Hz (Hertz)

- program execution time
    T = Time required by processor
    N = No of instruction execution
    S = avg no of steps for one instruction
    R = Clock Rate

### Performance Measurement

- SPEC (*System Performance Evaluation Corporation*) selects and publishes the standard programs along with their test results

- SPEC rating
      SPEC = Running time on reference comp/ Running time on Comp under test

# Machine Instructions and Programs

- Memory consists of cells
- Each cell can hold n bits
- Group of 8 bits is called a byte
- A group of n bits is called a **word**

Accessing the memeory to store or retrive a single item of information requrires distinct addresses for each item at each location.

- If 2<sup>k</sup> = no of addressable locations, the 2<sup>k</sup> constitute the addresss-space of the computer

![Words](https://cdn.imgchest.com/files/wye3c3br2m4.png)

Note : If the word length is 32, successive words are located at address 0,4,8.. with each word having 4 bytes

## Big Endian and Little Endian

Big Endian : Lower Bytes are used for the more significant bytes of the word

Little Endian: Lower Bytes are used for the less significant bytes of the word

![Big and Little Endian](https://cdn.imgchest.com/files/j7mmc85ood7.png)

### Word Alignment

- Words are said to be **Aligned* in memory if they begin at a byte address that is a multiple of the no of bytes in the word
- if word length = 16, (2 bytes (16/8)); The byte address should start with (0,2,4,6,8..)
- if word length = 64, (8 bytes (64/8)); The byte address should start with (0,8,16,24..)

A number usually occupies one word. It can be accessed in the memory by specifying its wordaddress.
similarly indivisual characters can be accessed by thier byte address

We can calculate the length of a string by:

- using a control char to indicate end of string
- seperate memeory word location or register containing the length of the string in bytes

## Memory Operations

The Two memory operations are

- Load (Read/Fetch)
- Store (Write)

Load : stores a copy of data at a perticular location into the processor

Steps to load:

1. processor sends the addresss of the location to the memory.
2. The memory issues a *read* signal to that loads a copy of the data.
3. The memory reads that data and then sends it to the processor.

Store: Transfers info from the registers to the specified memory location

Steps to store / write info:

1. Processor sends the address of where the data is supposed to be stored through the MAR
2. The Data is sent by the processor through the MDR
3. The memory reads the MAR and then issues a write signal to store the contents of the MDR in the address

### Register Transfer Notation

![RTN](https://cdn.imgchest.com/files/my2pcr62xe7.png)

## Instruction Execution and Straight Line Sequencing

- Initially the address of the first instaruciton is loaded onto the PC
- Then the processor control circuits use the information in the PC to fetch and execute the instrucitons one at a time in order of increasing addresses. This is calle dstraight line sequencing
- During  the execution of each instruction, the *program counter* is incremented by 4 to point to the next instruction.

![Program Exp](https://cdn.imgchest.com/files/pyq9cn6zz94.png)

## Addressing Modes

![Addressing Modes](https://cdn.imgchest.com/files/e4gdcrn2994.png)

**Variable** : is represented by allocation a memeory location to hold its value, thus athe value can be changed as needed using appropriate instructions

There are two methods or modes of accessing the variables:

1. Register Mode
2. Absolute Mode

Register Mode:

- The operand is the contents of a register
- the name of the reg is given in the instruction
- Reg are used as temp storage
- Eg: *Move R1,R2* which copies the content of R1 into R2

Absolute(Direct) Mode:

- The operand is in a memory location
- The absolute mode can represent global variables in the program
- Eg *Move LOC,R2* which coopies the content of LOC to R2

Immediate Mode:

- The operand is explicitly mentioned in the instruction
- eg *Move #200,R0* which sets the value of 200 to R0

## Inderection and Pointers

- Instructino does not give the operand or its address explicitly
- Rather, it provides the info from which the new address of the operand can be determined
- This address is called *Effective Address* of the operand

Indirect Mode:

- The EA is the contents of a reg or LOC
- The reg or LOC that holds EA is called a pointer
- We denote the indirection by name or new address
- Eg *Add(R1),R0* The operand is in memory, R1 gives an EA, B. Data is read from b and added to contents of R0

![Indirect Mode](https://cdn.imgchest.com/files/p7bwcob93l7.png)

## Indexing and Arrays

Index Mode:

- Indicated by X(R<sub>i</sub>)
- X is the constant value that defines an offset
- EA of the operand is given by EA = X + R<sub>i</sub>
