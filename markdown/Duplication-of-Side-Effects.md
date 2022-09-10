Next: [Using `__auto_type` for Local
Variables](Macros-and-Auto-Type.md), Previous: [Swallowing the
Semicolon](Swallowing-the-Semicolon.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.4 Duplication of Side Effects 


Many C programs define a macro `min`, for "minimum", like this:

``` C
#define min(X, Y)  ((X) < (Y) ? (X) : (Y))
```

When you use this macro with an argument containing a side effect, as
shown here,

``` C
next = min (x + y, foo (z));
```

it expands as follows:

``` C
next = ((x + y) < (foo (z)) ? (x + y) : (foo (z)));
```

where `x + y` has been substituted for `X` and `foo (z)` for `Y`.

The function `foo` is used only once in the statement as it appears in
the program, but the expression `foo (z)` has been substituted twice
into the macro expansion. As a result, `foo` might be called twice when
the statement is executed. If it has side effects or if it takes a long
time to compute, that may be undesirable. We say that `min` is an
*unsafe* macro.

The best solution to this problem is to define `min` in a way that
computes the value of `foo (z)` only once. In general, that requires
using `__auto_type` (see [Referring to a Type with
`__auto_type`](Auto-Type.md)). How to use it for this is described in
the following section. See [Using `__auto_type` for Local
Variables](Macros-and-Auto-Type.md).

Otherwise, you will need to be careful when *using* the macro `min`. For
example, you can calculate the value of `foo (z)`, save it in a
variable, and use that variable in `min`:

``` C
#define min(X, Y)  ((X) < (Y) ? (X) : (Y))
/* … */
{
  int tem = foo (z);
  next = min (x + y, tem);
}
```

(where we assume that `foo` returns type `int`).

When the repeated value appears as the condition of the `?:` operator
and again as its `iftrue` expression, you can avoid repeated
execution by omitting the `iftrue` expression, like this:

``` C
#define x_or_y(X, Y)  ((X) ? : (Y))
```

In GNU C, this expands to use the first macro argument's value if that
isn't zero. If that's zero, it compiles the second argument and uses
that value. See [Conditional Expression](Conditional-Expression.md).

------------------------------------------------------------------------

Next: [Using `__auto_type` for Local
Variables](Macros-and-Auto-Type.md), Previous: [Swallowing the
Semicolon](Swallowing-the-Semicolon.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
