# command injection

* https://github.com/fuzzdb-project/fuzzdb/tree/master/attack/os-cmd-execution
* http://www.betterhacker.com/2016/10/command-injection-without-spaces.html
* https://securityonline.info/command-injection-vulerabilitycommand-injection-commix/
* https://www.hackerone.com/blog/how-to-command-injections

## with openvpn

* https://medium.com/tenable-techblog/reverse-shell-from-an-openvpn-configuration-file-73fd8b1d38da
* https://security.stackexchange.com/questions/133613/is-it-okay-to-use-random-openvpn-config-files

- use nobind to open several openvpn instances

## Output
Sometime, the output (stdout and/or stderr) is on the response. 
TRY A SIMPLE COMMAND, may be the output will be displayed, try more complex commands (nc, wget) only if the output is not displayed.

## with bash

https://unix.stackexchange.com/questions/171346/security-implications-of-forgetting-to-quote-a-variable-in-bash-posix-shells
