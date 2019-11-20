### 4.1 Background
---

&emsp;&emsp;This chapter is language-oriented. Therefore, we can abstract away most of the details of the underlying hardware platform, deferring its description to the next chapter. Indeed, to give a general description of machine languages, it is sufficient to focus on three main abstractions only: a processor, a memory, and a set of registers.



#### 4.1.1 Machines

&emsp;&emsp;A <em>machine language </em>can be viewed as an agreed-upon formalism, designed to manipulate a memory using a processor and a set of registers.

&emsp;&emsp;**Memory** The term <em>memory</em> refers loosely to the collection of hardware devices that store data and instructions in a computer. From the programmer’s standpoint, all memories have the same structure: A continuous array of cells of some fixed width, also called words or locations, each having a unique address. Hence, an individual word (representing either a data item or an instruction) is specified by supplying its address. In what follows we will refer to such individual words using the equivalent notation Memory[address], RAM[address], or M[address] for brevity.

&emsp;&emsp;**Processor** The processor, normally called Central Processing Unit or CPU, is a device capable of performing a fixed set of elementary operations. These typically include arithmetic and logic operations, memory access operations, and control (also called branching) operations. The operands of these operations are binary values that come from registers and selected memory locations. Likewise, the results of the operations (the processor’s output) can be stored either in registers or in selected memory locations.

&emsp;&emsp;**Registers** Memory access is a relatively slow operation, requiring long instruction formats (an address may require 32 bits). For this reason, most processors are equipped with several registers, each capable of holding a single value. Located in the processor’s immediate proximity, the registers serve as a high- speed local memory, allowing the processor to manipulate data and instructions quickly. This setting enables the programmer to minimize the use of memory access commands, thus speeding up the program’s execution.



#### 4.1.2 Languages

&emsp;&emsp;A machine language program is a series of coded instructions. For example, a typical instruction in a 16- bit computer may be 1010001100011001. In order to figure out what this instruction means, we have to know the rules of the game, namely, the instruction set of the underlying hardware platform. For example, the language may be such that each instruction consists of four 4-bit fields: The left-most field codes a CPU operation, and the remaining three fields represent the operation’s operands. Thus the previous command may code the operation set R3 to R1 + R9, depending of course on the hardware specification and the machine language syntax.

&emsp;&emsp;Since binary codes are rather cryptic, machine languages are normally specified using both binary codes and symbolic mnemonics (a mnemonic is a symbolic label whose name hints at what it stands for— in our case hardware elements and binary operations). For example, the language designer can decide that the operation code 1010 will be represented by the mnemonic add and that the registers of the machine will be symbolically referred to using the symbols R0, R1, R2, and so forth. Using these conventions, one can specify machine language instructions either directly, as 1010001100011001, or symbolically, as, say, ADD R3,R1,R9.

&emsp;&emsp;Taking this symbolic abstraction one step further, we can allow ourselves not only to read symbolic notation, but to actually write programs using symbolic commands rather than binary instructions. Next, we can use a text processing program to parse the symbolic commands into their underlying fields (mnemonics and operands), translate each field into its equivalent binary representation, and assemble the resulting codes into binary machine instructions. The symbolic notation is called assembly language, or simply assembly, and the program that translates from assembly to binary is called assembler.

&emsp;&emsp;Since different computers vary in terms of CPU operations, number and type of registers, and assembly syntax rules, there is a Tower of Babel of machine languages, each with its own obscure syntax. Yet irrespective of this variety, all machine languages support similar sets of generic commands, which we now describe.



#### 4.1.3 Commands

&emsp;&emsp;**Arithmetic and Logic Operations** Every computer is required to perform basic arithmetic operations like addition and subtraction as well as basic Boolean operations like bit-wise negation, bit shifting, and so forth. Here are some examples, written in typical machine language syntax:

```
  ADD RR2,R1,R3    // R2<-R1+R3 where R1, R2, R3 are Registers
  ADD RR2,R1,foo   // R2<-R1+foo where foo stands for the
                   // value of the memory location pointed
                   // at by the user-defined label foo.
  AND R1,R1,R2     // R1<-bit wise And of RR1 and R2
```

&emsp;&emsp;**Memory Access** Memory access commands fall into two categories. First, as we have just seen, arithmetic and logical commands are allowed to operate not only on registers, but also on selected memory locations. Second, all computers feature explicit load and store commands, designed to move data between registers and memory. These memory access commands may use several types of addressing modes—ways of specifying the address of the required memory word. As usual, different computers offer different possibilities and different notations, but the following three memory access modes are almost always supported:
■ <em>Direct addressing</em> The most common way to address the memory is to express a specific address or use a symbol that refers to a specific address, as follows:

```
  LOAD R1,67   // R1<-Memory[67]
  // Or, assuming that bar refers to memory address 67:
  LOAD R1,bar  // R1<-Memory[67]
```

&emsp;&emsp;■ <em>Immediate addressing</em> This form of addressing is used to load constants—namely, load values that appear in the instruction code: Instead of treating the numeric field that appears in the instruction as an address, we simply load the value of the field itself into the register, as follows:

```
  LOAD R1,67   // R1<-67
```

&emsp;&emsp;■ <em>Indirect addressing</em> In this addressing mode the address of the required memory location is not hard- coded into the instruction; instead, the instruction specifies a memory location that holds the required address. This addressing mode is used to handle pointers. For example, consider the high-level command x=foo[j], where foo is an array variable and x and j are integer variables. What is the machine language equivalent of this command? Well, when the array foo is declared and initialized in the high-level program, the compiler allocates a memory segment to hold the array data and makes the symbol foo refer to the base address of that segment.

Now, when the compiler later encounters references to array cells like foo[j], it translates them as follows. First, note that the jth array entry should be physically located in a memory location that is at a displacement j from the array’s base address (assuming, for simplicity, that each array element uses a single word). Hence the address corresponding to the expression foo[j] can be easily calculated by adding the value of j to the value of foo. Thus in the C programming language, for example, a command like x=foo[j] can be also expressed as x=&ast;(foo+j), where the notation “&ast;n” stands for “the value of Memory[n]”. When translated into machine language, such commands typically generate the following code (depending on the assembly language syntax):

```
  // Translation of x=foo[j] or x=*(foo+j);
  ADD R1,foo,j    // R1<-foo+j
  LOAD* R2,R1     // R2<-Memory[R1]
  STR R2,x        // x<-R2
```

&emsp;&emsp;**Flow of Control** While programs normally execute in a linear fashion, one command after the other, they also include occasional branches to locations other than the next command. Branching serves several purposes including repetition (jump backward to the beginning of a loop), conditional execution (if a Boolean condition is false, jump forward to the location after the “if-then” clause), and subroutine calling (jump to the first command of some other code segment). In order to support these programming constructs, every machine language features the means to jump to selected locations in the program, both conditionally and unconditionally. In assembly languages, locations in the program can also be given symbolic names, using some syntax for specifying labels. Figure 4.1 illustrates a typical example.

<div align="center"><img width="500" src="../figure/04/4.1.png"/></div>

&emsp;&emsp;**Figure 4.1** High- and low-level branching logic. The syntax of goto commands varies from one language to another, but the basic idea is the same.

&emsp;&emsp;<em>Unconditional jump commands</em> like JMP beginWhile specify only the address of the target location. <em>Conditional jump commands</em> like JNG R1,endWhile must also specify a Boolean condition, expressed in some way. In some languages the condition is an explicit part of the command, while in others it is a by- product of executing a previous command.

&emsp;&emsp;This ends our informal introduction to machine languages and the generic operations that they normally support. The next section gives a formal description of one specific machine language—the native code of the computer that we will build in chapter 5.
