### 8.2 VM Specification, Part II
---


&emsp;&emsp;This section extends the basic VM specification from chapter 7 with program flow and <em>function calling</em> commands, thereby completing the overall VM specification.



#### 8.2.1 Program Flow Commands

&emsp;&emsp;The VM language features three program flow commands:

  &emsp;&emsp;■ label <em>label</em> This command labels the current location in the function’s code.

  &emsp;&emsp;Only labeled locations can be jumped to from other parts of the program. The scope of the label is the function in which it is defined. The label is an arbitrary string composed of any sequence of letters, digits, underscore (_), dot (.), and colon (:) that does not begin with a digit.

  &emsp;&emsp;■ goto <em>label</em> This command effects an unconditional goto operation, causing execution to continue from the location marked by the label. The jump destination must be located in the same function.

  &emsp;&emsp;■ if-goto <em>label</em> This command effects a conditional goto operation. The stack’s topmost value is popped; if the value is not zero, execution continues from the location marked by the label; otherwise, execution continues from the next command in the program. The jump destination must be located in the same function.



#### 8.2.2 Function Calling Commands

&emsp;&emsp;Different high-level languages have different names for program units including functions, procedures, methods, and subroutines. In our overall compilation model (elaborated in chapters 10-11), each such high-level program unit is translated into a low-level program unit called <em>VM function</em>, or simply function.

&emsp;&emsp;A function has a symbolic name that is used globally to call it. The function name is an arbitrary string composed of any sequence of letters, digits, underscore (_), dot (.), and colon (:) that does not begin with a digit. (We expect that a method bar in class Foo in some high-level language will be translated by the compiler to a VM function named Foo.bar). The scope of the function name is global: All functions in all files are seen by each other and may call each other using the function name.

&emsp;&emsp;The VM language features three function-related commands:

  &emsp;&emsp;■ function <em>f</em> n Here starts the code of a function named f that has n local variables;

  &emsp;&emsp;■ call <em>f m</em> Call function <em>f</em>, stating that m arguments have already been pushed onto the stack by the caller;

  &emsp;&emsp;■ return Return to the calling function.



#### 8.2.3 The Function Calling Protocol

&emsp;&emsp;The events of calling a function and returning from a function can be viewed from two different perspectives: that of the calling function and that of the called function.

&emsp;&emsp;<em>The calling function view:</em>

  &emsp;&emsp;■ Before calling the function, the caller must push as many arguments as necessary onto the stack;

  &emsp;&emsp;■ Next, the caller invokes the function using the call command;

  &emsp;&emsp;■ After the called function returns, the arguments that the caller has pushed before the call have disappeared from the stack, and a return value (that always exists) appears at the top of the stack;

  &emsp;&emsp;■ After the called function returns, the caller’s memory segments argument, local, static, this, that, and pointer are the same as before the call, and the temp segment is undefined.

&emsp;&emsp;<em>The called function view:</em>

  &emsp;&emsp;■ When the called function starts executing, its argument segment has been initialized with actual argument values passed by the caller and its local variables segment has been allocated and initialized to zeros. The static segment that the called function sees has been set to the static segment of the VM file to which it belongs, and the working stack that it sees is empty. The segments this, that, pointer, and temp are undefined upon entry.

  &emsp;&emsp;■ Before returning, the called function must push a value onto the stack.

&emsp;&emsp;To repeat an observation made in the previous chapter, we see that when a VM function starts running (or resumes its previous execution), it assumes that it is surrounded by a private world, all of its own, consisting of its memory segments and stack, waiting to be manipulated by its commands. The agent responsible for building this virtual worldview for every VM function is the VM implementation, as we elaborate in section 8.3.



#### 8.2.4 Initialization

&emsp;&emsp;A VM program is a collection of related VM functions, typically resulting from the compilation of some high-level program. When the VM implementation starts running (or is reset), the convention is that it always executes an argument-less VM function called Sys.init. Typically, this function then calls the main function in the user’s program. Thus, compilers that generate VM code must ensure that each translated program will have one such Sys.init function.
