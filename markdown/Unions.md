Next: [Packing With Unions](Packing-With-Unions.md), Previous:
[Structure Assignment](Structure-Assignment.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.13 Unions 


A *union type* defines alternative ways of looking at the same piece of
memory. Each alternative view is defined with a data type, and
identified by a name. A union definition looks like this:

``` C
union name
{
  alternative declarations…
};
```

Each alternative declaration looks like a structure field declaration,
except that it can't be a bit field. For instance,

``` C
union number
{
  long int integer;
  double float;
}
```

lets you store either an integer (type `long int`) or a floating point
number (type `double`) in the same place in memory. The length and
alignment of the union type are the maximum of all the
alternatives---they do not have to be the same. In this union example,
`double` probably takes more space than `long int`, but that doesn't
cause a problem in programs that use the union in the normal way.

The members don't have to be different in data type. Sometimes each
member pertains to a way the data will be used. For instance,

``` C
union datum
{
  double latitude;
  double longitude;
  double height;
  double weight;
  int continent;
}
```

This union holds one of several kinds of data; most kinds are floating
points, but the value can also be a code for a continent which is an
integer. You *could* use one member of type `double` to access all the
values which have that type, but the different member names will make
the program clearer.

The alignment of a union type is the maximum of the alignments of the
alternatives. The size of the union type is the maximum of the sizes of
the alternatives, rounded up to a multiple of the alignment (because
every type's size must be a multiple of its alignment).

All the union alternatives start at the address of the union itself. If
an alternative is shorter than the union as a whole, it occupies the
first part of the union's storage, leaving the last part unused *for
that alternative*.

**Warning:** if the code stores data using one union alternative and
accesses it with another, the results depend on the kind of computer in
use. Only wizards should try to do this. However, when you need to do
this, a union is a clean way to do it.

Assignment works on any union type by copying the entire value.

------------------------------------------------------------------------

Next: [Packing With Unions](Packing-With-Unions.md), Previous:
[Structure Assignment](Structure-Assignment.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
