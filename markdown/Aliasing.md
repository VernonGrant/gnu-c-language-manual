Next: [Digraphs](Digraphs.md), Previous: [Type
Alignment](Type-Alignment.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## Appendix B Aliasing 


We have already presented examples of casting a `void *` pointer to
another pointer type, and casting another pointer type to `void *`.

One common kind of pointer cast is guaranteed safe: casting the value
returned by `malloc` and related functions (see [Dynamic Memory
Allocation](Dynamic-Memory-Allocation.md)). It is safe because these
functions do not save the pointer anywhere else; the only way the
program will access the newly allocated memory is via the pointer just
returned.

In fact, C allows casting any pointer type to any other pointer type.
Using this to access the same place in memory using two different data
types is called *aliasing*.

Aliasing is necessary in some programs that do sophisticated memory
management, such as GNU Emacs, but most C programs don't need to do
aliasing. When it isn't needed, **stay away from it!** To do aliasing
correctly requires following the rules stated below. Otherwise, the
aliasing may result in malfunctions when the program runs.

The rest of this appendix explains the pitfalls and rules of aliasing.

-   [Aliasing and Alignment](Aliasing-Alignment.md)
-   [Aliasing and Length](Aliasing-Length.md)
-   [Type Rules for Aliasing](Aliasing-Type-Rules.md)
