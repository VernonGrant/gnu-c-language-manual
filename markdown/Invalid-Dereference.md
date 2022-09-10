Next: [Void Pointers](Void-Pointers.md), Previous: [Null
Pointers](Null-Pointers.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.7 Dereferencing Null or Invalid Pointers 

Trying to dereference a null pointer is an error. On most platforms, it
generally causes a signal, usually `SIGSEGV` (see
[Signals](Signals.md)).

``` C
char *foo = NULL;
c = *foo;    /* This causes a signal and terminates.  */
```

Likewise a pointer that has the wrong alignment for the target data type
(on most types of computer), or points to a part of memory that has not
been allocated in the process's address space.

The signal terminates the program, unless the program has arranged to
handle the signal (see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Signal-Handling.md#Signal-Handling)
in The GNU C Library Reference Manual).

However, the signal might not happen if the dereference is optimized
away. In the example above, if you don't subsequently use the value of
`c`, GCC might optimize away the code for `*foo`. You can prevent such
optimization using the `volatile` qualifier, as shown here:

``` C
volatile char *p;
volatile char c;
c = *p;
```

You can use this to test whether `p` points to unallocated memory. Set
up a signal handler first, so the signal won't terminate the program.
