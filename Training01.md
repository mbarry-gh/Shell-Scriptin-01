##### ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) Remove/turncat Logs
```html
#!/bin/bash
# cleanup, version 2
# Run as root, of course.
LOG_DIR=/var/log
ROOT_UID=0 # Only users with $UID 0 have root privileges.
LINES=50 # Default number of lines saved.
E_XCD=66 # Can't change directory?
E_NOTROOT=67 # Non−root exit error.
if [ "$UID" != "$ROOT_UID" ]
then
echo "Must be root to run this script."
exit $E_NOTROOT
fi
if [ −z "$1" ]
# Test if command line argument present (non−empty).
then
lines=$1
else
lines=$LINES # Default, if not specified on command line.
fi
cd $LOG_DIR
if [ `pwd` != "$LOG_DIR" ] # or if [ "$PWD" != "$LOG_DIR" ]
# Not in /var/log?
then
echo "Can't change to $LOG_DIR."
exit $E_XCD
fi
tail −$lines messages > mesg.temp # Saves last section of message log file.
mv mesg.temp messages # Becomes new log directory.

cat /dev/null > wtmp # ': > wtmp' and '> wtmp' have the same effect.
echo "Logs cleaned up."
exit 0
# A zero return value from the script upon exit
#+ indicates success to the shell.
```
