---
date: "2021-10-15T00:00:00+01:00"
draft: false
menu:
  intror_master:
    parent: Unidade 2
    weight: 11
title: Lab 2.1 - `ggplot`
toc: true
type: docs
weight: 11
---

A **Unidade 2** é estruturada considerando os seguintes tópicos:
- Estrutura de dados no R; 
- Tipos de dados, importação de base de dados, criação de objeto (vetores, matrizes, data frames), operadores aritméticos, de comparação e lógicos;
- Visualização de dados no R.

## **Diretrizes gerais**

1. Baixe o arquivo .Rmd e abra no RStudio. 

[Arquivo](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/EQRGYbjqPK9PpLiRI6M2SBUBsfh__B4NfDOM5EvLeYG_wg?e=z7pDKM)

2. Siga as diretrizes da atividade. 

3. Rode o arquivo .Rmd por meio do ícone `knitr` 

4. Salve o .Rmd e **submeta-o por meio da tarefa no Sigaa**. 

<hr></hr>

## **Atividade**

1. Dê uma olhada no dataframe Starwars.

```{r glimpse-starwars}
glimpse(starwars)
```

2. Modifique o seguinte gráfico para que a cor de todos os pontos seja ROSA.

```{r scatterplot}
ggplot(starwars, 
       aes(x = height, y = mass, color = gender, size = birth_year)) +
  geom_point(color = "pink")
```

3. Adicione texto no título, eixos x e y e tamanho dos pontos. Remova o comentário para ver o efeito.

```{r scatterplot-labels}
ggplot(starwars, 
       aes(x = height, y = mass, color = as.factor(gender), size = birth_year)) +
  geom_point() +
  labs(
    title = "TEste",
    x = "Adoro", 
    y = "WOW",
    size = "Idade"
    )
```

4. Escolha uma única variável categórica do conjunto de dados e faça um gráfico de barras de sua distribuição.

(Um pouco de código inicial é fornecido abaixo, e o chunk é definido para não ser rodado com `eval = FALSE` porque o código atual ali não é válido e, portanto, o documento não permitia o `knit`. Uma vez substituído o código por um código válido, defina a opção "eval = TRUE", ou remova a opção "eval" por completo, uma vez que está definida como "TRUE" por padrão).

```{r barplot, eval = FALSE}
ggplot(starwars, aes(___)) +
  geom___
```

5. Escolha uma única variável numérica e faça um histograma dela.

(Desta vez nenhum código inicial é fornecido, você está por sua conta!)

```{r histogram}

```

6. Escolha uma variável numérica e uma variável categórica e faça uma visualização (você escolhe o tipo!) para visualizar a relação entre as duas variáveis. Junto com seu código e sua saída, forneça uma interpretação da visualização.

```{r num-cat}

```

7. Escolha duas variáveis categóricas e faça uma visualização para entender visualmente a relação entre as duas variáveis. Junto com seu código e saída, forneça uma interpretação da visualização.

```{r cat-cat}

```

8. Escolha duas variáveis numéricas e duas variáveis categóricas e faça uma visualização que incorpore todas elas e forneça uma interpretação com sua resposta.

```{r multi}

```
