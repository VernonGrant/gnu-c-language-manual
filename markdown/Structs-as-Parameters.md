Previous: [Arrays as Parameters](Arrays-as-Parameters.md), Up:
[Function Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.5 Functions That Accept Structure Arguments 

Structures in GNU C are first-class objects, so using them as function
parameters and arguments works in the natural way. This function
`swapfoo` takes a `struct foo` with two fields as argument, and returns
a structure of the same type but with the fields exchanged.

``` C
struct foo { int a, b; };

struct foo x;

struct foo
swapfoo (struct foo inval)
{
  struct foo outval;
  outval.a = inval.b;
  outval.b = inval.a;
  return outval;
}
```

This simpler definition of `swapfoo` avoids using a local variable to
hold the result about to be return, by using a structure constructor
(see [Structure Constructors](Structure-Constructors.md)), like this:

``` C
struct foo
swapfoo (struct foo inval)
{
  return (struct foo) { inval.b, inval.a };
}
```

It is valid to define a structure type in a function's parameter list,
as in

``` C
int
frob_bar (struct bar { int a, b; } inval)
{
  body
}
```

and `body`{.variable} can access the fields of `inval`{.variable} since
the structure type `struct bar` is defined for the whole function body.
However, there is no way to create a `struct bar` argument to pass to
`frob_bar`, except with kludges. As a result, defining a structure type
in a parameter list is useless in practice.
