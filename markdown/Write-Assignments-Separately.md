Previous: [Pitfall: Assignment in
Subexpressions](Assignment-in-Subexpressions.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.7 Write Assignments in Separate Statements 

It is often convenient to write an assignment inside an `if`-condition,
but that can reduce the readability of the program. Here's an example of
what to avoid:

``` C
if (x = advance (x))
  …
```

The idea here is to advance `x` and test if the value is nonzero.
However, readers might miss the fact that it uses '`=`' and not
'`==`'. In fact, writing '`=`' where '`==`'
was intended inside a condition is a common error, so GNU C can give
warnings when '`=`' appears in a way that suggests it's an
error.

It is much clearer to write the assignment as a separate statement, like
this:

``` C
x = advance (x);
if (x != 0)
  …
```

This makes it unmistakably clear that `x` is assigned a new value.

Another method is to use the comma operator (see [Comma
Operator](Comma-Operator.md)), like this:

``` C
if (x = advance (x), x != 0)
  …
```

However, putting the assignment in a separate statement is usually
clearer unless the assignment is very short, because it reduces nesting.
