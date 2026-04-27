### Basic Commands
| Command             | Purpose                                   |
| ------------------- | ----------------------------------------- |
| `journalctl`        | Show all logs                             |
| `journalctl -b`     | Show logs from current boot               |
| `journalctl -b -1`  | Show logs from previous boot              |
| `journalctl -f`     | Follow logs in real-time (like `tail -f`) |
| `journalctl -n 100` | Show last 100 lines                       |

### Filtering by service
| Command                           | Purpose                          |
| --------------------------------- | -------------------------------- |
| `journalctl -u nginx`             | Logs for a service (e.g., Nginx) |
| `journalctl -u ssh --since today` | Logs for service since today     |
| `journalctl -u myservice -f`      | Live logs for a service          |
| `journalctl --unit=myservice`     | Same as `-u`                     |


### Time based filtering
| Command                                 | Purpose             |
| --------------------------------------- | ------------------- |
| `journalctl --since "2026-04-26"`       | Logs since a date   |
| `journalctl --since "1 hour ago"`       | Logs from last hour |
| `journalctl --until "2026-04-27 10:00"` | Logs until a time   |
| `journalctl --since yesterday`          | Logs from yesterday |
| `journalctl --since "10 min ago"`       | Recent logs         |


### Log level filtering
| Command                 | Purpose                      |
| ----------------------- | ---------------------------- |
| `journalctl -p err`     | Only error logs              |
| `journalctl -p warning` | Warnings and above           |
| `journalctl -p info`    | Info and above               |
| `journalctl -p debug`   | All logs (verbose)           |
| `journalctl -p 3`       | Numeric priority (3 = error) |

### Filtering by PID
| Command                         | Purpose                   |
| ------------------------------- | ------------------------- |
| `journalctl _PID=1234`          | Logs for a process ID     |
| `journalctl _UID=1000`          | Logs for a user           |
| `journalctl _COMM=nginx`        | Logs by command name      |
| `journalctl _EXE=/usr/bin/node` | Logs from specific binary |

### Output Formatting
| Command                     | Purpose                    |
| --------------------------- | -------------------------- |
| `journalctl -o short`       | Default output             |
| `journalctl -o verbose`     | Detailed output            |
| `journalctl -o json`        | JSON format                |
| `journalctl -o json-pretty` | Pretty JSON                |
| `journalctl -o cat`         | Only message (no metadata) |
