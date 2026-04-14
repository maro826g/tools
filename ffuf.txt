# ffuf (Fuzz Faster U Fool)

## Subdomain Enumeration
ffuf -u https://FUZZ.example.com -w wordlist.txt
ffuf -u https://FUZZ.hacked.example.com -w wordlist.txt
ffuf -u https://FUZZ-example.com -w wordlist.txt
ffuf -u https://FUZZ-hacked.example.com -w wordlist.txt
ffuf -u https://hacked-FUZZ.example.com -w wordlist.txt
ffuf -u https://FUZZwww.example.com -w wordlist.txt

## Virtual Host Enumeration
ffuf -u https://example.com -w wordlist.txt -H "Host: FUZZ.example.com"
ffuf -u http://<ip> -w wordlist.txt -H "Host: FUZZ.example.com"

## Directory and File Discovery
ffuf -u https://example.com/FUZZ -w wordlist.txt -t 2000 -mc 200
ffuf -u https://example.com:80/FUZZ -w wordlist.txt -X POST
ffuf -u https://192.1.2.3:80/FUZZ -w wordlist.txt
ffuf -u http://example.com/FUZZ -w wordlist.txt -e .html,.php,.asp,.aspx,.js,.json,.xml,.config,.bak,.old,.backup,.zip,.rar
ffuf -u http://example.com/FUZZ -w wordlist.txt -recursion
ffuf -u http://example.com/FUZZ -w wordlist.txt -recursion-depth 3

## Multi-Wordlist and Parameter Fuzzing
ffuf -u https://example.com/FUZZ/FUZZX -w list1.txt:FUZZ -w list2.txt:FUZZX
ffuf -u https://example.com/?username=FUZZ&password=FUZZX -w username.txt:FUZZ -w password.txt:FUZZX
ffuf -u https://example.com/FUZZ?param=FUZZX -w dirs.txt:FUZZ -w params.txt:FUZZX

## Authentication and Header Fuzzing
ffuf -u http://example.com/FUZZ -w wordlist.txt -H "Authorization: Bearer TOKEN"
ffuf -u https://example.com/admin -w 403-headers.txt -H "FUZZ" -mc 200,301,302,307,401

## Request File Fuzzing
ffuf -request fuzzing_login.txt -request-proto http -w password.txt:PASS
ffuf -request fuzzing_login.txt -request-proto https -w wordlist.txt:FUZZ

## Rate Limit Bypass
ffuf -u http://example.com/FUZZ -w wordlist.txt -H "X-Forwarded-For: 127.0.0.1" -H "X-Forwarded-Host: 127.0.0.1"
ffuf -u http://example.com/FUZZ -w wordlist.txt -p 0.1
ffuf -u http://example.com/FUZZ -w wordlist.txt -rate 100

## 403 Bypass Techniques
ffuf -u https://example.com/FUZZ -w wordlist.txt -H "X-Forwarded-For: 127.0.0.1" -H "X-Original-URL: /FUZZ"
ffuf -u https://example.com/admin -w 403-headers.txt -H "FUZZ" -mc 200,301,302,307,401
ffuf -u https://example.com/FUZZ -w wordlist.txt -H "X-Custom-IP-Authorization: 127.0.0.1"
ffuf -u https://example.com/FUZZ -w wordlist.txt -H "Referer: https://example.com"

## Proxy and Traffic Interception
ffuf -u http://example.com/FUZZ -w wordlist.txt -x http://127.0.0.1:8080
ffuf -u http://example.com/FUZZ -w wordlist.txt -x socks5://127.0.0.1:1080

## Output and Filtering
ffuf -u https://example.com/FUZZ -w wordlist.txt -o results.json -of json
ffuf -u https://example.com/FUZZ -w wordlist.txt -o results.csv -of csv
ffuf -u https://example.com/FUZZ -w wordlist.txt -mc 200,301,302,403
ffuf -u https://example.com/FUZZ -w wordlist.txt -fc 404,500
ffuf -u https://example.com/FUZZ -w wordlist.txt -fs 1234
ffuf -u https://example.com/FUZZ -w wordlist.txt -fw 10
ffuf -u https://example.com/FUZZ -w wordlist.txt -fl 5
ffuf -u https://example.com/FUZZ -w wordlist.txt -mr "admin panel"
ffuf -u https://example.com/FUZZ -w wordlist.txt -fr "not found"

## Advanced Techniques
ffuf -u https://example.com/FUZZ -w wordlist.txt -ac
ffuf -u https://example.com/FUZZ -w wordlist.txt -t 150 -timeout 10
ffuf -u https://example.com/FUZZ -w wordlist.txt -H "User-Agent: Mozilla/5.0" -c
ffuf -u https://example.com/FUZZ -w wordlist.txt -b "session=abc123; token=xyz"
ffuf -u https://example.com/api/FUZZ -w wordlist.txt -X POST -H "Content-Type: application/json" -d '{"key":"FUZZ"}'

## Common Flags
- `-u` - Target URL; place FUZZ keyword where fuzzing should occur
- `-w` - Wordlist path; supports named keywords via `wordlist.txt:KEYWORD` for multi-wordlist mode
- `-H` - Custom HTTP header; can be used multiple times; supports FUZZ keyword for header fuzzing
- `-X` - HTTP method to use (GET, POST, PUT, DELETE, etc.)
- `-d` - POST request body data; supports FUZZ keyword for body parameter fuzzing
- `-b` - Cookie data to include with each request
- `-t` - Number of concurrent threads (default: 40); increase carefully to avoid detection
- `-rate` - Rate limit in requests per second; use to avoid triggering WAF or IDS
- `-p` - Delay in seconds between requests; accepts ranges like `0.1-2.0` for randomization
- `-timeout` - Per-request timeout in seconds (default: 10)
- `-mc` - Match HTTP status codes (comma-separated); only show responses with these codes
- `-fc` - Filter HTTP status codes (comma-separated); hide responses with these codes
- `-fs` - Filter by response size in bytes; hide responses matching this size
- `-fw` - Filter by word count in response; hide responses with this word count
- `-fl` - Filter by line count in response; hide responses with this line count
- `-mr` - Match responses containing this regex pattern in body
- `-fr` - Filter responses containing this regex pattern in body; hide matching responses
- `-ac` - Automatically calibrate filtering by sending dummy requests to detect baseline responses
- `-e` - File extensions to append to each wordlist entry (comma-separated, e.g. `.php,.html`)
- `-recursion` - Enable recursive fuzzing on discovered directories
- `-recursion-depth` - Maximum recursion depth when `-recursion` is enabled
- `-x` - Proxy URL to route all traffic through (e.g. `http://127.0.0.1:8080`)
- `-o` - Output file path to save results
- `-of` - Output file format: `json`, `ejson`, `html`, `md`, `csv`, `all`
- `-c` - Colorize terminal output for easier reading
- `-v` - Verbose mode; show full URLs and redirect targets in results
- `-s` - Silent mode; suppress progress updates, only show results
- `-r` - Follow HTTP redirects automatically
- `-request` - Path to a raw HTTP request file to use as the fuzzing template
- `-request-proto` - Protocol to use with `-request` flag (`http` or `https`)
- `-replay-proxy` - Replay matched requests to a second proxy (useful for Burp logging)
