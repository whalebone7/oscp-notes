https://wiki.archlinux.org/index.php/Port_knocking

```
#!/bin/bash
HOST=$1
shift
for ARG in "$@"
do
        nmap -Pn --host-timeout 100 --max-retries 0 -p $ARG $HOST
done

```
BE CAREFUL : nmap with -p444,22,11 don't work, port order is not guaranteed.
