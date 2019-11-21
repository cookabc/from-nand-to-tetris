## Chapter 5: Computer Architecture
---


<br />

> ###### &emsp;&emsp;<em>Form ever follows function.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Louis Sullivan (1856—1924), architect</em></div>

> ###### &emsp;&emsp;<em>Form IS function.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Ludwig Mies van der Rohe (1886—1969), architect</em></div>

<br />

&emsp;&emsp;This chapter is the pinnacle of the “hardware” part of our journey. We are now ready to take all the chips that we built in chapters 1-3 and integrate them into a general-purpose computer capable of running stored programs written in the machine language presented in chapter 4. The specific computer we will build, called Hack, has two important virtues. On the one hand, Hack is a simple machine that can be constructed in just a few hours, using previously built chips and the hardware simulator supplied with the book. On the other hand, Hack is sufficiently powerful to illustrate the key operating principles and hardware elements of any digital computer. Therefore, building it will give you an excellent understanding of how modern computers work at the low hardware and software levels.

&emsp;&emsp;Following an introduction of the stored program concept, section 5.1 gives a detailed description of the von Neumann <em>architecture</em>—a central dogma in computer science underlying the design of almost all modern computers. The Hack platform is one example of a von Neumann machine, and section 5.2 gives its exact hardware specification. Section 5.3 describes how the Hack platform can be implemented from available chips, in particular the ALU built in chapter 2 and the registers and memory systems built in chapter 3.

&emsp;&emsp;The computer that will emerge from this construction will be as simple as possible, but not simpler. This means that it will have the minimal configuration necessary to run interesting programs and deliver a reasonable performance. The comparison of this machine to typical computers is taken up in section 5.4, which emphasizes the critical role that optimization plays in the design of industrial-strength computers, but not in this chapter. As usual, the simplicity of our approach has a purpose: All the chips mentioned in the chapter, culminating in the Hack computer itself, can be built and tested on a personal computer running our hardware simulator, following the technical instructions given in section 5.5. The result will be a minimal yet surprisingly powerful computer.
