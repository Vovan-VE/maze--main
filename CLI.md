Command Line Interface
======================

All implementation have the same CLI:

```
maze [command] [options]
maze (-h|--help)
```

## Info options

*   `-h`, `--help`

    Show usage help.

## Commands

There default command is `gen`.

#### `gen` command

```
maze gen [options]
```

Generate maze.

```
maze -s 30x20
```

Options:

*   `-W <WIDTH>`, `--width=<WIDTH>`

    Maze **width** in number of CELLs. Default is `30`.

*   `-H <HEIGHT>`, `--height=<HEIGHT>`

    Maze **height** in number of CELLs. Default is `10`.

    Notice about uppercase `-H` to not mix with `-h` which is usually "help".

*   `-s <SIZE>`, `--size=<SIZE>`

    Alternative way to set both **width** and **height** at once. The `SIZE`
    must be in form `<WIDTH>x<HEIGHT>`. So, the default size is `30x10`.

*   `-B <BL>`, `--branch-length=<BL>`

    The **branch length** option for generation. `BL` can be an integer > 1
    (number of CELLs), string `max` (which is `WIDTH * HEIGHT`), or decimal
    from 0 to 1 as fraction of max (for example, `0.2` is
    `round(0.2 * WIDTH * HEIGHT)`). Default is 10.

    See "Input options" in [Definitions and Algorithms](./ALGORITHM.md).

*   `-f <FORMAT>`, `--format=<FORMAT>`

    Output format. Can be one of `art`, `json` or `text`. The default is `art`
    to be human readable.

*   `-c <NAME>=<VALUE>`

    Output format option. The `<NAME>` depends on chosen format in `-f`.

#### `help` command

Show usage help.

```
maze help [command]
```

Show help either about specified `command` or common usage help.

#### `solve` command

Solve a maze from input.

*   `--input-format=<FORMAT>`
*   `--output-format=<FORMAT>`
