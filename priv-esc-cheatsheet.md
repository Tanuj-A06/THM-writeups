### This file contains the list of ways to locate an executable with suid bit enabled and use it run root-level commands

1) find / -user root -perm /4000

```
Explanation:

      i) '/' to start searching from the root directory

      ii) '-user root' This filters out files that are strictly owned by root

      iii) '-perm /4000' Here 4000 is the octal representation of SUID permissions and '/' is used to see if any of these permission bits are set.
```

2) find / -perm -u=s -type f 2>/dev/null

```
Explanation:

       i) '/' to start searching from the root directory.

       ii) '-perm -u=s' to search for files with s i.e (special) bit set. (SUID files)

       iii) '-type=f' to search only for files.

       iv) '2>/dev/null' to superess any errors.
```

3) find / -perm +6000 -type f -exec ls -ld {} \;

4) find / -perm /4000 -type f 2>/tmp/2
