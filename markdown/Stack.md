Next: [Example: Iterative Fibonacci](Iterative-Fibonacci.md),
Previous: [Example: Recursive Fibonacci](Recursive-Fibonacci.md), Up:
[The First Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 1.2 The Stack, And Stack Overflow 


Recursion has a drawback: there are limits to how many nested function
calls a program can make. In C, each function call allocates a block of
memory which it uses until the call returns. C allocates these blocks
consecutively within a large area of memory known as the *stack*, so we
refer to the blocks as *stack frames*.

The size of the stack is limited; if the program tries to use too much,
that causes the program to fail because the stack is full. This is
called *stack overflow*.


Stack overflow on GNU/Linux typically manifests itself as the *signal*
named `SIGSEGV`, also known as a "segmentation fault." By default, this
signal terminates the program immediately, rather than letting the
program try to recover, or reach an expected ending point. (We commonly
say in this case that the program "crashes"). See
[Signals](Signals.md).

It is inconvenient to observe a crash by passing too large an argument
to recursive Fibonacci, because the program would run a long time before
it crashes. This algorithm is simple but ridiculously slow: in
calculating `fib (n)`, the number of (recursive) calls `fib (1)` or
`fib (2)` that it makes equals the final result.

However, you can observe stack overflow very quickly if you use this
function instead:

``` C
int
fill_stack (int n)
{
  if (n <= 1)  /* This limits the depth of recursion.  */
    return 1;
  else
    return fill_stack (n - 1);
}
```

Under gNewSense GNU/Linux on the Lemote Yeeloong, without optimization
and using the default configuration, an experiment showed there is
enough stack space to do 261906 nested calls to that function. One more,
and the stack overflows and the program crashes. On another platform,
with a different configuration, or with a different function, the limit
might be bigger or smaller.

------------------------------------------------------------------------

Next: [Example: Iterative Fibonacci](Iterative-Fibonacci.md),
Previous: [Example: Recursive Fibonacci](Recursive-Fibonacci.md), Up:
[The First Example](The-First-Example.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
