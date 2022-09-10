Next: [The `#elif` directive](elif.md), Previous: [The `defined`
test](defined.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.2.4 The `#else` directive 


The `#else` directive can be added to a conditional to provide
alternative text to be used if the condition fails. This is what it
looks like:

``` C
#if expression
text-if-true
#else /* Not expression */
text-if-false
#endif /* Not expression */
```

If `expression` is nonzero, the `text-if-true` is
included and the `text-if-false` is skipped. If
`expression` is zero, the opposite happens.

You can use `#else` with `#ifdef` and `#ifndef`, too.
