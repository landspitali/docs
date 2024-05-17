---
title: 'Hvernig: SSH lyklar'
---

# Hvernig: SSH lyklar

Þar sem SSH er orðið aðgengilegt í Windows þá ættu þessar leiðbeiningar að virka
fyrir hvaða stýrikerfi sem þú vilt. En gott er að vita að þessir lyklar virðast
ekki virka með PuTTY. Ef þú vil PuTTY þá getur þú skoðað það [hér]({{ '/guides/is/SSH/ssh-lyklar-med-putty' | relative_url }})

1. [Einfalda leiðin](#einfalda-leiðin)
  * [Að búa til lyklaparið](#að-búa-til-lyklaparið)
  * [Að nota lyklaparið](#að-nota-lyklaparið)
2. [Aðeins minna einfalda leiðin](#aðeins-minna-einfalda-leiðin)
3. [SSH Vandamál](#ssh-vandamál)

## Einfalda leiðin

### Að búa til lyklaparið

```
$ ssh-keygen
...
# Bara ýta á enter þangað til þetta endar
...
```

Og þetta er komið. Það er mælt sterklega með að setja lykilorð á lykilinn. Þegar þú keyrir þessa
skipun þá er beðið um það sjálfkrafa.

Ef einhver biður um lykilinn þinn, key, pubkey, o.s.frv., þá skaltu __BARA__ gefa frá þér 
public lykilinn (lykillinn sem endar á _.pub_)

### Að nota lyklaparið

Sjálfgefinn staðsetning fyrir lyklana er:
* $HOME/.ssh/id_rsa (private lykill)
* $HOME/.ssh/id_rsa.pub (public lykill)

Við gefum okkur það að búið sé að bæta public lykil á þjón. Ef ekki þá er hægt að
skoða [þessar leiðbeiningar]({{ '/guides/en/SSH/adding-key-to-server' | relative_url }})

Núna ætti að vera einfalt að tengjast þjóninum:
```
$ ssh <notandanafn>@<þjónn>
# t.d. ssh jonjonsson@203.0.113.5
# það þarf ekki að skilgreina notandanafn sérstaklega ef það er það sama á þjóninum
# og tölvunni sem þú notar til að tengjast
```

Og þú ættir að komast inn

## Aðeins minna einfalda leiðin

Stundum viltu hafa fleiri en einn lykil. Þú hefur mörg umhverfi eða þig vantar
sjálfvirkni og nennir ekki að skrá inn lykilorð.

Þú gerir það sama nema þú þarft bara að skilgreina hvar þú vilt vista lyklaparið.
Passaðu þig að yfirskrifa óvart ekki gamla lyklaparið ef þú ert að nota það (ssh-keygen
mun var þig við.

```
# Þú getur vistað lykilinn hvar sem þú vilt annarsstaðar en $HOME/.ssh/, en þegar
# þú reynir að tengjast með SSH skoðar það sjálfkrafa lyklana undir þeirri möppu
# og reynir að nota þá þangað til einhver virkar.

$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/notandi/.ssh/id_rsa): /home/notandi/.ssh/bananalykill
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/notandi/.ssh/bananalykill
Your public key has been saved in /home/notandi/.ssh/bananalykill.pub
```

Ef að lykillinn var vistaður undir sjálfgefnu möppunni þá ætti að duga að keyra
`ssh <einhver.þjónn>`

Hinsvegar ef lykilinn er ekki vistaður í sjálfgefinni möppu eða þú ert með of marga
lykla og færð neitun eftir að hafa reynt á X marga lykla þá geturu sagt SSH að nota
ákveðinn lykil

```
ssh <einhver.þjónn> -i /MAPPA/MEÐ/LYKLI/lykill
```
Og þú ættir að komast inn


## SSH Vandamál

Ef þú lendir í veseni með að tengjast með SSH þá er góð leið að bæta við -v fyrir aftan ssh til þess að fá frekari upplýsingar, ef þú ert í vandræðum með að tenjast og þarft að hringja í vin þá mælum við með að senda þessar upplýsingar með.


```
# ssh -v banani@204.220.0.1
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: No credentials were supplied, or the credentials were unavailable or inaccessible
No Kerberos credentials available (default cache: KCM:)
debug1: No credentials were supplied, or the credentials were unavailable or inaccessible
No Kerberos credentials available (default cache: KCM:)
debug1: Next authentication method: publickey
debug1: Offering public key: /home/banani/.ssh/id_rsa RSA SHA256:asdfasdfasdfadsf agent
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Offering public key: /home/banani/.ssh/id_ed25519 ED25519 SHA256:ahfd371asgfasdf agent
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Offering public key: /home/banani/.ssh/id_git_rsa RSA SHA256:37uyadsgahdfhad agent
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Offering public key: banani RSA SHA256:asdh1347yasdgasdg agent
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Trying private key: /home/banani/.ssh/id_ecdsa
debug1: Trying private key: /home/banani/.ssh/id_ecdsa_sk
debug1: Trying private key: /home/banani/.ssh/id_ed25519_sk
debug1: Trying private key: /home/banani/.ssh/id_xmss
debug1: Trying private key: /home/banani/.ssh/id_dsa
debug1: Next authentication method: password
banani@204.220.0.1's password: 
```