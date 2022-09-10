Previous: [Shift Operations](Shift-Operations.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.8 Bitwise Operations 


Bitwise operators operate on integers, treating each bit independently.
They are not allowed for floating-point types.

The examples in this section use binary constants, starting with
'`0b`' (see [Integer Constants](Integer-Constants.md)). They
stand for 32-bit integers of type `int`.

`~a`

-   Unary operator for bitwise negation; this changes each bit of `a`
    from 1 to 0 or from 0 to 1.

    
    ``` C
    ~0b10101000 ⇒ 0b11111111111111111111111101010111
    ~0 ⇒ 0b11111111111111111111111111111111
    ~0b11111111111111111111111111111111 ⇒ 0
    ~ (-1) ⇒ 0
    ```
    

    It is useful to remember that `~x + 1` equals `-x`, for integers,
    and `~x` equals `-x - 1`. The last example above shows this with -1
    as `x`.

`a` & `b`

-   Binary operator for bitwise "and" or "conjunction." Each bit in the
    result is 1 if that bit is 1 in both `a` and `b`.

    
    ``` C
    0b10101010 & 0b11001100 ⇒ 0b10001000
    ```
    

`a` \| `b`

-   Binary operator for bitwise "or" ("inclusive or" or "disjunction").
    Each bit in the result is 1 if that bit is 1 in either `a` or `b`.

    
    ``` C
    0b10101010 | 0b11001100 ⇒ 0b11101110
    ```
    

`a` \^ `b`

-   Binary operator for bitwise "xor" ("exclusive or"). Each bit in the
    result is 1 if that bit is 1 in exactly one of `a` and `b`.

    
    ``` C
    0b10101010 ^ 0b11001100 ⇒ 0b01100110
    ```
    

To understand the effect of these operators on signed integers, keep in
mind that all modern computers use two's-complement representation (see
[Integer Representations](Integer-Representations.md)) for negative
integers. This means that the highest bit of the number indicates the
sign; it is 1 for a negative number and 0 for a positive number. In a
negative number, the value in the other bits *increases* as the number
gets closer to zero, so that `0b111…111` is -1 and `0b100…000` is the
most negative possible integer.

**Warning:** C defines a precedence ordering for the bitwise binary
operators, but you should never rely on it. You should never rely on how
bitwise binary operators relate in precedence to the arithmetic and
shift binary operators. Other programmers don't remember this precedence
ordering, so always use parentheses to explicitly specify the nesting.

For example, suppose `offset` is an integer that specifies the offset
within shared memory of a table, except that its bottom few bits
(`LOWBITS` says how many) are special flags. Here's how to get just that
offset and add it to the base address.

``` C
shared_mem_base + (offset & (-1 << LOWBITS))
```

Thanks to the outer set of parentheses, we don't need to know whether
'`&`' has higher precedence than '`+`'. Thanks to the
inner set, we don't need to know whether '`&`' has higher
precedence than '`<<`'. But we can rely on all unary operators
to have higher precedence than any binary operator, so we don't need
parentheses around the left operand of '`<<`'.

------------------------------------------------------------------------

Previous: [Shift Operations](Shift-Operations.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
