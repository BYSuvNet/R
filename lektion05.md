# Lektion 05 - Quarto

## Om SQL och R (1h)

* Exempel med Kristers databas

```r
install.packages("DBI")
install.packages("RMariaDB")

library(DBI)
library(RMariaDB)

# Skapa en uppkoppling till databasen:

con <- dbConnect(
  MariaDB(),
  dbname = "storedb",
  host = "comet-direct.usbx.me",
  port = 17815,
  user = "yhstudent",
  password = "darthvader123!"
)

# Gör en query

customers <- dbGetQuery(con, "SELECT * FROM Customer")

# Dela upp adressen till gatuadress och stad
splitAdress <- do.call(rbind, strsplit(customers$Address, ",\\s*")) # se kommentar längst ner vad detta gör
customers$Address <- splitAdress[,1]
customers$City <- splitAdress[,2]

# Räkna antalet gånger olika städer nämns
cityCount <- table(customers$City)

# Rita ett cirkeldiagram över fördelningen
pie(cityCount, main = "Kunder per stad")

# Stäng uppkopplingen till databasen

dbDisconnect(con)

# Kommentar om splitAdress:
# customers$Address är vektorn som innehåller alla adresser i stil med "Sågvägen 5, Borlänge"
# med strsplit(..., ",\\s*") delar vi den strängen i två bitar vid varje kommatecken följt av x antal mellanslag (det är det som \\s* betyder)
# vi får då en ny vektor med gatuadress som första index och stad som andra index
# do.call(rbind, ...) anropar rbind() och skickar in listans elements ett och ett
# rbind() = Row Bind. Binder ihop vektorer radvid med varandra, staplar dom på varandra. 
# resultatet blir en matris (som en dataframe fast bara samma datatyp överallt, och inte namngivna kolumner)
# Vi kan nu sätta den tidigare Adress till värdet på den första kolumnen i matrisen
# och skapa en ny tabell för City med värdet från den andra kolumnen

```

## Vad är Quarto? (Resten av dagen)

Quarto låter dig skriva text + kod i samma dokument och generera HTML, PDF eller Word-rapporter. Quarto är efterträdaren till R Markdown och fungerar också med Python, inte bara R.

## Skapa ett nytt dokument

File → New File → Quarto Document

* Skriv en Title och en Author om du vill. 
* Klicka sedan OK.

## Struktur i Quarto-dokument

Exempel på Quarto-dokument:

```yaml
---
title: "Min första Quarto-rapport"
author: "Gustav"
format: html
---

# Detta är en rubrik

Detta är lite text.

* Detta är en punktlista
* Med flera punkter

```{r, echo=FALSE, message=FALSE, warning=FALSE}
# Detta är ett kodblock i R
x <- c(1, 2, 3, 4, 5)
mean(x)

# En plot
plot(x, x^2)
```

## Rendera dokumentet

Klicka på "Render" uppe till höger i Quarto-filen.
RStudio kör all kod och skapar en HTML-fil med text, kod och resultat.

## Inställningar

| Option | Vad den gör | Visar kod | Visar output |
|---------|--------------|-----------|---------------|
| `echo: false` | Dölj koden, visa bara resultatet | ❌ | ✅ |
| `include: false` | Kör blocket men visa varken kod eller resultat | ❌ | ❌ |
| `eval: false` | Visa koden men kör den inte | ✅ | ❌ |
| `message: false` | Dölj meddelanden från `message()` (t.ex. paket-load-text) | ✅/❌ (beroende på echo) | ✅ (utan messages) |
| `warning: false` | Dölj `warning()`-utskrifter | ✅/❌ | ✅ (utan warnings) |
| `results: 'hide'` | Dölj text-resultat (console output), men behåll t.ex. plots | ✅/❌ | ✅ (endast plot) |
| `results: 'asis'` | Tolka R-utdata som ren text/HTML/Markdown (används ofta med `cat()`) | ✅/❌ | ✅ (formaterad text) |
| `fig.cap: "Text"` | Lägger till figurtext (caption) under plot | ✅/❌ | ✅ |
| `cache: true` | Sparar resultatet lokalt så blocket inte behöver köras igen om inget ändrats | ✅/❌ | ✅ |
| `error: true` | Låter dokumentet fortsätta även om blocket ger fel (visar felet) | ✅/❌ | ✅ (visar fel) |

Du kan ställa in detta per block eller globalt:

Detta är i block under efter {r}:
#| echo: false
#| message: false

Detta är i dokumentets YAML-header (gäller alla block):
execute:
  echo: false
  message: false

## Övningar med Quarto

1. Skapa ett nytt Quarto-dokument.
2. Skriv en kort text om dig själv.
3. Lägg till ett kodblock utan några inställningar alls (bara {r}). Kodblocket ska:
    * Skapar en vektor med talen 1 till 255.
    * Beräknar medelvärdet av vektorn och skriver ut värdet.
4. Rendera dokumentet och se hur det ser ut.
5. Ändra kodblocket så att koden inte visas, bara resultatet. Rendera igen och titta på resultatet.
6. Lägg till detta till ett nytt kodblock:
    ```{r}
    plot(1:255, (1:255)^2)
    ```