Previous: [Conditional Expression](Conditional-Expression.md), Up:
[Execution Control Expressions](Execution-Control-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 8.5 Comma Operator 


The comma operator stands for sequential execution of expressions. The
value of the comma expression comes from the last expression in the
sequence; the previous expressions are computed only for their side
effects. It looks like this:

``` C
exp1, exp2 …
```

You can bundle any number of expressions together this way, by putting
commas between them.

-   [The Uses of the Comma Operator](Uses-of-Comma.md)
-   [Clean Use of the Comma Operator](Clean-Comma.md)
-   [When Not to Use the Comma Operator](Avoid-Comma.md)
