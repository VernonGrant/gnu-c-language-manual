Next: [`if` Statement](if-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.1 Expression Statement 


The most common kind of statement in C is an *expression statement*. It
consists of an expression followed by a semicolon. The expression's
value is discarded, so the expressions that are useful are those that
have side effects: assignment expressions, increment and decrement
expressions, and function calls. Here are examples of expression
statements:

``` C
x = 5;              /* Assignment expression. */
p++;                /* Increment expression. */
printf ("Done\n");  /* Function call expression. */
*p;                 /* Cause SIGSEGV signal if p is null. */
x + y;              /* Useless statement without effect. */
```

In very unusual circumstances we use an expression statement whose
purpose is to get a fault if an address is invalid:

``` C
volatile char *p;
…
*p;                 /* Cause signal if p is null. */
```

If the target of `p` is not declared `volatile`, the compiler might
optimize away the memory access, since it knows that the value isn't
really used. See [`volatile` Variables and Fields](volatile.md).
