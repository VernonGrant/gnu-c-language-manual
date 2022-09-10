Next: [Advanced Function Features](Advanced-Definitions.md), Previous:
[Function Pointers](Function-Pointers.md), Up:
[Functions](Functions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 22.6 The `main` Function 


Every complete executable program requires at least one function, called
`main`, which is where execution begins. You do not have to explicitly
declare `main`, though GNU C permits you to do so. Conventionally,
`main` should be defined to follow one of these calling conventions:

``` C
int main (void) {…}
int main (int argc, char *argv[]) {…}
int main (int argc, char *argv[], char *envp[]) {…}
```

Using `void` as the parameter list means that `main` does not use the
arguments. You can write `char **argv` instead of `char *argv[]`, and
likewise for `envp`, as the two constructs are equivalent.

You can call `main` from C code, as you can call any other function,
though that is an unusual thing to do. When you do that, you must write
the call to pass arguments that match the parameters in the definition
of `main`.

The `main` function is not actually the first code that runs when a
program starts. In fact, the first code that runs is system code from
the file `crt0.o`. In Unix, this was hand-written assembler
code, but in GNU we replaced it with C code. Its job is to find the
arguments for `main` and call that.

-   [Returning Values from `main`](Values-from-main.md)
-   [Accessing Command-line
    Parameters](Command_002dline-Parameters.md)
-   [Accessing Environment Variables](Environment-Variables.md)
