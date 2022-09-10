Next: [Label Value Caveats](Label-Value-Caveats.md), Up: [Labels as
Values](Labels-as-Values.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.14.1 Label Value Uses 

One use for label-valued constants is to initialize a static array to
serve as a jump table:

``` C
static void *array[] = { &&foo, &&bar, &&hack };
```

Then you can select a label with indexing, like this:

``` C
goto *array[i];
```

Note that this does not check whether the subscript is in bounds---array
indexing in C never checks that.

You can make the table entries offsets instead of addresses by
subtracting one label from the others. Here is an example:

``` C
static const int array[] = { &&foo - &&foo, &&bar - &&foo,
                             &&hack - &&foo };
goto *(&&foo + array[i]);
```

Using offsets is preferable in shared libraries, as it avoids the need
for dynamic relocation of the array elements; therefore, the array can
be read-only.

An array of label values or offsets serves a purpose much like that of
the `switch` statement. The `switch` statement is cleaner, so use
`switch` by preference when feasible.

Another use of label values is in an interpreter for threaded code. The
labels within the interpreter function can be stored in the threaded
code for super-fast dispatching.
