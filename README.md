cheapci
=======

Simple CI framework in bash. Checks whether there have been any updates, runs tests and mails you on completion.

eg

```
./cheapci -m ian.miell@gmail.com -n shutit -d test -c ./test.sh -f -l /space/git/shutit -r https://github.com/ianmiell/shutit.git
```

or in a cron:

```
* * * * * /path/to/cheapci -m ian.miell@gmail.com -n shutit -d test -c ./test.sh -f -l /space/git/shutit -r https://github.com/ianmiell/shutit.git
```

Usage:

```
$ ./cheapci -h
./cheapci [-q <pre-script>] [-w <post-script>] [-m <email>] [-n name] [-d <dir>] [-c <command>] [-f] [-v] [-h] -r <repo> -l <local_checkout>

-q - script to run just before actually performing test (default /bin/true)
-w - script to run just after actually performing test (default /bin/true)
-m - email to send using "mail" command (default logs to stdout)
-n - name for ci (unique, must be a valid directory name), eg myproj (default=ci)
-d - directory within repository to navigate to (default=.)
-c - test command to run from -d directory (default=./test.sh)
-f - force a run even if repo has no updates (default off)
-v - verbose logging (default off)
-h - show help
-r - git repository, eg https://github.com/myname/myproj (required)
-l - local checkout of code (that gets updated to determine whether a run is needed) (required)
```
