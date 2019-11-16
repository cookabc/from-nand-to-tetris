## Chapter 7: Virtual Machine I: Stack Arithmetic
---


<br />

> ###### &emsp;&emsp;<em>Programmers are creators of universes for which they alone are responsible. Universes of virtually unlimited complexity can be created in the form of computer programs</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Joseph Weizenbaum, Computer Power and Human Reason (1974)</em></div>

<br />

&emsp;&emsp;This chapter describes the first steps toward building a compiler for a typical object-based high-level language. We will approach this substantial task in two stages, each spanning two chapters. High-level programs will first be translated into an intermediate code (chapters 10—11), and the intermediate code will then be translated into machine language (chapters 7-8). This two-tier translation model is a rather old idea that goes back to the 1970s. Recently, it made a significant comeback following its adoption by modern languages like Java and C#.

&emsp;&emsp;The basic idea is as follows: Instead of running on a real platform, the intermediate code is designed to run on a Virtual Machine. The VM is an abstract computer that does not exist for real, but can rather be realized on other computer platforms. There are many reasons why this idea makes sense, one of which being code transportability. Since the VM may be implemented with relative ease on multiple target platforms, VM-based software can run on many processors and operating systems without having to modify the original source code. The VM implementations can be realized in several ways, by software interpreters, by special-purpose hardware, or by translating the VM programs into the machine language of the target platform.

&emsp;&emsp;This chapter presents a typical VM architecture, modeled after the Java Virtual Machine (JVM) paradigm. As usual, we focus on two perspectives. First, we motivate and specify the VM abstraction. Next, we implement it over the Hack platform. Our implementation entails writing a program called VM translator, designed to translate VM code into Hack assembly code. The software suite that comes with the book illustrates yet another implementation vehicle, called VM emulator. This programimplements the VM by emulating it on a standard personal computer using Java.

&emsp;&emsp;A virtual machine model typically has a language, in which one can write VM programs. The VM language that we present here consists of four types of commands: arithmetic, memory access, program flow, and subroutine calling commands. We split the implementation of this language into two parts, each covered in a separate chapter and project. In this chapter we build a basic VM translator, capable of translating the VM’s arithmetic and memory access commands into machine language. In the next chapter we extend the basic translator with program flow and subroutine calling functionality. The result is a fullscale virtual machine that will serve as the backend of the compiler that we will build in chapters 10-11.

&emsp;&emsp;The virtual machine that emerges from this effort illustrates many important ideas in computer science. First, the notion of having one computer emulating another is a fundamental idea in the field, tracing back to Alan Turing in the 1930s. Over the years it had many practical implications, for example, using an emulator of an old generation computer running on a new platform in order to achieve upward code compatibility. More recently, the virtual machine model became the centerpiece of two competing mainstreams—the Java architecture and the .NET infrastructure. These software environments are rather complex, and one way to gain an inside view of their underlying structure is to build a simple version of their VM cores, as we do here.

&emsp;&emsp;Another important topic embedded in this chapter is stack processing. The stack is a fundamental and elegant data structure that comes to play in many computer systems and algorithms. Since the VM presented in this chapter is stack-based, it provides a working example of this remarkably versatile data structure.
