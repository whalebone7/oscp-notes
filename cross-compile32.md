https://www.cyberciti.biz/tips/compile-32bit-application-using-gcc-64-bit-linux.html
https://stackoverflow.com/questions/22355436/how-to-compile-32-bit-apps-on-64-bit-ubuntu

pyinstaller : 

c:\Users\Administrator\Desktop\pyInstaller-2.1\python pyinstaller.py --onefile c:\Users\Administrator\Downloads\37034.py

tftp transfert : 

tftp -i <kali ip> put 37034.exe

use impacket-smbserver if possible
atftp --daemon --port 69 /srv/atftp (very slow, 6k/s on lab)

