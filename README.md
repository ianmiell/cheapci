cheapci
=======

Simple CI framework in bash. Checks whether there have been any updates, runs tests 
and mails you on completion.

Usage:

```
$ ./cheapci 
./cheapci [-q <pre-script>] [-w <post-script>] [-m <email>] [-a <mail command>]
   [-t <mail command attach flag>] [-s <mail command subject flag]
   [-e <recipients flag>] [-n name] [-d <dir>] [-c <command>] [-f] [-v] [-h]
   -r <repo> -l <local_checkout>

-q - script to run just before actually performing test (default /bin/true)
-w - script to run just after actually performing test (default /bin/true)
-m - email to send using "mail" command (default logs to stdout)
-a - mail command to use (default=mail)
-n - name for ci (unique, must be a valid directory name), eg myproj (default=ci)
-d - directory within repository to navigate to (default=.)
-c - test command to run from -d directory (default=./test.sh)
-t - attach argument flag for mail command (default=-A, empty string means no-attach)
-s - subject flag for mail command (default=-s)
-e - recipients flag (default=-t, empty string means no flag needed)
-f - force a run even if repo has no updates (default off)
-v - verbose logging (default off)
-h - show help
-r - git repository, eg https://github.com/myname/myproj (required)
-l - local checkout of code (that gets updated to determine whether a run is needed) (required)

EXAMPLES

- "Clone -r https://github.com/ianmiell/shutit.git if a git pull on /space/git/shutit 
indicates there's been an update. Then navigate to test, run ./test.sh and mail 
ian.miell@gmail.com if there are any issues"

  ./cheapci \
      -r https://github.com/ianmiell/shutit.git \
      -l /space/git/shutit \
      -d test \
      -c ./test.sh \
      -m ian.miell@gmail.com


- "Run the above continuously in a crontab."

  Crontab line:

* * * * * cd /path/to/cheapci && ./cheapci \
            -r https://github.com/ianmiell/shutit.git \
            -l /space/git/shutit \
            -d test \
            -c ./test.sh \
            -m ian.miell@gmail.com

- "Test cheapci with cheapci"

  ./cheapci \
     -q "ls -l" \
     -w "ls -l" \
     -m ian.miell@gmail.com \
     -n cheapci \
     -d . \
     -c /bin/true \
     -v \
     -r https://github.com/ianmiell/cheapci \
     -l /space/git/cheapci \
     -f

```
