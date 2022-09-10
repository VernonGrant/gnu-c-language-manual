Previous: [Function Header](Function-Header.md), Up: [Example:
Recursive Fibonacci](Recursive-Fibonacci.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 1.1.2 Function Body 


The rest of the function definition is called the *function body*. Like
every function body, this one starts with '`{`', ends with
'`}`', and contains zero or more *statements* and
*declarations*. Statements specify actions to take, whereas declarations
define names of variables, functions, and so on. Each statement and each
declaration ends with a semicolon ('`;`').

Statements and declarations often contain *expressions*; an expression
is a construct whose execution produces a *value* of some data type, but
may also take actions through "side effects" that alter subsequent
execution. A statement, by contrast, does not have a value; it affects
further execution of the program only through the actions it takes.

This function body contains no declarations, and just one statement, but
that one is a complex statement in that it contains nested statements.
This function uses two kinds of statements:

`return`

-   The `return` statement makes the function return immediately. It
    looks like this:

    
    ``` C
    return value;
    ```
    

    Its meaning is to compute the expression `value` and exit
    the function, making it return whatever value that expression
    produced. For instance,

    
    ``` C
    return 1;
    ```
    

    returns the integer 1 from the function, and

    
    ``` C
    return fib (n - 1) + fib (n - 2);
    ```
    

    returns a value computed by performing two function calls as
    specified and adding their results.

`if`...`else`

-   The `if`...`else` statement is a *conditional*. Each time it
    executes, it chooses one of its two substatements to execute and
    ignores the other. It looks like this:

    
    ``` C
    if (condition)
      if-true-statement
    else
      if-false-statement
    ```
    

    Its meaning is to compute the expression `condition` and,
    if it's "true," execute `if-true-statement`. Otherwise,
    execute `if-false-statement`. See [`if-else`
    Statement](if_002delse-Statement.md).

    Inside the `if`...`else` statement, `condition` is simply
    an expression. It's considered "true" if its value is nonzero. (A
    comparison operation, such as `n <= 2`, produces the value 1 if it's
    "true" and 0 if it's "false." See [Numeric
    Comparisons](Numeric-Comparisons.md).) Thus,

    
    ``` C
    if (n <= 2)
      return 1;
    else
      return fib (n - 1) + fib (n - 2);
    ```
    

    first tests whether the value of `n` is less than or equal to 2. If
    so, the expression `n <= 2` has the value 1. So execution continues
    with the statement

    
    ``` C
    return 1;
    ```
    

    Otherwise, execution continues with this statement:

    
    ``` C
    return fib (n - 1) + fib (n - 2);
    ```
    

    Each of these statements ends the execution of the function and
    provides a value for it to return. See [`return`
    Statement](return-Statement.md).

Calculating `fib` using ordinary integers in C works only for
`n` \< 47, because the value of `fib (47)` is too large to
fit in type `int`. The addition operation that tries to add `fib (46)`
and `fib (45)` cannot deliver the correct result. This occurrence is
called *integer overflow*.

Overflow can manifest itself in various ways, but one thing that can't
possibly happen is to produce the correct value, since that can't fit in
the space for the value. See [Integer Overflow](Integer-Overflow.md).

See [Functions](Functions.md), for a full explanation about functions.

------------------------------------------------------------------------

Previous: [Function Header](Function-Header.md), Up: [Example:
Recursive Fibonacci](Recursive-Fibonacci.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
