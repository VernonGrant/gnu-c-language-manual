Previous: [Complete Program, Line by
Line](Complete-Line_002dby_002dLine.md), Up: [A Complete
Program](Complete-Program.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 2.4 Compiling the Example Program 


To run a C program requires converting the source code into an
*executable file*. This is called *compiling* the program, and the
command to do that using GNU C is `gcc`.

This example program consists of a single source file. If we call that
file `fib1.c`, the complete command to compile it is this:

``` C
gcc -g -O -o fib1 fib1.c
```

Here, `-g` says to generate debugging information,
`-O` says to optimize at the basic level, and
`-o fib1` says to put the executable program in the file
`fib1`.

To run the program, use its file name as a shell command. For instance,

``` C
./fib1
```

However, unless you are sure the program is correct, you should expect
to need to debug it. So use this command,

``` C
gdb fib1
```

which starts the GDB debugger (see [A Sample GDB
Session](https://sourceware.org/gdb/current/onlinedocs/gdb/Sample-Session.md#Sample-Session)
in Debugging with GDB) so you can run and debug the executable program
`fib1`.

See [Compilation](Compilation.md), for an introduction to compiling
more complex programs which consist of more than one source file.
