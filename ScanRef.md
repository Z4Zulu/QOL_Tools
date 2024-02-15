==============================Scanning==========================================
===RustScan====
rustscan -a $IP -n --ulimit 70000 -t 5000 -- -A -Pn

===Nmap====
nmap -p- -sT -sV -A $IP
nmap -p- --script=vuln $IP
###  --script smb-enum-shares
