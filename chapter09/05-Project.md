### 9.5 Project
---


&emsp;&emsp;**Objective** The hidden agenda of this project is to get acquainted with the Jack language, for two purposes: writing the Jack compiler in Projects 10 and 11, and writing the Jack operating system in Project 12.

&emsp;&emsp;**Resources** You will need three tools: the Jack compiler, to translate your program into a set of .vm files, the VM emulator, to run and test your translated program, and the Jack Operating System.

&emsp;&emsp;**Contract** Adopt or invent an application idea, for example, a simple computer game or some other interactive program. Then design and build the application.

&emsp;&emsp;**The Jack OS** The Jack Operating System is available as a set of .vm files. These files constitute an implementation of the standard library of the Jack programming language. In order for any Jack program to execute properly, the compiled .vm files of the program must reside in a directory that also contains all the .vm files of the Jack OS. When an OS-oriented error is detected by the Jack OS, it displays a numeric error code (rather than text, which wastes precious memory space). A list of all the currently supported error codes and their textual descriptions can be found in the file projects/09/OSerrors.txt.

&emsp;&emsp;**Compiling and Running a Jack Program**

&emsp;&emsp;0. Each program must be stored in a separate directory, say Xxx. Start by creating this directory, then copy all the files from tools/OS into it.

&emsp;&emsp;1. Write your Jack program—a set of one or more Jack classes—each stored in a separate ClassName.jack text file. Put all these .jack files in the Xxx directory.

&emsp;&emsp;2. Compile your program using the supplied Jack compiler. This is best done by applying the compiler to the name of the program directory (Xxx). This will cause the compiler to translate all the .jack classes found in the directory into corresponding .vm files. If a compilation error is reported, debug the program and recompile Xxx until no error messages are issued.

&emsp;&emsp;3. At this point the program directory should contain three sets of files: (i) your source .jack files, (ii) the compiled .vm files, one for each of your .jack class files, and (iii) additional .vm files, comprising the supplied Jack OS. To test the compiled program, invoke the VM emulator and load the entire Xxx program directory. Then run the program. In case of run-time errors or undesired program behavior, fix the program and go to stage 2.

&emsp;&emsp;**A Sample Jack Program** The book’s software suite includes a complete example of a Jack application, stored in projects/09/Square. This directory contains the source Jack code of three classes comprising a simple interactive game.
