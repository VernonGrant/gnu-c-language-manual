Next: [Type Tags](Type-Tags.md), Previous: [Incomplete
Types](Incomplete-Types.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.19 Intertwined Incomplete Types 

When several structure types contain pointers to each other, you can
define the types in any order because pointers to types that come later
are incomplete types. Thus, Here is an example.

``` C
/* An employee record points to a group.  */
struct employee
{
  char *name;
  …
  struct group *group;  /* incomplete type.  */
  …
};

/* An employee list points to employees.  */
struct employee_list
{
  struct employee *this_one;
  struct employee_list *next;  /* incomplete type.  */
  …
};
  
/* A group points to one employee_list.  */
struct group
{
  char *name;
  …
  struct employee_list *employees;
  …
};
```
