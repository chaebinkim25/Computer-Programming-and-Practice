## linux and c program

- **linux:** what is the core environment?
  linux is the operating system kernel that manages the computer's hardware resources (CPU, memory, storage) and
  provides the fundamental environment and API (system calls) that programs rely on to run.
  
- **wsl:** how do we run Linux on Windows?
  The Windows Subsystem for Linux. 
  It is a compatibility layer that allows developers to run a genuine Linux environment—complete with 
  command-line tools, utilities, and compilers—directly on a Windows machine without 
  the heavy resource overhead of a traditional virtual machine.

- **ls:** how do we see our files?
  A fundamental command-line utility in the Linux terminal used to "list" the contents of a directory. 
  It allows you to verify that your C source files (.c) and your compiled executables are where they should be.

- **cat:** how do we quickly view code?
  A command-line tool (short for "concatenate") used to read the contents of a file and print it directly to the terminal screen. 
  It is incredibly useful for taking a quick look at a C source file without opening a full text editor.

- **gcc:** how do we translate code?
  The GNU Compiler Collection. 
  It is the standard, open-source compiler used in Linux to translate human-readable C source code into machine-executable binary files through 
  a process of preprocessing, compiling, assembling, and linking.

- **`main`:** where does the program start?
  The mandatory entry point of any C program. 
  When the operating system executes the compiled binary, it specifically looks for a function named main and begins executing the instructions there.

- **`int`:** what kind of data is being returned?
  A fundamental C data type representing an integer (a whole number). 
  When placed right before main, it declares to the compiler that the function will return an integer value back to the operating system upon completion.

- **`()`:** where do we put the inputs?
  Parentheses enclose the parameters (or arguments) that a function accepts. 
  For main, this dictates what command-line arguments the program can process. 
  If it takes no arguments, it is often written as (void), which is excellent practice, particularly under the C89 standard.

- **`{}`:** how do we group instructions?
  Curly braces define a "block" of code or scope. 
  The opening { and closing } immediately following main() enclose the actual sequence of C instructions that make up the body of the program.

- **`return`:** how does the program finish?
  A keyword in C used to exit the current function and pass a specific value back to the entity that called it. 
  In the context of main, it passes an exit status code back to the Linux operating system shell.

- **`0`:** what does a successful finish look like?
  The standard integer value returned to the operating system at the end of main to signal that the program executed successfully and naturally, without encountering any fatal errors.

- **`;`:**
- **gdb:**
- **`+`:**
- **`-`:**
- **`*`:**
- **`/`:**
- **`%`:**
- **`=`:**
- **declaration:**
- **variable name:**
- **`()` in expression:**
- **code:** how do we launch our editor?
  A command-line instruction. 
  Typing code . in the terminal tells the system to open the current directory inside the Visual Studio Code editor, 
  seamlessly bridging the command line and the graphical text editor.

- **vscode:** where do we write the code?
  Visual Studio Code. 
  A lightweight, powerful source-code editor that provides features like syntax highlighting, code completion, and integrated debugging. 
  It interfaces perfectly with WSL, allowing you to edit files on the Windows side while compiling them on the Linux side.

- **json:**
- **launch.json**
- **c standard:***

















