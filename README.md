# Pictogram

🌲 A pictogram chart comparing the size of the red angelim (Dinizia excelsa), a South American canopy-emergent tree species, with the three tallest trees in the world.

ℹ️  [Wikipedia](https://en.wikipedia.org/wiki/List_of_tallest_trees).

- [Script `.R`](https://github.com/fblpalmeira/pictograma_arvores/blob/main/data/pictogram_v2.R)

- [Database `.html`](https://en.wikipedia.org/wiki/List_of_tallest_trees)

``` r
<img src="https://github.com/fblpalmeira/pictograma_arvores/blob/main/data/pictogram_v2.png">

library(tidyverse)
library(echarts4r)

Sequoia <- "https://i.pinimg.com/564x/23/8a/cd/238acdd6e1be0e1b0134117828b7da8e.jpg"
Shorea <-"https://www.frontiersin.org/files/Articles/462908/ffgc-02-00032-HTML/image_m/ffgc-02-00032-g001.jpg"
Eucalyptus <- "https://raw.githubusercontent.com/fblpalmeira/pictograma_arvores/main/data/Eucalyptus_regnans.jpg"
Dinizia <- "https://raw.githubusercontent.com/fblpalmeira/pictograma_arvores/main/data/Dinizia_excelsa.png"
Cristo <- "https://iconape.com/wp-content/files/gi/297679/png/cristo-redentor-brasil-logo.png"

data <- data.frame(
  x = c("Coast redwood", "Yellow meranti", "Mountain ash", "Red angelim", "Christ the Redeemer"), 
  value = c(115.92, 100.8, 100.5, 88.5, 38),
  symbol = c(paste0("image://", Sequoia),
             paste0("image://", Shorea),
             paste0("image://", Eucalyptus),
             paste0("image://", Dinizia),
             paste0("image://", Cristo))
)

data %>% 
  e_charts(x) %>% 
  e_pictorial(value, symbol) %>% 
  e_theme("westeros") %>% 
  e_legend(FALSE) %>% 
  # Title Alignment
  e_title(paste0("Comparing the size of the red angelim (Dinizia excelsa) with the 3 tallest trees in the world"), 
          subtext = "Based on Wikipedia data | Visualization by @fblpalmeira", 
          sublink = "https://github.com/fblpalmeira/pictograma_arvores", 
          left = "center", top = 10)%>%
  e_labels(show=TRUE) %>%
  e_x_axis(splitLine=list(show = FALSE)) %>%
  e_y_axis(show=FALSE, min=0, max=200, interval=20, splitLine=list(show = FALSE))

```
