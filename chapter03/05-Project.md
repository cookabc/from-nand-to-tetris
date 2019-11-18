### 3.5 Project
---


&emsp;&emsp;**Objective** Build all the chips described in the chapter. The only building blocks that you can use are primitive DFF gates, chips that you will build on top of them, and chips described in previous chapters.

&emsp;&emsp;**Resources** The only tool that you need for this project is the hardware simulator supplied with the book. All the chips should be implemented in the HDL language specified in appendix A. As usual, for each chip we supply a skeletal .hdl program with a missing implementation part, a .tst script file that tells the hardware simulator how to test it, and a .cmp compare file. Your job is to complete the missing implementation parts of the supplied .hdl programs.

&emsp;&emsp;**Contract** When loaded into the hardware simulator, your chip design (modified .hdl program), tested on the supplied .tst file, should produce the outputs listed in the supplied .cmp file. If that is not the case, the simulator will let you know.

&emsp;&emsp;**Tip** The Data Flip-Flop (DFF) gate is considered primitive and thus there is no need to build it: When the simulator encounters a DFF gate in an HDL program, it automatically invokes the built-in tools/builtIn/DFF.hdl implementation.

&emsp;&emsp;**The Directory Structure of This Project** When constructing RAM chips from smaller ones, we recommend using built-in versions of the latter. Otherwise, the simulator may run very slowly or even out of (real) memory space, since large RAM chips contain tens of thousands of lower-level chips, and all these chips are kept in memory (as software objects) by the simulator. For this reason, we have placed the RAM512.hdl, RAM4K.hdl, and RAM16K.hdl programs in a separate directory. This way, the recursive descent construction of the RAM4K and RAM16K chips stops with the RAM512 chip, whereas the lower-level chips from which the latter chip is made are bound to be built-in (since the simulator does not find them in this directory).

&emsp;&emsp;**Steps** We recommend proceeding in the following order:

&emsp;&emsp;0. The hardware simulator needed for this project is available in the tools directory of the book’s software suite.

&emsp;&emsp;1. Read appendix A, focusing on sections A.6 and A.7.

&emsp;&emsp;2. Go through the <em>hardware simulator tutorial</em>, focusing on parts IV and V.

&emsp;&emsp;3. Build and simulate all the chips specified in the projects/03 directory.
