##Setup

To perform the analysis on an input program, the sets \(A\) and \(A'\) need to be able to be calculated for each subsequent set of basic blocks in each function. A call graph is calculated to find which functions can be called from within a function. A call graph maps functions to those it can call. The call graph will allow Autopledge to find 

Afterwards, a map for each function is created which maps blocks of code to system calls. 