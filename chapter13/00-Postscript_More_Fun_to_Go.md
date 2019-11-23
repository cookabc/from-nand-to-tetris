## Chapter 13: Postscript: More Fun to Go
---


<br />

> ###### &emsp;&emsp;<em>We shall not cease from exploration, and at the end we will arrive where we started, and know the place for the first time.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——T. S. Eliot (1888-1965)</em></div>

<br />

&emsp;&emsp;Congratulations! You have finished the construction of a complete computing system. We hope that you enjoyed this journey. Let us, the authors of this book, share a secret with you: We suspect that we enjoyed writing the book even more. After all, we got to design this computing system, and design is often the “funnest” part of every project. We are sure that some of you, adventurous readers, would like to get in on some of that design action. Maybe you would like to improve the architecture; maybe you have ideas for adding new features here and there; maybe you envision a wider system. And then, maybe, you just want to be in the navigator’s seat and decide where to go, not only how to get there.

&emsp;&emsp;Many alternative design elements can be implemented by modifying and extending the software that you have written in the various projects. For example, the assembly language, the Jack language, and the operating system can be modified and extended at will, by changing their specifications and rewriting portions of your respective assembler, compiler, and OS implementations. Other changes would likely require modification of the software supplied by us. For example, if you change the VM specification or the hardware specification, then you would probably want to change the respective emulators as well. Or if you want to add a new input or output device to the Hack computer, you would probably need to model them as built-in chips in the hardware simulator.

&emsp;&emsp;In order to allow complete flexibility of modifications and extensions, we are making all the source code of the software associated with the book publicly available. All our code is 100 percent Java, expect for the batch files used for starting the software on the Windows and Linux platforms. The software and its documentation are available from the book’s Web site at [http://www.idc.ac.il/tecs](http://www.idc.ac.il/tecs). You are welcome to modify and extend all our tools as you deem desirable for your latest idea—and then share them with others, if you want. We hope that our code is written and documented well enough to make modification a satisfying experience. In particular, we wish to mention that the supplied hardware simulator has a simple and well-documented interface for adding new “built-in” chips. This interface can be used for extending the simulated hardware platform with, say, disk storage or communications devices.

&emsp;&emsp;While we cannot even start to imagine what your design improvements may be, we can briefly sketch some of the ones we were thinking of.
