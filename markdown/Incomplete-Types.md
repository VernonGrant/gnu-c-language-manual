Next: [Intertwined Incomplete Types](Intertwined-Incomplete-Types.md),
Previous: [Unnamed Types as Fields](Unnamed-Types-as-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.18 Incomplete Types 


A type that has not been fully defined is called an *incomplete type*.
Structure and union types are incomplete when the code makes a forward
reference, such as `struct foo`, before defining the type. An array type
is incomplete when its length is unspecified.

You can't use an incomplete type to declare a variable or field, or use
it for a function parameter or return type. The operators `sizeof` and
`_Alignof` give errors when used on an incomplete type.

However, you can define a pointer to an incomplete type, and declare a
variable or field with such a pointer type. In general, you can do
everything with such pointers except dereference them. For example:

``` C
extern void bar (struct mysterious_value *);

void
foo (struct mysterious_value *arg)
{
  bar (arg);
}

…

{
  struct mysterious_value *p, **q;

  p = *q;
  foo (p);
}
```

These examples are valid because the code doesn't try to understand what
`p` points to; it just passes the pointer around. (Presumably `bar` is
defined in some other file that really does have a definition for
`struct mysterious_value`.) However, dereferencing the pointer would get
an error; that requires a definition for the structure type.
