Next: [Duff's Device](Duffs-Device.md), Previous: [`switch`
Statement](switch-Statement.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.8 Example of `switch` 

Here's an example of using the `switch` statement to distinguish among
characters:


``` C
struct vp { int vowels, punct; };

struct vp
count_vowels_and_punct (char *string)
{
  int c;
  int vowels = 0;
  int punct = 0;
  /* Don’t change the parameter itself.  */
  /* That helps in debugging.  */
  char *p = string;
  struct vp value;

  while (c = *p++)
    switch (c)
      {
        case 'y':
        case 'Y':
          /* We assume y_is_consonant will check surrounding
                letters to determine whether this y is a vowel.  */
          if (y_is_consonant (p - 1))
            break;

          /* Falls through */

        case 'a':
        case 'e':
        case 'i':
        case 'o':
        case 'u':
        case 'A':
        case 'E':
        case 'I':
        case 'O':
        case 'U':
          vowels++;
          break;

        case '.':
        case ',':
        case ':':
        case ';':
        case '?':
        case '!':
        case '\"':
        case '\'':
          punct++;
          break;
      }

  value.vowels = vowels;
  value.punct = punct;

  return value;
}
```
