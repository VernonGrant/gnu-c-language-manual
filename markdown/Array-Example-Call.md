Next: [Variations for Array Example](Array-Example-Variations.md),
Previous: [An Example with Arrays](Array-Example.md), Up: [Beyond
Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 4.3 Calling the Array Example 

To call the function `avg_of_double` requires making an array and then
passing it as an argument. Here is an example.

``` C
{
  /* The array of values to average.  */
  double nums_to_average[5];
  /* The average, once we compute it.  */
  double average;

  /* Fill in elements of nums_to_average.  */

  nums_to_average[0] = 58.7;
  nums_to_average[1] = 5.1;
  nums_to_average[2] = 7.7;
  nums_to_average[3] = 105.2;
  nums_to_average[4] = -3.14159;

  average = avg_of_double (5, nums_to_average);

  /* …now make use of average… */
}
```

This shows an array subscripting expression again, this time on the left
side of an assignment, storing a value into an element of an array.

It also shows how to declare a local variable that is an array:
`double nums_to_average[5];`. Since this declaration allocates the space
for the array, it needs to know the array's length. You can specify the
length with any expression whose value is an integer, but in this
declaration the length is a constant, the integer 5.

The name of the array, when used by itself as an expression, stands for
the address of the array's data, and that's what gets passed to the
function `avg_of_double` in `avg_of_double (5, nums_to_average)`.

We can make the code easier to maintain by avoiding the need to write 5,
the array length, when calling `avg_of_double`. That way, if we change
the array to include more elements, we won't have to change that call.
One way to do this is with the `sizeof` operator:

``` C
  average = avg_of_double ((sizeof (nums_to_average)
                            / sizeof (nums_to_average[0])),
                           nums_to_average);
```

This computes the number of elements in `nums_to_average` by dividing
its total size by the size of one element. See [Type
Size](Type-Size.md), for more details of using `sizeof`.

We don't show in this example what happens after storing the result of
`avg_of_double` in the variable `average`. Presumably more code would
follow that uses that result somehow. (Why compute the average and not
use it?) But that isn't part of this topic.

------------------------------------------------------------------------

Next: [Variations for Array Example](Array-Example-Variations.md),
Previous: [An Example with Arrays](Array-Example.md), Up: [Beyond
Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
