Next: [Associativity and Ordering](Associativity-and-Ordering.md), Up:
[Order of Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.1 Reordering of Operands 


The C language does not necessarily carry out operations within an
expression in the order they appear in the code. For instance, in this
expression,

``` C
foo () + bar ()
```

`foo` might be called first or `bar` might be called first. If `foo`
updates a datum and `bar` uses that datum, the results can be
unpredictable.

The unpredictable order of computation of subexpressions also makes a
difference when one of them contains an assignment. We already saw this
example of bad code,

``` C
x = 20;
printf ("%d %d\n", x, x = 4);
```

in which the second argument, `x`, has a different value depending on
whether it is computed before or after the assignment in the third
argument.
