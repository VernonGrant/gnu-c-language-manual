Next: [Labels as Values](Labels-as-Values.md), Previous: [`goto`
Statement and Labels](goto-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.13 Locally Declared Labels 


In GNU C you can declare *local labels* in any nested block scope. A
local label is used in a `goto` statement just like an ordinary label,
but you can only reference it within the block in which it was declared.

A local label declaration looks like this:

``` C
__label__ label;
```

or

``` C
__label__ label1, label2, …;
```

Local label declarations must come at the beginning of the block, before
any ordinary declarations or statements.

The label declaration declares the label *name*, but does not define the
label itself. That's done in the usual way, with `label:`, before one of
the statements in the block.

The local label feature is useful for complex macros. If a macro
contains nested loops, a `goto` can be useful for breaking out of them.
However, an ordinary label whose scope is the whole function cannot be
used: if the macro can be expanded several times in one function, the
label will be multiply defined in that function. A local label avoids
this problem. For example:

``` C
#define SEARCH(value, array, target)              \
do {                                              \
  __label__ found;                                \
  __auto_type _SEARCH_target = (target);          \
  __auto_type _SEARCH_array = (array);            \
  int i, j;                                       \
  int value;                                      \
  for (i = 0; i < max; i++)                       \
    for (j = 0; j < max; j++)                     \
      if (_SEARCH_array[i][j] == _SEARCH_target)  \
        { (value) = i; goto found; }              \
  (value) = -1;                                   \
 found:;                                          \
} while (0)
```

This could also be written using a statement expression (see [Statements
and Declarations in Expressions](Statement-Exprs.md)):

``` C
#define SEARCH(array, target)                     \
({                                                \
  __label__ found;                                \
  __auto_type _SEARCH_target = (target);      \
  __auto_type _SEARCH_array = (array);     \
  int i, j;                                       \
  int value;                                      \
  for (i = 0; i < max; i++)                       \
    for (j = 0; j < max; j++)                     \
      if (_SEARCH_array[i][j] == _SEARCH_target)  \
        { value = i; goto found; }                \
  value = -1;                                     \
 found:                                           \
  value;                                          \
})
```

Ordinary labels are visible throughout the function where they are
defined, and only in that function. However, explicitly declared local
labels of a block are visible in nested function definitions inside that
block. See [Nested Functions](Nested-Functions.md), for details.

See [`goto` Statement and Labels](goto-Statement.md).

------------------------------------------------------------------------

Next: [Labels as Values](Labels-as-Values.md), Previous: [`goto`
Statement and Labels](goto-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
