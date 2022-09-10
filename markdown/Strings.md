Next: [Array Type Designators](Array-Type-Designators.md), Previous:
[Declaring an Array](Declaring-an-Array.md), Up: [Arrays](Arrays.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.3 Strings 


A string in C is a sequence of elements of type `char`, terminated with
the null character, the character with code zero.

Programs often need to use strings with specific, fixed contents. To
write one in a C program, use a *string constant* such as
`"Take me to your leader!"`. The data type of a string constant is
`char *`. For the full syntactic details of writing string constants,
[String Constants](String-Constants.md).

To declare a place to store a non-constant string, declare an array of
`char`. Keep in mind that it must include one extra `char` for the
terminating null. For instance,

``` C
char text[] = { 'H', 'e', 'l', 'l', 'o', 0 };
```

declares an array named '`text`' with six elements---five
letters and the terminating null character. An equivalent way to get the
same result is this,

``` C
char text[] = "Hello";
```

which copies the elements of the string constant, including *its*
terminating null character.

``` C
char message[200];
```

declares an array long enough to hold a string of 199 ASCII characters
plus the terminating null character.

When you store a string into `message` be sure to check or prove that
the length does not exceed its size. For example,

``` C
void
set_message (char *text)
{
  int i;
  for (i = 0; i < sizeof (message); i++)
    {
      message[i] = text[i];
      if (text[i] == 0)
        return;
    }
  fatal_error ("Message is too long for `message');
}
```

It's easy to do this with the standard library function `strncpy`, which
fills out the whole destination array (up to a specified length) with
null characters. Thus, if the last character of the destination is not
null, the string did not fit. Many system libraries, including the GNU C
library, hand-optimize `strncpy` to run faster than an explicit
`for`-loop.

Here's what the code looks like:

``` C
void
set_message (char *text)
{
  strncpy (message, text, sizeof (message));
  if (message[sizeof (message) - 1] != 0)
    fatal_error ("Message is too long for `message');
}
```

See [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/String-and-Array-Utilities.md#String-and-Array-Utilities)
in The GNU C Library Reference Manual, for more information about the
standard library functions for operating on strings.

You can avoid putting a fixed length limit on strings you construct or
operate on by allocating the space for them dynamically. See [Dynamic
Memory Allocation](Dynamic-Memory-Allocation.md).

------------------------------------------------------------------------

Next: [Array Type Designators](Array-Type-Designators.md), Previous:
[Declaring an Array](Declaring-an-Array.md), Up: [Arrays](Arrays.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
