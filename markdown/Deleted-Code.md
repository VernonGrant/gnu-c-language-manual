Previous: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md), Up:
[Conditionals](Conditionals.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.3 Deleted Code 


If you replace or delete a part of the program but want to keep the old
code in the file for future reference, commenting it out is not so
straightforward in C. Block comments do not nest, so the first comment
inside the old code will end the commenting-out. The probable result is
a flood of syntax errors.

One way to avoid this problem is to use an always-false conditional
instead. For instance, put `#if 0` before the deleted code and `#endif`
after it. This works even if the code being turned off contains
conditionals, but they must be entire conditionals (balanced `#if` and
`#endif`).

Some people use `#ifdef notdef` instead. This is risky, because `notdef`
might be accidentally defined as a macro, and then the conditional would
succeed. `#if 0` can be counted on to fail.

Do not use `#if 0` around text that is not C code. Use a real comment,
instead. The interior of `#if 0` must consist of complete tokens; in
particular, single-quote characters must balance. Comments often contain
unbalanced single-quote characters (known in English as apostrophes).
These confuse `#if 0`. They don't confuse '`/*`'.
