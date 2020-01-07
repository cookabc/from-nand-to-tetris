### 10.2 Specification
---


&emsp;&emsp;This section has two distinct parts. First, we specify the Jack language’s grammar. Next, we specify a syntax analyzer designed to parse programs according to this grammar.



#### 10.2.1 The Jack Language Grammar

&emsp;&emsp;The functional specification of the Jack language given in chapter 9 was aimed at Jack programmers. We now turn to giving a formal specification of the language, aimed at Jack compiler developers. Our grammar specification is based on the following conventions:

&emsp;&emsp;‘xxx’: quoted boldface is used for tokens that appear verbatim (“terminals”);

&emsp;&emsp;xxx: regular typeface is used for names of language constructs (“non-terminals”);

&emsp;&emsp;(): parentheses are used for grouping of language constructs;

&emsp;&emsp;x|y: indicates that either x or y can appear;

&emsp;&emsp;x?: indicates that x appears 0 or 1 times;

&emsp;&emsp;x*: indicates that x appears 0 or more times.

&emsp;&emsp;The Jack language syntax is given in figure 10.5, using the preceding conventions.

<div align="center"><img width="650" src="../figure/10/10.5.png"/></div>

<div align="center"><img width="650" src="../figure/10/10.5a.png"/></div>

&emsp;&emsp;**Figure 10.5** Complete grammar of the Jack language.



#### 10.2.2 A Syntax Analyzer for the Jack Language

&emsp;&emsp;The main purpose of the syntax analyzer is to read a Jack program and “understand” its syntactic structure according to the Jack grammar. By understanding, we mean that the syntax analyzer must know, at each point in the parsing process, the structural identity of the program element that it is currently reading, namely, whether it is an expression, a statement, a variable name, and so on. The syntax analyzer must possess this syntactic knowledge in a complete recursive sense. Without it, it will be impossible to move on to code generation—the ultimate goal of the overall compiler.

&emsp;&emsp;The fact that the syntax analyzer “understands” the programmatic structure of the input can be demonstrated by having it print the processed text in some well-structured and easy-to-read format. One can think of several ways to cook up such a demonstration. In this book, we decided to have the syntax analyzer output an XML file whose marked-up format reflects the syntactic structure of the underlying program. By viewing this XML output file—a task that can be conveniently done with any Web browser —one should be able to tell right away if the syntax analyzer is doing the job or not.



#### 10.2.3 The Syntax Analyzer’s Input

&emsp;&emsp;The Jack syntax analyzer accepts a single command line parameter, as follows:

```
  prompt> JackAnalyzer source
```

&emsp;&emsp;Where <em>source</em> is either a file name of the form Xxx.jack (the extension is mandatory) or a directory name containing one or more .jack files (in which case there is no extension). The syntax analyzer compiles the Xxx.jack file into a file named Xxx.xml, created in the same directory in which the source file is located. If source is a directory name, each .jack file located in it is compiled, creating a corresponding .xml file in the same directory.

&emsp;&emsp;Each Xxx.jack file is a stream of characters. This stream should be tokenized into a stream of tokens according to the rules specified by the lexical elements of the Jack language (see figure 10.5, top). The tokens may be separated by an arbitrary number of space characters, newline characters, and comments, which are ignored. Comments are of the standard formats /* comment until closing */, /** API comment */, and // comment to end of line.



#### 10.2.4 The Syntax Analyzer’s Output

&emsp;&emsp;Recall that the development of the Jack compiler is split into two stages (see figure 10.1), starting with the syntax analyzer. In this chapter, we want the syntax analyzer to emit an XML description of the input program, as illustrated in figure 10.6. In order to do so, the syntax analyzer has to recognize two major types of language constructs: terminal and non-terminal elements. These constructs are handled as follows.

&emsp;&emsp;**Non-Terminals** Whenever a non-terminal language element of type xxx is encountered, the syntax analyzer should generate the marked-up output:

```
  <xxx>
    Recursive code for the body of the xxx element
  </xxx>
```

&emsp;&emsp;Where xxx is one of the following (and only the following) non-terminals of the Jack grammar:

  &emsp;&emsp;■ class, classVarDec, subroutineDec, parameterList, subroutineBody, varDec;

  &emsp;&emsp;■ statements, whileSatement, ifStatement, returnStatement, letStatement, doStatement;

  &emsp;&emsp;■ expression, term, expressionList.

&emsp;&emsp;**Terminals** Whenever a terminal language element of type xxx is encountered, the syntax analyzer should generate the marked-up output:

```
  <xxx>terminal</xxx>
```

&emsp;&emsp;Where xxx is one of the five token types recognized by the Jack language (as specified in the Jack grammar’s “lexical elements” section), namely, keyword, symbol, integerConstant, stringConstant, or identifier.

&emsp;&emsp;Figure 10.6, which shows the analyzer’s output, should evoke some sense of déjà vu. Earlier in the chapter we noted that the structure of a program can be analyzed into a parse tree. And indeed, XML output is simply a textual description of a tree. In particular, note that in a parse tree, the non-terminal nodes form a “super structure” that describes how the tree’s terminal nodes (the tokens) are grouped into language constructs. This pattern is mirrored in the XML output, where non-terminal XML elements describe how terminal XML items are arranged. In a similar fashion, the tokens generated by the tokenizer form the lowest level of the XML output, just as they form the terminal leaves of the program’s parse tree.

<div align="center"><img width="500" src="../figure/10/10.6.png"/></div>

&emsp;&emsp;**Figure 10.6** Jack Analyzer in action.

&emsp;&emsp;**Code Generation** We have just finished specifying the analyzer’s XML output. In the next chapter we replace the software that generates this output with software that generates executable VM code, leading to a full-scale Jack compiler.
