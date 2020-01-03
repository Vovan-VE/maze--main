Maze export format
==================

Example maze in text art:

```
╶─┬─────┬─┐
╷ └─┐ ╷ ╵ │
├─╴ ╵ ├─╴ ╵
└─────┴───╴
```

## JSON

```
{
  "width": 5,
  "height": 3,
  "in": ["left", 0],   // entrance: side and zero based offset
  "out": ["right", 2], // exit: side and zero based offset
  "cells": [           // array of rows: array length is height
    "12010",           // row length is width
    "21120",           // each char describe left and down walls
    "00100"            // excluding outer wall
  ]
}
```

*   `width: number` - width of FIELD in CELLs;
*   `height: number` - height of FIELD in CELLs;
*   `in: [side, offset]` - entrance position:
    *   `side: string` - side of the OUTER WALL: `"top"`, `"right"`, `"bottom"`
        or `"left"`;
    *   `offset: number` - zero based offset on the `side` wall starting from
        top for `"right"` and `"left"` walls and from left for `"top"` and
        `"bottom"` walls.
*   `out: [side, offset]` - exit position in same structure as entrance in `in`.
*   `cells: string[]` - CELLS definition. An array `height` strings each has
    length of `width` chars. Each char describes right and down WALLs in a
    corresponding CELL:
    *   `"0"` - neither right not down walls;
    *   `"1"` - only right wall;
    *   `"2"` - only down wall;
    *   `"3"` - both right and down wall.
    The rightmost CELLs (that is the last chars in each string) does not
    describe the right OUTER WALL, so it can be only `"0"` or `"2"`. The most
    bottom CELLs (that is all chars in the last string) does not describe the
    bottom OUTER WALL, so it can be only `"0"` or `"1"`. As the result, the last
    char in the last string is always `"0"`.

## Text

```
###########
  #     # #
# ### # # #
#   # #   #
### # ### #
#     #           <-- Note: possible trailing spaces are kept
###########
```

As you can see, text maze is based on the grid pattern like following for 5*3
maze:

```
###########
# | | | | #
#-#-#-#-#-#
# | | | | #
#-#-#-#-#-#
# | | | | #
###########
```

So, each line is `width * 2 + 1` chars, and there are `height * 2 + 1` lines
total.

Any non-space chars can be used for WALLs.