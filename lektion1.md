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

* Köra kod
* Enkla datatyper: decimaltal, heltal, text, boolska värden ( samt komplexa (imaginära) tal)
* Aritmetiska operationer
* Variabeltilldelning
* Funktioner: sum, print, class, is, as

### Övningar #1

#### 1.1 - Testa konsolen

Syfte: Förstå skillnaden mellan Console och Script.

**Instruktion:**
1. Skriv `5 + 3` direkt i Console och tryck Enter.
2. Skriv sedan samma rad i Script Editor och kör raden med med **Ctrl + Enter** (Se till så att markören står på den rader).
3. Notera var resultatet hamnar.
4. Lägg till några rader i scriptfilen och **kör all kod** genom att trycka `ctrl + alt + r` (Windows) eller `command + option + r` (Mac)
5. Fråga: Varför kan man använda både Console och Script? Hur skiljer de sig åt?

#### 1.2 - Skapa och undersök objekt

Syfte: Se hur Environment-panelen uppdateras.

**Instruktion:**
1. Skriv och kör följande kod:
```r
50
75
a <- 10
b <- 5
summa <- a + b
```
2. Titta i Environment – vilka objekt syns?
3. Prova metoden rm() och skicka in variablen a som *argument*. Vad händer när du kör den raden?
5. Fråga: Varför hamnade vissa saker i Environment och andra inte?

#### 1.3 - Datatyper och class()

Syfte: Lära känna grundläggande datatyperna och hur du undersöker dem.

**Instruktion:**
1. Skapa en variabel av vardera typ: heltal, text, decimaltal, logiskt (boolean)
2. Använd metoden class() och skicka in variablernas namn som argument. Se vad som skrivs ut i konsolen.
3. Det går att konvertera mellan olika datatyper. Gör om ett heltal till ett decimaltal med metoden `as.numeric()` (du måste skicka in en siffra som argument, eller ett variabelnamn.
4. Testa med class() efteråt för att se att det funkade.
5. Du kan också testa om en variabel är av en viss sort med `is`. Testa att skriva tex `is.character` och skicka in en variabel som är av siffertyp och se vad som skrivs ut i konsolen.

#### 1.4 - Ta hjälp!

Syfte: Att bekanta sig med sätt att söka hjälp på i R
1. Skriv en ny rad med `?` följt av namnet på någon metod du använt och kör raden. Se var hjälpen hamnar.
2. Använd sökfunktionen i under-hjälp-tabben och sök på metoden `sum`
3. Fråga: Vad i hjälpen för `sum` är otydligt för dig?

#### 1.5 - Fler funktioner

Syfte: Att bekanta sig lite mer med några funktioner

1. Prova metoden sum()! Använd Hjälp för att se hur den fungerar.
2. Prova metoden mean()! Använd hjälpen för att se hur det fungerar.
3. Det funkar inte att slå ihop två strängar med sum()! Hur ska du kunna sätta ihop två variabler som innehåller text till att bli en variabel som innehåller texten från de båda andra?

## 4. Datastrukturer

De grundläggande datatyperna är de minsta beståndsdelarna av data vi kan hantera i R när vi gör analyser. Det är ju dock först när det blir samlingar av värden vi kan analysera det och vi kan skapa statistik!

* Vektorer - c(), length(), []
* Faktorer (kategorier) - order, levels
* Listor - $, [ [ ] ] (Nästlade objekt)
* Data Frames - 

### Övningar #2

#### 2.1 Vektorer
#### 2.1 Vektorer
#### 2.1 Vektorer
#### 2.1 Vektorer



## Viktiga ord och begrepp

#### Kortkommandon

`ctrl+enter` = kör nuvarandre rad kod
`ctrl + alt + r` = Kör all kod (Windows)
`command + option + r`= Kör all kod (Mac)
`alt + -` = Skriv ut <- inklusive mellanslag efter

#### Working directory / arbetskatalog
Den mapp på din dator där R letar efter filer att läsa in och där den sparar filer du skapar. Du kan ändra arbetskatalogen med `setwd("sökväg/till/mapp")` och kolla vilken katalog du är i med `getwd()`, eller använda RStudios grafiska gränssnitt för att ändra arbetskatalogen (Genom View Pane > Files > More > Set As Working Directory).

#### Objekt
I R är allt ett objekt, inklusive variabler, funktioner, data frames, vektorer, matriser, listor, etc. Objekt kan skapas, modifieras och manipuleras med olika funktioner och operationer. Det är liksom grunden för allt du gör i R.

#### Data frame
En dataram är en tvådimensionell tabellstruktur som används för att lagra data i R. Den liknar en tabell i en databas eller ett kalkylblad, där varje kolumn representerar en variabel och varje rad representerar en observation. Data frames är mycket användbara för dataanalys och manipulation i R.

#### Observation
En observation är en enskild rad i en data frame som representerar en enhet av data, till exempel en person, ett företag eller en händelse. Varje observation innehåller värden för olika variabler (kolumner) som beskriver egenskaper eller attribut för den enheten.
