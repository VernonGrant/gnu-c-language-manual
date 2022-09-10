Next: [Argument Prescan](Argument-Prescan.md), Previous: [Using
`__auto_type` for Local Variables](Macros-and-Auto-Type.md), Up:
[Macro Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.6 Self-Referential Macros 


A *self-referential* macro is one whose name appears in its definition.
Recall that all macro definitions are rescanned for more macros to
replace. If the self-reference were considered a use of the macro, it
would produce an infinitely large expansion. To prevent this, the
self-reference is not considered a macro call: preprocessing leaves it
unchanged. Consider an example:

``` C
#define foo (4 + foo)
```

where `foo` is also a variable in your program.

Following the ordinary rules, each reference to `foo` will expand into
`(4 + foo)`; then this will be rescanned and will expand into
`(4 + (4 + foo))`; and so on until the computer runs out of memory.

The self-reference rule cuts this process short after one step, at
`(4 + foo)`. Therefore, this macro definition has the possibly useful
effect of causing the program to add 4 to the value of `foo` wherever
`foo` is referred to.

In most cases, it is a bad idea to take advantage of this feature. A
person reading the program who sees that `foo` is a variable will not
expect that it is a macro as well. The reader will come across the
identifier `foo` in the program and think its value should be that of
the variable `foo`, whereas in fact the value is four greater.

It is useful to make a macro definition that expands to the macro name
itself. If you write

``` C
#define EPERM EPERM
```

then the macro `EPERM` expands to `EPERM`. Effectively, preprocessing
leaves it unchanged in the source code. You can tell that it's a macro
with `#ifdef`. You might do this if you want to define numeric constants
with an `enum`, but have `#ifdef` be true for each constant.

If a macro `x` expands to use a macro `y`, and the expansion of `y`
refers to the macro `x`, that is an *indirect self-reference* of `x`.
`x` is not expanded in this case either. Thus, if we have

``` C
#define x (4 + y)
#define y (2 * x)
```

then `x` and `y` expand as follows:

``` C
x    → (4 + y)
     → (4 + (2 * x))

y    → (2 * x)
     → (2 * (4 + y))
```

Each macro is expanded when it appears in the definition of the other
macro, but not when it indirectly appears in its own definition.

------------------------------------------------------------------------

Next: [Argument Prescan](Argument-Prescan.md), Previous: [Using
`__auto_type` for Local Variables](Macros-and-Auto-Type.md), Up:
[Macro Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
