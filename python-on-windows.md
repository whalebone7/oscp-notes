https://medium.com/ethical-hacking-blog/converting-python-into-exe-files-on-kali-fdff53b81aad


```
wget https://www.python.org/ftp/python/2.7.8/python-2.7.8.msi
wine msiexec /i python-2.7.8.msi
wget http://downloads.sourceforge.net/project/pywin32/pywin32/Build%20220/pywin32-220.win32-py2.7.exe
wine pywin32-220.win32-py2.7.exe
wget https://github.com/pyinstaller/pyinstaller/releases/download/v2.1/PyInstaller-2.1.zip
unzip PyInstaller-2.1.zip -d /opt
rm PyInstaller-2.1.zip
wine c:/Python27/python.exe /opt/PyInstaller-2.1/pyinstaller.py --onefile evil.py
```

=> dist/evil.exe

note: modern antivirus might see pyinstaller generates EXEs as malicious… some antivirus evasion products made heavy use of pyinstaller…
