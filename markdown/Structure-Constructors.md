Next: [Unnamed Types as Fields](Unnamed-Types-as-Fields.md), Previous:
[Cast to a Union Type](Cast-to-Union.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.17 Structure Constructors 


You can construct a structure value by writing its type in parentheses,
followed by an initializer that would be valid in a declaration for that
type. For instance, given this declaration,

``` C
struct foo {int a; char b[2];} structure;
```

you can create a `struct foo` value as follows:

``` C
((struct foo) {x + y, 'a', 0})
```

This specifies `x + y` for field `a`, the character '`a`' for
field `b`'s element 0, and the null character for field `b`'s element 1.

The parentheses around that constructor are to necessary, but we
recommend writing them to make the nesting of the containing expression
clearer.

You can also show the nesting of the two by writing it like this:

``` C
((struct foo) {x + y, {'a', 0} })
```

Each of those is equivalent to writing the following statement
expression (see [Statements and Declarations in
Expressions](Statement-Exprs.md)):

``` C
({
  struct foo temp = {x + y, 'a', 0};
  temp;
})
```

You can also use field labels in the structure constructor to indicate
which fields you're specifying values for, instead of using the order of
the fields to specify that:

``` C
(struct foo) {.a = x + y, .b = {'a', 0}}
```

You can also create a union value this way, but it is not especially
useful since that is equivalent to doing a cast:

``` C
  ((union whosis) {value})
is equivalent to
  ((union whosis) (value))
```
