# Unknown service

When a service give nothing with nmap :

- try a nc with long wait, sometimes some services (especially smtp) take a very long time to send banner.
- try with nmap --version-all. It will test all probes (Very noise !)
- use netstat when get a shell.
