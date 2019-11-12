### 1.3 Implementation
---


&emsp;&emsp;Similar to the role of axioms in mathematics, primitive gates provide a set of elementary building blocks from which everything else can be built. Operationally, primitive gates have an “off-the-shelf” implementation that is supplied externally. Thus, they can be used in the construction of other gates and chips without worrying about their internal design. In the computer architecture that we are now beginning to build, we have chosen to base all the hardware on one primitive gate only: Nand. We now turn to outlining the first stage of this bottom-up hardware construction project, one gate at a time.

&emsp;&emsp;Our implementation guidelines are intentionally partial, since we want you to discover the actual gate architectures yourself. We reiterate that each gate can be implemented in more than one way; the simpler the implementation, the better.

&emsp;&emsp;**Not:** The implementation of a unary Not gate froma binary Nand gate is simple. Tip: Think positive.

&emsp;&emsp;**And:** Once again, the gate implementation is simple. Tip: Think negative.

&emsp;&emsp;**Or/Xor:** These functions can be defined in terms of some of the Boolean functions implemented previously, using some simple Boolean manipulations. Thus, the respective gates can be built using previously built gates.

&emsp;&emsp;**Multiplexor/ Demultiplexor:** Likewise, these gates can be built using previously built gates.

&emsp;&emsp;**Multi-Bit Not/And/Or Gates:** Since we already know how to implement the elementary versions of these gates, the implementation of their n-ary versions is simply a matter of constructing arrays of n elementary gates, having each gate operate separately on its bit inputs. This implementation task is rather boring, but it will carry its weight when these multi-bit gates are used in more complex chips, as described in subsequent chapters.

&emsp;&emsp;**Multi-Bit Multiplexor:** The implementation of an n-ary multiplexor is simply a matter of feeding the same selection bit to every one of n binary multiplexors. Again, a boring task resulting in a very useful chip.

&emsp;&emsp;**Multi-Way Gates:** Implementation tip: Think forks.
