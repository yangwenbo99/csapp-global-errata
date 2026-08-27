## practice problem 12.2
both problem and solution text talk about deleting line 33 in figure 12.5 (closing the `connfd` in the parent process).
the solution claims the code remains leak free and correct, which is false. since the parent process never returns, the amount of open fds in the parent will, at some point, exceed the maximum allowed fd number and fail.
I assume the problem was actually trying to show that the line closing the fd in the child process could be deleted, since the child process exits immediately afterwards, letting the kernel reclaim the open fds.

### page 1011
**Practice Problem 12.2 (solution page 1072)**
`line 33` -> `line 30`

### page 1028
**Practice Problem 12.5 (solution page 1072)**
`line 33` -> `line 30`

### page 1072
**Solution to Problem 12.2 (page 1011)**
`parent` -> `child` (x2)
