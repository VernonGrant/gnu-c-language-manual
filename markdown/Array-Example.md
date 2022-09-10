Next: [Calling the Array Example](Array-Example-Call.md), Previous:
[An Example with Non-Integer Numbers](Float-Example.md), Up: [Beyond
Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 4.2 An Example with Arrays 


A function to take the average of three numbers is very specific and
limited. A more general function would take the average of any number of
numbers. That requires passing the numbers in an array. An array is an
object in memory that contains a series of values of the same data type.
This chapter presents the basic concepts and use of arrays through an
example; for the full explanation, see [Arrays](Arrays.md).

Here's a function definition to take the average of several
floating-point numbers, passed as type `double`. The first parameter,
`length`, specifies how many numbers are passed. The second parameter,
`input_data`, is an array that holds those numbers.

``` C
double
avg_of_double (int length, double input_data[])
{
  double sum = 0;
  int i;

  for (i = 0; i < length; i++)
    sum = sum + input_data[i];

  return sum / length;
}
```

This introduces the expression to refer to an element of an array:
`input_data[i]` means the element at index `i` in `input_data`. The
index of the element can be any expression with an integer value; in
this case, the expression is `i`. See [Accessing Array
Elements](Accessing-Array-Elements.md).


The lowest valid index in an array is 0, *not* 1, and the highest valid
index is one less than the number of elements. (This is known as
*zero-origin indexing*.)

This example also introduces the way to declare that a function
parameter is an array. Such declarations are modeled after the syntax
for an element of the array. Just as `double foo` declares that `foo` is
of type `double`, `double input_data[]` declares that each element of
`input_data` is of type `double`. Therefore, `input_data` itself has
type "array of `double`."

When declaring an array parameter, it's not necessary to say how long
the array is. In this case, the parameter `input_data` has no length
information. That's why the function needs another parameter, `length`,
for the caller to provide that information to the function
`avg_of_double`.

------------------------------------------------------------------------

Next: [Calling the Array Example](Array-Example-Call.md), Previous:
[An Example with Non-Integer Numbers](Float-Example.md), Up: [Beyond
Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
