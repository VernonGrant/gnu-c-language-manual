Previous: [The Stack, And Stack Overflow](Stack.md), Up: [The First
Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 1.3 Example: Iterative Fibonacci 


Here's a much faster algorithm for computing the same Fibonacci series.
It is faster for two reasons. First, it uses *iteration* (that is,
repetition or looping) rather than recursion, so it doesn't take time
for a large number of function calls. But mainly, it is faster because
the number of repetitions is small---only `n`.

``` C
int
fib (int n)
{
  int last = 1;   /* Initial value is fib (1).  */
  int prev = 0;   /* Initial value controls fib (2).  */
  int i;

  for (i = 1; i < n; ++i)
    /* If n is 1 or less, the loop runs zero times,  */
    /* since i < n is false the first time.  */
    {
      /* Now last is fib (i)
         and prev is fib (i - 1).  */
      /* Compute fib (i + 1).  */
      int next = prev + last;
      /* Shift the values down.  */
      prev = last;
      last = next;
      /* Now last is fib (i + 1)
         and prev is fib (i).
         But that won’t stay true for long,
         because we are about to increment i.  */
    }

  return last;
}
```

This definition computes `fib (n)` in a time proportional to `n`. The
comments in the definition explain how it works: it advances through the
series, always keeps the last two values in `last` and `prev`, and adds
them to get the next value.

Here are the additional C features that this definition uses:

Internal blocks

-   Within a function, wherever a statement is called for, you can write
    a *block*. It looks like `{ … }` and contains zero or more
    statements and declarations. (You can also use additional blocks as
    statements in a block.)

    The function body also counts as a block, which is why it can
    contain statements and declarations.

    See [Blocks](Blocks.md).

Declarations of local variables

-   This function body contains declarations as well as statements.
    There are three declarations directly in the function body, as well
    as a fourth declaration in an internal block. Each starts with `int`
    because it declares a variable whose type is integer. One
    declaration can declare several variables, but each of these
    declarations is simple and declares just one variable.

    Variables declared inside a block (either a function body or an
    internal block) are *local variables*. These variables exist only
    within that block; their names are not defined outside the block,
    and exiting the block deallocates their storage. This example
    declares four local variables: `last`, `prev`, `i`, and `next`.

    The most basic local variable declaration looks like this:

    
    ``` C
    type variablename;
    ```
    

    For instance,

    
    ``` C
    int i;
    ```
    

    declares the local variable `i` as an integer. See [Variable
    Declarations](Variable-Declarations.md).

Initializers

-   When you declare a variable, you can also specify its initial value,
    like this:

    
    ``` C
    type variablename = value;
    ```
    

    For instance,

    
    ``` C
    int last = 1;
    ```
    

    declares the local variable `last` as an integer (type `int`) and
    starts it off with the value 1. See
    [Initializers](Initializers.md).

Assignment

-   Assignment: a specific kind of expression, written with the
    '`=`' operator, that stores a new value in a variable or
    other place. Thus,

    
    ``` C
    variable = value
    ```
    

    is an expression that computes `value` and stores the value in
    `variable`. See [Assignment
    Expressions](Assignment-Expressions.md).

Expression statements

-   An expression statement is an expression followed by a semicolon.
    That computes the value of the expression, then ignores the value.

    An expression statement is useful when the expression changes some
    data or has other side effects---for instance, with function calls,
    or with assignments as in this example. See [Expression
    Statement](Expression-Statement.md).

    Using an expression with no side effects in an expression statement
    is pointless except in very special cases. For instance, the
    expression statement `x;` would examine the value of `x` and ignore
    it. That is not useful.

Increment operator

-   The increment operator is '`++`'. `++i` is an expression
    that is short for `i = i + 1`. See [Increment and Decrement
    Operators](Increment_002fDecrement.md).

`for` statements

-   A `for` statement is a clean way of executing a statement
    repeatedly---a *loop* (see [Loop Statements](Loop-Statements.md)).
    Specifically,

    
    ``` C
    for (i = 1; i < n; ++i)
      body
    ```
    

    means to start by doing `i = 1` (set `i` to one) to prepare for the
    loop. The loop itself consists of

    -   Testing `i < n` and exiting the loop if that's false.
    -   Executing `body`.
    -   Advancing the loop (executing `++i`, which increments `i`).

    The net result is to execute `body` with 1 in `i`, then
    with 2 in `i`, and so on, stopping just before the repetition where
    `i` would equal `n`. If `n` is less than 1, the loop will execute
    the body zero times.

    The body of the `for` statement must be one and only one statement.
    You can't write two statements in a row there; if you try to, only
    the first of them will be treated as part of the loop.

    The way to put multiple statements in such a place is to group them
    with a block, and that's what we do in this example.

------------------------------------------------------------------------

Previous: [The Stack, And Stack Overflow](Stack.md), Up: [The First
Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
