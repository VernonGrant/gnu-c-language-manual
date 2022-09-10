Next: [Variables](Variables.md), Previous: [Defining Typedef
Names](Defining-Typedef-Names.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 19 Statements 


A *statement* specifies computations to be done for effect; it does not
produce a value, as an expression would. In general a statement ends
with a semicolon ('`;`'), but blocks (which are statements,
more or less) are an exception to that rule. See [Blocks](Blocks.md).

The places to use statements are inside a block, and inside a complex
statement. A *complex statement* contains one or two components that are
nested statements. Each such component must consist of one and only one
statement. The way to put multiple statements in such a component is to
group them into a *block* (see [Blocks](Blocks.md)), which counts as
one statement.

The following sections describe the various kinds of statement.

-   [Expression Statement](Expression-Statement.md)
-   [`if` Statement](if-Statement.md)
-   [`if-else` Statement](if_002delse-Statement.md)
-   [Blocks](Blocks.md)
-   [`return` Statement](return-Statement.md)
-   [Loop Statements](Loop-Statements.md)
-   [`switch` Statement](switch-Statement.md)
-   [Example of `switch`](switch-Example.md)
-   [Duff's Device](Duffs-Device.md)
-   [Case Ranges](Case-Ranges.md)
-   [Null Statement](Null-Statement.md)
-   [`goto` Statement and Labels](goto-Statement.md)
-   [Locally Declared Labels](Local-Labels.md)
-   [Labels as Values](Labels-as-Values.md)
-   [Statements and Declarations in Expressions](Statement-Exprs.md)
