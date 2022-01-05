---
date: "2021-12-05T00:00:00+01:00"
draft: false
menu:
  sdss:
    parent: Unidade 2
    weight: 13
title: Atividade 2.2
toc: false
type: docs
weight: 13
---

## A **Unidade 6** é estruturada considerando os seguintes tópicos:

- Dados espaciais e geocodificação;    
- Estrutura de dados espaciais;   
- Como transformar dados não espaciais em espaciais


## Esta atividade deverá ser realizada até dia **06/01**. São propostas as seguintes atividades:

### 1. Faça uma pesquisa e defina:    
- Geocodificação   
- Geocodificação reversa

### 2. O que o OpenStreetMap? E o Nominatim? 

### 3. Instale e chame os pacotes:

```{r}
devtools::install_github("hrbrmstr/nominatim")
install.packages("ggmap")
install.packages("RCurl")
install.packages("jsonlite")
install.packages("tmaptools")
install.packages("leaflet")
install.packages("RgoogleMaps")
```

```{r}
library(nominatim)
library(ggmap)
library(tmaptools)
library(RCurl)
library(jsonlite)
library(tidyverse)
library(leaflet)
library(RgoogleMaps)

```

### 4. Geocodificação com o OSM

#### Usando o pacote `nominatim`:

```{r}
b1 <- osm_geocode("Berlin, Germany")
b1[c("lat", "lon")]
```

#### Usando o pacote `tmaptools`

```{r}
# modifying some search requests
pubs_m <- pubs
pubs_m[pubs_m=="The Crown and Sugar Loaf, Fleet Street"] <- "The Crown and Sugar Loaf"
pubs_m[pubs_m=="Ye Olde Mitre, Hatton Garden"] <- "Ye Olde Mitre"
pubs_m_df <- data.frame(Pubs = pubs_m, stringsAsFactors = FALSE)

# geocoding the London pubs
# "bar" is special phrase added to limit the search
pubs_tmaptools <- geocode_OSM(paste(pubs_m, "bar", sep = " "),
                              details = TRUE, as.data.frame = TRUE)

# extracting from the result only coordinates and address
pubs_tmaptools <- pubs_tmaptools[, c("lat", "lon", "display_name")]
pubs_tmaptools <- cbind(Pubs = pubs_m_df[-10, ], pubs_tmaptools)

# print the results
pubs_tmaptools
```

### 5. Geocodificação com o Google

Para usar o Google, cadastre-se na plataforma Cloud e substitua no código a seguir a sua API

```{r}
register_google(key = api_key)
```

#### Rode o código a seguir e veja o que acontece:
```{r}
library(ggmap)  
geocode("Berlin, Germany", source="google")
```

#### Outro exemplo: 

```{r}
# create a list of London pubs
pubs <- c("The Angel, Bermondsey", "The Churchill Arms, Notting Hill", "The Auld Shillelagh, Stoke Newington", "The Sekforde, Clerkenwell", "The Dove, Hammersmith", "The Crown and Sugar Loaf, Fleet Street", "The Lamb, Holborn", "Prince of Greenwich, Greenwich", "Ye Olde Mitre, Hatton Garden", "The Glory, Haggerston", "The Blue Posts, Soho", "The Old Bank of England, Fleet Street")
pubs_df <- data.frame(Pubs = pubs, stringsAsFactors = FALSE)

# run the geocode function from ggmap package
pubs_ggmap <- geocode(location = pubs, output = "more", source = "google")
pubs_ggmap <- cbind(pubs_df, pubs_ggmap)

# print the results
pubs_ggmap[, 1:6]
```

#### Mais uma opção usando o `RgoogleMaps`:

Crie o dataframe:

```{r}
cidades <- c("Belo Horizonte MG","Contagem MG", "Juiz de Fora MG",
             "Uberlandia MG", "Montes Claros MG", "Uberaba MG",
             "Varginha MG", "Governador Valadares MG", "Salto da Divisa MG",
             "Para de Minas MG", "Bom Despacho MG", "Manhuacu MG",
             "Rio Casca MG", "Tres Coracoes MG", "Tres Pontas MG",
             "Sao Sebastiao do Paraiso MG", "Iturama MG", "Joaima MG",
             "Vicosa MG", "Montalvania MG", "Frutal MG", "Ipatinga MG",
             "Aimores MG", "Muriae MG", "Januaria MG")
DF <- data.frame(cidade=cidades, lat=NA, lon=NA)
```

Rode os chunks de código:

```{r}
getGeoCode("Belo Horizonte, Minas Gerais, Brazil")
```
```{r}
DF <- with(DF,data.frame(cidade=cidade, t(sapply(DF$cidade, getGeoCode))))
knitr::kable(DF, format="markdown", digits=4)
```
Plote os pontos

```{r}
box <- make_bbox(lon, lat, data = DF)
map <-
  ggmap(
    get_map(location = box, maptype="toner", source="stamen")
    ) +
  geom_point(data=DF, x=DF$lon, y=DF$lat, color="red")
map
```

```{r}
maptype = c("terrain", "satellite", "roadmap", "hybrid", "toner", "watercolor")
source = c("google", "osm", "stamen", "cloudmade")
```

```{r}
map <-
  ggmap(
    get_map(location = box, maptype="terrain", source="google", color="bw")
    ) +
  geom_point(data=DF, x=DF$lon, y=DF$lat, color="red")
```

```{r}
map
```

Créditos: https://rstudio-pubs-static.s3.amazonaws.com/27602_ac1f676e281d4b0dbd21ceb29017c2ca.html
