---
date: "2021-10-15T00:00:00+01:00"
draft: false
menu:
  intror_master:
    parent: Unidade 1
    weight: 10
title: Lab 1
toc: false
type: docs
weight: 10
---

## A **Unidade 1** é estruturada considerando os seguintes tópicos:
- Instalação do R e do RStudio
- Como instalar o Git
- Criando uma conta no Github
- Instalar e carregar pacotes no R
- Instalar pacotes no R a partir do Github
- E aí, R? Entendendo o ambiente de trabalho
- Primeiros documentos no R - RMarkdown

## Diretrizes gerais:

1. Baixe o arquivo .Rmd e abra no RStudio. 

[Arquivo](https://cefetmgbr-my.sharepoint.com/:u:/g/personal/renataoliveira_cefetmg_br/EdTjtwRl5F5DjFDlgrOB6BgB4fqdODik9Jkp0cA_sB696Q?e=jdqlwW)

2. Instale os pacotes: 
  - `"tidyverse"`
  - `"tinytex"`
  - `"knitr"`
  - `"flexdashboard"`
  - `"xaringan"`
  - `"xaringanthemer"`
  
3. Chame as bibliotecas dos pacotes instalados
  - `library("tidyverse")`
  - `library("tinytex")`
  - `library("knitr")`
  - `library("flexdashboard")`
  - `library("xaringan")`
  - `library("xaringanthemer")`

4. Corrija os problemas de códigos nos respectivos chunks. 

5. Rode o arquivo .Rmd por meio do ícone `knitr` 

6. Salve o .Rmd e **submeta-o por meio da tarefa no Sigaa**. 

> Dica: As barras que delimitam o endereçamento do arquivo no seu computador, quando exibidas no explorer do Windows, são invertidas (\). O R trabalha com barras normais (/) para endereçamento. 

## Preparação para o exercício:

Carregue o *data frame* *mtcars*

```{r}
data(mtcars)
```

## Encontre o erro em todos os códigos abaixo, corrija-os e rode o script:

Q1)

```{r}
Head(mtcars)
```

Q2)

```{r}
str(Mtcars)
```

Q3)

```{r}
dim[mtcars]
```

Q4)

```{r}
nomes(mtcars)
```

Q5)

```{r}
head(mtcars, x = 10)
```

Q6)

```{r}
v1 <- ("pato", "cachorro", "minhoca", "lagarto")
```

Q7)

```{r}
v2 <- c("1", "2", "3", "4")
v1 + 42
```

Q8)

```{r}
v1 <- c("pato", "cachorro", "minhoca", "lagarto"
```

Q9)

```{r}
v3 <- c(33 31 40 25 27 40)
```

Q10)

```{r}
v1 <- c(pato, cachorro, minhoca, lagarto)
```

Q11)

```{r}
v1 <- c("pato" "cachorro" "minhoca" "lagarto")
```

Q12)

```{r}
v3 <- C(33, 31, 40, 25, 27, 40)
```

Q13)

```{r}
v1 <- c("pato", "cachorro"", "minhoca", "lagarto")
v3 <- c(33, 31, 40, 25, 27, 40)
myData <- data.frame(v1, v3)
```

Q14)

```{r}
v1 <- c("pato", "cachorro"", "minhoca", "lagarto")
v4 <- c(33, 31, 40, 25)
myData <- data.frame(v1 = animal, v4 = idade)
```

Q15)

```{r}
ls
```

Q16)

```{r}
v1 <- c("pato", "cachorro", "minhoca", "lagarto")
sum(v1)
```
