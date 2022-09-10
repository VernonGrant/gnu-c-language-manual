Previous: [Pointer-Integer
Conversion](Pointer_002dInteger-Conversion.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.16 Printing Pointers 

To print the numeric value of a pointer, use the '`%p`'
specifier. For example:

``` C
void
print_pointer (void *ptr)
{
  printf ("Pointer value is %p\n", ptr);
}
```

The specification '`%p`' works with any pointer type. It prints
'`0x`' followed by the address in hexadecimal, printed as the
appropriate unsigned integer type.
