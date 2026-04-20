**ls Command**

| Flag                        | Description                                          | Example                        |
| --------------------------- | ---------------------------------------------------- | ------------------------------ |
| `-a`                        | Show **all files**, including hidden (`.` files)     | `ls -a`                        |
| `-A`                        | Show almost all (exclude `.` and `..`)               | `ls -A`                        |
| `-l`                        | Long listing format (permissions, owner, size, date) | `ls -l`                        |
| `-h`                        | Human-readable sizes (KB, MB, GB)                    | `ls -lh`                       |
| `-R`                        | Recursive listing (subdirectories)                   | `ls -R`                        |
| `-t`                        | Sort by modification time (newest first)             | `ls -lt`                       |
| `-r`                        | Reverse sort order                                   | `ls -lr`                       |
| `-S`                        | Sort by file size (largest first)                    | `ls -lS`                       |
| `-d`                        | List directories themselves, not contents            | `ls -d */`                     |
| `-F`                        | Add indicator (`/`, `*`, etc.) to entries            | `ls -F`                        |
| `-i`                        | Show inode number                                    | `ls -i`                        |
| `-n`                        | Show numeric UID/GID instead of names                | `ls -ln`                       |
| `-o`                        | Like `-l` but without group info                     | `ls -lo`                       |
| `-g`                        | Like `-l` but without owner info                     | `ls -lg`                       |
| `-1`                        | One file per line                                    | `ls -1`                        |
| `-Q`                        | Quote file names                                     | `ls -Q`                        |
| `--color=auto`              | Colorized output (default in many systems)           | `ls --color=auto`              |
| `--color=never`             | Disable colors                                       | `ls --color=never`             |
| `--time=atime`              | Sort by access time                                  | `ls -lt --time=atime`          |
| `--time=ctime`              | Sort by change time                                  | `ls -lt --time=ctime`          |
| `--group-directories-first` | List directories before files                        | `ls --group-directories-first` |
| `--block-size=SIZE`         | Control size display units                           | `ls -lh --block-size=M`        |

**pwd**

| Command  | Description                            |
| -------- | -------------------------------------- |
| `pwd`    | Show current directory                 |
| `pwd -P` | Show physical path (resolves symlinks) |
| `pwd -L` | Logical path (default, keeps symlinks) |

**mkdir**

| Flag | Description                         | Example            |
| ---- | ----------------------------------- | ------------------ |
| `-p` | Create parent directories if needed | `mkdir -p a/b/c`   |
| `-v` | Verbose output                      | `mkdir -v dir`     |
| `-m` | Set permissions                     | `mkdir -m 755 dir` |

**cp**
| Flag        | Description                      | Example             |
| ----------- | -------------------------------- | ------------------- |
| `-r` / `-R` | Copy directories recursively     | `cp -r dir1 dir2`   |
| `-i`        | Prompt before overwrite          | `cp -i file1 file2` |
| `-f`        | Force overwrite                  | `cp -f file1 file2` |
| `-v`        | Verbose output                   | `cp -v file1 file2` |
| `-p`        | Preserve permissions, timestamps | `cp -p file1 file2` |

**mv**
| Flag | Description             | Example             |
| ---- | ----------------------- | ------------------- |
| `-i` | Prompt before overwrite | `mv -i file1 file2` |
| `-f` | Force overwrite         | `mv -f file1 file2` |
| `-v` | Verbose output          | `mv -v file1 dir/`  |

**rm**
| Flag | Description         | Example      |
| ---- | ------------------- | ------------ |
| `-r` | Recursive Delete    | `rm -r new/` |
| `-i` | Ask before deleting | `rm -i file` |
| `-f` | Force delete        | `rm -f file` |
| `-v` | Verbose output      | `rm -v file` |

**cat**
| Flag | Description                             | Example           |
| ---- | --------------------------------------- | ----------------- |
| `-n` | Show line numbers                       | `cat -n file.txt` |
| `-b` | Number non-empty lines                  | `cat -b file.txt` |
| `-s` | Squeeze multiple blank lines            | `cat -s file.txt` |
| `-A` | Show all characters (tabs, end-of-line) | `cat -A file.txt` |
| `-T` | Show tabs as `^I`                       | `cat -T file.txt` |
| `-E` | Show line endings `$`                   | `cat -E file.txt` |


