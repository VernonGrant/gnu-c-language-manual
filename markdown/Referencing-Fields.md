Next: [Arrays as Fields](Arrays-as-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.1 Referencing Structure Fields 


To make a structure useful, there has to be a way to examine and store
its fields. The '`.`' (period) operator does that; its use
looks like `object.field`.

Given this structure and variable,

``` C
struct intlistlink
  {
    int datum;
    struct intlistlink *next;
  };

struct intlistlink foo;
```

you can write `foo.datum` and `foo.next` to refer to the two fields in
the value of `foo`. These fields are lvalues, so you can store values
into them, and read the values out again.

Most often, structures are dynamically allocated (see the next section),
and we refer to the objects via pointers. `(*p).field` is somewhat
cumbersome, so there is an abbreviation: `p->field`. For instance,
assume the program contains this declaration:

``` C
struct intlistlink *ptr;
```

You can write `ptr->datum` and `ptr->next` to refer to the two fields in
the object that `ptr` points to.

If a unary operator precedes an expression using '`->`', the
'`->`' nests inside:

``` C
  -ptr->datum   is equivalent to   -(ptr->datum)
```

You can intermix '`->`' and '`.`' without parentheses,
as shown here:

``` C
struct { double d; struct intlistlink l; } foo;

…foo.l.next->next->datum…
```
