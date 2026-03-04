## Table of contents

1. [Section 2.1 Information Storage](#section-21-information-storage)
   1. [Page 73, Practice Problem 2.1](#page-73-practice-problem-21-solution-page-179)
2. [Section 2.2 Integer Representations](#section-22-integer-representations)
   1. [Page 94, Practice Problem 2.16](#page-94-practice-problem-216-solution-page-184)
   2. [Page 118, Practice Problem 2.24](#page-118-practice-problem-224-solution-page-186)
3. [Section 2.3 Integer Arithmetic](#section-23-integer-arithmetic)
   1. [Page 131, Practice Problem 2.33](#page-131-practice-problem-233-solution-page-189)
4. [Section 2.4 Floating Point](#section-24-floating-point)
   1. [Page 147, Practice Problem 2.45](#page-147-practice-problem-245-solution-page-193)

---
  
## Section 2.1 Information Storage
### Page 73, Practice Problem 2.1 <small>(solution page 179)</small>

#### A. **0x25B9D2 to binary**

- The solution given in the book converts $B_{16}$ to $1101_2$, which is incorrect, since $1101_2$ corresponds to $D_{16}$ 

The correct solution is:

| Hex | Binary | 
| --- | --- |
2 | 0010
5 | 0101
B | 1011
9 | 1001
D | 1101
2 | 0010

Thus, the full answer should be: 
```
0010 0101 1011 1001 1101 0010
```

#### B. **Binary 1010 1110 0100 1001 to decimal**

- The answer provided in the Global Edition of the book corresponds to the question from the North American Edition. Because the binary number given in the Global Edition is different, the answer presented there is incorrect.

The correct solution is:

| Binary | Hex | 
| --- | --- | 
| 1010 | A |
| 1110 | E | 
| 0100 | 4 | 
| 1001 | 9

Therefore, the answer is:
```
0xAE49
```


## Section 2.2 Integer Representations

### Page 94, Practice Problem 2.16 <small>(solution page 184)</small>

- There are two simple binary to hex conversion mistakes in the last column. 

The solution is:

**Arithmetic a \>\> 3 table:**
| Binary	|  Hex	|
| --- | --- |
| \[1111 1010\] | 0xFA  |
| \[0000 1100\] | 0x0C	|
| \[0000 1110\] | 0x0E	|
| \[0000 1000\] | 0x08	|

### Page 118, Practice Problem 2.24 <small>(solution page 186)</small>

- The last 3 rows of the Two's Complement Truncated column are wrong. I’m guessing the editors made a mistake and simply repeated the same three results of the Unsigned Truncated column here for some reason. They show 5, 4 and 6 as the results, which is just mathematically impossible, since $TMax_w = 2^{w-1} -1$, and therefore for a 3-bit signed value represented in two's complement form $TMax_3 = 3$

The correct Two's Complement table should be:

| Original | Truncated | 
| --- |--- |
| 1 | 1 | 
| 3 | 3 | 
| 5 | -3 | 
| -4 | -4 | 
| -2 | -2 | 

## Section 2.3 Integer Arithmetic
### Page 131, Practice Problem 2.33 <small>(solution page 189)</small>

- In the provided solution for Problem 2.33, the row corresponding to Hex 9 incorrectly lists the decimal value as −9. Since we are working with 4 bits ($w = 4$), it would be impossible to represent -9, since $TMin = -8$.

Correct solution:

1. Converting $9_{16}$ to binary: `1001`
2. Converting $1001_2$ (represented in two's-complement form) to decimal: $-2 \times 8 + 0 + 0 + 2 \times 1 = -8 + 1 = -7$

Therefore, the third row of the table given in the solution is wrong, and should be:

| Hex ($x$) | Decimal ($x$) | Decimal ( $-^t_4 x$ ) | Hex ($-^t_4 x$) 
| --- | --- | --- | --- |
| 9 | -7 | 7 | 7 | 

## Section 2.4 Floating Point

### Page 147, Practice Problem 2.45 <small>(solution page 193)</small>

- As listed in the [official errata](https://csapp.cs.cmu.edu/3e/errata.html), the fractional value in the third row should be $\frac{25}{16}$ instead of $\frac{5}{16}$. After this correction, the problem correctly aligns with the solution.





