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
*   `in: [side, offset] | null` - entrance position:
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

#### Options

*   `pretty`: pretty format JSON if option was set.

## Text

```
###########
i #     # #
# ### # # #
#   # #   #
### # ### #
#     #   E
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

#### Options

*   `wall`: a string to represent single wall block. Can be any UTF-8 string.
    Default is `#`.
*   `in`: a string to represent an Entrance door. Can be any UTF-8 string. When
    its length does not match with `wall` length, `in` will be repeated and
    truncated to reach exactly the same length as `wall`.
*   `out`: a string to represent an Exit door. All the rest is the same as `in`.

For example, setting `wall` to `@$%` (3 chars), `in` to `()` (2 chars) and `out`
to `EXIT` (4 chars), a `1x1` "maze" would look like following:

```
@$%@$%@$%
()(   @$%
@$%EXI@$%
```
