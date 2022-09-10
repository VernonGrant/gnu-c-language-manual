Next: [Static Local Variables](Static-Local-Variables.md), Previous:
[Local Variables](Local-Variables.md), Up: [Variables](Variables.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.6 File-Scope Variables 


A variable declaration at the top level in a file (not inside a function
definition) declares a *file-scope variable*. Loading a program
allocates the storage for all the file-scope variables in it, and
initializes them too.

Each file-scope variable is either *static* (limited to one compilation
module) or *global* (shared with all compilation modules in the
program). To make the variable static, write the keyword `static` at the
start of the declaration. Omitting `static` makes the variable global.

The initial value for a file-scope variable can't depend on the contents
of storage, and can't call any functions.

``` C
int foo = 5;         /* Valid. */
int bar = foo;       /* Invalid! */
int bar = sin (1.0); /* Invalid! */
```

But it can use the address of another file-scope variable:

``` C
int foo;
int *bar = &foo;     /* Valid. */
int arr[5];
int *bar3 = &arr[3]; /* Valid. */
int *bar4 = arr + 4; /* Valid. */
```

It is valid for a module to have multiple declarations for a file-scope
variable, as long as they are all global or all static, but at most one
declaration can specify an initial value for it.
