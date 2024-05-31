---
title: 'Windows: Prufa TCP tengingar'
---

# Prufa TCP tengingar (t.d. HTTP, RDP)

1. [Almennar TCP tengingar (RDP, SSH, HTTP, HTTPS)](#skref-1)
2. [HTTP og HTTPS](#skref-2)

Oft er gott að geta prufað hvort að tengingar virki fyrir þjónustur, t.d. þegar verið er að skoða hvort eldveggur gæti verið vandamál.

## Almennar TCP tengingar (RDP, SSH, HTTP, HTTPS) {#skref-1}

Powershell gefur aðgang að skipun __Test-NetConnection__ sem er hægt að skoða hvort sé hægt að tengjast endapunkti.

Hérna er dæmi með RDP:
```
> Test-NetConnection 192.0.2.100 -Port 3389

ComputerName     : 192.0.2.100
RemoteAddress    : 192.0.2.100
RemotePort       : 3389
InterfaceAlias   : Ethernet0
SourceAddress    : 192.0.2.15
TcpTestSucceeded : True
```

Hérna er mikilvægt að __TcpTestSucceeded__ sé _True_. Það þýðir að tenging virkar. Þá getur þú meira og minna útilokað að eldveggjavandamál.

## HTTP og HTTPS {#skref-2}

Einfaldast er bara að opna vafra og vera skýr (**http**://eitthvad.dot.is, **https**://eitthvad.dot.is). Og ef þú veist hvernig á að nota dev tools í þeim vafra sem þú notar
getur þú skoðaðbetur.

Önnur þæginleg leið er að nota curl. Í nýrri windows útgáfum kemur curl.exe á vélina (**.exe extension mjög mikilvægt**, annars er notað eitthvað powershell alias sem er ekki jafn hentugt).
Curl með __-v__ flagginu er mjög hjálplegt til að sjá hvað gengur á.
```
$ curl.exe -v eitthvad.dot.is
>
< HTTP/1.1 301 Moved Permanently
< Server: nginx
< Date: Fri, 31 May 2024 11:46:19 GMT
< Content-Type: text/html
< Content-Length: 178
< Connection: keep-alive
< Location: https://eitthvad.dot.is/
<
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
</body>
</html>
```
Með þessu getur þú t.d. séð að þú færð svar frá þjóninum og hann beinir þér eitthvað annað. 
