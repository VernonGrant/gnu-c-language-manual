Next: [`extern` Declarations](Extern-Declarations.md), Previous:
[File-Scope Variables](File_002dScope-Variables.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.7 Static Local Variables 


The keyword `static` in a local variable declaration says to allocate
the storage for the variable permanently, just like a file-scope
variable, even if the declaration is within a function.

Here's an example:

``` C
int
increment_counter ()
{
  static int counter = 0;
  return ++counter;
}
```

The scope of the name `counter` runs from the declaration to the end of
the containing block, just like an automatic local variable, but its
storage is permanent, so the value persists from one call to the next.
As a result, each call to `increment_counter` returns a different,
unique value.

The initial value of a static local variable has the same limitations as
for file-scope variables: it can't depend on the contents of storage or
call any functions. It can use the address of a file-scope variable or a
static local variable, because those addresses are determined before the
program runs.
