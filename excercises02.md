# Övningar Lektion 2

## mtcars dataset

Utgå från det inbyggda datasetet `mtcars` i R för att utforska och plotta data. Kopiera koden nedan och fyll i de saknade delarna.


```r

# 1. Skapa ett table utifrån antalet cylindrar i mtcars och gör ett stapeldiagram med barplot().
# Fråga: Vad gör table()-funktionen egentligen? Och varför behövs den till barplot()?

# 2. Beräkna följande sammanfattande statistik för mpg (miles per gallon):
#    - Medelvärde
#    - Median
#    - Standardavvikelse med sd()

# 3. Gör ett histogram som visar fördelningen av något annat än mpg, tex hp (hästkrafter). Lägg till en density-kurva ovanpå histogrammet.

# Lösning på 3:
hist(mtcars$hp, breaks = 15, freq = FALSE, main = "hp")
lines(density(mtcars$hp), lwd = 3)


```

# Histogram + density av mpg
hist(mtcars$mpg, breaks = 20, freq = FALSE, main = "mpg")
lines(density(mtcars$mpg), lwd = 3)

# Samband + linje
plot(mtcars$hp, mtcars$mpg, xlab = "hp", ylab = "mpg")
abline(lm(mpg ~ hp, data = mtcars), lwd = 2)