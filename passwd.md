# Crack passwd file

## get the hash algorithm

```
# grep -n ENCRYPT_METHOD /etc/login.defs
```

## unshadow passwd file (for jtr)

```
unshadow passwd shadow > unshadow
```

## search cracklib dicts

cracklib dictionnaries give forbidden passwords

```
cat /etc/cracklib/cracklib.conf
```

## links
* https://techglimpse.com/cracking-linux-password-hashes-with-hashcat/
* https://hashkiller.co.uk/

## create a hash

https://www.shellhacks.com/linux-generate-password-hash/
