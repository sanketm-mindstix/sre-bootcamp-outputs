## ps (process status)
| Flag           | Description                                              |
| -------------- | -------------------------------------------------------- |
| `-A` / `-e`    | Show all processes                                       |
| `-a`           | Show processes for all users (except session leaders)    |
| `-u`           | Display user-oriented format                             |
| `-x`           | Include processes without a terminal                     |
| `-f`           | Full-format listing (more details like PPID, start time) |
| `-l`           | Long format                                              |
| `-o <format>`  | Customize output columns                                 |
| `-p <PID>`     | Show specific process by PID                             |

### Note
ps aux is the combination of the following flags
- a (All Users)
- u (user format)
- x (no terminal)

## top Command 
| Flag         | Description                             |
| ------------ | --------------------------------------- |
| `-d <sec>`   | Set refresh delay                       |
| `-n <num>`   | Number of iterations before exit        |
| `-u <user>`  | Show processes for a specific user      |
| `-p <PID>`   | Monitor specific PID(s)                 |
| `-b`         | Batch mode (for logging/output to file) |
| `-i`         | Ignore idle processes                   |
| `-c`         | Show full command line                  |
| `-H`         | Show threads instead of processes       |
| `-o <field>` | Sort by a field (e.g., `%CPU`)          |
| `-w`         | Adjust output width                     |

## kill Command
| Flag               | Description                           |
| ------------------ | ------------------------------------- |
| `-l`               | List all available signals            |
| `-s <signal>`      | Specify signal by name                |
| `-n <number>`      | Specify signal by number              |
| `-SIGKILL` / `-9`  | Force kill (cannot be caught/ignored) |
| `-SIGTERM` / `-15` | Graceful termination (default)        |
| `-SIGSTOP`         | Pause process                         |
| `-SIGCONT`         | Resume process                        |
| `-SIGINT`          | Interrupt (like Ctrl+C)               |
| `-SIGHUP`          | Hangup (often reload config)          |


## pkill and pgrep
| Flag                           | Works with   | Meaning                                             | Example                  |
| ------------------------------ | ------------ | --------------------------------------------------- | ------------------------ |
| `-f`                           | pkill, pgrep | Match ##full command line## (not just process name) | `pgrep -f "node app.js"` |
| `-x`                           | pkill, pgrep | Exact match of process name                         | `pkill -x nginx`         |
| `-i`                           | pkill, pgrep | Case-insensitive match                              | `pgrep -i python`        |
| `-u`                           | pkill, pgrep | Match processes by ##user (effective UID)##         | `pkill -u ubuntu`        |
| `-U`                           | pkill, pgrep | Match by ##real user ID##                           | `pgrep -U root`          |
| `-g`                           | pkill, pgrep | Match by ##process group ID##                       | `pgrep -g 1234`          |
| `-G`                           | pkill, pgrep | Match by ##real group ID##                          | `pgrep -G 1000`          |
| `-P`                           | pkill, pgrep | Match by ##parent PID##                             | `pgrep -P 1`             |
| `-t`                           | pkill, pgrep | Match by ##terminal (TTY)##                         | `pgrep -t pts/0`         |
| `-n`                           | pkill, pgrep | Select ##newest process##                           | `pgrep -n node`          |
| `-o`                           | pkill, pgrep | Select ##oldest process##                           | `pkill -o bash`          |
| `-l`                           | pgrep only   | Show process name along with PID                    | `pgrep -l ssh`           |
| `-a`                           | pgrep only   | Show full command line with PID                     | `pgrep -a node`          |
| `-c`                           | pgrep only   | Count matching processes                            | `pgrep -c python`        |
| `-d`                           | pgrep only   | Set delimiter for output                            | `pgrep -d "," node`      |
| `-v`                           | pkill, pgrep | Invert match (NOT matching)                         | `pgrep -v root`          |
| `-w`                           | pgrep only   | Show ##thread IDs## instead of PIDs                 | `pgrep -w java`          |
| `-F`                           | pkill, pgrep | Read PIDs from file                                 | `pkill -F pidfile`       |
| `-L`                           | pkill, pgrep | Fail if PID file is not locked                      | `pkill -L -F pidfile`    |
| `-e`                           | pkill only   | Echo what is being killed                           | `pkill -e nginx`         |
| `-signal` (e.g. `-9`, `-TERM`) | pkill only   | Specify signal to send                              | `pkill -9 node`          |


## df (Disk Free)

| Flag        | Description                                     |
| ----------- | ----------------------------------------------- |
| `-h`        | Human-readable (KB, MB, GB)                     |
| `-H`        | Human-readable (powers of 1000 instead of 1024) |
| `-T`        | Show filesystem type                            |
| `-a`        | Include all filesystems (even empty)            |
| `-i`        | Show inode usage instead of space               |
| `-l`        | Show only local filesystems                     |
| `--total`   | Show grand total                                |
| `-x <type>` | Exclude filesystem type                         |
| `-t <type>` | Include only specific type                      |

## du (Disk Usage)
| Flag                | Description                          |
| ------------------- | ------------------------------------ |
| `-h`                | Human-readable                       |
| `-s`                | Summary (total only)                 |
| `-a`                | Show all files, not just directories |
| `-c`                | Show grand total                     |
| `-d <N>`            | Limit depth of directory traversal   |
| `--max-depth=N`     | Same as `-d`                         |
| `-x`                | Stay on one filesystem               |
| `--exclude=PATTERN` | Skip matching files                  |
| `-L`                | Follow symlinks                      |


## nohup
| Flag               | Description                                      |
| ------------------ | ------------------------------------------------ |
| *(no major flags)* | `nohup` is simple; behavior controlled via shell |
| `--help`           | Show help                                        |
| `--version`        | Version info                                     |

Usage 
```bash
nohup command > output.log 2>&1 &
```

## tail
| Flag        | Description                                          |
| ----------- | ---------------------------------------------------- |
| `-f`        | Follow file (live updates)                           |
| `-F`        | Follow + retry if file recreated (log rotation safe) |
| `-n N`      | Show last N lines                                    |
| `-c N`      | Show last N bytes                                    |
| `-q`        | Quiet (no headers)                                   |
| `-v`        | Verbose (always show headers)                        |
| `--pid=PID` | Stop following when process ends                     |
| `-s <sec>`  | Sleep interval for updates                           |

