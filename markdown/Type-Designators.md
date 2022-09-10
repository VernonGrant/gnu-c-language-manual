Previous: [Other Data Types](Other-Data-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 11.6 Type Designators 


Some C constructs require a way to designate a specific data type
independent of any particular variable or expression which has that
type. The way to do this is with a *type designator*. The constucts that
need one include casts (see [Explicit Type
Conversion](Explicit-Type-Conversion.md)) and `sizeof` (see [Type
Size](Type-Size.md)).

We also use type designators to talk about the type of a value in C, so
you will see many type designators in this manual. When we say, "The
value has type `int`," `int` is a type designator.

To make the designator for any type, imagine a variable declaration for
a variable of that type and delete the variable name and the final
semicolon.

For example, to designate the type of full-word integers, we start with
the declaration for a variable `foo` with that type, which is this:

``` C
int foo;
```

Then we delete the variable name `foo` and the semicolon, leaving
`int`---exactly the keyword used in such a declaration. Therefore, the
type designator for this type is `int`.

What about long unsigned integers? From the declaration

``` C
unsigned long int foo;
```

we determine that the designator is `unsigned long int`.

Following this procedure, the designator for any primitive type is
simply the set of keywords which specifies that type in a declaration.
The same is true for compound types such as structures, unions, and
enumerations.

Designators for pointer types do follow the rule of deleting the
variable name and semicolon, but the result is not so simple. See
[Pointer-Type Designators](Pointer-Type-Designators.md), as part of
the chapter about pointers. See [Array Type
Designators](Array-Type-Designators.md)), for designators for array
types.

To understand what type a designator stands for, imagine a variable name
inserted into the right place in the designator to make a valid
declaration. What type would that variable be declared as? That is the
type the designator designates.

------------------------------------------------------------------------

Previous: [Other Data Types](Other-Data-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
