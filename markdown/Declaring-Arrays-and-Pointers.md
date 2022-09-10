Next: [Combining Variable
Declarations](Combining-Variable-Declarations.md), Up: [Variable
Declarations](Variable-Declarations.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 20.1.1 Declaring Arrays and Pointers 


To declare a variable that is an array, write `variable[length]` for
`decorated-variable`:

``` C
int foo[5];
```

To declare a variable that has a pointer type, write `*variable` for
`decorated-variable`:

``` C
struct list_elt *foo;
```

These constructs nest. For instance,

``` C
int foo[3][5];
```

declares `foo` as an array of 3 arrays of 5 integers each,

``` C
struct list_elt *foo[5];
```

declares `foo` as an array of 5 pointers to structures, and

``` C
struct list_elt **foo;
```

declares `foo` as a pointer to a pointer to a structure.

``` C
int **(*foo[30])(int, double);
```

declares `foo` as an array of 30 pointers to functions (see [Function
Pointers](Function-Pointers.md)), each of which must accept two
arguments (one `int` and one `double`) and return type `int **`.

``` C
void
bar (int size)
{
  int foo[size];
  …
}
```

declares `foo` as an array of integers with a size specified at run time
when the function `bar` is called.
