Next: [Example of `switch`](switch-Example.md), Previous: [Loop
Statements](Loop-Statements.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.7 `switch` Statement 


The `switch` statement selects code to run according to the value of an
expression. The expression, in parentheses, follows the keyword
`switch`. After that come all the cases to select among, inside braces.
It looks like this:

``` C
switch (selector)
  {
    cases…
  }
```

A case can look like this:

``` C
case value:
  statements
  break;
```

which means "come here if `selector`{.variable} happens to have the
value `value`{.variable}," or like this (a GNU C extension):

``` C
case rangestart ... rangeend:
  statements
  break;
```

which means "come here if `selector`{.variable} happens to have a value
between `rangestart`{.variable} and `rangeend`{.variable} (inclusive)."
See [Case Ranges](Case-Ranges.md).

The values in `case` labels must reduce to integer constants. They can
use arithmetic, and `enum` constants, but they cannot refer to data in
memory, because they have to be computed at compile time. It is an error
if two `case` labels specify the same value, or ranges that overlap, or
if one is a range and the other is a value in that range.

You can also define a default case to handle "any other value," like
this:

``` C
default:
  statements
  break;
```

If the `switch` statement has no `default:` label, then it does nothing
when the value matches none of the cases.

The brace-group inside the `switch` statement is a block, and you can
declare variables with that scope just as in any other block (see
[Blocks](Blocks.md)). However, initializers in these declarations
won't necessarily be executed every time the `switch` statement runs, so
it is best to avoid giving them initializers.

`break;` inside a `switch` statement exits immediately from the `switch`
statement. See [`break` Statement](break-Statement.md).

If there is no `break;` at the end of the code for a case, execution
continues into the code for the following case. This happens more often
by mistake than intentionally, but since this feature is used in real
code, we cannot eliminate it.

**Warning:** When one case is intended to fall through to the next,
write a comment like '`falls through`' to say it's intentional.
That way, other programmers won't assume it was an error and "fix" it
erroneously.

Consecutive `case` statements could, pedantically, be considered an
instance of falling through, but we don't consider or treat them that
way because they won't confuse anyone.

------------------------------------------------------------------------

Next: [Example of `switch`](switch-Example.md), Previous: [Loop
Statements](Loop-Statements.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
