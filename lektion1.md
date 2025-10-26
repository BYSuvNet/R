# Lektion 1
R är ett programmeringsspråk och en mjukvarumiljö för statistisk analys, datavisualisering och rapportering. Det är särskilt populärt inom statistik, dataanalys och maskininlärning.

## 1. RStudio och de fyra panelerna
När du öppnar RStudio kommer du att se fyra huvudpaneler:
1. **Script Editor (Övre vänstra panelen)**: Här skriver och redigerar du din R-kod.
2. **Console (Nedre vänstra panelen)**: Här körs din R-kod och du kan se resultaten direkt. Allt du gör i R kan göras enbart i konsolen, alla andra saker är bara för att underlätta arbetet.
3. **Environment (Övre högra panelen)**: Aka workspace. Här syns dina objekt som du jobbar med i ditt projekt: värden, arrayer, matriser, data frames, funktioner. Här kan några av de enklare R-funktionerna också köras, såsom View().
4. **View (Nedre högra panelen)**: Här kan du navigera i filer, se grafer, hantera paket, få hjälp mm.

## 2. Få hjälp
Två sätt att få hjälp:

1. Använd sökfunktionen i View-panelen under Help-fliken.
2. skriv ? framför en funktion och sedan tryck ctrl + enter för att få upp hjälpsidan för den funktionen. Exempel: `?mean`

## 3. Grunder

R har många likheter med andra programmeringsspråk, men också en del unika egenskaper. Vi går igenom:

* Värden i R
* Aritmetiska operationer
* Variabeltilldelning
* Enkla datatyper: decimaltal, heltal, text, boolska värden, faktorer, imaginära tal
* Funktioner: sum, print, 
* Undersöka datatyper med funktionen class()

## Viktiga ord och begrepp

#### Working directory / arbetskatalog
Den mapp på din dator där R letar efter filer att läsa in och där den sparar filer du skapar. Du kan ändra arbetskatalogen med `setwd("sökväg/till/mapp")` och kolla vilken katalog du är i med `getwd()`, eller använda RStudios grafiska gränssnitt för att ändra arbetskatalogen (Genom View Pane > Files > More > Set As Working Directory).

#### Objekt
I R är allt ett objekt, inklusive variabler, funktioner, data frames, vektorer, matriser, listor, etc. Objekt kan skapas, modifieras och manipuleras med olika funktioner och operationer. Det är liksom grunden för allt du gör i R.

#### Data frame
En dataram är en tvådimensionell tabellstruktur som används för att lagra data i R. Den liknar en tabell i en databas eller ett kalkylblad, där varje kolumn representerar en variabel och varje rad representerar en observation. Data frames är mycket användbara för dataanalys och manipulation i R.

#### Observation
En observation är en enskild rad i en data frame som representerar en enhet av data, till exempel en person, ett företag eller en händelse. Varje observation innehåller värden för olika variabler (kolumner) som beskriver egenskaper eller attribut för den enheten.
