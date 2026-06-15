# Ruteoptimalisering · Google Maps

Et lite, gratis webverktøy for feltarbeid: start fra din egen posisjon, lim inn
alle adressene rått, og få korteste rekkefølge som en ferdig Google Maps-rute.
Ingen innlogging, ingen API-nøkkel, ingen backend — alt kjører i nettleseren.

### På mobil
Åpne [Ruteoptimalisering](https://michaelteknikerrk.github.io/Ruteoptimalisering/) i nettleseren og velg «Legg til på Hjem-skjerm». Da oppfører den seg
som en app i felt.

## Slik bruker du den

1. **Startpunkt** – trykk «Bruk min posisjon» (tillat posisjon når nettleseren
   spør), eller skriv inn en startadresse manuelt.
2. **Sted / kommune** – valgfritt, men anbefalt. Skriver du f.eks. `Mo i Rana`,
   tolkes alle gateadresser i riktig kommune og treffraten blir mye bedre.
3. **Stopp** – lim inn alle adressene rått, én per linje. Nummerering (`1.`),
   bindestreker og punktlister blir ryddet vekk automatisk, og duplikater fjernes.
4. Huk av/på **rundtur** (tilbake til start). På som standard.
5. Trykk **Optimaliser rute**.
6. Sjekk resultatet: velg riktig treff i nedtrekkslistene ved tvil, rett opp
   adresser som ikke ble funnet, eller flytt stopp med pilene. Trykk til slutt
   **Åpne rute i Google Maps**.

> Lange ruter deles automatisk opp i flere Google Maps-lenker (Maps tar maks
> ~10 stopp per lenke). Hver del fortsetter der forrige slapp.

## Hvordan det fungerer

- **Geokoding:** OpenStreetMap / Nominatim (gratis, ingen nøkkel). Hver adresse
  prøves i flere varianter for å tåle små skrivefeil og formateringsavvik:
  som skrevet → med sted/kommune → med husnummer-bokstav fjernet (f.eks.
  `1D` → `1`).
- **Optimalisering:** nærmeste-nabo + 2-opt på luftlinje-avstand. Raskt og gratis,
  og gir samme eller nær optimal rekkefølge for typiske feltdager. Faktisk
  kjøreavstand regner Google Maps ut når ruten åpnes.
- **Lagring:** sted/kommune, startadresse og rundtur-valg huskes lokalt i
  nettleseren (`localStorage`). Ingenting sendes til noen server utenom selve
  geokodingsoppslagene til Nominatim.

## Vær oppmerksom på (Nominatim)

Verktøyet bruker den offentlige Nominatim-tjenesten og respekterer grensen på
maks **1 oppslag per sekund** (innebygd forsinkelse). Det egner seg for vanlig
felt-/enkeltbruk. Skal mange bruke verktøyet samtidig eller med store volum, bør
du sette opp egen Nominatim-instans eller bruke en betalt geokodingstjeneste, i
tråd med Nominatims bruksvilkår.

## Personvern

Adressene geokodes mot Nominatim. Unngå å lime inn personidentifiserende
opplysninger (navn, fødselsnummer, EPJ-referanser e.l.) sammen med adressene —
bruk kun selve besøksadressene.

## Tilskrivelse

- Kart- og adressedata: © OpenStreetMap-bidragsytere (ODbL).
- Geokoding: Nominatim (OpenStreetMap Foundation).
- Rutevisning: Google Maps.
