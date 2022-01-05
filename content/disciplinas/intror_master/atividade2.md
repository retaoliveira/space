---
date: "2021-10-15T00:00:00+01:00"
draft: false
menu:
  intror_master:
    parent: Unidade 2
    weight: 10
title: Atividade 2
toc: true
type: docs
weight: 10
---

A **Unidade 2** é estruturada considerando os seguintes tópicos:

- Estrutura de dados no R; 
- Tipos de dados, importação de base de dados, criação de objeto (vetores, matrizes, data frames), operadores aritméticos, de comparação e lógicos;
- Visualização de dados no R.


Esta atividade deverá ser realizada até dia **26/10**, quando teremos nosso segundo encontro síncrono. São propostas as seguintes atividades:

1. Faça o download do arquivo disponível no [link](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/EeRUAZXugYhOqiO6lRHfbVYBYUZx8HUcj8vN538pmX0t4g?e=8UQAnq)
2. Resolva as questões.
3. Gere um tipo de documento .Rmd de sua preferência. 
4. Envie por email (renataoliveira@gmail.com ou renataoliveira@cefetmg.br) o arquivo .Rmd e o arquivo gerado. 


## A(s) entrega(s) será(ão):
- **Arquivos** referentes à **tarefa 4** desta atividade.

<hr></hr>

# Operações matemáticas e vetores

## Exercícios:

**Questão 1:**

Qual é a classe dos vetores abaixo? Imprima o vetor com _print_ e tente advinhar. Use a função _class_ para descobrir a resposta.

```{r}
v1 <- c(1, 2, TRUE, 4)
v2 <- c("T", "TRUE", "FALSE", "T")
v3 <- c("1", "2", "3", "4")
v4 <- c(1, "4", 4, 1)
v5 <- c(1, 2, "feijao com arroz")
v6 <- c("Beatriz", "Pedro", TRUE)
v7 <- c(T, T, F, T, F, F, 42)
```

Você consegue identificar as regras de combinação de tipos de dados diferentes em um mesmo vetor? Se tiver dúvidas, pergunte.

**Questão 2:**

Veja as cores de veículos comercializados por uma concessionária na semana passada. 

```{r echo=TRUE, message=FALSE, warning=FALSE}
colours <- factor(c("red","blue","red","white",
                    "silver","red","white","silver",
                    "red","red","white","silver","silver"),
                  levels=c("red","blue","white","silver","black"))
```


Se você colocar o código a seguir, o que acontece? Por que? Responda na atividade da semana.

```{r echo=TRUE, message=FALSE, warning=FALSE}
colours[4] <- "orange"
colours
```

Utilize a função `table` para determinar a quantidade de automóveis comercializados de cada cor. Pesquise na internet e pergunte caso tenha dúvidas. 

```{r}
table(colours)

```
```{r}
d11 <- plyr::count(colours)
d12 <- plyr::count(mtcars, vars = "cyl")
d13 <- gmodels::CrossTable(colours)
```


**Questão 3:**

Considere:

```{r echo=TRUE, message=FALSE, warning=FALSE}
car.type <- factor(c("saloon","saloon","hatchback",
    "saloon","convertible","hatchback","convertible",
    "saloon", "hatchback","saloon", "saloon",
    "saloon","hatchback"),
    levels=c("saloon","hatchback","convertible"))
```

Gere a tabela de frequências para os dados `car.type`. 

Experimente: 

```{r echo=TRUE, message=FALSE, warning=FALSE}
table(car.type, colours)
gmodels::CrossTable(car.type, colours)
```

Qual a diferença entre o uso da função `table` com um ou argumentos? 
Qual a diferença entre `table(car.type, colours)` e `table(colours, car.type)`?

**Questão 4:** 

- Crie dois novos vetores. No primeiro, anote (invente) o número de palavras que você escreveu no último trabalho acadêmico ou relatório técnico em cada semana, considerando os últimos três meses. No segundo, anote (chute, novamente) quantos litros de café você tomou em cada semana. 

- Nomeie os elementos dos 2 vetores. 

- Calcule sua produtividade em "palavras por Litro de café". Atribua o resultado a um novo vetor.

```{r}

```

