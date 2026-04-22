## grep Command

### Basic Flags

| Flag         | Description                            |
| ------------ | -------------------------------------- |
| `-i`         | Ignore case                            |
| `-v`         | Invert match (show non-matching lines) |
| `-w`         | Match whole words only                 |
| `-x`         | Match whole lines only                 |
| `-o`         | Show only the matched part             |
| `-e PATTERN` | Specify pattern (use multiple times)   |
| `-f FILE`    | Read patterns from file                |

### File and Directory Handling
| Flag                | Description                                           |
| ------------------- | ----------------------------------------------------- |
| `-r` / `-R`         | Recursive search in directories                       |
| `-d ACTION`         | How to handle directories (`read`, `skip`, `recurse`) |
| `--include=PATTERN` | Search only matching files                            |
| `--exclude=PATTERN` | Exclude matching files                                |
| `--exclude-dir=DIR` | Skip directories                                      |
| `-a`                | Treat binary files as text                            |
| `-I`                | Ignore binary files                                   |

### Output control
| Flag           | Description                       |
| -------------- | --------------------------------- |
| `-n`           | Show line numbers                 |
| `-H`           | Show filename                     |
| `-h`           | Hide filename                     |
| `-c`           | Count matches                     |
| `-l`           | Show filenames with matches       |
| `-L`           | Show filenames without matches    |
| `-q`           | Quiet (no output, exit code only) |
| `-s`           | Suppress error messages           |
| `--color=auto` | Highlight matches                 |

### Pattern Matching
| Flag | Description                                 |
| ---- | ------------------------------------------- |
| `-E` | Extended regex (same as `egrep`)            |
| `-F` | Fixed string (no regex, faster)             |
| `-G` | Basic regex (default)                       |
| `-P` | Perl regex (advanced, not always available) |
