http://hackingandsecurity.blogspot.com/2016/06/exploiting-network-file-system-nfs.html
https://pentestacademy.wordpress.com/2017/09/20/nfs/
https://github.com/NetDirect/nfsshell
https://resources.infosecinstitute.com/exploiting-nfs-share/#gref
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/s1-nfs-server-config-exports

note : config file is at /etc/exports

```
root@attacker]# showmount -e 192.168.0.1
Export list for 192.168.0.1:
/export/home/  (everyone)
/export/mnt/   (everyone)
/export/share/ (everyone)


[root@attacker~]#mount -t nfs 192.168.0.1:/export/home /local_dir
```

If we experience some permissions issues, the ID is maybe wrong, see no_root_squash.

https://formation-debian.viarezo.fr/nfs.html.

```
root@kali:/mnt# mount -t nfs 10.10.10.5:/home/vulnix /mnt/vulnix/
root@kali:/mnt# ls -aln /mnt
total 56
drwxr-xr-x  5     0          0  4096 janv. 11 23:19 .
drwxr-xr-x 19     0          0 36864 déc.  16 13:57 ..
drwxr-xr-x  2     0          0  4096 janv. 11 23:19 etc
drwxr-xr-x  2     0          0  4096 déc.  16 20:46 kali_share
drwxr-x---  4 65534 4294967294  4096 janv. 11 21:44 vulnix
root@kali:/mnt# 
```

The uid is wrong, we must find the good uid.

We can :

- brute force
- read the passwd to find the good uid

WHen find, we can read/write the nfs.






