The Maze Project
================

The Maze Project is a project where I'm going to implement the maze generation
and solving algorithms in different programming languages. The goal is to use
common development techniques like code and repo organizing and testing.

Further reading:

*   [Definitions and Algorithms](algorithms/README.md)
*   [Export formats](export/README.md)
*   [Command Line Interface](cli.md)
*   Wikipedia: [Maze generation algorithm](https://en.wikipedia.org/wiki/Maze_generation_algorithm)

## Implementations

Ready status covers following parts:

##### v1

*   `cli` — common ability to deal easy with CLI arguments;
*   `generate` — maze generation itself;
*   `solve` — solving a maze;
*   `export` — export results of (`generate` and `solve`) according to formats;
*   `import` — import a maze according to formats to `solve` it;
*   `validate` — report whether a maze is perfect or not;
*   `test` — tests for all implemented parts.

#### Ready 100%

*   (none yet)

#### WIP (alphabetical order)

*   [Go](https://github.com/Vovan-VE/maze-go) — 57%:
    no `import`, `solve`, `validate`.
*   [PHP](https://github.com/Vovan-VE/maze-php) — 71%:
    no `solve`, `validate`.

#### Next planned (alphabetical order)

*   Perl
*   Raku
*   TypeScript

#### Further wishes

*   Bash (crazy/stupid challenge)
