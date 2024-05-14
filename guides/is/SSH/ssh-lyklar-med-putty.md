---
title: "Hvernig: SSH lyklar með PuTTY"
---

# Hvernig: SSH lyklar með PuTTY

1. [Búa til SSH lyklapar](#búa-til-ssh-lyklapar)
2. [Að nota lykilinn með PuTTY](#að-nota-lykilinn-með-putty)


## Búa til SSH lyklapar

Þegar PuTTY er sett upp kemur með forritið __PuTTYgen__

1. Opna __PuTTYgen__
2. Smella á __Generate__
3. Fylgja leiðbeiningum (ef einhverjar, mögulega hreyfa mús yfir auða svæðið)
4. Það er STERKLEGA mælt með að setja lykilorð á lykilinn
5. Vista BÆÐI public og private lykilinn
  * Private lykillinn er bara fyrir þig!
  * Public lykill er það sem þú setur á þjóna til að leyfa notanda að auðkenna
  sig með private lykli. Ef það er beðið þig um lykil, "pubkey", o.s.frv., _þá áttu
  bara að gefa frá þér PUBLIC lykilinn_.

![PuTTYgen]({{ '/assets/images/SSH/puttygen.jpg' | relative_url }})

Viðbót: Þú getur valið týpu af lykli. En þú mátt bara googla það ef þú hefur áhuga

## Að nota lykilinn með PuTTY

Á þessu stigi er væntanlega búið að bæta þínum public lykil við þjóninn sem þú ert að
reyna að tengjast. Ef ekki þá getur þú skoðað [þessar leiðbeiningar]({{ '/guides/en/SSH/adding-key-to-server' | relative_url }})

Þegar þú notar PuTTY þarftu að segja forritinu hvaða lykil
þú vilt nota.

1. Í vinstri glugga putty þarftu að fara undir _Connection_ -> _SSH_ -> _Auth_ -> _Credential_
2. Undir _Private key file for authentication_ þarftu að fara og finna lykilinn sem
þú var búinn til. Private lyklar búnir til með PuTTY end á _.ppk_
3. Núna getur þú farið aftur í _Session_ (efst í vinstri glugga) og tengst þjóninum
eins og venjulega

![Using the PuTTY private key]({{ '/assets/images/SSH/puttyuse.jpg' | relative_url }})

