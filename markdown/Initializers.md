Next: [Designated Initializers](Designated-Inits.md), Previous:
[Variable Declarations](Variable-Declarations.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.2 Initializers 


A variable's declaration, unless it is `extern`, should also specify its
initial value. For numeric and pointer-type variables, the initializer
is an expression for the value. If necessary, it is converted to the
variable's type, just as in an assignment.

You can also initialize a local structure-type (see
[Structures](Structures.md)) or local union-type (see
[Unions](Unions.md)) variable this way, from an expression whose value
has the same type. But you can't initialize an array this way (see
[Arrays](Arrays.md)), since arrays are not first-class objects in C
(see [Limitations of C Arrays](Limitations-of-C-Arrays.md)) and there
is no array assignment.

You can initialize arrays and structures componentwise, with a list of
the elements or components. You can initialize a union with any one of
its alternatives.

-   A component-wise initializer for an array consists of element values
    surrounded by '`{…}`'. If the values in the initializer
    don't cover all the elements in the array, the remaining elements
    are initialized to zero.

    You can omit the size of the array when you declare it, and let the
    initializer specify the size:

    
    ``` C
    int array[] = { 3, 9, 12 };
    ```
    

-   A component-wise initializer for a structure consists of field
    values surrounded by '`{…}`'. Write the field values in the
    same order as the fields are declared in the structure. If the
    values in the initializer don't cover all the fields in the
    structure, the remaining fields are initialized to zero.

-   The initializer for a union-type variable has the form `{ value }`,
    where `value` initializes the *first alternative* in the
    union definition.

For an array of arrays, a structure containing arrays, an array of
structures, etc., you can nest these constructs. For example,

``` C
struct point { double x, y; };

struct point series[]
  = { {0, 0}, {1.5, 2.8}, {99, 100.0004} };
```

You can omit a pair of inner braces if they contain the right number of
elements for the sub-value they initialize, so that no elements or
fields need to be filled in with zeros. But don't do that very much, as
it gets confusing.

An array of `char` can be initialized using a string constant. Recall
that the string constant includes an implicit null character at the end
(see [String Constants](String-Constants.md)). Using a string constant
as initializer means to use its contents as the initial values of the
array elements. Here are examples:

``` C
char text[6] = "text!";     /* Includes the null. */
char text[5] = "text!";     /* Excludes the null. */
char text[] = "text!";      /* Gets length 6. */
char text[]
  = { 't', 'e', 'x', 't', '!', 0 };  /* same as above. */
char text[] = { "text!" };  /* Braces are optional. */
```

and this kind of initializer can be nested inside braces to initialize
structures or arrays that contain a `char`-array.

In like manner, you can use a wide string constant to initialize an
array of `wchar_t`.

------------------------------------------------------------------------

Next: [Designated Initializers](Designated-Inits.md), Previous:
[Variable Declarations](Variable-Declarations.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
