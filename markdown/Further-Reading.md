Previous: [Round-Trip Base
Conversion](Round_002dTrip-Base-Conversion.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.21 Further Reading 

The subject of floating-point arithmetic is much more complex than many
programmers seem to think, and few books on programming languages spend
much time in that area. In this chapter, we have tried to expose the
reader to some of the key ideas, and to warn of easily overlooked
pitfalls that can soon lead to nonsensical results. There are a few good
references that we recommend for further reading, and for finding other
important material about computer arithmetic:

-   Paul H. Abbott and 15 others, Architecture and software support in
    IBM S/390 Parallel Enterprise Servers for IEEE Floating-Point
    arithmetic, IBM Journal of Research and Development **43**(5/6)
    723--760 (1999), <https://doi.org/10.1147/rd.435.0723>. This article
    gives a good description of IBM's algorithm for exact
    decimal-to-binary conversion, complementing earlier ones by Clinger
    and others.
-   Nelson H. F. Beebe, The Mathematical-Function Computation Handbook:
    Programming Using the MathCW Portable Software Library, Springer
    (2017), ISBN 3-319-64109-3 (hardcover), 3-319-64110-7 (e-book)
    (xxxvi + 1114 pages), <https://doi.org/10.1007/978-3-319-64110-2>.
    This book describes portable implementations of a large superset of
    the mathematical functions available in many programming languages,
    extended to a future 256-bit format (70 decimal digits), for both
    binary and decimal floating point. It includes a substantial portion
    of the functions described in the famous NIST Handbook of
    Mathematical Functions, Cambridge (2018), ISBN 0-521-19225-0. See
    <http://www.math.utah.edu/pub/mathcw> for compilers and libraries.
-   William D. Clinger, How to Read Floating Point Numbers Accurately,
    ACM SIGPLAN Notices **25**(6) 92--101 (June 1990),
    <https://doi.org/10.1145/93548.93557>. See also the papers by Steele
    & White.
-   William D. Clinger, Retrospective: How to read floating point
    numbers accurately, ACM SIGPLAN Notices **39**(4) 360--371 (April
    2004), <http://doi.acm.org/10.1145/989393.989430>. Reprint of 1990
    paper, with additional commentary.
-   I. Bennett Goldberg, 27 Bits Are Not Enough For 8-Digit Accuracy,
    Communications of the ACM **10**(2) 105--106 (February 1967),
    <http://doi.acm.org/10.1145/363067.363112>. This paper, and its
    companions by David Matula, address the base-conversion problem, and
    show that the naive formulas are wrong by one or two digits.
-   David Goldberg, What Every Computer Scientist Should Know About
    Floating-Point Arithmetic, ACM Computing Surveys **23**(1) 5--58
    (March 1991), corrigendum **23**(3) 413 (September 1991),
    <https://doi.org/10.1145/103162.103163>. This paper has been widely
    distributed, and reissued in vendor programming-language
    documentation. It is well worth reading, and then rereading from
    time to time.
-   Norbert Juffa and Nelson H. F. Beebe, A Bibliography of Publications
    on Floating-Point Arithmetic,
    <http://www.math.utah.edu/pub/tex/bib/fparith.bib>. This is the
    largest known bibliography of publications about floating-point, and
    also integer, arithmetic. It is actively maintained, and in mid
    2019, contains more than 6400 references to original research
    papers, reports, theses, books, and Web sites on the subject matter.
    It can be used to locate the latest research in the field, and the
    historical coverage dates back to a 1726 paper on signed-digit
    arithmetic, and an 1837 paper by Charles Babbage, the intellectual
    father of mechanical computers. The entries for the Abbott, Clinger,
    and Steele & White papers cited earlier contain pointers to several
    other important related papers on the base-conversion problem.
-   William Kahan, Branch Cuts for Complex Elementary Functions, or Much
    Ado About Nothing's Sign Bit, (1987),
    <http://people.freebsd.org/~das/kahan86branch.pdf>. This Web
    document about the fine points of complex arithmetic also appears in
    the volume edited by A. Iserles and M. J. D. Powell, The State of
    the Art in Numerical Analysis: Proceedings of the Joint IMA/SIAM
    Conference on the State of the Art in Numerical Analysis held at the
    University of Birmingham, 14--18 April 1986, Oxford University Press
    (1987), ISBN 0-19-853614-3 (xiv + 719 pages). Its author is the
    famous chief architect of the IEEE 754 arithmetic system, and one of
    the world's greatest experts in the field of floating-point
    arithmetic. An entire generation of his students at the University
    of California, Berkeley, have gone on to careers in academic and
    industry, spreading the knowledge of how to do floating-point
    arithmetic right.
-   Donald E. Knuth, A Simple Program Whose Proof Isn't, in Beauty is
    our business: a birthday salute to Edsger W. Dijkstra, W. H. J.
    Feijen, A. J. M. van Gasteren, D. Gries, and J. Misra (eds.),
    Springer (1990), ISBN 1-4612-8792-8,
    <https://doi.org/10.1007/978-1-4612-4476-9>. This book chapter
    supplies a correctness proof of the decimal to binary, and binary to
    decimal, conversions in fixed-point arithmetic in the TeX
    typesetting system. The proof evaded its author for a dozen years.
-   David W. Matula, In-and-out conversions, Communications of the ACM
    **11**(1) 57--50 (January 1968),
    <https://doi.org/10.1145/362851.362887>.
-   David W. Matula, The Base Conversion Theorem, Proceedings of the
    American Mathematical Society **19**(3) 716--723 (June 1968). See
    also other papers here by this author, and by I. Bennett Goldberg.
-   David W. Matula, A Formalization of Floating-Point Numeric Base
    Conversion, IEEE Transactions on Computers **C-19**(8) 681--692
    (August 1970), <https://doi.org/10.1109/T-C.1970.223017>.
-   Jean-Michel Muller and eight others, Handbook of Floating-Point
    Arithmetic, Birkhäuser-Boston (2010), ISBN 0-8176-4704-X (xxiii +
    572 pages), <https://doi.org/10.1007/978-0-8176-4704-9>. This is a
    comprehensive treatise from a French team who are among the world's
    greatest experts in floating-point arithmetic, and among the most
    prolific writers of research papers in that field. They have much to
    teach, and their book deserves a place on the shelves of every
    serious numerical programmer.
-   Jean-Michel Muller and eight others, Handbook of Floating-Point
    Arithmetic, Second edition, Birkhäuser-Boston (2018), ISBN
    3-319-76525-6 (xxv + 627 pages),
    <https://doi.org/10.1007/978-3-319-76526-6>. This is a new edition
    of the preceding entry.
-   Michael Overton, Numerical Computing with IEEE Floating Point
    Arithmetic, Including One Theorem, One Rule of Thumb, and One
    Hundred and One Exercises, SIAM (2001), ISBN 0-89871-482-6 (xiv +
    104 pages), <http://www.ec-securehost.com/SIAM/ot76.md>. This is a
    small volume that can be covered in a few hours.
-   Guy L. Steele Jr. and Jon L. White, How to Print Floating-Point
    Numbers Accurately, ACM SIGPLAN Notices **25**(6) 112--126 (June
    1990), <https://doi.org/10.1145/93548.93559>. See also the papers by
    Clinger.
-   Guy L. Steele Jr. and Jon L. White, Retrospective: How to Print
    Floating-Point Numbers Accurately, ACM SIGPLAN Notices **39**(4)
    372--389 (April 2004), <http://doi.acm.org/10.1145/989393.989431>.
    Reprint of 1990 paper, with additional commentary.
-   Pat H. Sterbenz, Floating Point Computation, Prentice-Hall (1974),
    ISBN 0-13-322495-3 (xiv + 316 pages). This often-cited book provides
    solid coverage of what floating-point arithmetic was like *before*
    the introduction of IEEE 754 arithmetic.

------------------------------------------------------------------------

Previous: [Round-Trip Base
Conversion](Round_002dTrip-Base-Conversion.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
