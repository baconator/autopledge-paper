#Results

Due to time constraints, only a part of the analysis was completed by the time of submission. This included the computation of system calls on a per-function level and the propagation of said calls between all callers. As CIL lacks the same abstractions as LLVM/Clang, performing propagation on the block level was cumbersome; instead, it was performed on a per-statement level.