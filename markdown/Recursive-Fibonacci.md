Next: [The Stack, And Stack Overflow](Stack.md), Up: [The First
Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 1.1 Example: Recursive Fibonacci 


To introduce the most basic features of C, let's look at code for a
simple mathematical function that does calculations on integers. This
function calculates the `n`th number in the Fibonacci series,
in which each number is the sum of the previous two: 1, 1, 2, 3, 5, 8,
13, 21, 34, 55, ....

``` C
int
fib (int n)
{
  if (n <= 2)  /* This avoids infinite recursion.  */
    return 1;
  else
    return fib (n - 1) + fib (n - 2);
}
```

This very simple program illustrates several features of C:

-   A function definition, whose first two lines constitute the function
    header. See [Function Definitions](Function-Definitions.md).

-   A function parameter `n`, referred to as the variable `n` inside the
    function body. See [Function Parameter
    Variables](Function-Parameter-Variables.md). A function definition
    uses parameters to refer to the argument values provided in a call
    to that function.

-   Arithmetic. C programs add with '`+`' and subtract with
    '`-`'. See [Arithmetic](Arithmetic.md).

-   Numeric comparisons. The operator '`<=`' tests for "less
    than or equal." See [Numeric Comparisons](Numeric-Comparisons.md).

-   Integer constants written in base 10. See [Integer
    Constants](Integer-Constants.md).

-   A function call. The function call `fib (n - 1)` calls the function
    `fib`, passing as its argument the value `n - 1`. See [Function
    Calls](Function-Calls.md).

-   A comment, which starts with '`/*`' and ends with
    '`*/`'. The comment has no effect on the execution of the
    program. Its purpose is to provide explanations to people reading
    the source code. Including comments in the code is tremendously
    important---they provide background information so others can
    understand the code more quickly. See [Comments](Comments.md).

    In this manual, we present comment text in the variable-width
    typeface used for the text of the chapters, not in the fixed-width
    typeface used for the rest of the code. That is to make comments
    easier to read. This distinction of typeface does not exist in a
    real file of C source code.

-   Two kinds of statements, the `return` statement and the
    `if`...`else` statement. See [Statements](Statements.md).

-   Recursion. The function `fib` calls itself; that is called a
    *recursive call*. These are valid in C, and quite common.

    The `fib` function would not be useful if it didn't return. Thus,
    recursive definitions, to be of any use, must avoid *infinite
    recursion*.

    This function definition prevents infinite recursion by specially
    handling the case where `n` is two or less. Thus the maximum depth
    of recursive calls is less than `n`.

```{=html}
<!-- -->
```
-   [Function Header](Function-Header.md)
-   [Function Body](Function-Body.md)

------------------------------------------------------------------------

Next: [The Stack, And Stack Overflow](Stack.md), Up: [The First
Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
