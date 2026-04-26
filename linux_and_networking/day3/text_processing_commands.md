## Combining Commands with Pipes
The real power is chaining:
```bash
cat sample.log | grep ERROR | awk '{print $5}' | sort | uniq -c | sort -rn
```

This reads as: get all errors → extract the 5th column → sort them → count unique values → sort by count descending. This is a real pattern used to find the most frequent error type in logs.

## Text Processing Commands
| Command  | Flag(s)     | Use Case                   | Example                     |
| -------- | ----------- | -------------------------- | --------------------------- |
| **sort** | `-k`        | Sort by specific column(s) | `sort -k1,1 -k2,2 file.txt` |
|          | `-n`        | Numeric sort               | `sort -k2,2n file.txt`      |
|          | `-r`        | Reverse order              | `sort -r file.txt`          |
|          | `-u`        | Sort + remove duplicates   | `sort -u file.txt`          |
|          | `-t`        | Custom delimiter           | `sort -t',' -k2,2 file.csv` |
|          | `-f`        | Case-insensitive sort      | `sort -f file.txt`          |
|          | `-s`        | Stable sort                | `sort -s -k1,1 file.txt`    |
|          | `-k2.1,2.5` | Partial field sort         | `sort -k2.1,2.5 file.txt`   |

| Command  | Flag(s) | Use Case             | Example                    |
| -------- | ------- | -------------------- | -------------------------- |
| **uniq** | `-c`    | Count occurrences    | `sort file.txt \| uniq -c` |
|          | `-d`    | Show duplicates only | `sort file.txt \| uniq -d` |
|          | `-u`    | Show unique only     | `sort file.txt \| uniq -u` |
|          | `-i`    | Ignore case          | `sort file.txt \| uniq -i` |

| Command | Flag(s) | Use Case          | Example                    |
| ------- | ------- | ----------------- | -------------------------- |
| **cut** | `-d`    | Set delimiter     | `cut -d',' -f2 file.csv`   |
|         | `-f`    | Select fields     | `cut -d' ' -f1,3 file.txt` |
|         | `-c`    | Select characters | `cut -c1-5 file.txt`       |

| Command | Flag(s) | Use Case           | Example                     |
| ------- | ------- | ------------------ | --------------------------- |
| **tr**  | —       | Replace characters | `tr 'a-z' 'A-Z' < file.txt` |
|         | `-d`    | Delete characters  | `tr -d ',' < file.txt`      |
|         | `-s`    | Squeeze repeats    | `tr -s ' '`                 |

| Command | Flag(s) | Use Case    | Example          |
| ------- | ------- | ----------- | ---------------- |
| **wc**  | `-l`    | Count lines | `wc -l file.txt` |
|         | `-w`    | Count words | `wc -w file.txt` |
|         | `-c`    | Count bytes | `wc -c file.txt` |
