Next: [Null Statement](Null-Statement.md), Previous: [Duff's
Device](Duffs-Device.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.10 Case Ranges 


You can specify a range of consecutive values in a single `case` label,
like this:

``` C
case low ... high:
```

This has the same effect as the proper number of individual `case`
labels, one for each integer value from `low` to
`high`, inclusive.

This feature is especially useful for ranges of ASCII character codes:

``` C
case 'A' ... 'Z':
```

**Be careful:** with integers, write spaces around the `...` to prevent
it from being parsed wrong. For example, write this:

``` C
case 1 ... 5:
```

rather than this:

``` C
case 1...5:
```
