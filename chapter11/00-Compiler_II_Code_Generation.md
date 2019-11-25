## Chapter 11: Compiler II: Code Generation
---


<br />

> ###### &emsp;&emsp;<em>The syntactic component of a grammar must specify, for each sentence, a deep structure that determines its semantic interpretation.</em>

> ###### <div style="margin: -20px 50px 0 0; text-align: right"><em>——Noam Chomsky (b. 1928), mathematical linguist</em></div>

<br />

&emsp;&emsp;Most programmers take compilers for granted. But if you’ll stop to think about it for a moment, the ability to translate a high-level program into binary code is almost like magic. In this book we demystify this transformation by writing a compiler for Jack—a simple yet modern object-based language. As with Java and C#, the overall Jack compiler is based on two tiers: a virtual machine back-end, developed in chapters 7-8, and a typical front-end module, designed to bridge the gap between the high-level language and the VM language. The compiler’s front-end module consists of a syntax analyzer, developed in chapter 10, and a code generator—the subject of this chapter.

&emsp;&emsp;Although the compiler’s front-end comprises two conceptual modules, they are usually combined into a single program, as we will do here. Specifically, in chapter 10 we built a syntax analyzer capable of “understanding”—parsing—source Jack programs. In this chapter we extend the analyzer into a full-scale compiler that converts each “understood” high-level construct into an equivalent series of VM operations. This approach follows the modular analysis-synthesis paradigm underlying the construction of most compilers.

&emsp;&emsp;Modern high-level programming languages are rich and powerful. They allow defining and using elaborate abstractions such as objects and functions, implementing algorithms using elegant flow of control statements, and building data structures of unlimited complexity. In contrast, the target platforms on which these programs eventually run are spartan and minimal. Typically, they offer nothing more than a vector of registers for storage and a primitive instruction set for processing. Thus, the translation of programs from high-level to low-level is an interesting brain teaser. If the target platform is a virtual machine, life is somewhat easier, but still the gap between the expressiveness of a high-level language and that of a virtual machine is wide and challenging.

&emsp;&emsp;The chapter begins with a Background section covering the minimal set of topics necessary for completing the compiler’s development: managing a symbol table; representing and generating code for variables, objects, and arrays; and translating control flow commands into low-level instructions. The Specification section defines how to map the semantics of Jack programs on the VM platform and language, and the Implementation section proposes an API for a code generation module that performs this transformation. The chapter ends with the usual Project section, providing step-by-step guidelines and test programs for completing the compiler’s construction.

&emsp;&emsp;So what’s in it for you? Typically, students who don’t take a formal compilation course don’t have an opportunity to develop a full-scale compiler. Thus readers who follow our instructions and build the Jack compiler from scratch will gain an important lesson for a relatively small effort (of course, their knowledge of compilation theory will remain limited unless they take a course on the subject). Further, some of the tricks and techniques used in the code generation part of the compiler are rather clever. Seeing these tricks in action leads one to marvel, once again, at how human ingenuity can dress up a primitive switching machine to look like something approaching magic.
