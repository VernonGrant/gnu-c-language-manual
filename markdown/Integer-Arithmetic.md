Next: [Integer Overflow](Integer-Overflow.md), Previous: [Basic
Arithmetic](Basic-Arithmetic.md), Up: [Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.2 Integer Arithmetic 


Each of the basic arithmetic operations in C has two variants for
integers: *signed* and *unsigned*. The choice is determined by the data
types of their operands.

Each integer data type in C is either *signed* or *unsigned*. A signed
type can hold a range of positive and negative numbers, with zero near
the middle of the range. An unsigned type can hold only nonnegative
numbers; its range starts with zero and runs upward.

The most basic integer types are `int`, which normally can hold numbers
from -2,147,483,648 to 2,147,483,647, and `unsigned int`, which normally
can hold numbers from 0 to 4,294.967,295. (This assumes `int` is 32 bits
wide, always true for GNU C on real computers but not always on embedded
controllers.) See [Integer Data Types](Integer-Types.md), for full
information about integer types.

When a basic arithmetic operation is given two signed operands, it does
signed arithmetic. Given two unsigned operands, it does unsigned
arithmetic.

If one operand is `unsigned int` and the other is `int`, the operator
treats them both as unsigned. More generally, the common type of the
operands determines whether the operation is signed or not. See [Common
Type](Common-Type.md).

Printing the results of unsigned arithmetic with `printf` using
'`%d`' can produce surprising results for values far away from
zero. Even though the rules above say that the computation was done with
unsigned arithmetic, the printed result may appear to be signed!

The explanation is that the bit pattern resulting from addition,
subtraction or multiplication is actually the same for signed and
unsigned operations. The difference is only in the data type of the
result, which affects the *interpretation* of the result bit pattern,
and whether the arithmetic operation can overflow (see the next
section).

But '`%d`' doesn't know its argument's data type. It sees only
the value's bit pattern, and it is defined to interpret that as
`signed int`. To print it as unsigned requires using '`%u`'
instead of '`%d`'. See [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Formatted-Output.md#Formatted-Output)
in The GNU C Library Reference Manual.

Arithmetic in C never operates directly on narrow integer types (those
with fewer bits than `int`; [Narrow Integers](Narrow-Integers.md)).
Instead it "promotes" them to `int`. See [Operand
Promotions](Operand-Promotions.md).

------------------------------------------------------------------------

Next: [Integer Overflow](Integer-Overflow.md), Previous: [Basic
Arithmetic](Basic-Arithmetic.md), Up: [Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
