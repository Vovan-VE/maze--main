## Definitions and Algorithms

#### Definitions

The MAZE in this project is a "standard" (or "perfect") 2D rectangular maze.
A MAZE is a FIELD of CELLS. Adjacent CELLs are optionally separated by WALLs.
An absence of a WALLs forms a WAY to walkthrough. Perimeter is closed by the
OUTER WALL, but some two outer CELLS which are ENTRANCE and EXIT.

A "standard" (or "perfect") maze definition means, that any two CELLs of a MAZE
are always have the only way to walkthrough. This means there are no circular
WAYs and WALLs.

#### Algorithms

*   [Generation](generation.md)
*   [Base Walk](walk.md)
*   [Solution](solution.md)
*   [Validation](validation.md)
