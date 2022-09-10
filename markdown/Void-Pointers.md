Next: [Pointer Comparison](Pointer-Comparison.md), Previous:
[Dereferencing Null or Invalid Pointers](Invalid-Dereference.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.8 Void Pointers 


The peculiar type `void *`, a pointer whose target type is `void`, is
used often in C. It represents a pointer to we-don't-say-what. Thus,

``` C
void *numbered_slot_pointer (int);
```

declares a function `numbered_slot_pointer` that takes an integer
parameter and returns a pointer, but we don't say what type of data it
points to.

With type `void *`, you can pass the pointer around and test whether it
is null. However, dereferencing it gives a `void` value that can't be
used (see [The Void Type](The-Void-Type.md)). To dereference the
pointer, first convert it to some other pointer type.

Assignments convert `void *` automatically to any other pointer type, if
the left operand has a pointer type; for instance,

``` C
{
  int *p;
  /* Converts return value to int *.  */
  p = numbered_slot_pointer (5);
  …
}
```

Passing an argument of type `void *` for a parameter that has a pointer
type also converts. For example, supposing the function `hack` is
declared to require type `float *` for its argument, this will convert
the null pointer to that type.

``` C
/* Declare hack that way.
   We assume it is defined somewhere else.  */
void hack (float *);
…
/* Now call hack.  */
{
  /* Converts return value of numbered_slot_pointer
     to float * to pass it to hack.  */
  hack (numbered_slot_pointer (5));
  …
}
```

You can also convert to another pointer type with an explicit cast (see
[Explicit Type Conversion](Explicit-Type-Conversion.md)), like this:

``` C
(int *) numbered_slot_pointer (5)
```

Here is an example which decides at run time which pointer type to
convert to:

``` C
void
extract_int_or_double (void *ptr, bool its_an_int)
{
  if (its_an_int)
    handle_an_int (*(int *)ptr);
  else 
    handle_a_double (*(double *)ptr);
}
```

The expression `*(int *)ptr` means to convert `ptr` to type `int *`,
then dereference it.

------------------------------------------------------------------------

Next: [Pointer Comparison](Pointer-Comparison.md), Previous:
[Dereferencing Null or Invalid Pointers](Invalid-Dereference.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
