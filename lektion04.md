# Lektion 4

## Sammanfattande övning

Klistra in följande kommentarer i R och genomför varje steg:

```R
# Ladda in datasetet ToothGrowth som finns inbyggt i R och spara det i en variabel 'tg'

# 1) Skapa två enkla värden (skalärer) för 'dose' och 'length.limit'
# Sätt värdena till 1.0 för dose och 15 för length.limit


# 2) Skapa en logisk vektor du kallar 'mask'. Den ska alltså innehåller en lista med TRUE/FALSE
# baserat på om tg$dose är lika med värdet i 'dose'


# 3) Nu vill vi plocka ut längdvärdena från hela datasetet tg som matchar vår 'mask' (alltså alla längd-värden som matchar dose = 1.0) Så skapa en ny vektor du kallar 'length.by.dose' som innehåller dessa värden.


# 4) Beräkna nu medelvärde och median för de valda längderna


# Vi vill också veta hur många av dessa längder som är över vårt tidigare definierade 'length.limit'. Så, räkna ut detta med hjälp av sum() och skapa en ny variabel 'amount.over.limit' som innehåller detta värde.


# 5) Skapa nu en ny data.frame utifrån det ursprungliga tg-datasetet, men använd masken för att bara inkludera de rader som matchar vår dose, och inkludera endast kolumnerna 'len' och 'supp'. (Du måste nu använda dig av både rad- och kolumnindexering). Kalla data framen 'tg.chosen'.


# Använd plot för att visualisera supplement-typen ($supp) mot längderna ($len) i den nya data framen 'tg.chosen'. Om du vill, försök lägga till en titel som inkluderar dosen, samt etiketter för x- och y-axlarna.


# Använd hist() för att skapa ett histogram av längderna i 'length.by.dose'. Lägg till en titel och etikett för x-axeln.

```

## Aggregate()

* [Kapitel 10.3 i YaRrr](https://bookdown.org/ndphillips/YaRrr/aggregate-grouped-aggregation.html)

## CSV-filer

* working directory - vad det är och varf det är viktigt
* read.csv() och read.table()
* write.csv()

```r
#Kommande kodexempel

```

## REST API 

* Inläsning från APIer med biblioteken jsonlite och httr
* Exempel med /api/products

## SQL

* Exempel med Kristers Databas
