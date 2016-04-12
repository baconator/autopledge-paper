##Hypotheses

Upon executing the analysis, the set of system calls in each basic block \(F_i\) of every executable function \(f\) must be known. With this information, the set of system calls that have been executed \(A\) and the set of system calls that remain to be executed \(A'\) can be found for every basic block. To determine the earliest point in a program to remove a system call from those that are pledged, from the program's starting point, look at which types of system calls are in that first basic block of function \(f\) and add those to \(A\). The types of system calls that are in the remaining basic blocks of \(f\), as well as those from functions \(g_j\) that are on a call stack derived from \(f\), are added to \(A'\). \(A'\) is then set subtracted from \(A\) to determine if a system call in \(A\) will not be executed in the future of the program's execution. Since a pledge is a whitelist, the result of \(A\) \\ \(A'\) is subtracted from \(F\) to determine the set of system calls to be pledged. If that result has changed since the last basic block, a new pledge call is needed to remove the system call that should no longer be used from being executed. The analysis continues by unioning the next basic block's set of system calls \(F_{i+1}\) to \(A\) and computing \(A'\) without that set.

It then follows that in a function \(f\) with \(n\) basic blocks at basic block \(f_j\) whos set of system calls is \(F_j\):

\[F=\bigcup_{i \in I}F_i\]

\[A=\bigcup_{i=0}^{j}F_i\]

If function \(f\) was called by function \(g\), which also has a set of basic blocks that remain to be executed \(B'\), then:

\[A'=[ \bigcup_{i=j+1}^{n}F_i ] \cup B'\]

Otherwise \(G\) would just be the empty set.

(1) follows from the fact that sets of system calls for each basic block \(F_i\) form their containing function \(f\) while (2) and (3) made from two partitions of \(F_i\) for \(i..n\). However, (3) would require extra types of system calls if \(f\) were called from \(g\). Because the analysis is done on a per function basis but considers system calls from other functions, \(g\) would have it's own sets of executed and to be executed system call which we'll call \(B\) and \(B'\). The context of \(B'\) is required because if it contained a system call \(s\) that was also in \(A\) but not \(A'\), then a pledge discluding \(s\) would be made after the latest added basic block in \(A\). With that context unioned with \(A'\), \(s\) will not be removed from subsequent pledges within \(f\) since it will be required after \(f\) has completed in \(g\). It's also important to note that if an execution of a program has a call stack with multiple functions \(g_i\) called before \(f\), only the context of the function call before it is required because each function would union its context into its subsequent called function.

The notion of a call stack is a dynamic one that would be normally be seen in an execution trace even though this analysis is static. The information needed to complete the analysis meaningfully can be derived from a call graph. A call graph can be used to determine which functions can possibly be called from any function. That determination is used to derive any recursion as well as the necessary contexts that will be needed when solving for \(A'\) so breaking pledges are not made.

