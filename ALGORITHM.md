Definitions and Algorithms
==========================

## Definitions

The MAZE in this project is a "standard" (or "perfect") 2D rectangular maze.
A MAZE is a FIELD of CELLS. Adjacent CELLs are optionally separated by WALLs.
An absence of a WALLs forms a WAY to walkthrough. Perimeter is closed by the
OUTER WALL, but some two outer CELLS which are ENTRANCE and EXIT.

A "standard" (or "perfect") maze definition means, that any two CELLs of a MAZE
are always have the only way to walkthrough. This means there are no circular
WAYs and WALLs.

## Generation Algorithm

The maze generation algorithm used in the project is graph based algorithm.

Input options:

*   **width** `W` and **height** `H`: a size of the maze FIELD;
*   **branch length** `BL`: an integer number `1 <= BL <= W * H`. May be
    treated as complexity of a maze. The lower value, the easier the maze.

So, the maze generation algorithm:

1.  Start with a FIELD `M` with `W` width and `H` height of CELLs with all WALLs
    set (including the OUTER WALL without ENTRANCE and EXIT).
2.  Mark all CELLs as _free_ in any way you prefer. You will need to be able to
    check whether specific CELL is _free_ or _busy_. For example, it could be a
    static matrix `W`*`H` of boolean, or dynamic list of references to each
    _free_ CELL or something else. Let call it `aFree`.
3.  Prepare empty list or set of _frontier_ CELLs. Let call it `aFrontier`. You
    will need to add, remove CELLs, and pick a random CELL from it. Order of
    CELLs does not matter.
4.  Pick one random CELL `cStart` from `aFree`.
5.  Remove `cStart` from `aFree` and add in to `aFrontier`.
6.  While `aFree` is not empty:
    1.  Set `length` to `BL`.
    2.  Pick random cell `cCurrent` from `aFrontier`.
    3.  (`BRANCH:`) While `length` is greater then 0, do:
        1.  Decrement `length` by 1.
        2.  Choose random direction `dStart` (up/left/down/right).
        3.  Giving any static sequence of all 4 possible directions and starting
            with random direction `dStart` find a direction leading to _free_
            CELL `cNext` adjacent to `cCurrent` in that direction.
        4.  Remove `cNext` from `aFree`.
        5.  Remove WALL between `cCurrent` and `cNext`.
        6.  Remove `cCurrent` from `cFrontier` if `cCurrent` does not have
            adjacent _free_ CELLs anymore.
        7.  Set `cCurrent` to `cNext`.
        8.  Add `cCurrent` to `cFrontier` if `cCurrent` has any adjacent
            _free_ CELL, or exit loop `BRANCH` otherwise.
7.  Pick any two CELLS `cEntrance` and `cExit` adjacent to the OUTER WALL and
    remove one OUTER WALL in both. The choice may be fixed, like top-left and
    bottom-right.
