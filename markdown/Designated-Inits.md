Next: [Referring to a Type with `__auto_type`](Auto-Type.md),
Previous: [Initializers](Initializers.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.3 Designated Initializers 


In a complex structure or long array, it's useful to indicate which
field or element we are initializing.

To designate specific array elements during initialization, include the
array index in brackets, and an assignment operator, for each element:

``` C
int foo[10] = { [3] = 42, [7] = 58 };
```

This does the same thing as:

``` C
int foo[10] = { 0, 0, 0, 42, 0, 0, 0, 58, 0, 0 };
```

The array initialization can include non-designated element values
alongside designated indices; these follow the expected ordering of the
array initialization, so that

``` C
int foo[10] = { [3] = 42, 43, 44, [7] = 58 };
```

does the same thing as:

``` C
int foo[10] = { 0, 0, 0, 42, 43, 44, 0, 58, 0, 0 };
```

Note that you can only use constant expressions as array index values,
not variables.

If you need to initialize a subsequence of sequential array elements to
the same value, you can specify a range:

``` C
int foo[100] = { [0 ... 19] = 42, [20 ... 99] = 43 };
```

Using a range this way is a GNU C extension.

When subsequence ranges overlap, each element is initialized by the last
specification that applies to it. Thus, this initialization is
equivalent to the previous one.

``` C
int foo[100] = { [0 ... 99] = 43, [0 ... 19] = 42 };
```

as the second overrides the first for elements 0 through 19.

The value used to initialize a range of elements is evaluated only once,
for the first element in the range. So for example, this code

``` C
int random_values[100]
  = { [0 ... 99] = get_random_number() };
```

would initialize all 100 elements of the array `random_values` to the
same value---probably not what is intended.

Similarly, you can initialize specific fields of a structure variable by
specifying the field name prefixed with a dot:

``` C
struct point { int x; int y; };

struct point foo = { .y = 42; };
```

The same syntax works for union variables as well:

``` C
union int_double { int i; double d; };

union int_double foo = { .d = 34 };
```

This casts the integer value 34 to a double and stores it in the union
variable `foo`.

You can designate both array elements and structure elements in the same
initialization; for example, here's an array of point structures:

``` C
struct point point_array[10] = { [4].y = 32, [6].y = 39 };
```

Along with the capability to specify particular array and structure
elements to initialize comes the possibility of initializing the same
element more than once:

``` C
int foo[10] = { [4] = 42, [4] = 98 };
```

In such a case, the last initialization value is retained.

------------------------------------------------------------------------

Next: [Referring to a Type with `__auto_type`](Auto-Type.md),
Previous: [Initializers](Initializers.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
