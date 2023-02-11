# Miscellaneous

### Follow Links to Find Command Location
Mostly used when personally creating a link of an unversioned executable to a specific version among many on the system. E.g., multiple versions of `terraform` but changing the link depending on the version needed.
```bash
readlink -f $(which <command>)
```

### Download from URL
Using `curl` with first command keeping the same name as the remote file, and then showing how to rename the file.  
```bash
curl <URL> -O
curl <URL> -o </path/to/filename.ext>
```

Another option is to use wget which defaults to the behavior of `curl -O`.  
```bash
wget <URL>
```

### One-liner: Download and Extract in Current Directory
```bash
curl <URL> | tar -zxvf -
```

### LDAP Search
`<BASEDN1>` - The `-H` option is for a full URI for all connection info to an LDAP server, and the base DN can be specified as the path of the URI.
`<BASEDN2>` - Normal base DN using `-b`, but this one can have LDAP operations like `'(SOME_DN|OTHER_DN)'`.
```bash
ldapsearch -LLLx -w "" -o ldif-wrap=no -H "ldaps://<host>:636/<base DN 1>" -b '<base DN 2>' '(|(sAMAccountName=<value>)(userid=<value>))' "<return attribute(s)>"
```

# OpenSSL
```bash
openssl genrsa -out <host>.key 4096
openssl req -new -config csr_details.txt -key <host>.key -out <host>.csr
openssl req -x509 -days 730 -newkey rsa:4096 -nodes -subj "/CN=<host>" -addext "subjectAltName = DNS:<host>,DNS:<host>" -keyout <name>-key.pem -out <name>-cert.pem
openssl s_client -connect <host>:<tls port> --showcerts | openssl x509 -noout -text
openssl x509 -in <cert file> -text -noout
```

# big block of crap
```bash
declare
mkdir -pv {dir1,dir2,dir3}/{commonsubdirA,commonsubdirB,commonsubdirC}
# processes
ps -auxfww
# networking
ss -plant
netstat -plant
sipcalc <address>/<CIDR>
sipcalc <address> <subnet mask>
# git tricks, probably another one getting its own doc
git ls-remote --tags origin
git log -p <args>
git clone --depth N <GIT_REPO_URL>
# variable substition
echo "${${VARIABLE#substring}%substring}"
${VARIABLE#substring}
# diff stuff
diff -y <(sort -t $'\t' -k2,2nr sort5_testcase1.txt) sort5_expected_out.txt
diff -BbrN
# find with options
find
# grep with options...probably on it's own doc
grep
# less stuff I remember is important but forget what they are exactly
less -r
less -R
less -k
# time math and date command
date -d'@<epoch time>'
date +%s -d "1 month ago"
date +%s -d "1200 hours ago"
date +%s -d "13 hours ago"
date +%s -d "24 hours ago"
date +%s -d '500 hours ago'
date +%Y%m%d
date +%Y%m%d%H%M%S
date -d "+100 days"
date -d "1 month ago"
date -d "100 days after 2020-10-02"
date -d "100 days since 2020-10-02"
date -d "1000 hours ago"
date -d "2020-01-01 +1337 hours"
date -d "768 hours ago"
date -d '1732 hours ago'
date -d '500 hours ago'
date -u -d "1 month ago"
date -u -d "1000 hours ago"
date -u -d "10000 hours ago"
date -u -d "1200 hours ago"
date -u -d "18 months ago"
date -u -d "6 months ago"
date -u -d'@1569033236.4544852'
# ssh
ssh -R 8000:localhost:8000 vagrant@127.0.0.1 -p 2222
ssh -L 8082:<remote host>:8082 <user>@<remote host> -i <pem key file>
```