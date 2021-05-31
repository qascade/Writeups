# Grandpa-HTB
### Enumeration
Running nmap top 1000 port scan on the machine.

```
nmap -A -T4 10.10.10.14
```
You can do all ports scan by following command
```
nmap -A -T4 -p- 10.10.10.14
```
Nmap Output 
```
nmap -A -T4 10.10.10.14
Starting Nmap 7.91 ( https://nmap.org ) at 2021-05-25 12:17 EDT
Stats: 0:00:13 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 90.45% done; ETC: 12:18 (0:00:01 remaining)
Nmap scan report for 10.10.10.14
Host is up (0.21s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Microsoft IIS httpd 6.0
| http-methods: 
|_  Potentially risky methods: TRACE COPY PROPFIND SEARCH LOCK UNLOCK DELETE PUT MOVE MKCOL PROPPATCH
|_http-server-header: Microsoft-IIS/6.0
|_http-title: Under Construction
| http-webdav-scan: 
|   Public Options: OPTIONS, TRACE, GET, HEAD, DELETE, PUT, POST, COPY, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK, SEARCH
|   WebDAV type: Unknown
|   Server Date: Tue, 25 May 2021 16:25:55 GMT
|   Allowed Methods: OPTIONS, TRACE, GET, HEAD, COPY, PROPFIND, SEARCH, LOCK, UNLOCK
|_  Server Type: Microsoft-IIS/6.0
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 26.85 seconds
```

Information about type of Windows version is not available but one can see that port 80 is open and is running `Microsoft IIS httpd 6.0`.

Opening Metasploit using `msfconsole`.
On google searching I got to know that a exploit- exploit/windows/iis/iis_webdav_scstoragepathfromurl can be used for the given version.

