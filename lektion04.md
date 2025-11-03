# Lektion 4

## Repetition och sammanfattande övning (2h)

Klistra in följande kommentarer i R och genomför varje steg:

```R
# Ladda in datasetet ToothGrowth som finns inbyggt i R och spara det i en variabel 'tg'
# Utforska hur datasetet ser ut och vad det är med ?, head() samt att klicka på dataframen
# för att se det i tabellformat i RStudio

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

## Aggregate() (0.5h)

* [Kapitel 10.3 i YaRrr](https://bookdown.org/ndphillips/YaRrr/aggregate-grouped-aggregation.html)

```r
aggregate(weight ~ Diet + Time,
          FUN = mean,
          subset = Time < 10,
          data = ChickWeight)
```

## CSV-filer (2h)

* working directory - vad det är och varf det är viktigt
* read.csv() och read.table()

```r

# Sätt working directory till mappen där du har sparat filen pos_receipts_2025-06_-2025_08.csv
# Det kan du göra i file-tabben i RStudio, genom att navigera till mappen du har dina csv-filer i 
# och sedan klicka på kugghjulet och välja "Set As Working Directory"

# Läs in CSV-filen och spara den i en variabel som du kallar receipts
# OBS: Detta kommer inte funka om du inte satt working directory korrekt!
receipts <- read.csv("pos_receipts_2025-06_-2025_08.csv");

# Hur många enskilda kvitton finns i datat?
# Använd unique() för att få en vektor med alla enskilda ReceiptId, och sedan length() för att räkna hur många det är
length(unique(receipts$ReceiptId))

# Sammanställning av kvitton
summary(receipts$PriceVAT * receipts$Quantity)

# Total försäljning, summera ihop pris * kvantitet för alla rader
total.revenue <- sum(receipts$PriceVAT * receipts$Quantity)

# BÄSTSÄLARE - Vilka produkter sålde mest (i antal sålda enheter)?

# Börja med att summera Quantity per productId med aggregate()
product.sales <- aggregate(Quantity ~ ProductId, data = receipts, FUN = sum)

# Ordna listan utifrån quantity och hämta de 10 första
ordered.indexes <- order(-product.sales$Quantity)
top10 <- product.sales[ordered.indexes[1:10], ]

# FÖRSÄLJNING PER DAG

# Börja med att lägg till en kolumn med Date-objekt, baserat på datumkolumnen som redan finns
# Titta gärna på data framen innna och efter du kört raden nedan
receipts$Date <- as.Date(receipts$DateTime)

# Nu kan vi göra som innan med aggregate för att summera försäljning per dag istället för per produkt
daily.sales <- aggregate(Quantity * PriceVAT ~ Date, data = receipts, sum)

# Plotta försäljning per dag
plot(daily.sales$Date, daily.sales$Quantity) 

# Antal sålda enheter per dag som en barplot
barplot(daily.sales$Quantity)

# Date är ett objekt i R som håller bara datum, inget klockslag. 
# Vill man lagra datum med tid så använder man objekt av type POSIXct (!)
# Det är ett lite märkligt namn men det är som det är bara. Så exempelvis:

receipts$DateWithTime <- as.POSIXct(receipts$DateTime)

# TOTALT PRIS PER KÖP
receipts.total <- aggregate(Quantity * PriceVAT ~ ReceiptId, data = receipts, sum)

# Byt namn på kolumnerna i den nya data framen för att göra det tydligare, annars heter tex en kolumn "Quantity * PriceVAT"
names(receipts.total) <- c("ReceiptId", "TotalPrice")

# Medelvärde på totala köp per kvitto
mean(receipts.total$TotalPrice)

# Histogram över totala köp per kvitto
hist(receipts.total$TotalPrice)

# UTMANING: # Vilka tider på dagen säljer vi mest grejjer? Nu behöver du använda POSIXct! Se ovan.

```

## REST API KORT INTRO (0.5h)

* Inläsning från APIer med biblioteket jsonlite
* Exempel med /api/products och /api/orders från suvnet.se

```r
library(jsonlite)

products <- fromJSON("https://www.suvnet.se/api/products")

orders <- fromJSON("https://www.suvnet.se/api/orders")
```

Undersök orders och se att orderitems är en data.frame inuti en data.frame! Klicka på dem för att se innehållet.