Next: [Narrow Integers](Narrow-Integers.md), Previous: [Basic
Integers](Basic-Integers.md), Up: [Integer Data
Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.2 Signed and Unsigned Types 


An unsigned integer type can represent only positive numbers and zero. A
signed type can represent both positive and negative number, in a range
spread almost equally on both sides of zero. For instance,
`unsigned char` holds numbers from 0 to 255 (on most computers), while
`signed char` holds numbers from -128 to 127. Each of these types holds
256 different possible values, since they are both 8 bits wide.

Write `signed` or `unsigned` before the type keyword to specify a signed
or an unsigned type. However, the integer types other than `char` are
signed by default; with them, `signed` is a no-op.

Plain `char` may be signed or unsigned; this depends on the compiler,
the machine in use, and its operating system.

In many programs, it makes no difference whether `char` is signed. When
it does matter, don't leave it to chance; write `signed char` or
`unsigned char`.[^3^](#FOOT3)


------------------------------------------------------------------------

#### Footnotes 

##### [(3)](#DOCF3)

Personal note from Richard Stallman: Eating with hackers at a fish
restaurant, I ordered Arctic Char. When my meal arrived, I noted that
the chef had not signed it. So I complained, "This char is unsigned---I
wanted a signed char!" Or rather, I would have said this if I had
thought of it fast enough.
