Next: [Once-Only Headers](Once_002dOnly-Headers.md), Previous:
[`#include` Operation](include-Operation.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.4.3 Search Path 

GCC looks in several different places for header files to be included.
On the GNU system, and Unix systems, the default directories for system
header files are:

``` C
libdir/gcc/target/version/include
/usr/local/include
libdir/gcc/target/version/include-fixed
libdir/target/include
/usr/include/target
/usr/include
```

The list may be different in some operating systems. Other directories
are added for C++.

In the above, `target` is the canonical name of the system
GCC was configured to compile code for; often but not always the same as
the canonical name of the system it runs on. `version` is the
version of GCC in use.

You can add to this list with the `-Idir` command-line option.
All the directories named by `-I` are searched, in
left-to-right order, *before* the default directories. The only
exception is when `dir` is already searched by default. In this
case, the option is ignored and the search order for system directories
remains unchanged.

Duplicate directories are removed from the quote and bracket search
chains before the two chains are merged to make the final search chain.
Thus, it is possible for a directory to occur twice in the final search
chain if it was specified in both the quote and bracket chains.

You can prevent GCC from searching any of the default directories with
the `-nostdinc` option. This is useful when you are compiling
an operating system kernel or some other program that does not use the
standard C library facilities, or the standard C library itself.
`-I` options are not ignored as described above when
`-nostdinc` is in effect.

GCC looks for headers requested with `#include "file"` first in the
directory containing the current file, then in the *quote directories*
specified by `-iquote` options, then in the same places it
looks for a system header. For example, if
`/usr/include/sys/stat.h` contains `#include "types.h"`, GCC
looks for `types.h` first in `/usr/include/sys`, then
in the quote directories and then in its usual search path.

`#line` (see [Line Control](Line-Control.md)) does not change GCC's
idea of the directory containing the current file.


The `-I-` is an old-fashioned, deprecated way to specify the
quote directories. To look for headers in a directory named
`-`, specify `-I./-`. There are several more ways to
adjust the header search path. See [Invoking
GCC](https://gcc.gnu.org/onlinedocs/gcc/invocation.md#invocation) in
Using the GNU Compiler Collection.

------------------------------------------------------------------------

Next: [Once-Only Headers](Once_002dOnly-Headers.md), Previous:
[`#include` Operation](include-Operation.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
