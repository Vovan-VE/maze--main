## Maze Walk Algorithm

**Note:** This page refers to some [definitions](README.md).

The maze walk algorithm is based on a simple "rule of left hand". This is a
base algorithm for both solution and validation algorithms.

#### Input

*   **maze** `M` with help of export formats;
*   **use exit** `bExit`: whether to turn to exit;
*   Optional callback `willShortcut` receiving arguments `cCurrent` of type
    CELL, `cTarget` of type CELL and `dTarget` of type "direction", which will
    be called before stepping from CELL `cCurrent` to  CELL `cTarget` (adjacent
    in direction `dTarget`) in case when `cTarget` is non-previous part of
    visited WAY in a current state.

### Walk algorithm

>   DRAFT, not tested

1.  Get ENTRANCE `IN` of maze `M`. If ENTRANCE is not defined, fail;
2.  Set `cCurrent` to CELL adjacent to `IN`;
3.  Set `dLook` to direction opposite to `IN` side on the OUTER WALL;
4.  Initialize list `aSolve` of CELLs and add `cCurrent` to it;
5.  (`STEP:`) Loop:
    1.  Set `dNext` to opposite of `dLook`;
    2.  (`TURN:`) For each direction `dTurn` of: anti-clockwise to `dLook`,
        `dLook` and clockwise to `dLook`:
        1.  If CELL `cCurrent` has no WALL in direction `dTurn`, then:
            1.  If `bExit` is `true` OR direction `dTurn` at CELL `cCurrent` is
                not pointing to EXIT:
                1.  Set `dNext` to `dTurn` and exit loop `TURN:`.
    3.  If CELL `cCurrent` and direction `dNext` are pointing to ENTRANCE or
        EXIT, then finish the algorithm;
    4.  Set `cNext` to CELL adjacent to `cCurrent` in direction `dNext`;
    5.  If `cNext` is previous (last minus 1) item in `aSolve`, then:
        1.  Remove last item from `aSolve`.
    6.  Else If `aSolve` contains `cNext`, then:
        1.  If `willShortcut` input callback was set, then:
            1.  Call `willShortcut` callback passing `cCurrent`, `cNext` and
                `dNext` as arguments;
            2.  If `willShortcut` signals to finish or abort walk, then finish
                algorithm with appropriate status.
        2.  Remove from `aSolve` all items after `cNext` occurrence.
    7.  Else:
        1.  Add `cNext` to the end of `aSolve`.
    8.  End If;
    9.  Set `cCurrent` to `cNext`;
    10. Set `dLook` to `dNext`.
