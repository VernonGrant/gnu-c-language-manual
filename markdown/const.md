Next: [`volatile` Variables and Fields](volatile.md), Up: [Type
Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 21.1 `const` Variables and Fields 


You can mark a variable as "constant" by writing `const` in front of the
declaration. This says to treat any assignment to that variable as an
error. It may also permit some compiler optimizations---for instance, to
fetch the value only once to satisfy multiple references to it. The
construct looks like this:

``` C
const double pi = 3.14159;
```

After this definition, the code can use the variable `pi` but cannot
assign a different value to it.

``` C
pi = 3.0; /* Error! */
```

Simple variables that are constant can be used for the same purposes as
enumeration constants, and they are not limited to integers. The
constantness of the variable propagates into pointers, too.

A pointer type can specify that the *target* is constant. For example,
the pointer type `const double *` stands for a pointer to a constant
`double`. That's the type that results from taking the address of `pi`.
Such a pointer can't be dereferenced in the left side of an assignment.

``` C
*(&pi) = 3.0; /* Error! */
```

Nonconstant pointers can be converted automatically to constant
pointers, but not vice versa. For instance,

``` C
const double *cptr;
double *ptr;

cptr = &pi;    /* Valid. */
cptr = ptr;    /* Valid. */
ptr = cptr;    /* Error! */
ptr = &pi;     /* Error! */
```

This is not an ironclad protection against modifying the value. You can
always cast the constant pointer to a nonconstant pointer type:

``` C
ptr = (double *)cptr;    /* Valid. */
ptr = (double *)&pi;     /* Valid. */
```

However, `const` provides a way to show that a certain function won't
modify the data structure whose address is passed to it. Here's an
example:

``` C
int
string_length (const char *string)
{
  int count = 0;
  while (*string++)
    count++;
  return count;
}
```

Using `const char *` for the parameter is a way of saying this function
never modifies the memory of the string itself.

In calling `string_length`, you can specify an ordinary `char *` since
that can be converted automatically to `const char *`.

------------------------------------------------------------------------

Next: [`volatile` Variables and Fields](volatile.md), Up: [Type
Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
