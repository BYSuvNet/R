# Lektion 2

## Installera och använda bibliotek

Vi installerar tidyverse och yarrr biblioteket som vi kommer att använda för datahantering och visualisering.

## Yarrr och boken The Pirate's Guide to R

Yarrr är ett paket som innehåller funktioner och dataset som används i boken "The Pirate's Guide to R" av Nathaniel Phillips. Vi gör några övningar från boken för repetition:

* [Enkla värden](https://bookdown.org/ndphillips/YaRrr/test-your-r-might.html)
* [Övning: Skapa vektorer](https://bookdown.org/ndphillips/YaRrr/test-your-r-might-1.html) 

## Summering

* sum(), product() - summera eller multiplicera värden i en vektor
* min(), max() - hitta minsta och största värde
* mean(), median() - medelvärde och median
* sd(), var() - standardavvikelse och varians
* length() - antal element i en vektor
* quantile() - percentiler
* summary() - sammanfattande statistik

* round() - avrunda värden till ett visst antal decimaler
* ceiling() och floor() - avrunda uppåt eller nedåt

## Räkna saker

* unique() - hitta unika värden i en vektor
* table() - skapa en frekvenstabell

## Saknade värden

* is.na() - kolla vilka värden som är saknade (NA)
* na.omit() - ta bort saknade värden från en vektor eller data frame
* na.rm = TRUE - argument i många funktioner för att ignorera saknade värden vid beräkningar

## Standarisaring av data

[Läs detta kapitel](https://bookdown.org/ndphillips/YaRrr/standardization-z-score.html) och diskutera det i grupp.

[Sammanfattande Övningar](https://bookdown.org/ndphillips/YaRrr/test-your-r-might-2.html)

## Generera slumpdata

* sample() - slumpmässigt urval från en vektor
* rnorm() - generera slumpmässiga tal från en normalfördelning
* runif() - generera slumpmässiga tal från en uniform fördelning

## Mer plottning

* lines() → ritar linje från färdiga data (du ger x och y).
* curve() → ritar linje från en matematisk funktion (du anger formeln).
* density() → skapar en täthetsfunktion från data (används med plot() eller lines()). Visar var det finns många värden i en fördelning.
    * Visar samma sak som histogram men på olika sätt:
    * Histogram: staplar
    * Density: en jämn linje som följer staplarnas form

## Utforska och plotta data från dataset

Vi tittar på plottning av data och samband. Här är exempelkoden för att leta samband i luftkvalitetsdata:

```r
# Ladda in datasetet airquality, men ta först bort alla observationer som saknar någon data
aq <- na.omit(airquality)

# Lagra två variabler i a och b så att vi lätt kan testa olika saker här
a <- aq$Wind
b <- aq$Temp

# Plotta ut a och b med en scatterplot, döp axlarna till något om du vill
plot(a, b, pch = 19, xlab = "Vindstyrka", ylab = "Temperatur")

# Rita en mjuk linje genom punkterna. "f" bestämmer hur mjuk linjen ska vara. 1 = spikrak
lines(lowess(a, b, f = 0.3), lwd = 2, col = "red")

# Ritar ut den räta linje (regressionslinje) som bäst beskriver sambandet
# mellan temperatur (Temp) och vindhastighet (Wind) i datamängden 'aq'.
# Linjen beräknas med en linjär modell (lm) och läggs ovanpå den befintliga plotten.
abline(lm(Temp ~ Wind, data = aq))

# Beräknar korrelationskoefficienten (Pearsons r) mellan vektorerna a och b.
# Resultatet visar styrkan och riktningen på det linjära sambandet (-1 till +1).
# Noll betyder inget samband, de andra positiva eller negativa samband
cor(a, b)

# Utför ett statistiskt test på korrelationen mellan a och b.
# Testar om sambandet skiljer sig signifikant från 0 (ingen korrelation).
# Returnerar även p-värde, konfidensintervall och t-värde.
cor.test(a, b)
```