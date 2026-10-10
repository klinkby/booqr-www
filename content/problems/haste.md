---
title: "For mange anmodninger"
code: "haste"
status: 429
description: "Du sender anmodninger for hurtigt. Se hvad der kan udløse fejlen, og hvordan du kommer videre."
draft: false
---

## Hvad kan udløse fejlen?

Du har sendt for mange anmodninger på for kort tid. Det sker for eksempel hvis du klikker gentagne gange på samme knap, genindlæser siden i hurtig rækkefølge, eller hvis et program kalder API'et i en tæt løkke. For at beskytte tjenesten mod overbelastning sætter serveren dig midlertidigt på pause. Kort sagt: tag den med ro.

## Sådan kommer du videre

Træk vejret, og vent et øjeblik — typisk under et minut — før du prøver igen. Undgå at klikke flere gange på samme knap; én gang er nok. Kalder du API'et fra egen kode, så sænk tempoet, og respektér en eventuel `Retry-After`-header i svaret, der fortæller hvor længe du skal vente. Fortsætter fejlen længe efter, at du har holdt pause, så kontakt os.
