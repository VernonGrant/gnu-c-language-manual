Next: [Omitting Types in Declarations](Omitting-Types.md), Previous:
[Allocating File-Scope Variables](Allocating-File_002dScope.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.10 `auto` and `register` 


For historical reasons, you can write `auto` or `register` before a
local variable declaration. `auto` merely emphasizes that the variable
isn't static; it changes nothing.

`register` suggests to the compiler storing this variable in a register.
However, GNU C ignores this suggestion, since it can choose the best
variables to store in registers without any hints.

It is an error to take the address of a variable declared `register`, so
you cannot use the unary '`&`' operator on it. If the variable
is an array, you can't use it at all (other than as the operand of
`sizeof`), which makes it rather useless.
