# Binary four fours

(Use this FileName pattern for submissions: __binfours__) 

## Problem

Four is the sacred number for the Zia tribe. It is embodied in many
aspects of our world: the four cardinal directions, the four seasons
of the year, periods of each day (morning, noon, evening, and night),
seasons of life (childhood, youth, middle years, and old age), and the
sacred obligations one must develop (strong body, clear mind, pure
spirit, and work for the benefit of mankind). It also appears in the
Zia Sun Symbol, featured in the flag of New Mexico, a red circle with
groups of rays pointing in four directions, each group consisting of
four rays.

![](zia.png)

In this problem you will be asked to contribute to the greatness of
number four repeated four times.

Four fours is a well known a mathematical puzzle, where the goal is to
find a simple mathematical expression for expressing a given integer
using only mathematical symbols and exactly four fours.

In the digital age, we present a variation where expressions are
computed as 8-bit arithmetic (wrapping, i.e., 255+1 evaluates to 0, -1
evaluates to 255) using the following operators:

 - `x+y`: addition
 - `x*y`: multiplication
 - `-x`: negation
 - `~x`: bitwise not

For any given 8-bit input number (0 to 255) you must find an
expression that express that number, using exactly 4 digits and up to
8 operators (no more than 12 symbols). For example, the expressions on
the left (valid C, Lua, or Python expressions, or Prolog replacing `~`
by `\`) compute the numbers on the right:

```
4*4*4*4            ---> 0 (modulo 256)
4+(-(4+4+(~4)))    ---> 1
4+(-(4+(~4)+(~4))) ---> 10
4+4+(~(4+4))       ---> 255 (modulo 256)
```

To avoid the use of parenthesis, your output should use reverse Polish
notation (e.g., `4+(-(4+4+(~4)))` is represented as `4444~++-+`).

Some hints:

 - The combination `-(~x)` increments `x`. It could be used to any
   arbitrary number using just one 4, but you may not go too far
   before consuming the 12 symbols limit (note that other four fours
   puzzle variations do not impose a limit on the number of symbols).

 - To reduce the search space, as an heuristic you may restrict the
   expressions using `+` and `*` to `4+(~x)`, `(-4)+(~x)`,
   `(~4)+(~x)`, `4*(~x)`, `(-4)*(~x)`, `(~4)*(~x)`.

 - Since there may be more than one possible solution (any of them
   will be considered correct).

## Input

The input is a single fact `n(N)` specifying the 0-255 integer that
must be expressed as an arithmetic expression using the operators
described above.

## Output

The output must be a fact `op(I,Op)` encoding the expression in
reverse Polish notation, where `I` represents the position in the
sequence of operations, and `Op` can be one of:
```
  4 ---> number 4
mul ---> multiplication (*)
add ---> addition (+)
neg ---> negation (-)
not ---> bitwise not (~)
```

## Examples

### Instance 1

Input:
```
n(0).
```

Output:
```
% 4444***
op(0,4).
op(1,4).
op(2,4).
op(3,4).
op(4,mul).
op(5,mul).
op(6,mul).
```

### Instance 2

Input:
```
n(1).
```

Output:
```
% 4444~++-+
op(0,4).
op(1,4).
op(2,4).
op(3,4).
op(4,not).
op(5,add).
op(6,add).
op(7,neg).
op(8,add).
```

### Instance 3

Input:
```
n(10).
```

Output:
```
% 444~4~++-+
op(0,4).
op(1,4).
op(2,4).
op(3,not).
op(4,4).
op(5,not).
op(6,add).
op(7,add).
op(8,neg).
op(9,add).
```

### Instance 4

Input:
```
n(255).
```

Output:
```
% 4444+~++
op(0,4).
op(1,4).
op(2,4).
op(3,4).
op(4,add).
op(5,not).
op(6,add).
op(7,add).
```