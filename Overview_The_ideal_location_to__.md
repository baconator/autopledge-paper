##Overview

The ideal location to add a pledge call in a program is immediately after a system call to disclude its further use in security vulnerability attacks. Unfortunately, a pledge call will break normal execution if it is within a loop or a recursive function. Loops and recursion must be known during the analysis so that any system call within the loop or recursive function is not removed from use by a pledge before the loop or recursive function is finished executing. if a function \(f\) is called from a call site within a loop in \(g\) or is a recursive function, that context needs to be known so that pledge calls will not be inserted in \(f\). Otherwise, the second execution of \(f\) from a loop or recursive call will fail when the pledge stops the system call from passing.

