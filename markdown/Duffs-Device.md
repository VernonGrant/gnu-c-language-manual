Next: [Case Ranges](Case-Ranges.md), Previous: [Example of
`switch`](switch-Example.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.9 Duff's Device 


The cases in a `switch` statement can be inside other control
constructs. For instance, we can use a technique known as *Duff's
device* to optimize this simple function,

``` C
void
copy (char *to, char *from, int count)
{
  while (count > 0)
    *to++ = *from++, count--;
}
```

which copies memory starting at `from` to memory starting at
`to`.

Duff's device involves unrolling the loop so that it copies several
characters each time around, and using a `switch` statement to enter the
loop body at the proper point:

``` C
void
copy (char *to, char *from, int count)
{
  if (count <= 0)
    return;
  int n = (count + 7) / 8;
  switch (count % 8)
    {
      do {
        case 0: *to++ = *from++;
        case 7: *to++ = *from++;
        case 6: *to++ = *from++;
        case 5: *to++ = *from++;
        case 4: *to++ = *from++;
        case 3: *to++ = *from++;
        case 2: *to++ = *from++;
        case 1: *to++ = *from++;
        } while (--n > 0);
    }
}
```
