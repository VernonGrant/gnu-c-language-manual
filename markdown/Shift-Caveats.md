Next: [Shift Hacks](Shift-Hacks.md), Previous: [Shifting Makes New
Bits](Bits-Shifted-In.md), Up: [Shift
Operations](Shift-Operations.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 6.7.2 Caveats for Shift Operations 

**Warning:** If the shift count is greater than or equal to the width in
bits of the first operand, the results are machine-dependent. Logically
speaking, the "correct" value would be either -1 (for right shift of a
negative number) or 0 (in all other cases), but what it really generates
is whatever the machine's shift instruction does in that case. So unless
you can prove that the second operand is not too large, write code to
check it at run time.

**Warning:** Never rely on how the shift operators relate in precedence
to other arithmetic binary operators. Programmers don't remember these
precedences, and won't understand the code. Always use parentheses to
explicitly specify the nesting, like this:

``` C
a + (b << 5)   /* Shift first, then add.  */
(a + b) << 5   /* Add first, then shift.  */
```

Note: according to the C standard, shifting of signed values isn't
guaranteed to work properly when the value shifted is negative, or
becomes negative during the operation of shifting left. However, only
pedants have a reason to be concerned about this; only computers with
strange shift instructions could plausibly do this wrong. In GNU C, the
operation always works as expected,
