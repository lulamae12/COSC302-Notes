# Bit Arithmetic and Operations

Lecture notes Link: http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Bits/


## C/C++ Operators

Here is a simple table of bit arithmetic operators

| Operatrion | Operator |
| ----------- | ----------- |
|AND: this is a single ampersand:|	& |
|OR: this is a single vertical bar:| \| |
|XOR: this is a single carat: |	^ |
|NOT: this is a single tilde: |	~ |
|Left-shift: this is two less-than signs: |	<< |
|Right-shift: this is two greater-than signs: |	>> |



# AND ( & )

Anything AND 0 = 0

Examples:

- 0 & 0 = 0
- 1 & 0 = 0
- 1 & 1 = 1

```
5 & 9 = 1

5 = 0101
9 = 1001
    ----
    0001 -- The AND of each bit gives you 0001 in binary, which is 1.
```

# OR ( | )

Anything OR 1 = 1

Examples:

- 0 | 0 = 0
- 1 | 0 = 1
- 1 | 1 = 1


# XOR ( ^ )

XOR is Addition % 2 (2's Complement)

Examples:
```
5 ^ 9 = 12

5 = 0101
9 = 1001
    ----
    1100 -- The XOR of each bit gives you 1100 in binary, which is 12.

```


# NOT ( ~ )

NOT Inverts or Flips bits

Examples:

- ~0 = 1
- ~1 = 0

# Left Shift ( << )

you move each bit n binary digits to the left. The n right-most bits will be set to zero, and any bits which started out within n binary digits of the left end of the word, will be deleted.

usage: n << number to shift by

Example:

```

left-shift 3 by two digits

3 = 00000011

3 << 2 = 24

00000011 << 2 = 00001100

```


# Right Shift ( >> )

you move each bit n binary digits to the  right. The n left-most bits will be set to zero, and any bits which started out within n binary digits of the right end of the word, will be deleted.

usage: n >> number to shift by

Example:

```

right-shift 24 by two digits

42 = 00001100

24 >> 2 = 3

00001100 >> 2 = 00000011

```


# Clearing a Bit

To make sure that bit x is not set in a number, you take the AND of the number with the NOT of the number (one left-shifted by x)

Example:
```

clear bit x of number n

n &= (~(1ULL << x));


```



# Intersection (Test Question)

```

Returns Y ∩ X

y & (1 << x);

```