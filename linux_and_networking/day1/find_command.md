**find**

find [path] [conditions] [actions]

***Basic Filter**
| Option    | Meaning               | Example                   |
| --------- | --------------------- | ------------------------- |
| `-name`   | Match filename        | `find . -name "file.txt"` |
| `-iname`  | Case-insensitive name | `find . -iname "*.txt"`   |
| `-type f` | Files only            | `find . -type f`          |
| `-type d` | Directories only      | `find . -type d`          |
| `-type l` | Symlinks              | `find . -type l`          |
| `-size +10M` | Larger than 10MB      | `find . -size +10M` |
| `-size -1k`  | Less than 1KB         | `find . -size -1k`  |
| `-mtime +7`  | Modified > 7 days ago | `find . -mtime +7`  |
| `-mtime -1`  | Modified within 1 day | `find . -mtime -1`  |
| `-atime`     | Last accessed time    | `find . -atime +5`  |
| `-ctime`     | Metadata change time  | `find . -ctime +2`  |
| `-user`       | Owned by user    | `find . -user root`  |
| `-group`      | Group ownership  | `find . -group dev`  |
| `-perm`       | Permission match | `find . -perm 777`   |
| `-perm -4000` | SUID files       | `find / -perm -4000` |

***Operators***
| Option        | Meaning       |
| ------------- | ------------- |
| `-and` / `-a` | AND (default) |
| `-or` / `-o`  | OR            |
| `!`           | NOT           |


***Actions***
| Option        | Meaning                | Example                        |
| ------------- | ---------------------- | ------------------------------ |
| `-print`      | Show results (default) | `find . -print`                |
| `-delete`     | Delete files           | `find . -name "*.log" -delete` |
| `-exec`       | Run command            | `find . -exec rm {} \;`        |
| `-exec ... +` | Faster batch execution | `find . -exec rm {} +`         |


