# exec inside

Some programs can be use to exec code, if suid, we can escalade.

* less, more, man : https://download.vulnhub.com/brainpan/brainpan3.zip.torrent

* vi

If we cannot give executable rigth to a binary, we can use the loader :

```
root@kali:~# file /usr/bin/id
/usr/bin/id: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=8c73e741721895ec03faeed359ecba2ca5776665, stripped
root@kali:~# /lib64/ld-linux-x86-64.so.2 /usr/bin/id
uid=0(root) gid=0(root) groupes=0(root)
```
