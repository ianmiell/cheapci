cheapci
=======

Simple CI framework in bash. Checks whether there have been any updates, runs tests
and mails you on completion.

To show flags etc:

```
$ ./cheapci -h
```

Examples
========

```
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

* * * * * cd /path/to/cheapci && ./cheapci -r https://github.com/ianmiell/shutit.git -l /space/git/shutit -d test -c ./test.sh -m ian.miell@gmail.com

- "Test cheapci with cheapci"

# Check out cheapci to the folder specific in the -l argument below, and update that argument for your context
./cheapci \
     -n cheapci \
     -d . \
     -c /bin/true \
     -r https://github.com/ianmiell/cheapci \
     -l /home/imiell/git/cheapci \
     -f \
     -a echo
```
