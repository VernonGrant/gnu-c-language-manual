Next: [Constructing Array Values](Constructing-Array-Values.md),
Previous: [Limitations of C Arrays](Limitations-of-C-Arrays.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.7 Multidimensional Arrays 


Strictly speaking, all arrays in C are unidimensional. However, you can
create an array of arrays, which is more or less equivalent to a
multidimensional array. For example,

``` C
struct chesspiece *board[8][8];
```

declares an array of 8 arrays of 8 pointers to `struct chesspiece`. This
data type could represent the state of a chess game. To access one
square's contents requires two array index operations, one for each
dimension. For instance, you can write `board[row][column]`, assuming
`row` and `column` are variables with integer values in the proper
range.

How does C understand `board[row][column]`? First of all, `board` is
converted automatically to a pointer to the zeroth element (at index
zero) of `board`. Adding `row` to that makes it point to the desired
element. Thus, `board[row]`'s value is an element of `board`---an array
of 8 pointers.

However, as an expression with array type, it is converted automatically
to a pointer to the array's zeroth element. The second array index
operation, `[column]`, accesses the chosen element from that array.

As this shows, pointer-to-array types are meaningful in C. You can
declare a variable that points to a row in a chess board like this:

``` C
struct chesspiece *(*rowptr)[8];
```

This points to an array of 8 pointers to `struct chesspiece`. You can
assign to it as follows:

``` C
rowptr = &board[5];
```

The dimensions don't have to be equal in length. Here we declare
`statepop` as an array to hold the population of each state in the
United States for each year since 1900:

``` C
#define NSTATES 50
{
  int nyears = current_year - 1900 + 1;
  int statepop[NSTATES][nyears];
  …
}
```

The variable `statepop` is an array of `NSTATES` subarrays, each indexed
by the year (counting from 1900). Thus, to get the element for a
particular state and year, we must subscript it first by the number that
indicates the state, and second by the index for the year:

``` C
statepop[state][year - 1900]
```


The subarrays within the multidimensional array are allocated
consecutively in memory, and within each subarray, its elements are
allocated consecutively in memory. The most efficient way to process all
the elements in the array is to scan the last subscript in the innermost
loop. This means consecutive accesses go to consecutive memory
locations, which optimizes use of the processor's memory cache. For
example:

``` C
int total = 0;
float average;

for (int state = 0; state < NSTATES, ++state)
  {
    for (int year = 0; year < nyears; ++year)
      {
        total += statepop[state][year];
      }
  }

average = total / nyears;
```

C's layout for multidimensional arrays is different from Fortran's
layout. In Fortran, a multidimensional array is not an array of arrays;
rather, multidimensional arrays are a primitive feature, and it is the
first index that varies most rapidly between consecutive memory
locations. Thus, the memory layout of a 50x114 array in C matches that
of a 114x50 array in Fortran.

------------------------------------------------------------------------

Next: [Constructing Array Values](Constructing-Array-Values.md),
Previous: [Limitations of C Arrays](Limitations-of-C-Arrays.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
