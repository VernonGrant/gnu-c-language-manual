Next: [`do-while` Statement](do_002dwhile-Statement.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.1 `while` Statement 


The `while` statement is the simplest loop construct. It looks like
this:

``` C
while (test)
  body
```

Here, `body` is a statement (often a nested block) to repeat,
and `test` is the test expression that controls whether to
repeat it again. Each iteration of the loop starts by computing
`test` and, if it is true (nonzero), that means the loop
should execute `body` again and then start over.

Here's an example of advancing to the last structure in a chain of
structures chained through the `next` field:

``` C
#include <stddef.h> /* Defines NULL. */
…
while (chain->next != NULL)
  chain = chain->next;
```

This code assumes the chain isn't empty to start with; if the chain is
empty (that is, if `chain` is a null pointer), the code gets a `SIGSEGV`
signal trying to dereference that null pointer (see
[Signals](Signals.md)).
