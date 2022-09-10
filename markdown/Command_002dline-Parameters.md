Next: [Accessing Environment Variables](Environment-Variables.md),
Previous: [Returning Values from `main`](Values-from-main.md), Up:
[The `main` Function](The-main-Function.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.6.2 Accessing Command-line Parameters 


If the program was invoked with any command-line arguments, it can
access them through the arguments of `main`, `argc` and `argv`. (You can
give these arguments any names, but the names `argc` and `argv` are
customary.)

The value of `argv` is an array containing all of the command-line
arguments as strings, with the name of the command invoked as the first
string. `argc` is an integer that says how many strings `argv` contains.
Here is an example of accessing the command-line parameters, retrieving
the program's name and checking for the standard `--version`
and `--help` options:

``` C
#include <string.h> /* Declare strcmp. */

int
main (int argc, char *argv[])
{
  char *program_name = argv[0];

  for (int i = 1; i < argc; i++)
    {
      if (!strcmp (argv[i], "--version"))
        {
          /* Print version information and exit. */
          …
        }
      else if (!strcmp (argv[i], "--help"))
        {
          /* Print help information and exit. */
          …
        }
    }
  …
}
```
