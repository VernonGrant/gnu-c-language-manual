Next: [Function Call Semantics](Function-Call-Semantics.md), Previous:
[Function Declarations](Function-Declarations.md), Up:
[Functions](Functions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 22.3 Function Calls 


Starting a program automatically calls the function named `main` (see
[The `main` Function](The-main-Function.md)). Aside from that, a
function does nothing except when it is *called*. That occurs during the
execution of a function-call expression specifying that function.

A function-call expression looks like this:

``` C
function (arguments…)
```

Most of the time, `function` is a function name. However, it
can also be an expression with a function pointer value; that way, the
program can determine at run time which function to call.

The `arguments` are a series of expressions separated by
commas. Each expression specifies one argument to pass to the function.

The list of arguments in a function call looks just like use of the
comma operator (see [Comma Operator](Comma-Operator.md)), but the fact
that it fills the parentheses of a function call gives it a different
meaning.

Here's an example of a function call, taken from an example near the
beginning (see [A Complete Program](Complete-Program.md)).

``` C
printf ("Fibonacci series item %d is %d\n",
        19, fib (19));
```

The three arguments given to `printf` are a constant string, the integer
19, and the integer returned by `fib (19)`.
