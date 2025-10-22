---
title: 'Almennar upplýsingar um SSH lykla'
---


# SSH lyklar

SSH Lyklar nýtast við public/private key cryptography. Sá aðili sem er með lesaðgang að `private` lyklinum getur notað lykilinn til auðkenningar. Þess vegna má __BARA__ sá aðili sem á lykilinn hafa réttindi til að lesa lykilinn.

Geymslustaðir fyrir private lykla.
- Ódulkóðaður á tölvunni þinni (Diskurinn tryggður með bitlocker eða luks)
- Dulkóðaður á tölvunni þinni
- Dulkóðaður eða ódulkóðaður í Password manager sem aðeins þú hefur aðgang að.

Vondir staðir fyrir private lykla.
- Á netþjónum sem aðrir hafa aðgang að.
- Á internetinu
- Í git repo

## Landspítali býður bara upp á auðkenningu á linux þjóna með SSH lyklum

## Lokað er á SSH milli þjóna.

# Notkun:

Putty: [SSH með Putty](/guides/is/SSH/ssh-lyklar-med-putty)
ssh: [SSH með native ssh](/guides/is/SSH/ssh-lyklar)