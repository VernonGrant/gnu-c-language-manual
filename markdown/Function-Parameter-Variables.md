Next: [Forward Function
Declarations](Forward-Function-Declarations.md), Up: [Function
Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.1 Function Parameter Variables 


A function parameter variable is a local variable (see [Local
Variables](Local-Variables.md)) used within the function to store the
value passed as an argument in a call to the function. Usually we say
"function parameter" or "parameter" for short, not mentioning the fact
that it's a variable.

We declare these variables in the beginning of the function definition,
in the *parameter list*. For example,

``` C
fib (int n)
```

has a parameter list with one function parameter `n`, which has type
`int`.

Function parameter declarations differ from ordinary variable
declarations in several ways:

-   Inside the function definition header, commas separate parameter
    declarations, and each parameter needs a complete declaration
    including the type. For instance, if a function `foo` has two `int`
    parameters, write this:

    
    ``` C
    foo (int a, int b)
    ```
    

    You can't share the common `int` between the two declarations:

    
    ``` C
    foo (int a, b)      /* Invalid! */
    ```
    

-   A function parameter variable is initialized to whatever value is
    passed in the function call, so its declaration cannot specify an
    initial value.

-   Writing an array type in a function parameter declaration has the
    effect of declaring it as a pointer. The size specified for the
    array has no effect at all, and we normally omit the size. Thus,

    
    ``` C
    foo (int a[5])
    foo (int a[])
    foo (int *a)
    ```
    

    are equivalent.

-   The scope of the parameter variables is the entire function body,
    notwithstanding the fact that they are written in the function
    header, which is just outside the function body.

If a function has no parameters, it would be most natural for the list
of parameters in its definition to be empty. But that, in C, has a
special meaning for historical reasons: "Do not check that calls to this
function have the right number of arguments." Thus,

``` C
int
foo ()
{
  return 5;
}

int
bar (int x)
{
  return foo (x);
}
```

would not report a compilation error in passing `x` as an argument to
`foo`. By contrast,

``` C
int
foo (void)
{
  return 5;
}

int
bar (int x)
{
  return foo (x);
}
```

would report an error because `foo` is supposed to receive no arguments.

------------------------------------------------------------------------

Next: [Forward Function
Declarations](Forward-Function-Declarations.md), Up: [Function
Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
