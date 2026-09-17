# Regnskapsanalyse via Brønnøysund

Et verktøy i R som automatisk henter et norsk selskaps årsregnskap fra
Brønnøysundregistrenes åpne API og lager en ferdig PDF-analyse med nøkkeltall.

## Hva det gjør

- Slår opp et selskap på organisasjonsnummer
- Henter siste innsendte årsregnskap fra Regnskapsregisterets åpne API, og
  selskapsnavnet fra Enhetsregisteret
- Beregner sju nøkkeltall: likviditetsgrad 1, egenkapitalandel, gjeldsgrad,
  rentedekningsgrad, driftsmargin, totalkapitalrentabilitet og
  egenkapitalrentabilitet
- Vurderer hvert tall mot veiledende terskler (grønn/gul/rød)
- Genererer en PDF-rapport med tabell, grafer og plass til egen analyse

## Slik kjører du

1. Åpne `regnskapsanalyse-auto.Rmd` i RStudio.
2. Installer pakkene:
   ```r
   install.packages(c("tidyverse", "knitr", "kableExtra", "scales",
                      "jsonlite", "rmarkdown", "tinytex"))
   tinytex::install_tinytex()   # kjøres én gang
   ```
3. Sett `orgnr` øverst i filen til ønsket selskap (9 siffer).
4. Trykk **Knit**. Ut kommer en PDF-rapport.

## Begrensning

Den åpne delen av Regnskapsregisteret gir kun siste innsendte år, og bryter ikke
ut varelager og kundefordringer. Derfor er likviditetsgrad 2 og kredittid
utelatt. Full flerårshistorikk på linjenivå ligger i den lukkede delen som er
forbeholdt offentlige myndigheter.

## Teknisk

R, R Markdown, tidyverse, ggplot2 og kableExtra. Data hentes fra
data.brreg.no (åpne data, gratis).
