Next: [Directing Compilation](Directing-Compilation.md), Previous:
[Floating Point in Depth](Floating-Point-in-Depth.md), Up: [GNU C
Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 29 Compilation 


Early in the manual we explained how to compile a simple C program that
consists of a single source file (see [Compiling the Example
Program](Compile-Example.md)). However, we handle only short programs
that way. A typical C program consists of many source files, each of
which is usually a separate *compilation module*---meaning that it has
to be compiled separately. (The source files that are not separate
compilation modules are those that are used via `#include`; see [Header
Files](Header-Files.md).)

To compile a multi-module program, you compile each of the program's
compilation modules, making an *object file* for that module. The last
step is to *link* the many object files together into a single
executable for the whole program.

The full details of how to compile C programs (and other programs) with
GCC are documented in xxxx. Here we give only a simple introduction.

These commands compile two compilation modules, `foo.c` and
`bar.c`, running the compiler for each module:

``` C
gcc -c -O -g foo.c
gcc -c -O -g bar.c
```

In these commands, `-g` says to generate debugging information,
`-O` says to do some optimization, and `-c` says to
put the compiled code for that module into a corresponding object file
and go no further. The object file for `foo.c` is automatically
called `foo.o`, and so on.

If you wish, you can specify the additional compilation options. For
instance, `-Wformat -Wparenthesis -Wstrict-prototypes` request
additional warnings.


After you compile all the program's modules, you link the object files
into a combined executable, like this:

``` C
gcc -o foo foo.o bar.o
```

In this command, `-o foo` species the file name for the
executable file, and the other arguments are the object files to link.
Always specify the executable file name in a command that generates one.

One reason to divide a large program into multiple compilation modules
is to control how each module can access the internals of the others.
When a module declares a function or variable `extern`, other modules
can access it. The other functions and variables defined in a module
can't be accessed from outside that module.

The other reason for using multiple modules is so that changing one
source file does not require recompiling all of them in order to try the
modified program. It is sufficient to recompile the source file that you
changed, then link them all again. Dividing a large program into many
substantial modules in this way typically makes recompilation much
faster.

Normally we don't run any of these commands directly. Instead we write a
set of *make rules* for the program, then use the `make` program to
recompile only the source files that need to be recompiled, by following
those rules. See [The GNU Make Manual](../Make/index.md#Top) in The
GNU Make Manual.

------------------------------------------------------------------------

Next: [Directing Compilation](Directing-Compilation.md), Previous:
[Floating Point in Depth](Floating-Point-in-Depth.md), Up: [GNU C
Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
