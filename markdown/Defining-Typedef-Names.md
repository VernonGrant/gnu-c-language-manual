Next: [Statements](Statements.md), Previous: [Enumeration
Types](Enumeration-Types.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 18 Defining Typedef Names 


You can define a data type keyword as an alias for any type, and then
use the alias syntactically like a built-in type keyword such as `int`.
You do this using `typedef`, so these aliases are also called *typedef
names*.

`typedef` is followed by text that looks just like a variable
declaration, but instead of declaring variables it defines data type
keywords.

Here's how to define `fooptr` as a typedef alias for the type
`struct foo *`, then declare `x` and `y` as variables with that type:

``` C
typedef struct foo *fooptr;

fooptr x, y;
```

That declaration is equivalent to the following one:

``` C
struct foo *x, *y;
```

You can define a typedef alias for any type. For instance, this makes
`frobcount` an alias for type `int`:

``` C
typedef int frobcount;
```

This doesn't define a new type distinct from `int`. Rather, `frobcount`
is another name for the type `int`. Once the variable is declared, it
makes no difference which name the declaration used.

There is a syntactic difference, however, between `frobcount` and `int`:
A typedef name cannot be used with `signed`, `unsigned`, `long` or
`short`. It has to specify the type all by itself. So you can't write
this:

``` C
unsigned frobcount f1;  /* Error! */
```

But you can write this:

``` C
typedef unsigned int unsigned_frobcount;

unsigned_frobcount f1;
```

In other words, a typedef name is not an alias for *a keyword* such as
`int`. It stands for a *type*, and that could be the type `int`.

Typedef names are in the same namespace as functions and variables, so
you can't use the same name for a typedef and a function, or a typedef
and a variable. When a typedef is declared inside a code block, it is in
scope only in that block.

**Warning:** Avoid defining typedef names that end in '`_t`',
because many of these have standard meanings.

You can redefine a typedef name to the exact same type as its first
definition, but you cannot redefine a typedef name to a different type,
even if the two types are compatible. For example, this is valid:

``` C
typedef int frobcount;
typedef int frotzcount;
typedef frotzcount frobcount;
typedef frobcount frotzcount;
```

because each typedef name is always defined with the same type (`int`),
but this is not valid:

``` C
enum foo {f1, f2, f3};
typedef enum foo frobcount;
typedef int frobcount;
```

Even though the type `enum foo` is compatible with `int`, they are not
the *same* type.

------------------------------------------------------------------------

Next: [Statements](Statements.md), Previous: [Enumeration
Types](Enumeration-Types.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
