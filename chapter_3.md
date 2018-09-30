# Chapter 3 Machine-Level Representation of Programs


<!-- vim-markdown-toc GFM -->

1. [Section 3.6 Control](#section-36-control)
    1. [Page 240, Practical Problem 3.13 (corrected)](#page-240-practical-problem-313-corrected)
    1. [Page 248, Practice Problem 3.16](#page-248-practice-problem-316)
    1. [Page 258, Practice Problem 3.23](#page-258-practice-problem-323)
    1. [Page 274, Figure 3.24 (code of Practice Problem 3.31)](#page-274-figure-324-code-of-practice-problem-331)
1. [Section 3.8 Array Allocation and Access](#section-38-array-allocation-and-access)
    1. [Page 298, Practice Problem 3.40](#page-298-practice-problem-340)
1. [Section 3.9 Heterogeneous Data Structure](#section-39-heterogeneous-data-structure)
    1. [Page 304, Practice Problem 3.41](#page-304-practice-problem-341)
        1. [Aside: How can you know?](#aside-how-can-you-know)

<!-- vim-markdown-toc -->

## Section 3.6 Control
### Page 240, Practical Problem 3.13 (corrected)
D. 
```
cmpq  %rsi, %rdi
setne %a
```
The last line should be changed to
```
cmpq  %rsi, %rdi
setne %al
```


### Page 248, Practice Problem 3.16
```
cond:
  testq %rdi, %rdi
  je    .L1
  cmpq  %rsi, (%rdi)
  jle   .L1
  movq  %rdi, (%rsi)
.L1:
  rep; ret
```

The fifth line should be changed to `  cmpq  (%rsi), %rdi`

### Page 258, Practice Problem 3.23 

The C code and assembly code do not correspond to each other, if I change
the assembly code, it should be like:
```
7       leaq    5(rbp, %rcx), %rbx
```

And the answer from page 370 should also be changed.

### Page 274, Figure 3.24 (code of Practice Problem 3.31)

The second line of (the comment of) the assembly code, `%rdi and %rdi` 
are reversed and should be changed to 
```
a in %rdi, b in %rsi, c in %rdx, d in %rcx
```

## Section 3.8 Array Allocation and Access
### Page 298, Practice Problem 3.40 

The second line of the comments of the first line of assembly code should be:
```
A in %rdi, val in %esi
```

## Section 3.9 Heterogeneous Data Structure 

### Page 304, Practice Problem 3.41

In fact, some of the sub-problems are impossible to answer, and some of the 
answers from page 279 is definitely incorrect. This is due to a C language 
feature mentioned in the next of the next sub-section. According to 
C11 (6.7.2.1 14), the way of _alignment_ of `struct`'s members are 
_implement-defined_.
> Each non-bit-field member of a structure or union object is aligned in an implementation-defined manner appropriate to its type.
That is, if no compiler (and even version) specified in this question, 
there will be no answer. If it is for GCC, then according to GCC's 
documentation, it is 
> Determined by ABI. 
Meaning that GCC on different platforms may produce different result. 

Thus, this question itself is incorrect.

On my x86_64 machine with GCC version 8.2.1, the result is like:
```c
short *p;            // 8 bytes
short s.x;           // 2 bytes
short s.y;           // 2 bytes
padding              // 4 bytes
struct test *next;   // 8 bytes
```

#### Aside: How can you know?
I wrote a program.

```c
struct test_struct {
	short *p;
	struct {
		short x;
		short y;
	} s;
	struct test_struct *test;
};

int main (void) {
	struct test_struct ts;
	ts.p = NULL;
	ts.p += 0x1234567812345678 / 2;
	ts.s.x = 0x1111;
	ts.s.y = 0x2222;
	ts.test = NULL;
	ts.test += 0x8989898989898900 / sizeof(struct test_struct);
	
	dump(&ts, sizeof(struct test_struct));

	return 0;
}
```

Which yields the following result
```
0x   0-0x   8:	78 56 34 12 78 56 34 12 
0x   8-0x  10:	11 11 22 22 10 56  0  0 
0x  10-0x  17:	f8 88 89 89 89 89 89 89 
```



