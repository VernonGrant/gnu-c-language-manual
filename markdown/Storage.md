Next: [Beyond Integers](Beyond-Integers.md), Previous: [A Complete
Program](Complete-Program.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 3 Storage and Data 


Storage in C programs is made up of units called *bytes*. A byte is the
smallest unit of storage that can be used in a first-class manner.

On nearly all computers, a byte consists of 8 bits. There are a few
peculiar computers (mostly "embedded controllers" for very small
systems) where a byte is longer than that, but this manual does not try
to explain the peculiarity of those computers; we assume that a byte is
8 bits.

Every C data type is made up of a certain number of bytes; that number
is the data type's *size*. See [Type Size](Type-Size.md), for details.
The types `signed char` and `unsigned char` are one byte long; use those
types to operate on data byte by byte. See [Signed and Unsigned
Types](Signed-and-Unsigned-Types.md). You can refer to a series of
consecutive bytes as an array of `char` elements; that's what a
character string looks like in memory. See [String
Constants](String-Constants.md).
