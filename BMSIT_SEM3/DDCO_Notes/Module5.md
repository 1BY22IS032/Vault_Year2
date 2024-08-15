<!--markdownlint-disable MD033-->
# Basic Processing Unit

To execute a operation, the following steps take place

- Fetch the contents pointed by the PC, the instruciton is loaded into the IR

        IR [[PC]]

- Increment the PC by 4
    PC + 4

- Execute the instruction

First two steps are called **Fetch Phase** and the final step is the **Execution Phase**.

Steps taken by the processor:

- Read given memory location and load it into a register
- Read registers
- Perform Arithmetic or Logical operation and write the result to a register
- load register content into memory location

The below image indicates the components required to perform the actions

![HardwareComponents](https://cdn.imgchest.com/files/84jdc9bo6g4.png)

## Single Bus Organisation

- ALU and all the registers are connected via a single bus
- The *external* memory bus and the processor bus are connected via the MAR and MDR
- The MDR has 2 inputs and 2 outputs
- The MAR's input is connected to the internal bus and the output to the external bus(cuz its job is just to transfer the address for MDR)
- Instruction Decoder and Control unit is responsible for control signals to all the registers and impmlementing the actions specified by the instruction
- R<sub>0</sub> to R<sub>n-1</sub> are called Processor registers, these can be used by the developer for use.
- Y,Z & Temp are the 3 registers that are reserved only for the processor. Developer can't access these registers

- In the ALU, A is the output of the Multiplexer
- B is directly obtained from the Processor bus
- the mux selects either output of Y register or a constant value of 4 which is used to increment PC

![Single Bus Organisation](https://cdn.imgchest.com/files/my8xc8pbrd4.png)

## Register Transfers

- Each register has 2 signals called **Gating Signals** , R<sub>i<sub>in</sub></sub> and R<sub>i<sub>out</sub></sub>
- R<sub>i<sub>in</sub></sub> = 1 --> Memory is loaded into register by bus
- R<sub>i<sub>out</sub></sub> = 1 --> Memory is loaded from register onto bus

Example

- Move R1,R2
- R<sub>1<sub>out</sub></sub> = 1
- R<sub>2<sub>in</sub></sub> = 1
- All operations happen around the cycles of the processor clock
  
## Performing An Arithmetic Or Logical Operation

- The ALU performs arithmetic operations on 2 operands on its A and B inputs
- One of the operands is the output of MUX and the other is dircectly from the bus
- the result is stored temporarily in register Z
- The sequence of the Operation is as follows
  - R1<sub>out</sub>, Y<sub>in</sub>
  - R2<sub>out</sub>, SELECT Y ,Add ,Z<sub>in</sub>
  - Z<sub>out</sub>, R3<sub>in</sub>
- Here contents of R2 and Y are input into the ALU and the output is stored in the register Z

## Control Signal of the MDR

- The MDR register has 4 control signals
  - MDR<sub>in</sub> MDR<sub>out</sub> are connected to the internal processer bus
  - MDR<sub>inE</sub> MDR<sub>outE</sub> are connected to the external memory bus
- The MAR register has 2 control signals
  - MAR<sub>in</sub> controls the input from the internal processor bus
  - MAR<sub>out</sub> controls the output to the external memory bus

![MDR](https://cdn.imgchest.com/files/84jdc9b5684.png)

## Fetching a word from memory

- To fetch an instruction from mem, proc transfers required address to MAR and simultaneously issues a read signal on control lines of the memory bus

- When the signal is received, the data is then transferred over to the MDR. The data is then passed on via the MDR to the processor registers

- There might be a variance in the response time of the MDR and hence we use MFC(Memory Function Completed)

- MFC is a signal that is released by the memory to indicate the completion of a data transfer

Example:

    Move R1,R2
    The specifics are:
    - R1out ,MARin, Read // add is loaded into the MAR and read is issued.
    - MDRinE ,WMFC // Call in MDR in from external at specific add and wait for MFC to come
    - MDRout,R2in load R2 from MDR





## Execution of a complete Instruction

- Add R3,R1
- The actions required
  - Fetch the Instruction
  - Fetch the first operand
  - perform the addition with the operand stored in second register
  - store in second register

