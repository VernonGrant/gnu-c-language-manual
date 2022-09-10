Previous: [Caveats for Shift Operations](Shift-Caveats.md), Up: [Shift
Operations](Shift-Operations.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 6.7.3 Shift Hacks 

You can use the shift operators for various useful hacks. For example,
given a date specified by day of the month `d`, month `m`, and year `y`,
you can store the entire date in a single integer `date`:

``` C
unsigned int d = 12;
unsigned int m = 6;
unsigned int y = 1983;
unsigned int date = ((y << 4) + m) << 5) + d;
```

To extract the original day, month, and year out of `date`, use a
combination of shift and remainder.

``` C
d = date % 32;
m = (date >> 5) % 16;
y = date >> 9;
```

`-1 << LOWBITS` is a clever way to make an integer whose `LOWBITS`
lowest bits are all 0 and the rest are all 1. `-(1 << LOWBITS)` is
equivalent to that, due to associativity of multiplication, since
negating a value is equivalent to multiplying it by -1.
