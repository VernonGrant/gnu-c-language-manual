Next: [Conditional Expression](Conditional-Expression.md), Previous:
[Logical Operators and Comparisons](Logicals-and-Comparison.md), Up:
[Execution Control Expressions](Execution-Control-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 8.3 Logical Operators and Assignments 

There are cases where assignments nested inside the condition can
actually make a program *easier* to read. Here is an example using a
hypothetical type `list` which represents a list; it tests whether the
list has at least two links, using hypothetical functions, `nonempty`
which is true if the argument is a nonempty list, and `list_next` which
advances from one list link to the next. We assume that a list is never
a null pointer, so that the assignment expressions are always "true."

``` C
if (nonempty (list)
    && (temp1 = list_next (list))
    && nonempty (temp1)
    && (temp2 = list_next (temp1)))
  …  /* use temp1 and temp2 */
```

Here we take advantage of the '`&&`' operator to avoid
executing the rest of the code if a call to `nonempty` returns "false."
The only natural place to put the assignments is among those calls.

It would be possible to rewrite this as several statements, but that
could make it much more cumbersome. On the other hand, when the test is
even more complex than this one, splitting it into multiple statements
might be necessary for clarity.

If an empty list is a null pointer, we can dispense with calling
`nonempty`:

``` C
if ((temp1 = list_next (list))
    && (temp2 = list_next (temp1)))
 …
```
