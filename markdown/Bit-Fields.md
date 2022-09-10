Next: [Bit Field Packing](Bit-Field-Packing.md), Previous: [Packed
Structures](Packed-Structures.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.6 Bit Fields 


A structure field declaration with an integer type can specify the
number of bits the field should occupy. We call that a *bit field*.
These are useful because consecutive bit fields are packed into a larger
storage unit. For instance,

``` C
unsigned char opcode: 4;
```

specifies that this field takes just 4 bits. Since it is unsigned, its
possible values range from 0 to 15. A signed field with 4 bits, such as
this,

``` C
signed char small: 4;
```

can hold values from -8 to 7.

You can subdivide a single byte into those two parts by writing

``` C
unsigned char opcode: 4;
signed char small: 4;
```

in the structure. With bit fields, these two numbers fit into a single
`char`.

Here's how to declare a one-bit field that can hold either 0 or 1:

``` C
unsigned char special_flag: 1;
```

You can also use the `bool` type for bit fields:

``` C
bool special_flag: 1;
```

Except when using `bool` (which is always unsigned, see [Boolean
Type](Boolean-Type.md)), always specify `signed` or `unsigned` for a
bit field. There is a default, if that's not specified: the bit field is
signed if plain `char` is signed, except that the option
`-funsigned-bitfields` forces unsigned as the default. But it
is cleaner not to depend on this default.

Bit fields are special in that you cannot take their address with
'`&`'. They are not stored with the size and alignment
appropriate for the specified type, so they cannot be addressed through
pointers to that type.

------------------------------------------------------------------------

Next: [Bit Field Packing](Bit-Field-Packing.md), Previous: [Packed
Structures](Packed-Structures.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
