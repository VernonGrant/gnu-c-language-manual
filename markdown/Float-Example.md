Next: [An Example with Arrays](Array-Example.md), Up: [Beyond
Integers](Beyond-Integers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 4.1 An Example with Non-Integer Numbers 


Here's a function that operates on and returns *floating point* numbers
that don't have to be integers. Floating point represents a number as a
fraction together with a power of 2. (For more detail, see
[Floating-Point Data Types](Floating_002dPoint-Data-Types.md).) This
example calculates the average of three floating point numbers that are
passed to it as arguments:

``` C
double
average_of_three (double a, double b, double c)
{
  return (a + b + c) / 3;
}
```

The values of the parameter `a`{.variable}, `b`{.variable} and
`c`{.variable} do not have to be integers, and even when they happen to
be integers, most likely their average is not an integer.

`double` is the usual data type in C for calculations on floating-point
numbers.

To print a `double` with `printf`, we must use '`%f`' instead
of '`%d`':

``` C
printf ("Average is %f\n",
        average_of_three (1.1, 9.8, 3.62));
```

The code that calls `printf` must pass a `double` for printing with
'`%f`' and an `int` for printing with '`%d`'. If the
argument has the wrong type, `printf` will produce garbage output.

Here's a complete program that computes the average of three specific
numbers and prints the result:

``` C
double
average_of_three (double a, double b, double c)
{
  return (a + b + c) / 3;
}

int
main (void)
{
    printf ("Average is %f\n",
            average_of_three (1.1, 9.8, 3.62));
    return 0;
}
```

From now on we will not present examples of calls to `main`. Instead we
encourage you to write them for yourself when you want to test executing
some code.
