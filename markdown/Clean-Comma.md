Next: [When Not to Use the Comma Operator](Avoid-Comma.md), Previous:
[The Uses of the Comma Operator](Uses-of-Comma.md), Up: [Comma
Operator](Comma-Operator.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 8.5.2 Clean Use of the Comma Operator 

Always write parentheses around a series of comma operators, except when
it is at top level in an expression statement, or within the parentheses
of an `if`, `for`, `while`, or `switch` statement (see
[Statements](Statements.md)). For instance, in

``` C
for (i = 0, j = 10, k = 20; i < n; i++)
```

the commas between the assignments are clear because they are between a
parenthesis and a semicolon.

The arguments in a function call are also separated by commas, but that
is not an instance of the comma operator. Note the difference between

``` C
foo (4, 5, 6)
```

which passes three arguments to `foo` and

``` C
foo ((4, 5, 6))
```

which uses the comma operator and passes just one argument (with value
6).

**Warning:** don't use the comma operator around an argument of a
function unless it helps understand the code. When you do so, don't put
part of another argument on the same line. Instead, add a line break to
make the parentheses around the comma operator easier to see, like this.

``` C
foo ((mumble (x, y), frob (z)),
     *p)
```
