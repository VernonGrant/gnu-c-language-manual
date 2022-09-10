Previous: [`restrict`-Qualified Pointers](restrict-Pointers.md), Up:
[Type Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 21.4 `restrict` Pointer Example 

Here are examples where `restrict` enables real optimization.

In this example, `restrict` assures GCC that the array `out` points to
does not overlap with the array `in` points to.

``` C
void
process_data (const char *in,
              char * restrict out,
              size_t size)
{
  for (i = 0; i < size; i++)
    out[i] = in[i] + in[i + 1];
}
```

Here's a simple tree structure, where each tree node holds data of type
`PAYLOAD` plus two subtrees.

``` C
struct foo
  {
    PAYLOAD payload;
    struct foo *left;
    struct foo *right;
  };
```

Now here's a function to null out both pointers in the `left` subtree.

``` C
void
null_left (struct foo *a)
{
  a->left->left = NULL;
  a->left->right = NULL;
}
```

Since `*a` and `*a->left` have the same data type, they could
legitimately alias (see [Aliasing](Aliasing.md)). Therefore, the
compiled code for `null_left` must read `a->left` again from memory when
executing the second assignment statement.

We can enable optimization, so that it does not need to read `a->left`
again, by writing `null_left` in a less obvious way.

``` C
void
null_left (struct foo *a)
{
  struct foo *b = a->left;
  b->left = NULL;
  b->right = NULL;
}
```

A more elegant way to fix this is with `restrict`.

``` C
void
null_left (struct foo *restrict a)
{
  a->left->left = NULL;
  a->left->right = NULL;
}
```

Declaring `a` as `restrict` asserts that other pointers such as
`a->left` will not point to the same memory space as `a`. Therefore, the
memory location `a->left->left` cannot be the same memory as `a->left`.
Knowing this, the compiled code may avoid reloading `a->left` for the
second statement.
