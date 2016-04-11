##Hypotheses

Upon executing the analysis, the set of system calls in each basic block \(F_i\) of every executable function \(f\) must be known. With this information, the set of system calls that have been executed \(A\) and the set of system calls that remain to be executed \(A'\) can be found for every basic block. The following are the equations that will be used for inserting pledges:

\[F=\bigcup_{i \in I}F_i\]

\[A=\bigcup_{i=0}^{j}F_i\]

\[A'=F \backslash A\]