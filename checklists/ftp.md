# FTP checklist

## header check
with nc, get the banner for guess the ftp server version

## Anon login
try anonymous/anonymous

## User enum
As the server a different response when the user don't exists? -> enum users with dico

## online attack 
with a username, can we connect with leak password (same as login or no password)?

## Files enum
What is the root? Any chroot?
Where can we write?
can we get the system version? (EULA for windows or /etc/issue - /etc/*-release for linux)
What can we learn from the readeds files?
