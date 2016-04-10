##Overview

A control-flow hijacking attack is considered successful when malicious code begins executing. A meaningful attack often requires the execution of system calls \cite{Szekeres_2013}. Pledges can be applied to mitigate the effectiveness of attacks through security vulnerabilities by reducing the available resources, i.e. types of system calls, to the attacker.

Security vulnerability attacks can possibly occur at any buffer through a buffer overflow.  The ideal location to add a pledge call is directly after a system call so that any buffer  
    