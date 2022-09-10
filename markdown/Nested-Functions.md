Next: [Inline Function Definitions](Inline-Function-Definitions.md),
Previous: [Variable-Length Parameter
Lists](Variable-Number-of-Arguments.md), Up: [Advanced Function
Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.7.3 Nested Functions 


A *nested function* is a function defined inside another function. The
nested function's name is local to the block where it is defined. For
example, here we define a nested function named `square`, and call it
twice:

``` C
foo (double a, double b)
{
  double square (double z) { return z * z; }

  return square (a) + square (b);
}
```

The nested function can access all the variables of the containing
function that are visible at the point of its definition. This is called
*lexical scoping*. For example, here we show a nested function that uses
an inherited variable named `offset`:

``` C
bar (int *array, int offset, int size)
{
  int access (int *array, int index)
    { return array[index + offset]; }
  int i;
  …
  for (i = 0; i < size; i++)
    … access (array, i) …
}
```

Nested function definitions can appear wherever automatic variable
declarations are allowed; that is, in any block, interspersed with the
other declarations and statements in the block.

The nested function's name is visible only within the parent block; the
name's scope starts from its definition and continues to the end of the
containing block. If the nested function's name is the same as the
parent function's name, there wil be no way to refer to the parent
function inside the scope of the name of the nested function.

Using `extern` or `static` on a nested function definition is an error.

It is possible to call the nested function from outside the scope of its
name by storing its address or passing the address to another function.
You can do this safely, but you must be careful:

``` C
hack (int *array, int size, int addition)
{
  void store (int index, int value)
    { array[index] = value + addition; }

  intermediate (store, size);
}
```

Here, the function `intermediate` receives the address of `store` as an
argument. If `intermediate` calls `store`, the arguments given to
`store` are used to store into `array`. `store` also accesses `hack`'s
local variable `addition`.

It is safe for `intermediate` to call `store` because `hack`'s stack
frame, with its arguments and local variables, continues to exist during
the call to `intermediate`.

Calling the nested function through its address after the containing
function has exited is asking for trouble. If it is called after a
containing scope level has exited, and if it refers to some of the
variables that are no longer in scope, it will refer to memory
containing junk or other data. It's not wise to take the risk.

The GNU C Compiler implements taking the address of a nested function
using a technique called *trampolines*. This technique was described in
Lexical Closures for C++ (Thomas M. Breuel, USENIX C++ Conference
Proceedings, October 17--21, 1988).

A nested function can jump to a label inherited from a containing
function, provided the label was explicitly declared in the containing
function (see [Locally Declared Labels](Local-Labels.md)). Such a jump
returns instantly to the containing function, exiting the nested
function that did the `goto` and any intermediate function invocations
as well. Here is an example:

``` C
bar (int *array, int offset, int size)
{
  /* Explicitly declare the label failure. */
  __label__ failure;
  int access (int *array, int index)
    {
      if (index > size)
        /* Exit this function,
           and return to bar. */
        goto failure;
      return array[index + offset];
    }
```

``` C
```

``` C
  int i;
  …
  for (i = 0; i < size; i++)
    … access (array, i) …
  …
  return 0;

 /* Control comes here from access
    if it does the goto.  */
 failure:
  return -1;
}
```

To declare the nested function before its definition, use `auto` (which
is otherwise meaningless for function declarations; see [`auto` and
`register`](auto-and-register.md)). For example,

``` C
bar (int *array, int offset, int size)
{
  auto int access (int *, int);
  …
  … access (array, i) …
  …
  int access (int *array, int index)
    {
      …
    }
  …
}
```

------------------------------------------------------------------------

Next: [Inline Function Definitions](Inline-Function-Definitions.md),
Previous: [Variable-Length Parameter
Lists](Variable-Number-of-Arguments.md), Up: [Advanced Function
Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
