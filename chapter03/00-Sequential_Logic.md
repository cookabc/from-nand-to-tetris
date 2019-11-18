## Chapter 3: Sequential Logic
---


<br />

> ###### &emsp;&emsp;<em>It’s a poor sort of memory that only works backward.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Lewis Carroll (1832-1898)</em></div>

<br />

&emsp;&emsp;All the Boolean and arithmetic chips that we built in chapters 1 and 2 were combinational. Combinational chips compute functions that depend solely on combinations of their input values. These relatively simple chips provide many important processing functions (like the ALU), but they cannot maintain state. Since computers must be able to not only compute values but also store and recall values, they must be equipped with memory elements that can preserve data over time. These memory elements are built from sequential chips.

&emsp;&emsp;The implementation of memory elements is an intricate art involving synchronization, clocking, and feedback loops. Conveniently, most of this complexity can be embedded in the operating logic of very low-level sequential gates called flip-flops. Using these flip-flops as elementary building blocks, we will specify and build all the memory devices employed by typical modern computers, from binary cells to registers to memory banks and counters. This effort will complete the construction of the chip set needed to build an entire computer—a challenge that we take up in the chapter 5.

&emsp;&emsp;Following a brief overview of clocks and flip-flops, the Background section introduces all the memory chips that we will build on top of them. The next two sections describe the chips Specification and Implementation, respectively. As usual, all the chips mentioned in the chapter can be built and tested using the hardware simulator supplied with the book, following the instructions given in the final Project section.
