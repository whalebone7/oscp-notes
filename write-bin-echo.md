# write binary via echo

```
cat hello | hexdump -v -e '"echo -n " 16/1 "\\x%02X" "\n"'
```

but how to manage double quotes ?

```
cat hello | hexdump -v -e '16/1 "\\x%02X" "\n"' | tee hello.echo
```


