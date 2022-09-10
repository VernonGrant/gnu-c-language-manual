Next: [Incomplete Array Types](Incomplete-Array-Types.md), Previous:
[Strings](Strings.md), Up: [Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.4 Array Type Designators 

Every C type has a type designator, which you make by deleting the
variable name and the semicolon from a declaration (see [Type
Designators](Type-Designators.md)). The designators for array types
follow this rule, but they may appear surprising.

``` C
type   int a[5];           designator   int [5]
type   double a[5][3];     designator   double [5][3]
type   struct foo *a[5];   designator   struct foo *[5]
```
