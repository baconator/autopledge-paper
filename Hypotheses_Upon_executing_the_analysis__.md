##Hypotheses

Upon executing the analysis, the set of system calls in each basic block \(F_i\) of every executable function \(f\) must be known. With this information, the set of system calls that have been executed \(A\) and the set of system calls that remain to be executed \(A'\) can be found for every basic block. To determine the earliest point in a program to remove a system call from those that are pledged, from the program's starting point, look at which types of system calls are in that first basic block of function \(f\) and add those to \(A\). The types of system calls that are in the remaining basic blocks of \(f\), as well as those from functions \(g_j\) that are on a call stack derived from \(f\), are added to \(A'\). \(A'\) is then set subtracted from \(A\) to determine if a system call in \(A\) will not be executed in the future of the program's execution. Since a pledge is a whitelist, the result of \(A\) \\ \(A'\) is subtracted from \(F\) to determine the set of system calls to be pledged. If that result has changed since the last basic block, a new pledge call is needed to remove the system call that should no longer be used from being executed. The analysis continues by unioning the next basic block's set of system calls \(F_{i+1}\) to \(A\) and computing \(A'\) without that set.

It then follows that in a function \(f\) with \(n\) basic blocks at basic block \(f_j\) whos set of system calls is \(F_j\):

\[F=\bigcup_{i \in I}F_i\]

\[A=\bigcup_{i=0}^{j}F_i\]

\[A'=[ \bigcup_{i=j+1}^{n}F_i ] \cup G\]

(1) follows from the fact that sets of system calls for each basic block \(F_i\) form their containing function \(f\). Then

