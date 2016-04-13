##Overview

A control-flow hijacking attack is considered successful when malicious code begins executing. A meaningful attack often requires the execution of system calls \cite{Szekeres_2013}. Pledges can be applied to mitigate the effectiveness of attacks through security vulnerabilities by reducing the available resources, i.e. types of system calls, to the attacker.

Security vulnerability attacks can possibly occur at any buffer through a buffer overflow.  The ideal location to add a pledge call is directly after a system call so it cannot be used by any security vulnerability attack following that system call. However, if there is a subsequent use of that same system call later in the execution of the program, the pledge should only be placed after that last execution. If the pledge were placed after the first execution of a system call, the normal execution of the program would fail on any subsequent execution of the same system call. Therefore, the analysis must know the set of system calls that will execute in the future so that they are not pledged until they are no longer in that set.

