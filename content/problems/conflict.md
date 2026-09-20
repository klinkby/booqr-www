---
title: "Ressourcekonflikt"
code: "conflict"
status: 409
description: "Handlingen er i konflikt med systemets tilstand. Se hvad der kan udløse fejlen, og hvordan du kommer videre."
draft: false
---

## Hvad kan udløse fejlen?

Handlingen strider mod systemets nuværende tilstand. Typisk fordi noget allerede findes — for eksempel en dobbeltbooking af samme tidspunkt, en e-mail der allerede er i brug, eller et element du forsøger at oprette to gange. Serveren afviser handlingen for at bevare konsistensen i dine data.

## Sådan kommer du videre

Genindlæs siden for at se den aktuelle tilstand, og prøv igen med andre værdier. Er tidspunktet optaget, så vælg et ledigt. Er e-mailen allerede i brug, findes kontoen måske i forvejen — prøv at logge ind i stedet. Undgå at klikke flere gange på samme knap, da det kan skabe dubletter. Når du har justeret det der var i konflikt, kan handlingen gennemføres.
