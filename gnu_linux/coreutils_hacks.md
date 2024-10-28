# GNU Coreutils Hacks
Missing a tool to check connectivity to a port? (`nmap`, `nc`, `curl`, `wget`, etc) What if you need to see a process list without `top`/`ps`? These hacks can help with that. They are most useful on containers, since they are usually minimized and lack debugging utilities.

## List Processes (`top`/`ps`)
```bash
for pid in /proc/[0-9]*; do
  printf "PID: ${pid##*/}\t"
  cat $pid/cmdline 2>/dev/null | tr '\0' ' ' && echo
done
```

## Port Connectivity
Network connections exist as files under `/dev` (device), allowing you to `cat`/`echo`/etc into the filesystem to start a network connection.

```bash
timeout 1 bash -c "cat < /dev/null > /dev/tcp/$DOMAIN_OR_IP/$PORT" && echo open || echo closed
```
