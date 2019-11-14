### 2.3 Implementation
---


&emsp;&emsp;Our implementation guidelines are intentionally partial, since we want you to discover the actual chip architectures yourself. As usual, each chip can be implemented in more than one way; the simpler the implementation, the better.

&emsp;&emsp;**Half-Adder** An inspection of figure 2.2 reveals that the functions sum(a, b) and carry(a, b) happen to be identical to the standard Xor(a, b) and And(a, b) Boolean functions. Thus, the implementation of this adder is straightforward, using previously built gates.

&emsp;&emsp;**Full-Adder** A full adder chip can be implemented from two half adder chips and one additional simple gate. A direct implementation is also possible, without using half-adder chips.

&emsp;&emsp;**Adder** The addition of two signed numbers represented by the 2’s complement method as two n-bit buses can be done bit-wise, from right to left, in n steps. In step 0, the least significant pair of bits is added, and the carry bit is fed into the addition of the next significant pair of bits. The process continues until in step n–1 the most significant pair of bits is added. Note that each step involves the addition of three bits. Hence, an n-bit adder can be implemented by creating an array of n full-adder chips and propagating the carry bits up the significance ladder.

&emsp;&emsp;**Incrementer** An n-bit incrementer can be implemented trivially from an n-bit adder. ALU Note that our ALU was carefully planned to effect all the desired ALU operations logically, using simple Boolean operations. Therefore, the physical implementation of the ALU is reduced to implementing these simple Boolean operations, following their pseudo-code specifications. Your first step will likely be to create a logic circuit that manipulates a 16-bit input according to the nx and zx control bits (i.e., the circuit should conditionally zero and negate the 16-bit input). This logic can be used to manipulate the x and y inputs, as well as the out output. Chips for bit-wise And-ing and addition have already been built in this and in the previous chapter. Thus, what remains is to build logic that chooses between them according to the f control bit. Finally, you will need to build logic that integrates all the other chips into the overall ALU. (When we say “build logic,” we mean “write HDL code”).
