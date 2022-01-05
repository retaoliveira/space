---
date: "2021-10-15T00:00:00+01:00"
draft: false
menu:
  intror_master:
    parent: Unidade 2
    weight: 12
title: Lab 2.2 - `ggplot` e `dplyr`
toc: true
type: docs
weight: 12
---

A **Unidade 2** é estruturada considerando os seguintes tópicos:
- Estrutura de dados no R; 
- Tipos de dados, importação de base de dados, criação de objeto (vetores, matrizes, data frames), operadores aritméticos, de comparação e lógicos;
- Visualização de dados no R.

## **Diretrizes gerais**

1. Baixe o arquivo .Rmd e abra no RStudio. 

[Arquivo](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/EdOhUzJEDXhFsbtqeXPtQk4BG0o3aTwZCnp8ZdotdiNaxg?e=gHdRz4)

2. Siga as diretrizes da atividade. 

3. Rode o arquivo .Rmd por meio do ícone `knitr` 

4. Salve o .Rmd e **submeta-o por meio da tarefa no Sigaa**. 

<hr></hr>

## **Atividade**

Nessa mini-análise trabalharemos com os dados usados no projeto publicada por Five Thirty Eight ["The Dollar-And-Cents Case Against Hollywood's Exclusion of Women"](https://fivethirtyeight.com/features/the-dollar-and-cents-case-against-hollywoods-exclusion-of-women/).

Sua tarefa é preencher os espaços em branco assinalados por `___`.

### Dados e pacotes

Começamos com o carregamento dos pacotes que vamos utilizar. Lembrem-se que, caso haja algum problema com o carregamento dos pacotes, tente instalá-los novamente. 

```{r load-packages, message=FALSE}
library(fivethirtyeight)
library(tidyverse)
```

O conjunto de dados contém informações sobre `r nrow(bechdel)` filmes lançados entre `r min(bechdel$year)` e `r max(bechdel$year)`.

Entretanto, vamos focar nossa análise em filmes lançados entre 1990 e 2013.

```{r}
bechdel90_13 <- bechdel %>% 
  filter(between(year, 1990, 2013))
```

Existem '___' filmes. (insira a quantidade de filmes)

---

As variáveis financeiras em que vamos nos concentrar são as seguintes:

- `budget_2013`: Orçamento em dólares de 2013 ajustados à inflação.
- `domgross_2013`: Dólares internos brutos (EUA) em 2013, dólares ajustados pela inflação.
- `intgross_2013`: Total internacional (i.e., mundial) bruto em 2013 dólares corrigidos da inflação.

E também utilizaremos as variáveis `binary` e `clean_test` para **grouping**.

---

### Análise

Vamos ver como o orçamento médio e o bruto variam conforme o filme caso tenha passado no teste de Bechdel, que é armazenado na variável "binary".

```{r message = FALSE}
bechdel90_13 %>%
  group_by(binary) %>%
  summarise(med_budget = median(budget_2013),
            med_domgross = median(domgross_2013, na.rm = TRUE),
            med_intgross = median(intgross_2013, na.rm = TRUE))
```

Em seguida, vamos ver como o orçamento meidano e o bruto variam por um indicador mais detalhado do resultado do teste de Bechdel.

Essa informação é armazenada na variável 'clean_test', que assume os seguintes valores:

- `ok` = passa no teste
- `dubious`.
- `men` = as mulheres só falam de homens
- `notalk` = as mulheres não falam umas com as outras
- `nowomen` = menos de duas mulheres

```{r message = FALSE}
bechdel90_13 %>%
  group_by(clean_test) %>%
  summarise(med_budget = median(budget_2013),
            med_domgross = median(domgross_2013, na.rm = TRUE),
            med_intgross = median(intgross_2013, na.rm = TRUE))
```

A fim de avaliar como o retorno do investimento varia entre os filmes que passam e fracassam no **teste de Bechdel**, vamos primeiro criar uma nova variável chamada `roi` como uma razão do orçamento bruto.

```{r}
bechdel90_13 <- bechdel90_13 %>%
  mutate(roi = (intgross_2013 + domgross_2013) / budget_2013)
```

Vamos ver quais filmes têm o maior retorno sobre o investimento.

```{r}
bechdel90_13 %>%
  arrange(desc(roi)) %>% 
  select(title, roi, year)
```

Abaixo está uma visualização do retorno do investimento por resultado de teste, porém é difícil ver as distribuições devido a algumas observações extremas.

```{r warning = FALSE}
ggplot(data = bechdel90_13, 
       mapping = aes(x = clean_test, y = roi, color = binary)) +
  geom_boxplot() +
  labs(title = "Retorno do investimento vs. Resultados do teste Bechdel",
       x = "Resultado detalhado de Bechdel",
       y = "___",
       color = "Resultado binário de Bechdel")
```

Quais são os filmes com retorno de investimento *muito altos*?

```{r}
bechdel90_13 %>%
  filter(roi > 400) %>%
  select(title, budget_2013, domgross_2013, year)
```

Veja como é a relação entre os filmes com menor retorno e o resultado detalhado do teste Bechedel. 

A ampliação dos filmes com `roi < ___` proporciona uma melhor visão de como os medianos através das categorias se comparam:

```{r warning = FALSE}
ggplot(data = bechdel90_13, mapping = aes(x = clean_test, y = roi, color = binary)) +
  geom_boxplot() +
  labs(title = "Retorno do investimento vs. Resultado do teste de Bechdel",
       subtitle = "___", # Something about zooming in to a certain level
       x = "Resultado detalhado de Bechdel",
       y = "Retorno do investimento",
       color = "Resultado binário de Bechdel") +
  coord_cartesian(ylim = c(0, 15))
```
