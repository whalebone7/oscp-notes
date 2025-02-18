# checklist smb

## toolbox
smbclient - rpcclient

# information gathering
* Workgroup
* available folders
* smb version
* linux -> samba or windows? match up with basic enum

## enum4linux with null byte
If session work, enum users with rpcclient

## rpcclient
https://pen-testing.sans.org/blog/2013/07/24/plundering-windows-account-info-via-authenticated-smb-sessions
try : 
enumdomusers
net add user
...

## winexe
try to execute a payload

## msf-psexec

## online attack if username/creds

If work, re run enum4linux with creds

# net service
Can we execute a service?

## Pass the hash

## some exploits
linux? -> trans2open
windows? -> ms08_65?


## Files enum
Can we read all files?
What can we lear from readable files?
can we get the system version? (EULA for windows or /etc/issue - /etc/*-release for linux)
Can we list all system with dir traversal?
Where can we write files?

## if login not work
Sometime, the null session not work but a random user can connect :

```
root@kali:~# smbclient -W 'WORKGROUP' -L '10.10.10.7' -U''%''

	Sharename       Type      Comment
	---------       ----      -------
smb1cli_req_writev_submit: called for dialect[SMB2_10] server[10.10.10.7]
Error returning browse list: NT_STATUS_REVISION_MISMATCH
Reconnecting with SMB1 for workgroup listing.
Connection to 10.10.10.7 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Failed to connect with SMB1 -- no workgroup available
root@kali:~/10.10.10.7# smbclient -W 'WORKGROUP' -L '10.10.10.7'
Enter WORKGROUP\root's password: 

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
Reconnecting with SMB1 for workgroup listing.
Connection to 10.10.10.7 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Failed to connect with SMB1 -- no workgroup available
```

## LINKS

# netbios -smb
* http://www.linux-france.org/article/serveur/netbios/
* https://doc.ubuntu-fr.org/samba
* https://linux.developpez.com/formation_debian/samba.html
* https://labs.portcullis.co.uk/tools/enum4linux/
* https://fr.wikipedia.org/wiki/Remote_procedure_call
* http://bruno.duffet.free.fr/technique/reseaums/resms.htm
* smbclient [fr] : http://www.linux-france.org/prj/edu/archinet/systeme/ch25s09.html
* smbclient : https://www.computerhope.com/unix/smbclien.htm
* messages d'erreur : https://msdn.microsoft.com/en-us/library/cc246324.aspx
* psexec pth : https://www.offensive-security.com/metasploit-unleashed/psexec-pass-hash/
* ocsp notes : https://securism.wordpress.com/oscp-notes-password-attacks/
* psexec : https://blogs.technet.microsoft.com/systemcenteressentials/2009/09/01/using-psexec-to-open-a-remote-command-window/
* https://docs.microsoft.com/fr-fr/sysinternals/downloads/psexec
* av évasion : https://reload.eez.fr/blog:2017:09:19:metasploit_meterpreter_contre_les_antivirus
* smb how-to : http://www.tldp.org/HOWTO/SMB-HOWTO.html#toc8
*  rpcclient exploitation : https://pen-testing.sans.org/blog/2013/07/24/plundering-windows-account-info-via-authenticated-smb-sessions
*  service restart : https://lifehacker.com/5575671/restart-windows-services-from-your-linux-pc
*  
