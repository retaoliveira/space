---
date: "2021-12-05T00:00:00+01:00"
draft: false
menu:
  sdss:
    parent: Unidade 2
    weight: 10
title: Atividade 2.1
toc: false
type: docs
weight: 10
---

## A **Unidade 6** é estruturada considerando os seguintes tópicos:

- Dados espaciais e geocodificação;    
- Estrutura de dados espaciais;   
- Como transformar dados não espaciais em espaciais


## Esta atividade deverá ser realizada até dia **06/01**. São propostas as seguintes atividades:

### 1. Chame os pacotes:

```{r}
library(sf)      # vector data package
library(dplyr)   # tidyverse package for data frame manipulation
library(spData)  # spatial data package
```
Os conjuntos de dados vetoriais geográficos são estruturados no R graças à classe `sf`, que estende o data.frame da base R. Como os data.frames, os objetos `sf` têm uma coluna por variável (como 'nome') e uma linha por observação ou característica (por exemplo, por estação de ônibus). Os objetos `sf` diferem dos data.frame básicos porque têm uma coluna geométrica de classe `sfc` que pode conter uma gama de entidades geográficas (ponto único e 'multi', linha e características de polígono) por linha. 

### 2. Siga os comandos a seguir para explorar e manipular dados geográficos com o pacote `sf`:

`world` é um `sf data frame` contendo colunas espaciais e de atributos, cujos nomes são retornados pela função `names()`(a última coluna deste exemplo contém as informações geográficas).

```{r}
class(world)
names(world)
```

Veja o que acontece quando você roda o código a seguir:

```{r}
world_agg1 = world %>%
  group_by(continent) %>%
  summarize(pop = sum(pop, na.rm = TRUE))
```
Copie o código abaixo e rode-o no seu `.Rmd`:

```{r}
world_agg2  = world %>% 
  group_by(continent) %>%
  summarize(pop = sum(pop, na.rm = TRUE), `area (sqkm)` = sum(area_km2), n = n())
```

O que quer dizer a representação gerada por você?

### 3. Junção de atributos vetoriais

```{r}
world_coffee = left_join(world, coffee_data)
class(world_coffee)
plot(world_coffee["coffee_production_2017"])

```

E agora? O que aconteceu? 

O que mudou quando você rodou o código a seguir? 

```{r}
coffee_renamed = rename(coffee_data, nm = name_long)
world_coffee2 = left_join(world, coffee_renamed, by = c(name_long = "nm"))
plot(world_coffee2["coffee_production_2017"])
```

### 4. Realize as atividades a seguir e responda as questões: 

a. Crie um documento `.Rmd` para que você armazene o código gerado. 
b. Carregue os dados e os pacotes

```{r}
library(sf)
library(dplyr)
library(terra)
library(spData)
data(us_states)
data(us_states_df)
```

c. Crie um novo objeto chamado `us_states_name` que contenha apenas a coluna `NAME` do objeto `us_states` usando a sintaxe do tidyverse (select()). Qual é a classe do novo objeto e o que o torna geográfico?

d. Selecione colunas do objeto `us_states` que contenham dados da população e crie um novo objeto.

e. Encontre e plot (salve a figura) todos os estados com as seguintes características:

   - Pertencem à região Centro-Oeste.   
   - Pertence à região Oeste, têm uma área abaixo de 250.000 km2 e em 2015 uma população maior que 5.000.000 de residentes (dica: você pode precisar usar as unidades funcionais::set_units() ou as.numeric()).   
   - Pertencente à região Sul, tinha uma área maior que 150.000 km2 ou uma população total em 2015 maior que 7.000.000 de residentes.

f. Qual era a população total em 2015 no conjunto de dados us_states? Qual era a população total, mínima e máxima em 2015?

g. Quantos estados existem em cada região?

h. Qual era a população total mínima e máxima em 2015 em cada região? Qual era a população total em 2015 em cada região?

i. Adicione variáveis de `us_states_df` aos `us_states`, e crie um novo objeto chamado `us_states_stats`. Qual função foi utilizada e por quê? Qual variável é a chave em ambos os conjuntos de dados? Qual é a classe do novo objeto?

j. Qual era a densidade populacional em 2015 em cada estado? Qual foi a densidade de população em 2010 em cada estado?

k. Quanto a densidade populacional mudou entre 2010 e 2015 em cada estado? Calcule a mudança nas porcentagens e mapeie-as.

**VOCÊ ESTÁ MANIPULANDO DADOS ESPACIAIS. MAS AINDA PRECISAMOS EVOLUIR PARA A ANÁLISE ESPACIAL DE DADOS, OK?**

Créditos: Lovelace - Geocomputing (https://geocompr.robinlovelace.net/attr.html#exercises-1). Best book ever! 
