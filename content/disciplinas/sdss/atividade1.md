---
date: "2021-12-05T00:00:00+01:00"
draft: false
menu:
  sdss:
    parent: Unidade 1
    weight: 9
title: Atividade 1.1
toc: false
type: docs
weight: 9
---

## A **Unidade 5** é estruturada considerando os seguintes tópicos:
- Representação de fenômenos no espaço   
- Sistemas de coordenadas geográficas   
- Sistemas de coordenadas projetadas   
- Cartografia temática


## Esta atividade deverá ser realizada até dia **16/12**. São propostas as seguintes atividades:

### 1. Faça o download do shapefile referente às regionais de BH, atividades econômicas formais e autônomos (formais e informais) no site [BHMAP](https://bhmap.pbh.gov.br/v2/mapa/idebhgeo?#zoom=4&lat=7796893.0925&lon=609250.9075&baselayer=base) ou pelo [link]()

### 2. Instale os pacotes:

```{r}
install.packages("sf")
install.packages("terra")
install.packages("spData")
install.packages("spDataLarge", repos = "https://nowosad.r-universe.dev")
```
### 3. Explore a documentação do pacote `sf`

```{r}
vignette(package = "sf") # see which vignettes are available
vignette("sf1")          # an introduction to the package
```

### 4. Siga os comandos a seguir para explorar o pacote `sf`:

`world` é um `sf data frame` contendo colunas espaciais e de atributos, cujos nomes são retornados pela função `names()`(a última coluna deste exemplo contém as informações geográficas).

```{r}
library(sf)
library(terra)
library(spData)
library(spDataLarge) 
class(world)
names(world)
```

Veja o que acontece quando você roda o comando `plot` sobre esse dataframe:

```{r}
plot(world)
```
Copie o código abaixo e rode-o no seu `.Rmd`:

```{r}
plot(world["continent"], reset = FALSE)
cex = sqrt(world$pop) / 10000
world_cents = st_centroid(world, of_largest = TRUE)
plot(st_geometry(world_cents), add = TRUE, cex = cex)
```

O que quer dizer a representação gerada por você?

Os objetos sf podem armazenar informações adicionais sobre os sistemas de referência de coordenadas (CRS). O valor padrão é NA (Não Disponível), como pode ser verificado com st_crs():

```{r}
st_crs(world)
```

[EPSG](https://epsg.io/) simplifica a exploração de sistemas de referência de coordenadas utilizados em todo o mundo para a criação de mapas e geodados e para a identificação da geo-posição. É uma ferramenta prática para qualquer pessoa interessada em cartografia e elaboração de mapas digitais, que precisa conhecer os valores exatos de latitude e longitude para coordenadas numéricas em diferentes sistemas de referência espacial. 

Quando um sistema de referência de coordenadas (CRS) está faltando ou o CRS errado está configurado, a função `st_set_crs()` pode ser usada:

```{r}
new_vector = st_set_crs(new_vector, "EPSG:4326") # set CRS
```

Caso você queira carregar um shapefile para o ambiente R/RStudio, utilize a função: 

```{r}
shapefile <- st_read('caminho do arquivo')
```

### 5. Responda, para você mesmo, as seguintes perguntas que seguem:

a. Qual a diferença entre dados espaciais e dados não-espaciais? 

b. Qual a diferença entre dados vetoriais e raster? 

c. Quais os cuidados necessários para representação geográfica em diferentes sistemas de projeção geográfica?

d. Quais os tipos de geometria de dados vetoriais são representados por meio do pacote `sf`?

e. Qual o EPGS para estudos em BH que precisem de um sistema de projeção de coordenadas? 


### 6. Realize as questões a seguir: 

a. Crie um documento `.Rmd` para que você armazene o código gerado.    

b. Carregue os shapefiles referentes às atividades econômicas e autônomos.

c. Carregue o shapefile referente às regionais de BH. 

d. Verifique os CRS e se necessário, altere os sistemas de coordenadas. 

e. Represente os shapefiles por meio do pacote
[`tmap`](https://cran.r-project.org/web/packages/tmap/vignettes/tmap-getstarted.html). 

>> Dica: tm_shape(objeto_sf) + tm_borders() para polígonos e tm_shape(objeto_sf) + tm_symbols(col = "red", scale = .05) para pontos. Veja a seguir o código onde regional são as feições geométricas poligonais e econ são os pontos referentes às atividades econômicas formais. 

```{r}
tm_shape(regional) + tm_borders() + tm_shape(econ) + tm_symbols(col = "red", scale = .05)
```






