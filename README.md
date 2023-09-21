# Pictogram

🌲 A pictogram chart comparing the size of the red angelim (Dinizia excelsa), a South American canopy-emergent tree species, with the three tallest trees in the world.

<img src="https://github.com/fblpalmeira/pictograma_arvores/blob/main/data/pictogram_v2.png">

ℹ️  [Wikipedia](https://en.wikipedia.org/wiki/List_of_tallest_trees).

- [Script `.R`](https://github.com/fblpalmeira/pictograma_arvores/blob/main/data/pictogram_v2.R)

- [Database `.html`](https://en.wikipedia.org/wiki/List_of_tallest_trees)

-----

# Aprenda a fazer um pictograma

Crie gráficos interativos utilizando o pacote 'echarts4r' uma extensão da biblioteca 'Echarts Javascript', que inclui 36 tipos de gráficos, temas, 'Shiny' proxies e animações. O código é dividido em três pequenas partes e é super simples. 

# Instalando e abrindo o pacote `echarts4r`

Primeiro, instale o pacote utilizando o comando `install.packages("echarts4r")` e, em seguida, utilize o comando `library(echarts4r)` para abrir o pacote. Também vamos utilizar o pacote `tidyverse` para manipular os dados que serão utilizados.

``` r

library(tidyverse)
library(echarts4r)

```

# Primeira parte

Crie os objetos que irão compor o pictograma. Neste caso, temos 4 espécies de árvores (Sequoia, Shorea, Eucalyptus e Dinizia) e o Cristo Redentor que vai servir como uma escala comparativa para mostrar o tamanho das árvores. Dentro de cada objeto, vamos inserir o link de onde estão as figuras que iremos utilizar para fazer o pictograma. Temos duas opções, ou pegamos os links da internet ou carregamos a figura dentro do repositório no GitHub.  

``` r

Sequoia <- "https://i.pinimg.com/564x/23/8a/cd/238acdd6e1be0e1b0134117828b7da8e.jpg"
Shorea <- "https://www.frontiersin.org/files/Articles/462908/ffgc-02-00032-HTML/image_m/ffgc-02-00032-g001.jpg"
Eucalyptus <- "https://raw.githubusercontent.com/fblpalmeira/pictograma_arvores/main/data/Eucalyptus_regnans.jpg"
Dinizia <- "https://raw.githubusercontent.com/fblpalmeira/pictograma_arvores/main/data/Dinizia_excelsa.png"
Cristo <- "https://iconape.com/wp-content/files/gi/297679/png/cristo-redentor-brasil-logo.png"

```

# Segunda parte 

Agora, vamos criar outro objeto chamado `data` para armazenar as informações das figuras que vamos utilizar. Neste caso, vamos criar um `data.frame` inserindo o nome popular das espécies de árvores ("Coast redwood", "Yellow meranti", "Mountain ash", "Red angelim", "Christ the Redeemer") e, em seguida, adicionar a altura de cada uma delas na mesma ordem dos nomes populares. Neste mesmo `data.frame`, vamos adicionar os nomes dos objetos que criamos para armazenar os links das figura (vide na primeira parte do código).

``` r

data <- data.frame(
  x = c("Coast redwood", "Yellow meranti", "Mountain ash", "Red angelim", "Christ the Redeemer"), 
  value = c(115.92, 100.8, 100.5, 88.5, 38),
  symbol = c(paste0("image://", Sequoia),
             paste0("image://", Shorea),
             paste0("image://", Eucalyptus),
             paste0("image://", Dinizia),
             paste0("image://", Cristo))
                  )

```

# Terceira parte 

Para finalizar, vamos chamar o objeto `data` criado na seção anterior

``` r

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

----

# References

Coene J (2022). _echarts4r: Create Interactive Graphs with 'Echarts JavaScript' Version 5_.
  R package version 0.4.4, <https://CRAN.R-project.org/package=echarts4r>.

  

```
