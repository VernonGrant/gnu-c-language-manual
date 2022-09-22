Next: [Incomplete Types](Incomplete-Types.md), Previous: [Structure
Constructors](Structure-Constructors.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.18 Unnamed Types as Fields 


A structure or a union can contain, as fields, unnamed structures and
unions. Here's an example:

``` C
struct
{
  int a;
  union
  {
    int b;
    float c;
  };
  int d;
} foo;
```

You can access the fields of the unnamed union within `foo` as if they
were individual fields at the same level as the union definition:

``` C
foo.a = 42;
foo.b = 47;
foo.c = 5.25; // Overwrites the value in foo.b.
foo.d = 314;
```

Avoid using field names that could cause ambiguity. For example, with
this definition:

``` C
struct
{
  int a;
  struct
  {
    int a;
    float b;
  };
} foo;
```

it is impossible to tell what `foo.a` refers to. GNU C reports an error
when a definition is ambiguous in this way.
