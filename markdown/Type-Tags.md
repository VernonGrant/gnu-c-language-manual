Previous: [Intertwined Incomplete
Types](Intertwined-Incomplete-Types.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.20 Type Tags 


The name that follows `struct` (see [Structures](Structures.md)),
`union` (see [Unions](Unions.md), or `enum` (see [Enumeration
Types](Enumeration-Types.md)) is called a *type tag*. In C, a type tag
never conflicts with a variable name or function name; the type tags
have a separate *name space*. Thus, there is no name conflict in this
code:

``` C
struct pair { int a, b; };
int pair = 1;
```

nor in this one:

``` C
struct pair { int a, b; } pair;
```

where `pair` is both a structure type tag and a variable name.

However, `struct`, `union`, and `enum` share the same name space of
tags, so this is a conflict:

``` C
struct pair { int a, b; };
enum pair { c, d };
```

and so is this:

``` C
struct pair { int a, b; };
struct pair { int c, d; };
```

When the code defines a type tag inside a block, the tag's scope is
limited to that block (as for local variables). Two definitions for one
type tag do not conflict if they are in different scopes; rather, each
is valid in its scope. For example,

``` C
struct pair { int a, b; };

void
pair_up_doubles (int len, double array[])
{
  struct pair { double a, b; };
  …
}
```

has two definitions for `struct pair` which do not conflict. The one
inside the function applies only within the definition of
`pair_up_doubles`. Within its scope, that definition *shadows* the outer
definition.

If `struct pair` appears inside the function body, before the inner
definition, it refers to the outer definition---the only one that has
been seen at that point. Thus, in this code,

``` C
struct pair { int a, b; };

void
pair_up_doubles (int len, double array[])
{
  struct two_pairs { struct pair *p, *q; };
  struct pair { double a, b; };
  …
}
```

the structure `two_pairs` has pointers to the outer definition of
`struct pair`, which is probably not desirable.

To prevent that, you can write `struct pair;` inside the function body
as a variable declaration with no variables. This is a *forward
declaration* of the type tag `pair`: it makes the type tag local to the
current block, with the details of the type to come later. Here's an
example:

``` C
void
pair_up_doubles (int len, double array[])
{
  /* Forward declaration for pair.  */
  struct pair;
  struct two_pairs { struct pair *p, *q; };
  /* Give the details.  */
  struct pair { double a, b; };
  …
}
```

However, the cleanest practice is to avoid shadowing type tags.

------------------------------------------------------------------------

Previous: [Intertwined Incomplete
Types](Intertwined-Incomplete-Types.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
