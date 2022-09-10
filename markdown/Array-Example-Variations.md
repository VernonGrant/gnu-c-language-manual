Previous: [Calling the Array Example](Array-Example-Call.md), Up:
[Beyond Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 4.4 Variations for Array Example 

The code to call `avg_of_double` has two declarations that start with
the same data type:

``` C
  /* The array of values to average.  */
  double nums_to_average[5];
  /* The average, once we compute it.  */
  double average;
```

In C, you can combine the two, like this:

``` C
  double nums_to_average[5], average;
```

This declares `nums_to_average` so each of its elements is a `double`,
and `average` so that it simply is a `double`.

However, while you *can* combine them, that doesn't mean you *should*.
If it is useful to write comments about the variables, and usually it
is, then it's clearer to keep the declarations separate so you can put a
comment on each one.

We set all of the elements of the array `nums_to_average` with
assignments, but it is more convenient to use an initializer in the
declaration:

``` C
{
  /* The array of values to average.  */
  double nums_to_average[]
    = { 58.7, 5.1, 7.7, 105.2, -3.14159 };

  /* The average, once we compute it.  */
  average = avg_of_double ((sizeof (nums_to_average)
                            / sizeof (nums_to_average[0])),
                           nums_to_average);

  /* …now make use of average… */
}
```

The array initializer is a comma-separated list of values, delimited by
braces. See [Initializers](Initializers.md).

Note that the declaration does not specify a size for `nums_to_average`,
so the size is determined from the initializer. There are five values in
the initializer, so `nums_to_average` gets length 5. If we add another
element to the initializer, `nums_to_average` will have six elements.

Because the code computes the number of elements from the size of the
array, using `sizeof`, the program will operate on all the elements in
the initializer, regardless of how many those are.

------------------------------------------------------------------------

Previous: [Calling the Array Example](Array-Example-Call.md), Up:
[Beyond Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
