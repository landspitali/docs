---
title: Wireshark
---

# Wireshark

[Wireshark](https://www.wireshark.org/download.html) skoðar pakka sem að eru sendir
til og frá tölvu yfir net og getur verið nokkuð hjálplegt þegar verið er að greina netvandamál.

## Að keyra Wireshark

1. [Sækja](https://www.wireshark.org/download.html) og setja upp Wireshark
2. Keyra Wireshark

Þegar þú opnar Wireshark þarftu að velja á hvað _Network interface_ þú vilt hlusta
á. Rétta valið er venjulega þar sem er einhver traffík í línuritinu.
![Wireshark Network Interfaces]({{ '/assets/images/Debug/wireshark-interfaces.jpg' | relative_url }})

Ef þú tvísmellir á interface þá mun Wireshark byrja að grípa pakka. Ef ekkert meira
er gert þá mun Wireshark byrja að grípa alla nettraffík sem að er ekki endilega
það sem þú vilt. Þá vilt þú nota capture filter.


## Capture filter

Capture filter grípur bara þá traffík sem að þú biður um. Þetta er gagnlegt ef
þú ert að skoða ákveðna týpu af traffík, eða traffík til/frá ákveðnum þjón o.s.frv.

Nokkrir gagnlegir capture filters:
  * Hlusta á alla traffík við ákveðinn þjón (t.d. 192.0.2.65)
    * `host 192.0.2.65`
  * Hlusta á alla traffík á ákveðið port (t.d. 443 (https))
    * `port 443`
  * Hlusta á alla traffík á ákveðin þjón á ákveðið port (t.d. 192.0.2.65:443)
    * `host 192.0.2.65 and port 443`

## Vista upplýsingar

Í versta falli ef þú skilur ekki neitt þá er hægt að vista upplýsingarnar sem að
þú grípur og senda á vin sem getur skoðað hjá sér.

Þetta er hjálplegt þegar verið er að skoða vandamál á biðlara(client) sem að ekki
er greiður aðgangur að fyrir neinn annan en notandann sjálfan. Þá getur notandinn
einfaldlega keyrt Wireshark, vistað það sem hann grípur og sent upplýsingarnar áfram.


