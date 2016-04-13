##Threats to validity

In order to create as simple of an analysis as possible, we have intentionally overlooked a number of possible, valid program behaviours. These include a lack of support for threads and child processes, which would be of particular issue in interpreters attempting to adapt our work. Furthermore, we use a context insensitive analysis: beyond any context information used indirectly by the call graph module within CIL, we do not consider the possibility of improving precision by determining which parts of a called function will be executed.