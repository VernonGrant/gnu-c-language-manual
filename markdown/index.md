# GNU C Language Manual 

Next: [The First Example](The-First-Example.md)  
[Contents](#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


# GNU C Manual 

This manual explains the C language for use with the GNU Compiler
Collection (GCC) on the GNU/Linux system and other systems. We refer to
this dialect as GNU C. If you already know C, you can use this as a
reference manual.

If you understand basic concepts of programming but know nothing about
C, you can read this manual sequentially from the beginning to learn the
C language.

If you are a beginner in programming, we recommend you first learn a
language with automatic garbage collection and no explicit pointers,
rather than starting with C. Good choices include Lisp, Scheme, Python
and Java. C's explicit pointers mean that programmers must be careful to
avoid certain kinds of errors.

C is a venerable language; it was first used in 1973. The GNU C
Compiler, which was subsequently extended into the GNU Compiler
Collection, was first released in 1987. Other important languages were
designed based on C: once you know C, it gives you a useful base for
learning C++, C#, Java, Scala, D, Go, and more.

The special advantage of C is that it is fairly simple while allowing
close access to the computer's hardware, which previously required
writing in assembler language to describe the individual machine
instructions. Some have called C a "high-level assembler language"
because of its explicit pointers and lack of automatic management of
storage. As one wag put it, "C combines the power of assembler language
with the convenience of assembler language." However, C is far more
portable, and much easier to read and write, than assembler language.

This manual describes the GNU C language supported by the GNU Compiler
Collection, as of roughly 2017. Please inform us of any changes needed
to match the current version of GNU C.

When a construct may be absent or work differently in other C compilers,
we say so. When it is not part of ISO standard C, we say it is a "GNU C
extension," because it is useful to know that. However, standards and
other dialects are secondary topics for this manual. For simplicity's
sake, we keep those notes short, unless it is vital to say more.

Likewise, we hardly mention C++ or other languages that the GNU Compiler
Collection supports. We hope this manual will serve as a base for
writing manuals for those languages, but languages so different can't
share one common manual.

Some aspects of the meaning of C programs depend on the target platform:
which computer, and which operating system, the compiled code will run
on. Where this is the case, we say so.

The C language provides no built-in facilities for performing such
common operations as input/output, memory management, string
manipulation, and the like. Instead, these facilities are provided by
functions defined in the standard library, which is automatically
available in every C program. See [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/index.md#Top)
in The GNU C Library Reference Manual.

GNU/Linux systems use the GNU C Library to do this job. It is itself a C
program, so once you know C you can read its source code and see how its
library functions do their jobs. Some fraction of the functions are
implemented as *system calls*, which means they contain a special
instruction that asks the system kernel (Linux) to do a specific task.
To understand how those are implemented, you'd need to read Linux source
code instead. Whether a library function is a system call is an internal
implementation detail that makes no difference for how to call the
function.

This manual incorporates the former GNU C Preprocessor Manual, which was
among the earliest GNU manuals. It also uses some text from the earlier
GNU C Manual that was written by Trevis Rothwell and James Youngman.

GNU C has many obscure features, each one either for historical
compatibility or meant for very special situations. We have left them to
a companion manual, the GNU C Obscurities Manual, which will be
published digitally later.

Please report errors and suggestions to c-manual\@gnu.org.

## Table of Contents 

-   [1 The First
    Example](The-First-Example.md)
    -   [1.1 Example: Recursive
        Fibonacci](Recursive-Fibonacci.md)
        -   [1.1.1 Function
            Header](Function-Header.md)
        -   [1.1.2 Function
            Body](Function-Body.md)
    -   [1.2 The Stack, And Stack
        Overflow](Stack.md)
    -   [1.3 Example: Iterative
        Fibonacci](Iterative-Fibonacci.md)
-   [2 A Complete
    Program](Complete-Program.md)
    -   [2.1 Complete Program
        Example](Complete-Example.md)
    -   [2.2 Complete Program
        Explanation](Complete-Explanation.md)
    -   [2.3 Complete Program, Line by
        Line](Complete-Line_002dby_002dLine.md)
    -   [2.4 Compiling the Example
        Program](Compile-Example.md)
-   [3 Storage and Data](Storage.md)
-   [4 Beyond Integers](Beyond-Integers.md)
    -   [4.1 An Example with Non-Integer
        Numbers](Float-Example.md)
    -   [4.2 An Example with
        Arrays](Array-Example.md)
    -   [4.3 Calling the Array
        Example](Array-Example-Call.md)
    -   [4.4 Variations for Array
        Example](Array-Example-Variations.md)
-   [5 Lexical Syntax](Lexical-Syntax.md)
    -   [5.1 Write Programs in
        English!](English.md)
    -   [5.2 Characters](Characters.md)
    -   [5.3 Whitespace](Whitespace.md)
    -   [5.4 Comments](Comments.md)
    -   [5.5 Identifiers](Identifiers.md)
    -   [5.6 Operators and
        Punctuation](Operators_002fPunctuation.md)
    -   [5.7 Line
        Continuation](Line-Continuation.md)
-   [6 Arithmetic](Arithmetic.md)
    -   [6.1 Basic
        Arithmetic](Basic-Arithmetic.md)
    -   [6.2 Integer
        Arithmetic](Integer-Arithmetic.md)
    -   [6.3 Integer
        Overflow](Integer-Overflow.md)
        -   [6.3.1 Overflow with Unsigned
            Integers](Unsigned-Overflow.md)
        -   [6.3.2 Overflow with Signed
            Integers](Signed-Overflow.md)
    -   [6.4 Mixed-Mode
        Arithmetic](Mixed-Mode.md)
    -   [6.5 Division and
        Remainder](Division-and-Remainder.md)
    -   [6.6 Numeric
        Comparisons](Numeric-Comparisons.md)
    -   [6.7 Shift
        Operations](Shift-Operations.md)
        -   [6.7.1 Shifting Makes New
            Bits](Bits-Shifted-In.md)
        -   [6.7.2 Caveats for Shift
            Operations](Shift-Caveats.md)
        -   [6.7.3 Shift Hacks](Shift-Hacks.md)
    -   [6.8 Bitwise
        Operations](Bitwise-Operations.md)
-   [7 Assignment
    Expressions](Assignment-Expressions.md)
    -   [7.1 Simple
        Assignment](Simple-Assignment.md)
    -   [7.2 Lvalues](Lvalues.md)
    -   [7.3 Modifying
        Assignment](Modifying-Assignment.md)
    -   [7.4 Increment and Decrement
        Operators](Increment_002fDecrement.md)
    -   [7.5 Postincrement and
        Postdecrement](Postincrement_002fPostdecrement.md)
    -   [7.6 Pitfall: Assignment in
        Subexpressions](Assignment-in-Subexpressions.md)
    -   [7.7 Write Assignments in Separate
        Statements](Write-Assignments-Separately.md)
-   [8 Execution Control
    Expressions](Execution-Control-Expressions.md)
    -   [8.1 Logical
        Operators](Logical-Operators.md)
    -   [8.2 Logical Operators and
        Comparisons](Logicals-and-Comparison.md)
    -   [8.3 Logical Operators and
        Assignments](Logicals-and-Assignments.md)
    -   [8.4 Conditional
        Expression](Conditional-Expression.md)
        -   [8.4.1 Rules for the Conditional
            Operator](Conditional-Rules.md)
        -   [8.4.2 Conditional Operator
            Branches](Conditional-Branches.md)
    -   [8.5 Comma Operator](Comma-Operator.md)
        -   [8.5.1 The Uses of the Comma
            Operator](Uses-of-Comma.md)
        -   [8.5.2 Clean Use of the Comma
            Operator](Clean-Comma.md)
        -   [8.5.3 When Not to Use the Comma
            Operator](Avoid-Comma.md)
-   [9 Binary Operator
    Grammar](Binary-Operator-Grammar.md)
-   [10 Order of
    Execution](Order-of-Execution.md)
    -   [10.1 Reordering of
        Operands](Reordering-of-Operands.md)
    -   [10.2 Associativity and
        Ordering](Associativity-and-Ordering.md)
    -   [10.3 Sequence
        Points](Sequence-Points.md)
    -   [10.4 Postincrement and
        Ordering](Postincrement-and-Ordering.md)
    -   [10.5 Ordering of
        Operands](Ordering-of-Operands.md)
    -   [10.6 Optimization and
        Ordering](Optimization-and-Ordering.md)
-   [11 Primitive Data
    Types](Primitive-Types.md)
    -   [11.1 Integer Data
        Types](Integer-Types.md)
        -   [11.1.1 Basic
            Integers](Basic-Integers.md)
        -   [11.1.2 Signed and Unsigned
            Types](Signed-and-Unsigned-Types.md)
        -   [11.1.3 Narrow
            Integers](Narrow-Integers.md)
        -   [11.1.4 Conversion among Integer
            Types](Integer-Conversion.md)
        -   [11.1.5 Boolean
            Type](Boolean-Type.md)
        -   [11.1.6 Integer
            Variations](Integer-Variations.md)
    -   [11.2 Floating-Point Data
        Types](Floating_002dPoint-Data-Types.md)
    -   [11.3 Complex Data
        Types](Complex-Data-Types.md)
    -   [11.4 The Void Type](The-Void-Type.md)
    -   [11.5 Other Data
        Types](Other-Data-Types.md)
    -   [11.6 Type
        Designators](Type-Designators.md)
-   [12 Constants](Constants.md)
    -   [12.1 Integer
        Constants](Integer-Constants.md)
    -   [12.2 Integer Constant Data
        Types](Integer-Const-Type.md)
    -   [12.3 Floating-Point
        Constants](Floating-Constants.md)
    -   [12.4 Imaginary
        Constants](Imaginary-Constants.md)
    -   [12.5 Invalid
        Numbers](Invalid-Numbers.md)
    -   [12.6 Character
        Constants](Character-Constants.md)
    -   [12.7 String
        Constants](String-Constants.md)
    -   [12.8 UTF-8 String
        Constants](UTF_002d8-String-Constants.md)
    -   [12.9 Unicode Character
        Codes](Unicode-Character-Codes.md)
    -   [12.10 Wide Character
        Constants](Wide-Character-Constants.md)
    -   [12.11 Wide String
        Constants](Wide-String-Constants.md)
-   [13 Type Size](Type-Size.md)
-   [14 Pointers](Pointers.md)
    -   [14.1 Address of
        Data](Address-of-Data.md)
    -   [14.2 Pointer Types](Pointer-Types.md)
    -   [14.3 Pointer-Variable
        Declarations](Pointer-Declarations.md)
    -   [14.4 Pointer-Type
        Designators](Pointer-Type-Designators.md)
    -   [14.5 Dereferencing
        Pointers](Pointer-Dereference.md)
    -   [14.6 Null Pointers](Null-Pointers.md)
    -   [14.7 Dereferencing Null or Invalid
        Pointers](Invalid-Dereference.md)
    -   [14.8 Void Pointers](Void-Pointers.md)
    -   [14.9 Pointer
        Comparison](Pointer-Comparison.md)
    -   [14.10 Pointer
        Arithmetic](Pointer-Arithmetic.md)
    -   [14.11 Pointers and
        Arrays](Pointers-and-Arrays.md)
    -   [14.12 Pointer Arithmetic at
        Low-Level](Low_002dLevel-Pointer-Arithmetic.md)
    -   [14.13 Pointer Increment and
        Decrement](Pointer-Increment_002fDecrement.md)
    -   [14.14 Drawbacks of Pointer
        Arithmetic](Pointer-Arithmetic-Drawbacks.md)
    -   [14.15 Pointer-Integer
        Conversion](Pointer_002dInteger-Conversion.md)
    -   [14.16 Printing
        Pointers](Printing-Pointers.md)
-   [15 Structures](Structures.md)
    -   [15.1 Referencing Structure
        Fields](Referencing-Fields.md)
    -   [15.2 Dynamic Memory
        Allocation](Dynamic-Memory-Allocation.md)
    -   [15.3 Field Offset](Field-Offset.md)
    -   [15.4 Structure
        Layout](Structure-Layout.md)
    -   [15.5 Packed
        Structures](Packed-Structures.md)
    -   [15.6 Bit Fields](Bit-Fields.md)
    -   [15.7 Bit Field
        Packing](Bit-Field-Packing.md)
    -   [15.8 `const` Fields](const-Fields.md)
    -   [15.9 Arrays of Length
        Zero](Zero-Length.md)
    -   [15.10 Flexible Array
        Fields](Flexible-Array-Fields.md)
    -   [15.11 Overlaying Different
        Structures](Overlaying-Structures.md)
    -   [15.12 Structure
        Assignment](Structure-Assignment.md)
    -   [15.13 Unions](Unions.md)
    -   [15.14 Packing With
        Unions](Packing-With-Unions.md)
    -   [15.15 Cast to a Union
        Type](Cast-to-Union.md)
    -   [15.16 Structure
        Constructors](Structure-Constructors.md)
    -   [15.17 Unnamed Types as
        Fields](Unnamed-Types-as-Fields.md)
    -   [15.18 Incomplete
        Types](Incomplete-Types.md)
    -   [15.19 Intertwined Incomplete
        Types](Intertwined-Incomplete-Types.md)
    -   [15.20 Type Tags](Type-Tags.md)
-   [16 Arrays](Arrays.md)
    -   [16.1 Accessing Array
        Elements](Accessing-Array-Elements.md)
    -   [16.2 Declaring an
        Array](Declaring-an-Array.md)
    -   [16.3 Strings](Strings.md)
    -   [16.4 Array Type
        Designators](Array-Type-Designators.md)
    -   [16.5 Incomplete Array
        Types](Incomplete-Array-Types.md)
    -   [16.6 Limitations of C
        Arrays](Limitations-of-C-Arrays.md)
    -   [16.7 Multidimensional
        Arrays](Multidimensional-Arrays.md)
    -   [16.8 Constructing Array
        Values](Constructing-Array-Values.md)
    -   [16.9 Arrays of Variable
        Length](Arrays-of-Variable-Length.md)
-   [17 Enumeration
    Types](Enumeration-Types.md)
-   [18 Defining Typedef
    Names](Defining-Typedef-Names.md)
-   [19 Statements](Statements.md)
    -   [19.1 Expression
        Statement](Expression-Statement.md)
    -   [19.2 `if` Statement](if-Statement.md)
    -   [19.3 `if-else`
        Statement](if_002delse-Statement.md)
    -   [19.4 Blocks](Blocks.md)
    -   [19.5 `return`
        Statement](return-Statement.md)
    -   [19.6 Loop
        Statements](Loop-Statements.md)
        -   [19.6.1 `while`
            Statement](while-Statement.md)
        -   [19.6.2 `do-while`
            Statement](do_002dwhile-Statement.md)
        -   [19.6.3 `break`
            Statement](break-Statement.md)
        -   [19.6.4 `for`
            Statement](for-Statement.md)
        -   [19.6.5 Example of
            `for`](Example-of-for.md)
        -   [19.6.6 Omitted
            `for`-Expressions](Omitted-for_002dExpressions.md)
        -   [19.6.7 `for`-Index
            Declarations](for_002dIndex-Declarations.md)
        -   [19.6.8 `continue`
            Statement](continue-Statement.md)
    -   [19.7 `switch`
        Statement](switch-Statement.md)
    -   [19.8 Example of
        `switch`](switch-Example.md)
    -   [19.9 Duff's Device](Duffs-Device.md)
    -   [19.10 Case Ranges](Case-Ranges.md)
    -   [19.11 Null
        Statement](Null-Statement.md)
    -   [19.12 `goto` Statement and
        Labels](goto-Statement.md)
    -   [19.13 Locally Declared
        Labels](Local-Labels.md)
    -   [19.14 Labels as
        Values](Labels-as-Values.md)
        -   [19.14.1 Label Value
            Uses](Label-Value-Uses.md)
        -   [19.14.2 Label Value
            Caveats](Label-Value-Caveats.md)
    -   [19.15 Statements and Declarations in
        Expressions](Statement-Exprs.md)
-   [20 Variables](Variables.md)
    -   [20.1 Variable
        Declarations](Variable-Declarations.md)
        -   [20.1.1 Declaring Arrays and
            Pointers](Declaring-Arrays-and-Pointers.md)
        -   [20.1.2 Combining Variable
            Declarations](Combining-Variable-Declarations.md)
    -   [20.2 Initializers](Initializers.md)
    -   [20.3 Designated
        Initializers](Designated-Inits.md)
    -   [20.4 Referring to a Type with
        `__auto_type`](Auto-Type.md)
    -   [20.5 Local
        Variables](Local-Variables.md)
    -   [20.6 File-Scope
        Variables](File_002dScope-Variables.md)
    -   [20.7 Static Local
        Variables](Static-Local-Variables.md)
    -   [20.8 `extern`
        Declarations](Extern-Declarations.md)
    -   [20.9 Allocating File-Scope
        Variables](Allocating-File_002dScope.md)
    -   [20.10 `auto` and
        `register`](auto-and-register.md)
    -   [20.11 Omitting Types in
        Declarations](Omitting-Types.md)
-   [21 Type Qualifiers](Type-Qualifiers.md)
    -   [21.1 `const` Variables and
        Fields](const.md)
    -   [21.2 `volatile` Variables and
        Fields](volatile.md)
    -   [21.3 `restrict`-Qualified
        Pointers](restrict-Pointers.md)
    -   [21.4 `restrict` Pointer
        Example](restrict-Pointer-Example.md)
-   [22 Functions](Functions.md)
    -   [22.1 Function
        Definitions](Function-Definitions.md)
        -   [22.1.1 Function Parameter
            Variables](Function-Parameter-Variables.md)
        -   [22.1.2 Forward Function
            Declarations](Forward-Function-Declarations.md)
        -   [22.1.3 Static
            Functions](Static-Functions.md)
        -   [22.1.4 Arrays as
            Parameters](Arrays-as-Parameters.md)
            -   [22.1.4.1 Array parameters are
                pointers](Array-Parm-Pointer.md)
            -   [22.1.4.2 Passing array
                arguments](Passing-Array-Args.md)
            -   [22.1.4.3 Type qualifiers on array
                parameters](Array-Parm-Qualifiers.md)
        -   [22.1.5 Functions That Accept Structure
            Arguments](Structs-as-Parameters.md)
    -   [22.2 Function
        Declarations](Function-Declarations.md)
    -   [22.3 Function
        Calls](Function-Calls.md)
    -   [22.4 Function Call
        Semantics](Function-Call-Semantics.md)
    -   [22.5 Function
        Pointers](Function-Pointers.md)
        -   [22.5.1 Declaring Function
            Pointers](Declaring-Function-Pointers.md)
        -   [22.5.2 Assigning Function
            Pointers](Assigning-Function-Pointers.md)
        -   [22.5.3 Calling Function
            Pointers](Calling-Function-Pointers.md)
    -   [22.6 The `main`
        Function](The-main-Function.md)
        -   [22.6.1 Returning Values from
            `main`](Values-from-main.md)
        -   [22.6.2 Accessing Command-line
            Parameters](Command_002dline-Parameters.md)
        -   [22.6.3 Accessing Environment
            Variables](Environment-Variables.md)
    -   [22.7 Advanced Function
        Features](Advanced-Definitions.md)
        -   [22.7.1 Variable-Length Array
            Parameters](Variable_002dLength-Array-Parameters.md)
        -   [22.7.2 Variable-Length Parameter
            Lists](Variable-Number-of-Arguments.md)
        -   [22.7.3 Nested
            Functions](Nested-Functions.md)
        -   [22.7.4 Inline Function
            Definitions](Inline-Function-Definitions.md)
    -   [22.8 Obsolete Function
        Features](Obsolete-Definitions.md)
        -   [22.8.1 Older GNU C
            Inlining](Old-GNU-Inlining.md)
        -   [22.8.2 Old-Style Function
            Definitions](Old_002dStyle-Function-Definitions.md)
-   [23 Compatible
    Types](Compatible-Types.md)
-   [24 Type
    Conversions](Type-Conversions.md)
    -   [24.1 Explicit Type
        Conversion](Explicit-Type-Conversion.md)
    -   [24.2 Assignment Type
        Conversions](Assignment-Type-Conversions.md)
    -   [24.3 Argument
        Promotions](Argument-Promotions.md)
    -   [24.4 Operand
        Promotions](Operand-Promotions.md)
    -   [24.5 Common Type](Common-Type.md)
-   [25 Scope](Scope.md)
-   [26 Preprocessing](Preprocessing.md)
    -   [26.1 Preprocessing
        Overview](Preproc-Overview.md)
    -   [26.2 Directives](Directives.md)
    -   [26.3 Preprocessing
        Tokens](Preprocessing-Tokens.md)
    -   [26.4 Header Files](Header-Files.md)
        -   [26.4.1 `#include`
            Syntax](include-Syntax.md)
        -   [26.4.2 `#include`
            Operation](include-Operation.md)
        -   [26.4.3 Search Path](Search-Path.md)
        -   [26.4.4 Once-Only
            Headers](Once_002dOnly-Headers.md)
        -   [26.4.5 Computed
            Includes](Computed-Includes.md)
    -   [26.5 Macros](Macros.md)
        -   [26.5.1 Object-like
            Macros](Object_002dlike-Macros.md)
        -   [26.5.2 Function-like
            Macros](Function_002dlike-Macros.md)
        -   [26.5.3 Macro
            Arguments](Macro-Arguments.md)
        -   [26.5.4
            Stringification](Stringification.md)
        -   [26.5.5
            Concatenation](Concatenation.md)
        -   [26.5.6 Variadic
            Macros](Variadic-Macros.md)
        -   [26.5.7 Predefined
            Macros](Predefined-Macros.md)
        -   [26.5.8 Undefining and Redefining
            Macros](Undefining-and-Redefining-Macros.md)
        -   [26.5.9 Directives Within Macro
            Arguments](Directives-Within-Macro-Arguments.md)
        -   [26.5.10 Macro
            Pitfalls](Macro-Pitfalls.md)
            -   [26.5.10.1
                Misnesting](Misnesting.md)
            -   [26.5.10.2 Operator Precedence
                Problems](Operator-Precedence-Problems.md)
            -   [26.5.10.3 Swallowing the
                Semicolon](Swallowing-the-Semicolon.md)
            -   [26.5.10.4 Duplication of Side
                Effects](Duplication-of-Side-Effects.md)
            -   [26.5.10.5 Using `__auto_type` for Local
                Variables](Macros-and-Auto-Type.md)
            -   [26.5.10.6 Self-Referential
                Macros](Self_002dReferential-Macros.md)
            -   [26.5.10.7 Argument
                Prescan](Argument-Prescan.md)
    -   [26.6 Conditionals](Conditionals.md)
        -   [26.6.1 Uses of Conditional
            Directives](Conditional-Uses.md)
        -   [26.6.2 Syntax of Preprocessing
            Conditionals](Conditional-Syntax.md)
            -   [26.6.2.1 The `#ifdef`
                directive](ifdef.md)
            -   [26.6.2.2 The `#if`
                directive](if.md)
            -   [26.6.2.3 The `defined`
                test](defined.md)
            -   [26.6.2.4 The `#else`
                directive](else.md)
            -   [26.6.2.5 The `#elif`
                directive](elif.md)
        -   [26.6.3 Deleted
            Code](Deleted-Code.md)
    -   [26.7 Diagnostics](Diagnostics.md)
    -   [26.8 Line Control](Line-Control.md)
    -   [26.9 Null
        Directive](Null-Directive.md)
-   [27 Integers in
    Depth](Integers-in-Depth.md)
    -   [27.1 Integer
        Representations](Integer-Representations.md)
    -   [27.2 Maximum and Minimum
        Values](Maximum-and-Minimum-Values.md)
-   [28 Floating Point in
    Depth](Floating-Point-in-Depth.md)
    -   [28.1 Floating-Point
        Representations](Floating-Representations.md)
    -   [28.2 Floating-Point Type
        Specifications](Floating-Type-Specs.md)
    -   [28.3 Special Floating-Point
        Values](Special-Float-Values.md)
    -   [28.4 Invalid
        Optimizations](Invalid-Optimizations.md)
    -   [28.5 Floating Arithmetic Exception
        Flags](Exception-Flags.md)
    -   [28.6 Exact Floating-Point
        Arithmetic](Exact-Floating_002dPoint.md)
    -   [28.7 Rounding](Rounding.md)
    -   [28.8 Rounding
        Issues](Rounding-Issues.md)
    -   [28.9 Significance
        Loss](Significance-Loss.md)
    -   [28.10 Fused
        Multiply-Add](Fused-Multiply_002dAdd.md)
    -   [28.11 Error
        Recovery](Error-Recovery.md)
    -   [28.12 Exact Floating-Point
        Constants](Exact-Floating-Constants.md)
    -   [28.13 Handling
        Infinity](Handling-Infinity.md)
    -   [28.14 Handling NaN](Handling-NaN.md)
    -   [28.15 Signed Zeros](Signed-Zeros.md)
    -   [28.16 Scaling by Powers of the
        Base](Scaling-by-the-Base.md)
    -   [28.17 Rounding
        Control](Rounding-Control.md)
    -   [28.18 Machine
        Epsilon](Machine-Epsilon.md)
    -   [28.19 Complex
        Arithmetic](Complex-Arithmetic.md)
    -   [28.20 Round-Trip Base
        Conversion](Round_002dTrip-Base-Conversion.md)
    -   [28.21 Further
        Reading](Further-Reading.md)
-   [29 Compilation](Compilation.md)
-   [30 Directing
    Compilation](Directing-Compilation.md)
    -   [30.1 Pragmas](Pragmas.md)
        -   [30.1.1 Pragma
            Basics](Pragma-Basics.md)
        -   [30.1.2 Severity
            Pragmas](Severity-Pragmas.md)
        -   [30.1.3 Optimization
            Pragmas](Optimization-Pragmas.md)
    -   [30.2 Static
        Assertions](Static-Assertions.md)
-   [Appendix A Type
    Alignment](Type-Alignment.md)
-   [Appendix B Aliasing](Aliasing.md)
    -   [B.1 Aliasing and
        Alignment](Aliasing-Alignment.md)
    -   [B.2 Aliasing and
        Length](Aliasing-Length.md)
    -   [B.3 Type Rules for
        Aliasing](Aliasing-Type-Rules.md)
-   [Appendix C Digraphs](Digraphs.md)
-   [Appendix D Attributes in
    Declarations](Attributes.md)
-   [Appendix E Signals](Signals.md)
-   [Appendix F GNU Free Documentation
    License](GNU-Free-Documentation-License.md)
-   [Index of Symbols and
    Keywords](Symbol-Index.md)
-   [Concept Index](Concept-Index.md)

## Short Table of Contents 

-   [1 The First
    Example](#toc-The-First-Example-1)
-   [2 A Complete
    Program](#toc-A-Complete-Program)
-   [3 Storage and Data](#toc-Storage-and-Data)
-   [4 Beyond Integers](#toc-Beyond-Integers-1)
-   [5 Lexical Syntax](#toc-Lexical-Syntax-1)
-   [6 Arithmetic](#toc-Arithmetic-1)
-   [7 Assignment
    Expressions](#toc-Assignment-Expressions-1)
-   [8 Execution Control
    Expressions](#toc-Execution-Control-Expressions-1)
-   [9 Binary Operator
    Grammar](#toc-Binary-Operator-Grammar-1)
-   [10 Order of
    Execution](#toc-Order-of-Execution-1)
-   [11 Primitive Data
    Types](#toc-Primitive-Data-Types)
-   [12 Constants](#toc-Constants-1)
-   [13 Type Size](#toc-Type-Size-1)
-   [14 Pointers](#toc-Pointers-1)
-   [15 Structures](#toc-Structures-1)
-   [16 Arrays](#toc-Arrays-1)
-   [17 Enumeration
    Types](#toc-Enumeration-Types-1)
-   [18 Defining Typedef
    Names](#toc-Defining-Typedef-Names-1)
-   [19 Statements](#toc-Statements-1)
-   [20 Variables](#toc-Variables-1)
-   [21 Type
    Qualifiers](#toc-Type-Qualifiers-1)
-   [22 Functions](#toc-Functions-1)
-   [23 Compatible
    Types](#toc-Compatible-Types-1)
-   [24 Type
    Conversions](#toc-Type-Conversions-1)
-   [25 Scope](#toc-Scope-1)
-   [26 Preprocessing](#toc-Preprocessing-1)
-   [27 Integers in
    Depth](#toc-Integers-in-Depth-1)
-   [28 Floating Point in
    Depth](#toc-Floating-Point-in-Depth-1)
-   [29 Compilation](#toc-Compilation-1)
-   [30 Directing
    Compilation](#toc-Directing-Compilation-1)
-   [Appendix A Type
    Alignment](#toc-Type-Alignment-1)
-   [Appendix B Aliasing](#toc-Aliasing-1)
-   [Appendix C Digraphs](#toc-Digraphs-1)
-   [Appendix D Attributes in
    Declarations](#toc-Attributes-in-Declarations)
-   [Appendix E Signals](#toc-Signals-1)
-   [Appendix F GNU Free Documentation
    License](#toc-GNU-Free-Documentation-License-1)
-   [Index of Symbols and
    Keywords](#toc-Index-of-Symbols-and-Keywords)
-   [Concept Index](#toc-Concept-Index-1)

------------------------------------------------------------------------

Next: [The First Example](The-First-Example.md)  
[Contents](#SEC_Contents "Table of contents")  
