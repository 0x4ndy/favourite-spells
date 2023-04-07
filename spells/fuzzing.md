# Web content (files and folders)

### dirb: non-recursive scan with a delay between request
```bash
dirb <url> -r -z <time_milliseconds>
```
---

### gobuster: endpoint discovery
```bash
gobuster dir -u http://<ip>/ -w <wordlist> -s '200,204,301,302,307,403,500' -e

# -b - opposite to '-s'
# -t - number of threads
```
---

# Web files

### wfuzz: fuzzing for files with a wordlist, excluding 404
```bash
export URL=http://$IP/FUZZ 
wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-large-files.txt --hc 404 "$URL"
```
---

### FFuf: Web file extensions fuzzing with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http://<ip>:<port>/<file_name>FUZZ
```
---

### FFuF: Web file names fuzzing with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http://<ip>:<port>/FUZZ.<extension>
```
---

# Web directories

### wfuzz: fuzzing for directories with a wordlist, excluding 404
```bash
export URL=http://$IP/FUZZ/
wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt --hc 404 "$URL"
```
---

### FFuF: Directory fuzzing with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http://<ip>:<port>/FUZZ
```
---

### FFuF: Recursive (files/directories) Scanning with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http://<ip>:<port>/FUZZ -recursion -recursion-depth 1 -e <file-extension> -v
```
---

# Sub-domains

### gobuster: subdomain enumeration
```bash
gobuster dns -d <domain> -w <wordlist> -t 30
```
---

### FFuF: Fuzzing sub-domains with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://FUZZ.<domain-name>
```
---

# VHosts

### FFuF: Fuzzing Vhosts with FFuf
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://<domain>:<port>/ -H 'Host: FUZZ.<domain>'
```
---

# Parameters

### FFuF: Fuzzing GET parameters with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://<domain>:<port>/<path>?FUZZ=key
```
---

### FFuF: Fuzzing POST parameters with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://<domain>:<port>/<path> -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded'
```
---

### FFuF: Fuzzing GET parameters value with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://<domain>:<port>/<path>?<parameter-name>=FUZZ
```
---

### FFuF: Fuzzing POST parameters value with FFuF
```bash
ffuf -w <wordlist>:FUZZ -u http(s)://<domain>:<port>/<path> -X POST -d '<param-name>=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded'
```
---

