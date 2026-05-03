## CURL Command

### Basic Flags
| Flag | Meaning                    | Example                 | Usage                      |
| ---- | -------------------------- | ----------------------- | -------------------------- |
| `-X` | HTTP method                | `curl -X POST URL`      | Change GET/POST/PUT/DELETE |
| `-L` | Follow redirects           | `curl -L example.com`   | Follow 301/302 redirects   |
| `-I` | Fetch headers only         | `curl -I google.com`    | Check response headers     |
| `-v` | Verbose mode               | `curl -v URL`           | Debug full request flow    |
| `-s` | Silent mode                | `curl -s URL`           | Hide progress output       |
| `-S` | Show errors in silent mode | `curl -sS URL`          | Clean logs but show errors |
| `-o` | Save output to file        | `curl -o file.html URL` | Download with custom name  |
| `-O` | Save with original name    | `curl -O URL`           | Auto filename download     |

### Body Flags
| Flag         | Meaning                 | Example                     | Usage              |
| ------------ | ----------------------- | --------------------------- | ------------------ |
| `-d`         | Send data (POST body)   | `curl -d "a=1" URL`         | Form submission    |
| `-H`         | Add headers             | `curl -H "Auth: token" URL` | API authentication |
| `-F`         | File upload (form-data) | `curl -F file=@a.png URL`   | Upload files       |
| `--data-raw` | Raw body                | `curl --data-raw '{}' URL`  | JSON APIs          |
| `--json`     | Send JSON (new curl)    | `curl --json '{"a":1}' URL` | Clean API calls    |

### Authentication Flags
| Flag              | Meaning      | Example                          | Usage      |
| ----------------- | ------------ | -------------------------------- | ---------- |
| `-u`              | Basic auth   | `curl -u user:pass URL`          | Login APIs |
| `--oauth2-bearer` | Bearer token | `curl --oauth2-bearer TOKEN URL` | OAuth APIs |

### Network and Connection Flag
| Flag                | Meaning               | Example                            | Usage                       |
| ------------------- | --------------------- | ---------------------------------- | --------------------------- |
| `--connect-timeout` | Connection timeout    | `curl --connect-timeout 5 URL`     | Fail fast if server is slow |
| `--max-time`        | Total request timeout | `curl --max-time 10 URL`           | Limit full request time     |
| `-m`                | Same as max-time      | `curl -m 10 URL`                   | Quick timeout               |
| `-4`                | Force IPv4            | `curl -4 URL`                      | Fix IPv6 issues             |
| `-6`                | Force IPv6            | `curl -6 URL`                      | Test IPv6                   |
| `--resolve`         | Custom DNS mapping    | `curl --resolve a.com:443:1.2.3.4` | Bypass DNS                  |

### Security/TLS Flag
| Flag       | Meaning            | Example                    | Usage              |
| ---------- | ------------------ | -------------------------- | ------------------ |
| `-k`       | Ignore SSL errors  | `curl -k https://site`     | Self-signed certs  |
| `--cert`   | Client certificate | `curl --cert file.pem URL` | Mutual TLS         |
| `--key`    | Private key        | `curl --key key.pem URL`   | Secure auth        |
| `--cacert` | Custom CA          | `curl --cacert ca.pem URL` | Trust custom certs |
