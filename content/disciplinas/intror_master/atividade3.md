---
date: "2021-10-15T00:00:00+01:00"
draft: false
menu:
  intror_master:
    parent: Unidade 3
    weight: 11
title: Atividade 3
toc: true
type: docs
weight: 11
---

## A **Unidade 3** é estruturada considerando os seguintes tópicos:
- Manipulação e transformação de dados no R: funções para manipulação e tratamento de dados. 
- Estatística descritiva e mineração de dados


## Esta atividade deverá ser realizada até dia **09/11**, quando teremos nosso segundo encontro síncrono. São propostas as seguintes atividades:

1. Faça o download do arquivo disponível no [link](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/EX0uowQRoZZMlQnHVPmDy5sBtJt3ZVjBLNcDuNvS1qZU6Q?e=3z9FTB)
2. Resolva as questões.
3. Gere um tipo de documento .Rmd de sua preferência. 
4. Envie por email (renataoliveira@gmail.com ou renataoliveira@cefetmg.br) o arquivo .Rmd e o arquivo gerado. 


## A(s) entrega(s) será(ão):
- **Arquivos** referentes à **tarefa 4** desta atividade.

<hr></hr>

A poluição por plástico é um problema importante e crescente, afetando negativamente a saúde dos oceanos e da vida selvagem.
[Our World in Data](https://ourworldindata.org/plastic-pollution) tem muitos  dados em vários níveis, em escala global, por país e ao longo do tempo.

Para este laboratório, nos concentramos nos dados de 2010.

Além disso, a National Geographic realizou um concurso de comunicação de visualização de dados sobre resíduos plásticos, como visto [aqui](https://www.nationalgeographic.org/funding-opportunities/innovation-challenges/plastic/dataviz/).

Os dados estão no [Link](https://cefetmgbr-my.sharepoint.com/:x:/g/personal/renataoliveira_cefetmg_br/ESK2oL3BBs1FgbPSB8LbpbEBQVLJX5MmsHnTKqFkFJbYPA?e=fbprgc)

# Objetivos de aprendizagem

- Visualizar dados numéricos e categóricos e interpretar visualizações
- Recriação de visualizações


## Pacotes

Usaremos o pacote **tidyverse*** para esta análise.
Execute o seguinte código no Console para carregar este pacote.

```{r load-packages, message=FALSE, eval=TRUE}
library(tidyverse)
```

## Dados

O conjunto de dados para esta tarefa pode ser encontrado no link a seguir, acessado por meio do comando:

```{r load-data, message=FALSE, eval=TRUE}

#url_file <- "atalho no seu computador/plastic-waste.csv"

#plastic_waste <- read_csv(url_file)

#library(readr)
plastic_waste <- read_csv("D:/OneDrive - cefetmg.br/01_disciplinas/ERE/2020_2/R_adm/00_aulas/class07_dados_adm/data/plastic-waste.csv")

View(plastic_waste)
```

As descrições das variáveis são as seguintes:

-   `code`: código do país
-   `entity`: Nome do país
-   `continent`: Nome do continente
-   `year`: Ano
-   `gdp_per_cap`: PIB per capita internacional 2011 \$, taxa
-   `plastic_waste_per_cap`: Quantidade de resíduos plásticos per capita em kg/dia
-   `mismanaged_plastic_waste_per_cap`: Quantidade de resíduos plásticos mal administrados per capita em kg/dia
-   `mismanaged_plastic_waste`: Toneladas de resíduos plásticos mal administrados
-   `coastal_pop`: Número de indivíduos que vivem no litoral/na costa
-   `total_pop`: População total de acordo com Gapminder

# Warm up

- Recorde que o RStudio está dividido em quatro painéis. Sem olhar, você pode nomeá-las todas e descrever brevemente seu propósito?

- Verifique se o conjunto de dados foi carregado para o Ambiente. Quantas observações há no conjunto de dados? Ao clicar no conjunto de dados no Ambiente, você poderá inspecioná-lo com mais cuidado. Alternativamente, você pode digitar `View(plastic_waste)` no Console para fazer isso.

- Dê uma rápida olhada nos dados e observe que há células que levam o valor `NA` - o que isso significa?

# Exercícios

Vamos começar dando uma olhada na distribuição de resíduos plásticos per capita em 2010.

```{r plastic_waste_per_cap-hist, eval=TRUE}
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram(binwidth = 0.2)
```

Um país se destaca como uma observação incomum no topo da distribuição.

Uma maneira de identificar este país é filtrar os dados para países onde os resíduos plásticos per capita são maiores que 3,5 kg/pessoa.

```{r plastic_waste_per_cap-max, eval=TRUE}
plastic_waste %>%
  filter(plastic_waste_per_cap > 3.5)
```

Você esperava este resultado?

Você poderia considerar fazer alguma pesquisa sobre Trinidad e Tobago para ver por que os resíduos plásticos per capita são tão altos lá, ou se isto é um erro de dados.

1.  Faça um histograma para a distribuição de resíduos plásticos per capita desagregados (facet) por continente. O que você pode dizer sobre como os continentes se comparam uns aos outros em termos de seus resíduos plásticos per capita?

```{r}
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram() +
  facet_wrap(~ continent)

```

Outra forma de visualizar os dados numéricos é utilizando gráficos de densidade.

```{r plastic_waste_per_cap-dens}
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_density()
```

E comparar as distribuições entre continentes por curvas de densidade de coloração por continente.

```{r plastic_waste_per_cap-dens-color}
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, 
                     color = continent)) +
  geom_density()
```

O gráfico resultante pode ser um pouco difícil de ler, então vamos também preencher as curvas com cores.

```{r plastic_waste_per_cap-dens-color-fill}
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, 
                     color = continent, 
                     fill = continent)) +
  geom_density()
```

A sobreposição de cores torna difícil dizer o que está acontecendo com as distribuições nos continentes plotados devido a continentes plotados sobre eles.

Podemos mudar o nível de transparência da cor de preenchimento para ajudar nisso.

O argumento `alpha` recebe valores entre 0 e 1: 0 é completamente transparente e 1 é completamente opaco.
Não há como dizer qual valor funcionará melhor, então você só precisa tentar alguns valores.

```{r plastic_waste_per_cap-dens-color-fill-alpha}
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, 
                     color = continent, 
                     fill = continent)) +
  geom_density(alpha = 0.5)
```

Isto ainda não parece ótimo...

1.  Recriar as parcelas de densidade acima usando um nível `alpha` diferente (inferior) que funcione melhor para exibir as curvas de densidade para todos os continentes.

2.  Descreva porque definimos a "cor" e "preenchimento" das curvas através do mapeamento estético do gráfico, mas definimos o nível "alpha" como uma característica da geometria de plotagem.

E ainda outra maneira de visualizar esta relação é utilizando gráficos boxplot.

```{r plastic_waste_per_cap-box}
ggplot(data = plastic_waste, 
       mapping = aes(x = continent, 
                     y = plastic_waste_per_cap)) +
  geom_boxplot()
```

1.  Converta os boxplot da tarefa anterior para [plot de violino](http://ggplot2.tidyverse.org/reference/geom_violin.html). O que os gráficos de violino revelam que os boxplot não revelam? Quais características são aparentes nas parcelas de box mas não nas parcelas de violino?

```{r}
ggplot(data = plastic_waste, 
       mapping = aes(x = continent, 
                     y = plastic_waste_per_cap)) +
  geom_violin()
```

1.  Visualizar a relação entre os resíduos plásticos per capita e os resíduos plásticos mal administrados per capita usando um gráfico de dispersão. Descrever a relação.

2.  Colorir os pontos no gráfico de dispersão por continente.
    Parece haver alguma distinção clara entre continentes com relação a como os resíduos plásticos per capita e os resíduos plásticos mal administrados per capita estão associados?

3.  Visualize a relação entre os resíduos plásticos per capita e a população total, assim como os resíduos plásticos per capita e a população costeira.
    Você precisará fazer duas parcelas separadas.
    Algum destes pares de variáveis parece estar associado de forma mais linear?

```{r}

plastic_waste %>% 
  ggplot(aes(x = mismanaged_plastic_waste_per_cap, y = plastic_waste_per_cap, color = continent)) + 
    geom_point() +
    scale_color_viridis_d() +
    labs(x = "Resíduos plásticos mal administrados per capita", 
         y = "Resíduos plásticos per capita", 
         color = "Continente",
         title = "Resíduos plásticos per capita e os resíduos plásticos mal administrados per capita",
         subtitle = "por continente") +
    theme_minimal()

plastic_waste %>% 
  ggplot(aes(x = coastal_pop, y = plastic_waste_per_cap, color = continent)) + 
    geom_point() +
    scale_color_viridis_d() +
    labs(x = "Resíduos plásticos mal administrados per capita", 
         y = "Resíduos plásticos per capita", 
         color = "Continente",
         title = "Resíduos plásticos per capita e os resíduos plásticos mal administrados per capita",
         subtitle = "por continente") +
    theme_minimal()

plastic_waste %>% 
  ggplot(aes(x = total_pop, y = plastic_waste_per_cap, color = continent)) + 
    geom_point() +
    scale_color_viridis_d() +
    labs(x = "Resíduos plásticos mal administrados per capita", 
         y = "Resíduos plásticos per capita", 
         color = "Continente",
         title = "Resíduos plásticos per capita e os resíduos plásticos mal administrados per capita",
         subtitle = "por continente") +
    theme_minimal()


```

1.  Recrie o seguinte gráfico e interprete o que você vê no contexto dos dados.

```{r echo=FALSE, message=FALSE, eval=TRUE, warning=FALSE}
plastic_waste %>% 
  mutate(coastal_pop_prop = coastal_pop / total_pop) %>%
  filter(plastic_waste_per_cap < 3) %>%
  ggplot(aes(x = coastal_pop_prop, y = plastic_waste_per_cap, color = continent)) + 
    geom_point() +
    geom_smooth(color = "black") +
    scale_color_viridis_d() +
    labs(x = "Coastal population proportion (Coastal / total population)", 
         y = "Plastic waste per capita ", 
         color = "Continent",
         title = "Plastic waste vs. coastal population proportion",
         subtitle = "by continent") +
    theme_minimal()
```
