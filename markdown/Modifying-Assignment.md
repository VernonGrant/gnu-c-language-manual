Next: [Increment and Decrement Operators](Increment_002fDecrement.md),
Previous: [Lvalues](Lvalues.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.3 Modifying Assignment 


You can abbreviate the common construct

``` C
lvalue = lvalue + expression
```

as

``` C
lvalue += expression
```

This is known as a *modifying assignment*. For instance,

``` C
i = i + 5;
i += 5;
```

shows two statements that are equivalent. The first uses simple
assignment; the second uses modifying assignment.

Modifying assignment works with any binary arithmetic operator. For
instance, you can subtract something from an lvalue like this,

``` C
lvalue -= expression
```

or multiply it by a certain amount like this,

``` C
lvalue *= expression
```

or shift it by a certain amount like this.

``` C
lvalue <<= expression
lvalue >>= expression
```

In most cases, this feature adds no power to the language, but it
provides substantial convenience. Also, when `lvalue`{.variable}
contains code that has side effects, the simple assignment performs
those side effects twice, while the modifying assignment performs them
once. For instance,

``` C
x[foo ()] = x[foo ()] + 5;
```

calls `foo` twice, and it could return different values each time. If
`foo ()` returns 1 the first time and 3 the second time, then the effect
could be to add `x[3]` and 5 and store the result in `x[1]`, or to add
`x[1]` and 5 and store the result in `x[3]`. We don't know which of the
two it will do, because C does not specify which call to `foo` is
computed first.

Such a statement is not well defined, and shouldn't be used.

By contrast,

``` C
x[foo ()] += 5;
```

is well defined: it calls `foo` only once to determine which element of
`x` to adjust, and it adjusts that element by adding 5 to it.

------------------------------------------------------------------------

Next: [Increment and Decrement Operators](Increment_002fDecrement.md),
Previous: [Lvalues](Lvalues.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
