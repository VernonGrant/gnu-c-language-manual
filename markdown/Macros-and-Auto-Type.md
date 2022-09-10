Next: [Self-Referential Macros](Self_002dReferential-Macros.md),
Previous: [Duplication of Side
Effects](Duplication-of-Side-Effects.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.5 Using `__auto_type` for Local Variables 


The operator `__auto_type` makes it possible to define macros that can
work on any data type even though they need to generate local variable
declarations. See [Referring to a Type with
`__auto_type`](Auto-Type.md).

For instance, here's how to define a safe "maximum" macro that operates
on any arithmetic type and computes each of its arguments exactly once:

``` C
#define max(a,b) \
  ({ __auto_type _a = (a); \
      __auto_type _b = (b); \
    _a > _b ? _a : _b; })
```

The '`({ … })`' notation produces *statement expression*---a
statement that can be used as an expression (see [Statements and
Declarations in Expressions](Statement-Exprs.md)). Its value is the
value of its last statement. This permits us to define local variables
and store each argument value into one.


The reason for using names that start with underscores for the local
variables is to avoid conflicts with variable names that occur within
the expressions that are substituted for `a` and `b`. Underscore
followed by a lower case letter won't be predefined by the system in any
way.
