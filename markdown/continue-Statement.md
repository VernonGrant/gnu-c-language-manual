Previous: [`for`-Index Declarations](for_002dIndex-Declarations.md),
Up: [Loop Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.8 `continue` Statement 


The `continue` statement looks like '`continue;`', and its
effect is to jump immediately to the end of the innermost loop
construct. If it is a `for`-loop, the next thing that happens is to
execute the loop's `advance` expression.

For example, this loop increments `p` until the next null character or
newline, and operates (in some way not shown) on all the characters in
the line except for spaces. All it does with spaces is skip them.

``` C
for (;*p; ++p)
  {
    /* End loop if we have reached a newline.  */
    if (*p == '\n')
      break;
    /* Pay no attention to spaces.  */
    if (*p == ' ')
      continue;
    /* Operate on the next character.  */
    …
  }
```

Executing '`continue;`' skips the loop body but it does not
skip the `advance` expression, `p++`.

We could also write it like this:

``` C
for (;*p; ++p)
  {
    /* Exit if we have reached a newline.  */
    if (*p == '\n')
      break;
    /* Pay no attention to spaces.  */
    if (*p != ' ')
      {
        /* Operate on the next character.  */
        …
      }
  }
```

The advantage of using `continue` is that it reduces the depth of
nesting.

Contrast `continue` with the `break` statement. See [`break`
Statement](break-Statement.md).
