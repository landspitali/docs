---
title: 'Vandamálagreining á Windows: Netþjónustur'
---

# Vandamálagreining á Windows: Netþjónustur - Grunnskref

Þessar leiðbeiningar er til að safna grunnupplýsingum þegar koma upp vandamál með netþjónustur.
Ekki ætlað fyrir kerfisstjóra sem kunna allt nú þegar.

1. [Grunnupplýsingar](#skref-1)
2. [Fyrstu skref, biðlari (client side)](#skref-2)
    1. [Byrja á að pinga netþjón](#skref-2-1)
    2. [Skoða hvort að hægt sé að tengjast netþjónustu](#skref-2-2)
    3. [Ef þú nærð sambandi en þjónusta virkar ekki](#skref-2-3)
3. [Fyrir lengra komna: Vandamálagreining á miðlara (server side)](#skref-3)
    * [Þjónusta keyrandi?](#skref-3-1)
    * [Er þjónustan að hlusta á PORT?](#skref-3-2)
    * [Event viewer](#skref-3-3)
    * [Wireshark](#skref-3-4)
4. [Hringja í vin](#skref-4)

## Grunnupplýsingar {#skref-1}

Áður en leitað er aðstoðar á næsta stigi er gott að vera búinn að safna grunnupplýsingum
um umhverfið sem þú ert keyrandi á. Gott er að hafa þessar upplýsingar með þegar
leitað er frekari aðstoðar

* IP tala tölvu notanda. Powershell skipun `> ipconfig` þar finnuru _IPv4 Address_
  * Ef beðið er um PUBLIC IP tölu þá er hægt að finna hana með því að fara inn á
  [https://myip.is](https://myip.is)
  * Ef þú ert að tengjast yfir internetið, þá er það public IP talan sem að skiptir máli
* Nafn á þjónustu
* Nafn á þjón eða IP tölu sem að hýsir þjónustu, eða hvert er verið að reyna
    að tengjast (t.d. https://einhver.vefsida.is)
* Hvaða PORT þjónustan á að vera að hlusta á

Svo væri gott að ganga í gegnum [Fyrstu skref, biðlari (client side)](#skref-2) sem
er hérna fyrir neðan.

## Fyrstu skref, biðlari (client side) {#skref-2}

### 1. Byrja á að pinga netþjón {#skref-2-1}

```
ping server.example
```
Ef ekkert er um að vera þá líklegast nærðu ekki að tengjast þjóninum

### 2. Skoða hvort að hægt sé að tengjast netþjónustu {#skref-2-2}

Þú þarft að vitahvaða __port__ þú ert að reyna að tengjast.
(algeng port t.d. http(80, 8080), https(443, 8443))

```
> Test-NetConnection server.example -Port <PORT> 

ComputerName     : server.example
RemoteAddress    : 192.0.2.55
RemotePort       : <PORT>
InterfaceAlias   : Ethernet
SourceAddress    : 192.168.2.5
TcpTestSucceeded : True
```
Það sem skiptir máli hér er TcpTestSucceeded. Ef að það tekst að pinga þjón en
TcpTestSucceeded er ekki _True_ þá gæti verið annaðhvort að netþjónustan sé ekki
keyrandi á þjóninum EÐA einhver eldveggur er að stoppa traffík.

### 3. Ef þú nærð sambandi en þjónusta virkar ekki {#skref-2-3}

Þá er líklegast málið miðlaramegin(server side) og þarf að greina þar.


## Fyrir lengra komna: Vandamálagreining á miðlara (server side) {#skref-3}
Þetta skref á einungis við um þá sem að hafa aðgang að þjónunum sem hýsa þjónusturnar.
Ef þú ert kominn á þetta stig þá hefuru eflaust grunnþekkingu þannig þetta eru
léttar tillögur meira en leiðbeiningar.

### Þjónusta keyrandi? {#skref-3-1} 

Ef þú ert kominn hingað þá eflaust veistu hvernig átt að kíkja hvort þjónustan sé keyrandi

### Er þjónustan að hlusta á PORT? {#skref-3-2}

Gott er að skoða hvort þjónusta sé í raun að hlusta á PORTið sem það á að gera.
```
# Í Powershell
> netstat -ano | findstr LISTENING

# Í dálk nr.2 er listað portin sem verið er að hlusta á
```
Ef að portið er ekki í listanum þá er eitthvað grunsamlegt í gangi

### Event viewer {#skref-3-3}

Fínt er að opna Event viewer og skoða hvort séu einhverjar augljósar villur

### Wireshark {#skref-3-4}

Fínt er að sækja Wireshark og skoða hvort að traffíkin líti út eins og 

## Hringja í vin {#skref-4}

Áður en hringt er í vin er gott að hafa í huga að vinur þinn hefur ekki endilega
aðgang að tölvunni þinni og umhverfinu þínu. Þá er gott að vera búinn að ganga í
gegnum skref __[Grunnupplýsingar](#skref-1)__ og __[Fyrstu skref, biðlari (client side)](#skref-2)__
áður en lengra er farið.


