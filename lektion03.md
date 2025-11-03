# Lektion 3

## Första timmen - Indexering av vektorer

https://web.archive.org/web/20250404224047/https://bookdown.org/ndphillips/YaRrr/vectorindexing.html

```R
people <- c("kim", "sam", "timmy", "anna", "bob")
age <- c(30, 32, 45, 30, 50)
favouriteColor <- c("red", "blue", "brown", "black", "blue")

# Ta ut det tredje elementet i listan
people[3]

# Ta ut de tre första elementen i listan
people[1:3]

# Ta ut det femte och det tredje elementet i listan
people[c(5, 3)]

# Ta ut alla personer vars ålder är över 30 men under 50
people[age > 30 & age < 50]

# Ta ut alla namn vars längd är under 4
people[nchar(people) < 4]

# Räkna ut medelålder på alla vars namn är 3 tecken eller kortare
mean(age[nchar(people) < 4])

# Räkna ut medelålder på alla vars namn är 3 tecken eller kortare && vars 
# favvofärg är blå
mean(age[nchar(people) < 4 & favouriteColor == "blue"])
```

## Andra och tredje timmen- Ändra värden i en vektor samt övningar

```R

# Byt ut det tredje namnet i people-vektorn mot "tim"
names[3] <- "tim"

# Sätt de tre första elementen i vektorn till tomma strängar
names[1:3] <- ""

# Sätt alla namn med längd 1 eller mindre till "noname"
names[nchar(names) <= 1] <- "noname"

```

Hantering av saknade värden med na.rm = TRUE

```R
age <- c(-30, 30, 45, 30, 75, 31, 666)

# Sätt alla åldrar som uppenbarligen är fel till NA
age[age > 130 | age < 0] <- NA

# Skippa NA-värden när vi beräknar medelvärde
mean(age, na.rm = TRUE)
```

Övningar: https://web.archive.org/web/20250404162352/https://bookdown.org/ndphillips/YaRrr/test-your-r-might-movie-data.html

## Fjärde timmen - Dataframe slicing och manipulation

```r
# Hämta ut alla rader där age är över 40
df[df$Age > 40, ]

# Välj ut de första sex kolumnerna
myPirates <-pirates[,1:6]

# Välj ut alla pensionerade kvinnliga pirater som bär pannband
femalePirates <- myPirates[myPirates$sex == "female" & 
                             myPirates$age >= 65 & 
                             myPirates$headband == "yes", ]

# Räkna ut deras medelålder
meanFemalePirateAge <- length(femalePirates)
meanFemalePirateAge

aSubset <- subset(myPirates, 
  subset = sex == "female" &
    age >= 65 & 
    headband == "yes"
       )

meanFemalePirateAge <- mean(myPirates[myPirates$sex == 'female' & myPirates$age > 35,]$age)
meanFemalePirateAge

```



