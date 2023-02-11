# Package Management on Linux

## `yum`
The Yellowdog Updater, Modified (YUM) is a free and open-source command-line package-management utility for computers running the Linux operating system using the RPM Package Manager. Typically this is on enterprise linux flavors starting from RHEL (RedHat Enterprise Linux), like CentOS and Fedora.

### Include Multiple Package Versions in Search
```bash
yum search --show-duplicates <package>
```

## `rpm`

```bash
# query config files managed by package
rpm -qc <package>
# query all files managed by package
rpm -ql <package>
# verify all files managed by package
rpm -Vf postgresql14-server.x86_64
# find what package manages a file (if any)
rpm -qf <file>
```