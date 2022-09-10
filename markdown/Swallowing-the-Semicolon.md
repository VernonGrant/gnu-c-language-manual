Next: [Duplication of Side Effects](Duplication-of-Side-Effects.md),
Previous: [Operator Precedence
Problems](Operator-Precedence-Problems.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.3 Swallowing the Semicolon 


Often it is desirable to define a macro that expands into a compound
statement. Consider, for example, the following macro, that advances a
pointer (the parameter `p` says where to find it) across whitespace
characters:

``` C
#define SKIP_SPACES(p, limit)  \
{ char *lim = (limit);         \
  while (p < lim) {            \
    if (*p++ != ' ') {         \
      p--; break; }}}
```

Here backslash-newline is used to split the macro definition, which must
be a single logical line, so that it resembles the way such code would
be laid out if not part of a macro definition.

A call to this macro might be `SKIP_SPACES (p, lim)`. Strictly speaking,
the call expands to a compound statement, which is a complete statement
with no need for a semicolon to end it. However, since it looks like a
function call, it minimizes confusion if you can use it like a function
call, writing a semicolon afterward, as in `SKIP_SPACES (p, lim);`

This can cause trouble before `else` statements, because the semicolon
is actually a null statement. Suppose you write

``` C
if (*p != 0)
  SKIP_SPACES (p, lim);
else /* … */
```

The presence of two statements---the compound statement and a null
statement---in between the `if` condition and the `else` makes invalid C
code.

The definition of the macro `SKIP_SPACES` can be altered to solve this
problem, using a `do … while` statement. Here is how:

``` C
#define SKIP_SPACES(p, limit)     \
do { char *lim = (limit);         \
     while (p < lim) {            \
       if (*p++ != ' ') {         \
         p--; break; }}}          \
while (0)
```

Now `SKIP_SPACES (p, lim);` expands into

``` C
do { /* … */ } while (0);
```

which is one statement. The loop executes exactly once; most compilers
generate no extra code for it.

------------------------------------------------------------------------

Next: [Duplication of Side Effects](Duplication-of-Side-Effects.md),
Previous: [Operator Precedence
Problems](Operator-Precedence-Problems.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
