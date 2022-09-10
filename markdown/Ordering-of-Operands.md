Next: [Optimization and Ordering](Optimization-and-Ordering.md),
Previous: [Postincrement and Ordering](Postincrement-and-Ordering.md),
Up: [Order of Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.5 Ordering of Operands 


Operands and arguments can be computed in any order, but there are
limits to this intermixing in GNU C:

-   The operands of a binary arithmetic operator can be computed in
    either order, but they can't be intermixed: one of them has to come
    first, followed by the other. Any side effects in the operand that's
    computed first are executed before the other operand is computed.
-   That applies to assignment operators too, except that in simple
    assignment the previous value of the left operand is unused.
-   The arguments in a function call can be computed in any order, but
    they can't be intermixed. Thus, one argument is fully computed, then
    another, and so on until they are all done. Any side effects in one
    argument are executed before computation of another argument begins.

These rules don't cover side effects caused by postincrement and
postdecrement operators---those can be deferred up to the next sequence
point.

If you want to get pedantic, the fact is that GCC can reorder the
computations in many other ways provided that doesn't alter the result
of running the program. However, because they don't alter the result of
running the program, they are negligible, unless you are concerned with
the values in certain variables at various times as seen by other
processes. In those cases, you can use `volatile` to prevent
optimizations that would make them behave strangely. See [`volatile`
Variables and Fields](volatile.md).
