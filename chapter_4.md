1. [Section 4.1 The Y64-86 Instruction Set Architecture](#section-41-the-y6486-instruction-set-architecture)
    1. [Page 406, Practice Problem 4.4](#page-406-practice-problem-44)

## Section 4.1 The Y64-86 Instruction Set Architecture

### Page 406, Practice Problem 4.4

Global edition makes this problem *significantly* harder and if not only that, the solution for it is very wrong as well.

The original problem statement (found in the north american edition) asked us to translate the following code:

```c
long rsum(long *start, long count)
{
    if (count <= 0)
        return O;
    return *Start + rsum(start + 1, count - 1);
}
```

<details>
<summary>Click here to reveal the solution for the north american edition</summary>

```
rsum:
  xorq %rax,%rax      # Set return value to 0
  andq %rsi,o/orsi    # Set condition codes
  jle return           # If count <= 0, return 0
  
  pushq rbx           # Save callee-saved register
  
  mrmovq (%rdi),%rbx  # Get *start
  irmovq $-1,%r10     
  addq %r10,%rsi      # count--
  irmovq $8,%r10      
  addq %r10,%rdi      # start++
  call rsum
  addq %rbx,%rax      # Add *start to sum
  popq %rbx           # Restore callee-saved ·register.

return:
  ret
```

</details>

In the global edition, however, they changed a few things in this code that make it very complicated to solve.
And for the solution, whoever made global edition basically copied from the north american one and changed the comments, without considering the modifications they made to the C snippet. They also used an instruction that doesn't even exist.

Erratas in the global ed. solution:

1. `xor %rax, $rax` sets %rax to $0$, not to $1$
2. The checking doesnt match the condition in the C code
3. For some reason it does the multiplication with `imulq`, this instruction doesn't even exist in Y64-86. To multiply we would have to use addq in a loop.

Given that, in the global edition this problem is significantly harder, requiring us to implement a multiplication only using addition, while handling both negative and positive values of *start. I would recommend just solving the original problem.
However, if you feel ambitious, and want to give the global edition problem a try, go ahead. And if you get it working, add your solution below. I will open an issue for it.

<details>
<summary>Solution for global edition</summary>

```
TO-DO: add solution to global ed. here 
```

</details>
