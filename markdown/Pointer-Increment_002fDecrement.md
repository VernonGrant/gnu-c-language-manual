Next: [Drawbacks of Pointer
Arithmetic](Pointer-Arithmetic-Drawbacks.md), Previous: [Pointer
Arithmetic at Low-Level](Low_002dLevel-Pointer-Arithmetic.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.13 Pointer Increment and Decrement 


The '`++`' operator adds 1 to a variable. We have seen it for
integers (see [Increment and Decrement
Operators](Increment_002fDecrement.md)), but it works for pointers
too. For instance, suppose we have a series of positive integers,
terminated by a zero, and we want to add them up. Here is a simple way
to step forward through the array by advancing a pointer.

``` C
int
sum_array_till_0 (int *p)
{
  int sum = 0;

  for (;;)
    {
      /* Fetch the next integer.  */
      int next = *p++;
      /* Exit the loop if it’s 0.  */
      if (next == 0)
        break;
      /* Add it into running total.  */
      sum += next;
    }

  return sum;
}
```

The statement '`break;`' will be explained further on (see
[`break` Statement](break-Statement.md)). Used in this way, it
immediately exits the surrounding `for` statement.

`*p++` uses postincrement (`++`; see [Postincrement and
Postdecrement](Postincrement_002fPostdecrement.md)) on the pointer
`p`. that expression parses as `*(p++)`, because a postfix operator
always takes precedence over a prefix operator. Therefore, it
dereferences the entering value of `p`, then increments `p` afterwards.

Incrementing a variable means adding 1 to it, as in `p = p + 1`. Since
`p` is a pointer, adding 1 to it advances it by the width of the datum
it points to---in this case, `sizeof (int)`. Therefore, each iteration
of the loop picks up the next integer from the series and puts it into
`next`.

This `for`-loop has no initialization expression since `p` and `sum` are
already initialized, has no end-test since the '`break;`'
statement will exit it, and needs no expression to advance it since
that's done within the loop by incrementing `p` and `sum`. Thus, those
three expressions after `for` are left empty.

Another way to write this function is by keeping the parameter value
unchanged and using indexing to access the integers in the table.

``` C
int
sum_array_till_0_indexing (int *p)
{
  int i;
  int sum = 0;

  for (i = 0; ; i++)
    {
      /* Fetch the next integer.  */
      int next = p[i];
      /* Exit the loop if it’s 0.  */
      if (next == 0)
        break;
      /* Add it into running total.  */
      sum += next;
    }

  return sum;
}
```

In this program, instead of advancing `p`, we advance `i` and add it to
`p`. (Recall that `p[i]` means `*(p + i)`.) Either way, it uses the same
address to get the next integer.

It makes no difference in this program whether we write `i++` or `++i`,
because the value *of that expression* is not used. We use it for its
effect, to increment `i`.

The '`--`' operator also works on pointers; it can be used to
step backwards through an array, like this:

``` C
int
after_last_nonzero (int *p, int len)
{
  /* Set up q to point just after the last array element.  */
  int *q = p + len;

  while (q != p)
    /* Step q back until it reaches a nonzero element.  */
    if (*--q != 0)
      /* Return the index of the element after that nonzero.  */
      return q - p + 1;

  return 0;
}
```

That function returns the length of the nonzero part of the array
specified by its arguments; that is, the index of the first zero of the
run of zeros at the end.

------------------------------------------------------------------------

Next: [Drawbacks of Pointer
Arithmetic](Pointer-Arithmetic-Drawbacks.md), Previous: [Pointer
Arithmetic at Low-Level](Low_002dLevel-Pointer-Arithmetic.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
