Next: [Omitted `for`-Expressions](Omitted-for_002dExpressions.md),
Previous: [`for` Statement](for-Statement.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.5 Example of `for` 

Here is the `for` statement from the iterative Fibonacci function:

``` C
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
```

In this example, `start` is `i = 1`, meaning set `i` to 1.
`continue-test` is `i < n`, meaning keep repeating the loop
as long as `i` is less than `n`. `advance` is `i++`, meaning
increment `i` by 1. The body is a block that contains a declaration and
two statements.
