Next: [Locally Declared Labels](Local-Labels.md), Previous: [Null
Statement](Null-Statement.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.12 `goto` Statement and Labels 


The `goto` statement looks like this:

``` C
goto label;
```

Its effect is to transfer control immediately to another part of the
current function---where the label named `label`{.variable} is defined.

An ordinary label definition looks like this:

``` C
label:
```

and it can appear before any statement. You can't use `default` as a
label, since that has a special meaning for `switch` statements.

An ordinary label doesn't need a separate declaration; defining it is
enough.

Here's an example of using `goto` to implement a loop equivalent to
`do`--`while`:

``` C
{
 loop_restart:
  body
  if (condition)
    goto loop_restart;
}
```

The name space of labels is separate from that of variables and
functions. Thus, there is no error in using a single name in both ways:

``` C
{
  int foo;    // Variable foo.
 foo:         // Label foo.
  body
  if (foo > 0)  // Variable foo.
    goto foo;   // Label foo.
}
```

Blocks have no effect on ordinary labels; each label name is defined
throughout the whole of the function it appears in. It looks strange to
jump into a block with `goto`, but it works. For example,

``` C
if (x < 0)
  goto negative;
if (y < 0)
  {
   negative:
    printf ("Negative\n");
    return;
  }
```

If the goto jumps into the scope of a variable, it does not initialize
the variable. For example, if `x` is negative,

``` C
if (x < 0)
  goto negative;
if (y < 0)
  {
    int i = 5;
   negative:
    printf ("Negative, and i is %d\n", i);
    return;
  }
```

prints junk because `i` was not initialized.

If the block declares a variable-length automatic array, jumping into it
gives a compilation error. However, jumping out of the scope of a
variable-length array works fine, and deallocates its storage.

A label can't come directly before a declaration, so the code can't jump
directly to one. For example, this is not allowed:

``` C
{
  goto foo;
foo:
  int x = 5;
  bar(&x);
}
```

The workaround is to add a statement, even an empty statement, directly
after the label. For example:

``` C
{
  goto foo;
foo:
  ;
  int x = 5;
  bar(&x);
}
```

Likewise, a label can't be the last thing in a block. The workaround
solution is the same: add a semicolon after the label.

These unnecessary restrictions on labels make no sense, and ought in
principle to be removed; but they do only a little harm since labels and
`goto` are rarely the best way to write a program.

These examples are all artificial; it would be more natural to write
them in other ways, without `goto`. For instance, the clean way to write
the example that prints '`Negative`' is this:

``` C
if (x < 0 || y < 0)
  {
    printf ("Negative\n");
    return;
  }
```

It is hard to construct simple examples where `goto` is actually the
best way to write a program. Its rare good uses tend to be in complex
code, thus not apt for the purpose of explaining the meaning of `goto`.

The only good time to use `goto` is when it makes the code simpler than
any alternative. Jumping backward is rarely desirable, because usually
the other looping and control constructs give simpler code. Using `goto`
to jump forward is more often desirable, for instance when a function
needs to do some processing in an error case and errors can occur at
various different places within the function.

------------------------------------------------------------------------

Next: [Locally Declared Labels](Local-Labels.md), Previous: [Null
Statement](Null-Statement.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
