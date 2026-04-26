
## Assignment 3D — Log Analysis Pipeline
Using sample.log, write single-line pipe commands (not scripts) to:

### Print all unique log levels that appear in the file.
```bash
cat sample.log | awk '{print $3}' | sort | uniq
```

### Find the most recent ERROR message (by timestamp).
```bash
cat sample.log | grep ERROR | sort -k1,1 -k2,2
```

### Count how many log entries exist per minute (hint: column 2 gives you the time — use the first 5 chars).
```bash
cat sample.log | awk '{print substr($2,1,5)}' | sort | uniq -c
```

### Extract all error messages (the text after the log level) and sort them alphabetically.
```bash
cat sample.log | grep ERROR | awk '{$1=$2=$3=""; print $0}'
```