Next: [Search Path](Search-Path.md), Previous: [`#include`
Syntax](include-Syntax.md), Up: [Header Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.4.2 `#include` Operation 

The `#include` directive works by scanning the specified header file as
input before continuing with the rest of the current file. The result of
preprocessing consists of the text already generated, followed by the
result of preprocessing the included file, followed by whatever results
from the text after the `#include` directive. For example, if you have a
header file `header.h` as follows,

``` C
char *test (void);
```

and a main program called `program.c` that uses the header
file, like this,

``` C
int x;
#include "header.h"

int
main (void)
{
  puts (test ());
}
```

the result is equivalent to putting this text in `program.c`:

``` C
int x;
char *test (void);

int
main (void)
{
  puts (test ());
}
```

Included files are not limited to declarations and macro definitions;
those are merely the typical uses. Any fragment of a C program can be
included from another file. The include file could even contain the
beginning of a statement that is concluded in the containing file, or
the end of a statement that was started in the including file. However,
an included file must consist of complete tokens. Comments and string
literals that have not been closed by the end of an included file are
invalid. For error recovery, the compiler terminates them at the end of
the file.

To avoid confusion, it is best if header files contain only complete
syntactic units---function declarations or definitions, type
declarations, etc.

The line following the `#include` directive is always treated as a
separate line, even if the included file lacks a final newline. There is
no problem putting a preprocessing directive there.

------------------------------------------------------------------------

Next: [Search Path](Search-Path.md), Previous: [`#include`
Syntax](include-Syntax.md), Up: [Header Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
