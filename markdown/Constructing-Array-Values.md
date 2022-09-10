Next: [Arrays of Variable Length](Arrays-of-Variable-Length.md),
Previous: [Multidimensional Arrays](Multidimensional-Arrays.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.8 Constructing Array Values 


You can construct an array from elements by writing them inside braces,
and preceding all that with the array type's designator in parentheses.
There is no need to specify the array length, since the number of
elements determines that. The constructor looks like this:

``` C
(elttype[]) { elements };
```

Here is an example, which constructs an array of string pointers:

``` C
(char *[]) { "x", "y", "z" };
```

That's equivalent in effect to declaring an array with the same
initializer, like this:

``` C
char *array[] = { "x", "y", "z" };
```

and then using the array.

If all the elements are simple constant expressions, or made up of such,
then the compound literal can be coerced to a pointer to its zeroth
element and used to initialize a file-scope variable (see [File-Scope
Variables](File_002dScope-Variables.md)), as shown here:

``` C
char **foo = (char *[]) { "x", "y", "z" };
```

The data type of `foo` is `char **`, which is a pointer type, not an
array type. The declaration is equivalent to defining and then using an
array-type variable:

``` C
char *nameless_array[] = { "x", "y", "z" };
char **foo = &nameless_array[0];
```
