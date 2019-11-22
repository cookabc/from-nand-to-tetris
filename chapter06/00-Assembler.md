## Chapter 6: Assembler
---


<br />

> ###### &emsp;&emsp;<em>What’s in a name? That which we call a rose by any other name would smell as sweet.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Shakespeare, from Romeo and Juliet</em></div>

<br />

&emsp;&emsp;The first half of the book (chapters 1-5) described and built a computer’s hardware platform. The second half of the book (chapters 6-12) focuses on the computer’s software hierarchy, culminating in the development of a compiler and a basic operating system for a simple, object-based programming language. The first and most basic module in this software hierarchy is the assembler. In particular, chapter 4 presented machine languages in both their assembly and binary representations. This chapter describes how assemblers can systematically translate programs written in the former into programs written in the latter. As the chapter unfolds, we explain how to develop a Hack <em>assembler</em>—a program that generates binary code that can run as is on the hardware platform built in chapter 5.

&emsp;&emsp;Since the relationship between symbolic assembly commands and their corresponding binary codes is straightforward, writing an assembler (using some high-level language) is not a difficult task. One complication arises from allowing assembly programs to use symbolic references to memory addresses. The assembler is expected to manage these user-defined symbols and resolve them to physical memory addresses. This task is normally done using a symbol <em>table</em>—a classical data structure that comes to play in many software translation projects.

&emsp;&emsp;As usual, the Hack assembler is not an end in itself. Rather, it provides a simple and concise demonstration of the key software engineering principles used in the construction of any assembler. Further, writing the assembler is the first in the series of seven software development projects that accompany the rest of the book. Unlike the hardware projects, which were implemented in HDL, the software projects that construct the translator programs (<em>assembler</em>, virtual machine, and compiler) may be implemented in any programming language. In each project, we provide a language-neutral API and a detailed step-by-step test plan, along with all the necessary test programs and test scripts. Each one of these projects, beginning with the assembler, is a stand-alone module that can be developed and tested in isolation from all the other projects.
