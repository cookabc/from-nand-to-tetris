## Chapter 12: Operating System
---


<br />

> ###### &emsp;&emsp;<em>Civilization progresses by extending the number of operations that we can perform without thinking about them.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Alfred North Whitehead, Introduction to Mathematics (1911)</em></div>

<br />

&emsp;&emsp;In previous chapters of this book, we described and built the hardware architecture of a computer platform, called Hack, and the software hierarchy that makes it usable. In particular, we introduced an object-based language, called Jack, and described how to write a compiler for it. Other high-level programming languages can be specified on top of the Hack platform, each requiring its own compiler.

&emsp;&emsp;The last major interface missing in this puzzle is an operating system (OS). The OS is designed to close gaps between the computer’s hardware and software systems, and to make the overall computer more accessible to programmers and users. For example, in order to render the text “Hello World” on our computer’s screen, several hundred pixels must be drawn at specific screen locations. This can be done by consulting the hardware specification and writing code that puts the necessary bits in the RAM- resident screen memory map. Obviously, high-level programmers expect something better than that. They want to use a command like printString(“Hello World”) and let someone else worry about the details. And that’s where the operating system enters the picture.

&emsp;&emsp;Throughout this chapter, the term operating system is used rather loosely. In fact, the OS services that we describe comprise an operating system in a very minimal fashion, aiming at (i) encapsulating various hardware-specific services in a software-friendly way, and (ii) extending high-level languages with various functions and abstract data types. The dividing line between an operating system in this sense and a standard language library is not very clear. Indeed, some modern languages, most notably Java, tend to pack many classic operating system services like GUI management, memory management, and multitasking in its standard software library, along with many language extensions.

&emsp;&emsp;Following this pattern, the collection of services that we specify and build in this chapter can be viewed as a combination of a simple OS and a standard library for the Jack language. This OS is packaged as a collection of Jack classes, each providing a set of related services via Jack subroutine calls. The resulting OS has many features resembling those of industrial strength operating systems, but it still lacks numerous OS features such as process handling, disk management, communications, and more.

&emsp;&emsp;Operating systems are usually written in a high-level language and compiled into binary form, just like any other program. Our OS is no exception—it can be written completely in Jack. Yet unlike other programs written in high-level languages, the operating system code must be aware of the hardware platform on which it runs. In other words, in order to hide the gory hardware details from the application programmer, the OS programmer must write code that manipulates these details directly (a task that requires access to the hardware documentation). Conveniently, this can be done using the Jack language. As we observe in this chapter, Jack was defined with sufficient “lowness” in it, permitting an intimate closeness to the hardware when needed.

&emsp;&emsp;The chapter starts with a relatively long Background section, describing key algorithms normally used to implement basic operating system services. These include mathematical functions, string operations, memory management, handling text and graphics output to the screen, and handling inputs from the keyboard. This algorithmic introduction is followed by a Specification section, providing the complete API of the Jack OS, and an Implementation section, describing how to build the OS using the classic algorithms presented earlier. As usual, the final Project section provides all the necessary project materials for gradual construction and unit-testing the entire OS presented in the chapter.

&emsp;&emsp;The chapter provides two key lessons, one in software engineering and one in computer science. First, we complete the construction of the high-level language, compiler, and operating system trio. Second, since operating system services must execute efficiently, we pay attention to running time considerations. The result is an elegant series of algorithms, each being a computer science gem.
