## sed Command
| Flag        | Use Case                                                            | Example                                                          |
| ----------- | ------------------------------------------------------------------- | ---------------------------------------------------------------- |
| `-n`        | When you only want specific output (avoid printing everything)      | `sed -n 'p' file.txt` → prints only lines you explicitly request |
| `-e`        | When chaining multiple commands                                     | `sed -e 's/foo/bar/' -e 's/hello/world/' file.txt`               |
| `-f`        | When commands are stored in a script file                           | `sed -f script.sed file.txt`                                     |
| `-i`        | Editing files directly (no separate output file)                    | `sed -i 's/foo/bar/' file.txt`                                   |
| `-r` / `-E` | When you need cleaner regex (no excessive escaping)                 | `sed -E 's/[0-9]+/NUMBER/' file.txt`                             |
| `-s`        | When processing multiple files independently (line numbers reset)   | `sed -s '1d' file1 file2`                                        |
| `-u`        | For real-time processing (logs, streams)                            | `tail -f log.txt \| sed -u 's/error/ERROR/'`                     |
| `-z`        | When input is null-separated (e.g., filenames with spaces)          | `find . -print0 \| sed -z 's/.txt/.bak/g'`                       |
| `-l`        | For formatting long lines (debugging output)                        | `sed -n 'l' file.txt`                                            |
| `-c`        | Rare; used with in-place editing behavior (implementation-specific) | Not commonly used in practice                                    |
| `--help`    | Quick reference for available options                               | `sed --help`                                                     |
| `--version` | Check installed sed version                                         | `sed --version`                                                  |


### -i can take a suffix for backup
```bash
sed -i.bak 's/foo/bar/' file.txt
```

### Replace first occurrence of a word per line
```bash
sed 's/old/new/' file.txt
```
By default, sed replaces only the first match per line

### Replace all occurrences of a word
```bash
sed 's/old/new/g' file.txt
```
The g flag = global replacement on each line

### Delete lines matching a pattern
```bash
sed '/pattern/d' file.txt
```
### Removes every line that contains "pattern"
Example:
```bash
sed '/error/d' log.txt
```

### Print only lines 5–10
```bash
sed -n '5,10p' file.txt
```
-n suppresses default output, p prints only selected lines