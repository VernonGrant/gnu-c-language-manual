Next: [Complete Program, Line by
Line](Complete-Line_002dby_002dLine.md), Previous: [Complete Program
Example](Complete-Example.md), Up: [A Complete
Program](Complete-Program.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 2.2 Complete Program Explanation 

Here's the explanation of the code of the example in the previous
section.

This sample program prints a message that shows the value of `fib (20)`,
and exits with code 0 (which stands for successful execution).

Every C program is started by running the function named `main`.
Therefore, the example program defines a function named `main` to
provide a way to start it. Whatever that function does is what the
program does. See [The `main` Function](The-main-Function.md).

The `main` function is the first one called when the program runs, but
it doesn't come first in the example code. The order of the function
definitions in the source code makes no difference to the program's
meaning.

The initial call to `main` always passes certain arguments, but `main`
does not have to pay attention to them. To ignore those arguments,
define `main` with `void` as the parameter list. (`void` as a function's
parameter list normally means "call with no arguments," but `main` is a
special case.)

The function `main` returns 0 because that is the conventional way for
`main` to indicate successful execution. It could instead return a
positive integer to indicate failure, and some utility programs have
specific conventions for the meaning of certain numeric *failure codes*.
See [Returning Values from `main`](Values-from-main.md).


The simplest way to print text in C is by calling the `printf` function,
so here we explain very briefly what that function does. For a full
explanation of `printf` and the other standard I/O functions, see [The
GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/I_002fO-on-Streams.md#I_002fO-on-Streams)
in The GNU C Library Reference Manual.


The first argument to `printf` is a *string constant* (see [String
Constants](String-Constants.md)) that is a template for output. The
function `printf` copies most of that string directly as output,
including the newline character at the end of the string, which is
written as '`\n`'. The output goes to the program's *standard
output* destination, which in the usual case is the terminal.

'`%`' in the template introduces a code that substitutes other
text into the output. Specifically, '`%d`' means to take the
next argument to `printf` and substitute it into the text as a decimal
number. (The argument for '`%d`' must be of type `int`; if it
isn't, `printf` will malfunction.) So the output is a line that looks
like this:

``` C
Fibonacci series item 20 is 6765
```

This program does not contain a definition for `printf` because it is
defined by the C library, which makes it available in all C programs.
However, each program does need to *declare* `printf` so it will be
called correctly. The `#include` line takes care of that; it includes a
*header file* called `stdio.h` into the program's code. That
file is provided by the operating system and it contains declarations
for the many standard input/output functions in the C library, one of
which is `printf`.

Don't worry about header files for now; we'll explain them later in
[Header Files](Header-Files.md).

The first argument of `printf` does not have to be a string constant; it
can be any string (see [Strings](Strings.md)). However, using a
constant is the most common case.

------------------------------------------------------------------------

Next: [Complete Program, Line by
Line](Complete-Line_002dby_002dLine.md), Previous: [Complete Program
Example](Complete-Example.md), Up: [A Complete
Program](Complete-Program.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
