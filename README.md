cheapci
=======

Simple CI framework in bash. Checks whether there have been any updates, runs tests and mails you on completion.

eg

```
./cheapci -m ian.miell@gmail.com -n shutit -d test -c ./test.sh -f -l /space/git/shutit -r https://github.com/ianmiell/shutit.git
```

Usage:

```
./cheapci [-m <email>] [-n name] [-d <dir>] [-c <command>] [-f] [-v] [-h] -r <repo> -l <local_checkout>

-h - show help
-m - email to send using "mail" command (default logs to stdout)
-n - name for ci (unique, must be a valid directory name), eg myproj, (default=ci)
-d - directory within repository to navigate to, (default=.)
-c - test command to run from -d directory (default=./test.sh)
-f - force a run even if repo has no updates (default off)
-v - verbose logging (default off)
-r - git repository, eg https://github.com/myname/myproj (required)
-l - local checkout (that gets updated to determine whether a run is needed) (required)
```
