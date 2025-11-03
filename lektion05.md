# Lektion 05 - Quarto

## Om SQL och R (1h)

* Exempel med Kristers databas
* Plottning 

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

