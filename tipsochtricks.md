# Tips och tricks

## Hur rensar jag bort rader med NA-värden ur en data.frame?
```r
cleaned_data <- na.omit(original_data)
```

## Hur ser jag till att tomma strängar ("") blir NA när jag läser in data med read.csv()?
```r
data <- read.csv("file.csv", na.strings = c("", "NA"))
```

## Hur konverterar jag en datum-sträng till ett datum-objekt i R?
Används as.Date():
```r
date_vector <- as.Date(date_strings, format="%Y-%m-%d")
```

## Hur får jag ut alla år från ett datum-objekt?
Använd format():
```r
years <- format(date_vector, "%Y")
```

Detta kan användas för att ta ut alla rader från en datafram för ett visst år:
```r
data_2020 <- data[format(data$date_column, "%Y") == "2020", ]
```

I kombination med table() kan du räkna antal observationer per år:
```r
yearly_counts <- table(format(data$date_column, "%Y"))
```

## Hur ser jag hur många av något som finns i en kolumn?
Använd table():
```r
counts <- table(data$column_name)
```

## Hur sorterar jag en table i fallande ordning?
Använd sort() med decreasing = TRUE:
```r
sorted_counts <- sort(counts, decreasing = TRUE)
```

## Hur väljer jag ut de fem första raderna i en data frame eller vektor?
Använd head():
```r
top5 <- head(data, 5)
```

## Hur väljer jag ut rader som uppfyller ett villkor?
Använd logisk indexering:
```r
filtered_data <- data[data$column_name > threshold, ]
```

## Hur väljer jag ut alla rader som har en kolumn vars värde stämmer överens med en lista av värden?
Använd %in% operatorn:
```r
allasomheterbobkimellesam <- people[people$name %in% c("bob", "kim", "sam"), ]
```

# Hur väljer jag ut alla rader från en dataframe som kommer efter ett visst datum?
```r
data_after_gustavs_birtday <- data[data$date_column > as.Date("1981-06-01"), ]
```




