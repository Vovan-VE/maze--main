## Maze Solution Algorithm

**Note:** This page refers to some [definitions](README.md).

The Maze Solution Algorithm is based on [walk algorithm](walk.md) with following
additions:

*   Input option **use exit** `bExit` is fixed to `true`;

#### Input

*   **maze** `M` with help of export formats;

#### Output

*   If EXIT reached, then the result is an ordered list of CELLs to show a
    solution way;
*   If EXIT was not reached, then the result is `null` (empty result);
*   If the input maze `M` has neither ENTRANCE nor EXIT, or contains some
    unexpected holes in the OUTER WALL, then fail (exception thrown).
