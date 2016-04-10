#Analysis

### Overview

### Notation

## Hypothesis
- Pledges will work best when a pledge occurs immediately after a system call so any method of making a subsequent system call of the same type cannot be used. 
- However, if in the flow of the program there is more than one execution of a system call, a pledge cannot occur after the first or else the second call will fail from the pledge.
    - Loops may run the system call many times and Recursive calls may run the same block of code many times by calling itself or through mutual recursion.
- Need information about what can happen in the future of an execution

- Introduce the notion of A and A'
    - A is what has already been executed in a function f
    - A' is the set of system calls that can occur in the future of the execution of a function f, including those from functions that can possibly be called from a callsite in f or any function down that chain
    - CONTEXT: If f is called from g_k where g_0 to g_k is on the call stack, then each g can possibly have a set of system calls that can occur in the future of its execution. Therefore, A' must also be aware of the future execution of functions deeper on the call stack. ONLY NEED THE LAST FUNCTION CONTEXT


\[F=\bigcup_{i \in I}S_{f_i}\]

\[A=\bigcup_{i=0}^{j}S_{f_i}\]

\[A'=F \backslash A\]

