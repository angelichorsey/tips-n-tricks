# `perl` command-line find/replace
Replacing `sed` with superior PCRE (Perl Compatible Regular Expressions)
```
perl -pi -e 's/^\s*\n/\n/g' filename
  -p                assume loop like -n but print line also, like sed
  -i[extension]     edit <> files in place (makes backup if extension supplied)
  -e program        one line of program (several -e's allowed, omit programfile)

  use \n instead of $ as $ denotes variables in Perl
```