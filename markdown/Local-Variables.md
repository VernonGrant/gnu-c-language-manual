Next: [File-Scope Variables](File_002dScope-Variables.md), Previous:
[Referring to a Type with `__auto_type`](Auto-Type.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.5 Local Variables 


Declaring a variable inside a function definition (see [Function
Definitions](Function-Definitions.md)) makes the variable name *local*
to the containing block---that is, the containing pair of braces. More
precisely, the variable's name is visible starting just after where it
appears in the declaration, and its visibility continues until the end
of the block.

Local variables in C are generally *automatic* variables: each
variable's storage exists only from the declaration to the end of the
block. Execution of the declaration allocates the storage, computes the
initial value, and stores it in the variable. The end of the block
deallocates the storage.[^6^](#FOOT6)

**Warning:** Two declarations for the same local variable in the same
scope are an error.

**Warning:** Automatic variables are stored in the run-time stack. The
total space for the program's stack may be limited; therefore, in using
very large arrays, it may be necessary to allocate them in some other
way to stop the program from crashing.

**Warning:** If the declaration of an automatic variable does not
specify an initial value, the variable starts out containing garbage. In
this example, the value printed could be anything at all:

``` C
{
  int i;

  printf ("Print junk %d\n", i);
}
```

In a simple test program, that statement is likely to print 0, simply
because every process starts with memory zeroed. But don't rely on it to
be zero---that is erroneous.

**Note:** Make sure to store a value into each local variable (by
assignment, or by initialization) before referring to its value.


------------------------------------------------------------------------

#### Footnotes 

##### [(6)](#DOCF6)

Due to compiler optimizations, allocation and deallocation don't
necessarily really happen at those times.

------------------------------------------------------------------------

Next: [File-Scope Variables](File_002dScope-Variables.md), Previous:
[Referring to a Type with `__auto_type`](Auto-Type.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
