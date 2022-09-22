Next: [Structure Constructors](Structure-Constructors.md), Previous:
[Packing With Unions](Packing-With-Unions.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.16 Cast to a Union Type 


In GNU C, you can explicitly cast any of the alternative types to the
union type; for instance,

``` C
(union eight_bytes) (long long) 5
```

makes a value of type `union eight_bytes` which gets its contents
through the alternative named `big_int_elt`.

The value being cast must exactly match the type of the alternative, so
this is not valid:

``` C
(union eight_bytes) 5  /* Error!  5 is int. */
```

A cast to union type looks like any other cast, except that the type
specified is a union type. You can specify the type either with
`union tag` or with a typedef name (see [Defining Typedef
Names](Defining-Typedef-Names.md)).

Using the cast as the right-hand side of an assignment to a variable of
union type is equivalent to storing in an alternative of the union:

``` C
union foo u;

u = (union foo) x   means   u.i = x

u = (union foo) y   means   u.d = y
```

You can also use the union cast as a function argument:

``` C
void hack (union foo);
…
hack ((union foo) x);
```
