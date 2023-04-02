# Web content 

### cewl: generating based on a website
```bash
sudo cewl -d <depth> -m <min_no_letters> -w <outputfile> <url>
```
---

### other: generate a wordlist base on all binary names
```bash
ls -sa /usr/bin | sed 's/[0-9]*//g' | sed -r 's/\s+//g' | sort -u > <outputfile>
```
---

