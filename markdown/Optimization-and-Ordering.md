Previous: [Ordering of Operands](Ordering-of-Operands.md), Up: [Order
of Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.6 Optimization and Ordering 


Sequence points limit the compiler's freedom to reorder operations
arbitrarily, but optimizations can still reorder them if the compiler
concludes that this won't alter the results. Thus, in this code,

``` C
x++;
y = z;
x++;
```

there is a sequence point after each statement, so the code is supposed
to increment `x` once before the assignment to `y` and once after.
However, incrementing `x` has no effect on `y` or `z`, and setting `y`
can't affect `x`, so the code could be optimized into this:

``` C
y = z;
x += 2;
```

Normally that has no effect except to make the program faster. But there
are special situations where it can cause trouble due to things that the
compiler cannot know about, such as shared memory. To limit optimization
in those places, use the `volatile` type qualifier (see [`volatile`
Variables and Fields](volatile.md)).
