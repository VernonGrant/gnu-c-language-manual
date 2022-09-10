Next: [Strings](Strings.md), Previous: [Accessing Array
Elements](Accessing-Array-Elements.md), Up: [Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.2 Declaring an Array 


To make an array declaration, write `[length]` after the name being
declared. This construct is valid in the declaration of a variable, a
function parameter, a function value type (the value can't be an array,
but it can be a pointer to one), a structure field, or a union
alternative.

The surrounding declaration specifies the element type of the array;
that can be any type of data, but not `void` or a function type. For
instance,

``` C
double a[5];
```

declares `a` as an array of 5 `double`s.

``` C
struct foo bstruct[length];
```

declares `bstruct` as an array of `length` objects of type `struct foo`.
A variable array size like this is allowed when the array is not
file-scope.

Other declaration constructs can nest within the array declaration
construct. For instance:

``` C
struct foo *b[length];
```

declares `b` as an array of `length` pointers to `struct foo`. This
shows that the length need not be a constant (see [Arrays of Variable
Length](Arrays-of-Variable-Length.md)).

``` C
double (*c)[5];
```

declares `c` as a pointer to an array of 5 `double`s, and

``` C
char *(*f (int))[5];
```

declares `f` as a function taking an `int` argument and returning a
pointer to an array of 5 strings (pointers to `char`s).

``` C
double aa[5][10];
```

declares `aa` as an array of 5 elements, each of which is an array of 10
`double`s. This shows how to declare a multidimensional array in C (see
[Multidimensional Arrays](Multidimensional-Arrays.md)).

All these declarations specify the array's length, which is needed in
these cases in order to allocate storage for the array.

------------------------------------------------------------------------

Next: [Strings](Strings.md), Previous: [Accessing Array
Elements](Accessing-Array-Elements.md), Up: [Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
