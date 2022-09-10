Next: [Arrays](Arrays.md), Previous: [Pointers](Pointers.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 15 Structures 


A *structure* is a user-defined data type that holds various *fields* of
data. Each field has a name and a data type specified in the structure's
definition.

Here we define a structure suitable for storing a linked list of
integers. Each list item will hold one integer, plus a pointer to the
next item.

``` C
struct intlistlink
  {
    int datum;
    struct intlistlink *next;
  };
```

The structure definition has a *type tag* so that the code can refer to
this structure. The type tag here is `intlistlink`. The definition
refers recursively to the same structure through that tag.

You can define a structure without a type tag, but then you can't refer
to it again. That is useful only in some special contexts, such as
inside a `typedef` or a `union`.

The contents of the structure are specified by the *field declarations*
inside the braces. Each field in the structure needs a declaration
there. The fields in one structure definition must have distinct names,
but these names do not conflict with any other names in the program.

A field declaration looks just like a variable declaration. You can
combine field declarations with the same beginning, just as you can
combine variable declarations.

This structure has two fields. One, named `datum`, has type `int` and
will hold one integer in the list. The other, named `next`, is a pointer
to another `struct intlistlink` which would be the rest of the list. In
the last list item, it would be `NULL`.

This structure definition is recursive, since the type of the `next`
field refers to the structure type. Such recursion is not a problem; in
fact, you can use the type `struct intlistlink *` before the definition
of the type `struct intlistlink` itself. That works because pointers to
all kinds of structures really look the same at the machine level.

After defining the structure, you can declare a variable of type
`struct intlistlink` like this:

``` C
struct intlistlink foo;
```

The structure definition itself can serve as the beginning of a variable
declaration, so you can declare variables immediately after, like this:

``` C
struct intlistlink
  {
    int datum;
    struct intlistlink *next;
  } foo;
```

But that is ugly. It is almost always clearer to separate the definition
of the structure from its uses.

Declaring a structure type inside a block (see [Blocks](Blocks.md))
limits the scope of the structure type name to that block. That means
the structure type is recognized only within that block. Declaring it in
a function parameter list, as here,

``` C
int f (struct foo {int a, b} parm);
```

(assuming that `struct foo` is not already defined) limits the scope of
the structure type `struct foo` to that parameter list; that is
basically useless, so it triggers a warning.

Standard C requires at least one field in a structure. GNU C does not
require this.

-   [Referencing Structure Fields](Referencing-Fields.md)
-   [Dynamic Memory Allocation](Dynamic-Memory-Allocation.md)
-   [Field Offset](Field-Offset.md)
-   [Structure Layout](Structure-Layout.md)
-   [Packed Structures](Packed-Structures.md)
-   [Bit Fields](Bit-Fields.md)
-   [Bit Field Packing](Bit-Field-Packing.md)
-   [`const` Fields](const-Fields.md)
-   [Arrays of Length Zero](Zero-Length.md)
-   [Flexible Array Fields](Flexible-Array-Fields.md)
-   [Overlaying Different Structures](Overlaying-Structures.md)
-   [Structure Assignment](Structure-Assignment.md)
-   [Unions](Unions.md)
-   [Packing With Unions](Packing-With-Unions.md)
-   [Cast to a Union Type](Cast-to-Union.md)
-   [Structure Constructors](Structure-Constructors.md)
-   [Unnamed Types as Fields](Unnamed-Types-as-Fields.md)
-   [Incomplete Types](Incomplete-Types.md)
-   [Intertwined Incomplete Types](Intertwined-Incomplete-Types.md)
-   [Type Tags](Type-Tags.md)

------------------------------------------------------------------------

Next: [Arrays](Arrays.md), Previous: [Pointers](Pointers.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
