Next: [Flexible Array Fields](Flexible-Array-Fields.md), Previous:
[`const` Fields](const-Fields.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.9 Arrays of Length Zero 


GNU C allows zero-length arrays. They are useful as the last element of
a structure that is really a header for a variable-length object. Here's
an example, where we construct a variable-size structure to hold a line
which is `this_length` characters long:

``` C
struct line {
  int length;
  char contents[0];
};

struct line *thisline
  = ((struct line *)
     malloc (sizeof (struct line)
             + this_length));
thisline->length = this_length;
```

In ISO C90, we would have to give `contents` a length of 1, which means
either wasting space or complicating the argument to `malloc`.
