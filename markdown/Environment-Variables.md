Previous: [Accessing Command-line
Parameters](Command_002dline-Parameters.md), Up: [The `main`
Function](The-main-Function.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.6.3 Accessing Environment Variables 


You can optionally include a third parameter to `main`, another array of
strings, to capture the environment variables available to the program.
Unlike what happens with `argv`, there is no additional parameter for
the count of environment variables; rather, the array of environment
variables concludes with a null pointer.

``` C
#include <stdio.h>   /* Declares printf. */

int
main (int argc, char *argv[], char *envp[])
{
  /* Print out all environment variables. */
  int i = 0;
  while (envp[i])
    {
      printf ("%s\n", envp[i]);
      i++;
    }
}
```

Another method of retrieving environment variables is to use the library
function `getenv`, which is defined in `stdlib.h`. Using `getenv` does
not require defining `main` to accept the `envp` pointer. For example,
here is a program that fetches and prints the user's home directory (if
defined):

``` C
#include <stdlib.h>  /* Declares getenv. */
#include <stdio.h>   /* Declares printf. */

int
main (void)
{
  char *home_directory = getenv ("HOME");
  if (home_directory)
    printf ("My home directory is: %s\n", home_directory);
  else
    printf ("My home directory is not defined!\n");
}
```
