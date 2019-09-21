# Alien sums

(Use this FileName pattern for submissions: __aliensum__) 

## Problem

Scientists at Las Cruces detected an extraterrestrial radio signal,
which they believe is a series of 8-bit codes, packed in groups of
three, like the following:

```
A:  48 48 49 48
B:  49 48 49 48
C:  49 48 48 49 
```

Our scientists suspect that ultimate purpose of those messages is
teaching us their numbering systems. So far, we suspect that each
group encodes a base-n number, least significant digit first, and that
it must follow A+B=C. Both the base and the mapping from 8-bit codes
to digits are unknown. However, since aliens are definitely belevolent
and sympathetic, all the additions they send us have a unique mapping.

For example, the numbers in the stream above may represent the
addition (note that least significant digit is the last now):
```
  48 49 48 48
+ 48 49 48 49
-------------
  49 48 48 49
```
which has a unique mapping and base:
```
 48 ---> digit 0
 49 ---> digit 1
```
So in this case the numering system is binary, with our natural ASCII
encoding for 0 (48) and 1 (49). No other assignment makes the equation
A+B=C work.

## Input format:

An input file for LP systems contains the following facts:

- Facts `a(I,C)`, `b(I,C)`, `c(I,C)`, where `I` is the position in the
  stream (0 is the least significant digit), and `C` is a 8-bit
  number.

## Output format:

The output should contain facts of the form `decode(C,D)`, for each
different `C` appearing in any of the `a/2`, `b/2`, or `c/2` facts
above, and `D` is a number (the digit value corresponding to that
code).

## Example instances:

### Instance 1

Input:
```
a(0,48). a(1,48). a(2,49). a(3,48).
b(0,49). b(1,48). b(2,49). b(3,48).
c(0,49). c(1,48). c(2,48). c(3,49).
```

Output:
```
decode(48,0). % 0 --> 0
decode(49,1). % 1 --> 1
```

### Instance 2

Input:
```
%  cudcuc
% +ctucuu
% -------
%  uctcdu

a(0,99).  a(1,117). a(2,99). a(3,100). a(4,117). a(5,99).
b(0,117). b(1,117). b(2,99). b(3,117). b(4,116). b(5,99).
c(0,117). c(1,100). c(2,99). c(3,116). c(4,99).  c(5,117).
```

Output:
```
decode(99,0).  % c --> 0
decode(117,1). % u --> 1
decode(100,2). % d --> 2
decode(116,3). % t --> 3
```

