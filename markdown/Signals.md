Next: [GNU Free Documentation
License](GNU-Free-Documentation-License.md), Previous: [Attributes in
Declarations](Attributes.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## Appendix E Signals 


Some program operations bring about an error condition called a
*signal*. These signals terminate the program, by default.

There are various different kinds of signals, each with a name. We have
seen several such error conditions through this manual:

`SIGSEGV`

-   This signal is generated when a program tries to read or write
    outside the memory that is allocated for it, or to write memory that
    can only be read. The name is an abbreviation for "segmentation
    violation".

`SIGFPE`

-   This signal indicates a fatal arithmetic error. The name is an
    abbreviation for "floating-point exception", but covers all types of
    arithmetic errors, including division by zero and overflow.

`SIGBUS`

-   This signal is generated when an invalid pointer is dereferenced,
    typically the result of dereferencing an uninintalized pointer. It
    is similar to `SIGSEGV`, except that `SIGSEGV` indicates invalid
    access to valid memory, while `SIGBUS` indicates an attempt to
    access an invalid address.

These kinds of signal allow the program to specify a function as a
*signal handler*. When a signal has a handler, it doesn't terminate the
program; instead it calls the handler.

There are many other kinds of signal; here we list only those that come
from run-time errors in C operations. The rest have to do with the
functioning of the operating system. The GNU C Library Reference Manual
gives more explanation about signals (see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Program-Signal-Handling.md#Program-Signal-Handling)
in The GNU C Library Reference Manual).

------------------------------------------------------------------------

Next: [GNU Free Documentation
License](GNU-Free-Documentation-License.md), Previous: [Attributes in
Declarations](Attributes.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
