# ssh

## ssh from specific source port

```
ncat -l 1234 --sh-exec 'ncat 192.168.0.2 987 -p 53'
```

And connect to localhost on port 1234 with ssh :

```
ssh -oPort=1234 user@localhost

## links
* https://www.pentestpartners.com/security-blog/how-to-abuse-ssh-keys/

