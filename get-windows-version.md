# get windows version

https://security.stackexchange.com/questions/110673/how-to-find-windows-version-from-the-file-on-a-remote-system



Based on https://superuser.com/questions/363018/how-do-i-tell-what-version-and-edition-of-windows-is-on-the-filesystem you can find the Windows Version and Service pack in C:\Windows\System32\license.rtf for Windows 7. For Windows XP the information is in C:\Windows\System32\eula.txt. For Windows 10 licenses.rtf does not contain the version. Instead it contains the EULA code, which you can use to find the version online.

I tested this on XP SP3, 7, 7 SP1, and 10 and found that this works for each OS.

The current language pack is a little more tricky. You can find what appears to be the currently available languages in C:\Windows\System32. The folders are in the format of xx-XX (xx = language, XX = country). For example en-US is English-United States, es-MX is Spanish-Mexico.

The packs that have been used are copied to C:\Windows.

To test this I switched my Windows 7 SP1 and Windows 10 Pro machines over to es-MX and, once I rebooted the computer, found that the es-MX folder was created in C:\Windows. Unfortunately the en-US was still there making the current language ambiguous. However you should be able to use the combination of active packs and the names of Documents, Photos, Music ect. to get the current language.

I was unable to test this in XP as I could not risk bricking my last running example of XP.




Not installed (so I don't know the product ID) - from MSDN:

Windows XP Professional N English VL - EULAID:XPSP2_RM.4_RME-PRO_RTL_EN
Windows XP Professional English x64 - EULAID:WS03SP1_RM.0_PX64_RTL_EN
Windows XP Media Center Edition 2005 English - EULAID:MCE05_RM.0_PRO_RTL_EN
Windows XP Professional English - EULAID:WX.4_PRO_RTL_EN
Windows XP Professional with SP1a English - EULAID:XPSP1_RM.1_PRO_RTL_EN
Windows XP Professional with SP2 English - EULAID:XPSP2_RM.0_PRO_RTL_EN
Windows XP Professional with SP2 English VL - EULAID:XPSP2_RM.0_PRO_RTL_EN
Windows Server 2003 Standard - EULAID:WNET_RM.5_SRV-ENT_RTL_EN
Windows Server 2003 Standard with SP1 - EULAID:WS03SP1_RM.2_STD-ENT_RTL_EN
Windows Server 2003 Enterprise with SP1 - EULAID:WS03SP1_RM.2_STD-ENT_RTL_EN

