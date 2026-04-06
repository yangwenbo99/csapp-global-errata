1. [Section 4.1 The Y64-86 Instruction Set Architecture](#section-41-the-y6486-instruction-set-architecture)
    1. [Page 406, Practice Problem 4.4](#page-406-practice-problem-44)

## Section 4.1 The Y64-86 Instruction Set Architecture

### Page 406, Practice Problem 4.4

Global edition makes this problem *significantly* harder and if not only that, the solution for it is very wrong as well.

Erratas in the global ed. solution:

1. `xor %rax, $rax` sets %rax to $0$, not to $1$
2. The checking doesnt match the condition in the C code
3. For some reason it does the multiplication with `imulq`, this instruction doesn't even exist in Y64-86. To multiply we would have to use addq in a loop.

The main problem is with errata number 3. Since there are no multiplication instructions, we have to implement a multiplication only using addition. Shifting does not exist in Y64-86 so there is no way of using left shifts combined with addition or subtraction to implement multiplication. The only way of doing it is via repeated addition (an addition loop).

What I would recommend doing is to simply change the multiplication (`*`) to an addition (`+`), and solve the modified problem. This aligns better with the original problem found in the NA edition.

However, if you feel ambitious, and want to give the global edition problem a try, go ahead. And if you get it working, you can delete this line and add your solution below. I opened an issue for it, so make sure to check the issues tab.

```asm
TO-DO: add solution to global ed. here 
```
