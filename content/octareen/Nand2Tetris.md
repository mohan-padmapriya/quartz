## To-Do
1. Verilog or VHDL
2. What is modularity and abstraction?

# Week 1
A bunch of gates
 - Implementing your chipset

## Perspectives
1. Why NAND gates?
	- Pretty easy, cost effective. But could use NOR, AND, etc.
2. How would you build a NAND gate?
	- Using NMOS (transistors) etc. A bunch of ways to build them, but delves into transistors, and other electronic devices.
3. How does one go about designing complex chips containing hundreds of parts and connections?
	- Silicon compilers, etc. But basically, You break a complex problem into simpler parts, and the simpler parts are simpler to optimize and to construct. And at the end of the day, after you use all your tools, after you use all your techniques, you go back and use this modularity at the idea.

 # Week 2
 Go from these basic gates to a family of adders, subtractors, and then the ALU.
 
 ## Negative binary numbers
 How can we go about representing?
 [A suggestion](n2t1.png)
 - But not good enough
 Therefore, use 2's complement to represent it
  
### Represent negative number *-x* using positive number $2^n - x$
![](n2t2.png)
 
**Why does this work?**
This rep is modulo $2^n $, and even addition is modulo $2^n$ too

**Some more (formal) clarity**
![](n2t3.png)
Essentially, this is why we get 2's complement of a number if we flip digits and add one

> Figure out how to arrive at 2's complement of a number

***How is 1 added to a binary number?*** (When you dont want to build a full on adder circuit)
- Flip the bits of the number from right to left, stopping the first time 0 is flipped to 1

### Von Neumann Architecture
![](von_neumann.png)
![](alu1.png)

#### The Hack ALU
- You could build your ALU to provide any variety of functions that it can compute.
- If you miss out providing certain functionality in hardware, you can always provide for it using software
![](alu2.png)

***How does it actually work?***
- Depends on the specification table
![](alu3.png)

> How is this spec table and ALU designed/ interfaced? How does one come up with these?

- Hack's control bits:
![](alu4.png)

## Perspectives
1. Adder we've designed is not very efficient. Therefore carry look ahead
2. Unit testing and (local failures) - why is it important?

# Week 3
Combinational to Sequential logic
![](n2t5.png)
![](n2t6.png)

### Flip Flops
![](ff1.png)
![](dff.png)
- The little triangle reps that it's sequential

![](dff2.png)

So now, we've got D flip flops and NAND gates 
### 1. 1 Bit Register
> What is a register? How is it different from a flip flops?

![](bitr1.png)


Implementation:
![](bitr2.png)
- A MUX with inputs input and output (of DFF), select line as load, and the output of the MUX to a DFF

Put several of these registers together and you have a multibit register

### RAM
And putting several of these multibit registers together, we've got a RAM unit
![](ram1.png)

At any given moment in time, only 1 register is interesting, others not relevant. In order to recognise that one relevant register, we've got the *address*

***Read a register in RAM***
![](ram2.png)
***Write a register in RAM***
![](ram3.png)

***Why Random Access Memory?***
- Because irrespective of the size of RAM (no. of registers), chips can be accessed in the same access time, instantaneously (How?)

### Counter
![](count1.png)

The PC has 3 control bits: Load, Reset, Increment

# Week 4
*Universality* --> Universal Turing Machine
Von Neumann architechture brings UTM to life. 3 important aspects:
1. Specifying instructions - How?
2. How do we know which instruction to do when?
3. Addresssing - Where?

Machine language and assembly language
[Machine Language](ml.png)

> Why is accessing memory expensive?

![](mem.png)

#### Addressing Modes
![](address.png)

> How are i/o devices *connected* to the device? (With regard to registers)

#### Flow control
- Loops 
- Conditional jumps

### Hack hardware and software
![](hh.png)
![](hs.png)

### Instructions
#### A for addressing
![](a.png)

#### C for addressing
![](c.png)