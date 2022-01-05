---
title: "Introdução ao R"
draft: no
date: '2021-05-15T00:00:00Z'
menu:
  intror_master:
    name: Organização do curso
    weight: 10
lastmod: '2021-10-15T00:00:00Z'
toc: yes
type: docs
weight: 10
---

## Proposta pedagógica

A intenção desta disciplina é fazer com que o aprendizado seja mais dinâmico e ocorra de forma simultânea, fazendo com que o aluno tenha as bases teóricas e teste-as ao mesmo tempo.

A proposta pedagógica para desenvolvimento deste curso fundamenta-se no conceito de `Aprendizagem Baseada em Projetos`. São propostos `projetos incrementais` para apreensão do conhecimento.

## Ementa da disciplina

- Importação de base de dados
- Criação de objeto (vetores, matrizes, data frames)
- Operações com matrizes (transposição, inversão, multiplicação)
- Funções básicas do R (for, if, else, união, intercessão, True, False).

## Objetivos de aprendizagem

Por meio desta disciplina, os alunos desenvolverão competências para:

1. Entender a linguagem básica de programação no R. 
2. Conhecer as funções básicas para manipular bases de dados.

## Planejamento de encontros síncronos

Os encontros síncronos acontecerão nas **terças-feiras**, de **08:00 às 12:00h**. Acontecerão na plataforma `Teams`. Vocês poderão acessar o servidor da disciplina pelo [link](https://teams.microsoft.com/l/team/19%3aMP6yYq2Q8ZbGcsY-Daeh0wNcbWQ0WgNMjxk98MTFJ081%40thread.tacv2/conversations?groupId=b1d6c669-b6bb-4279-a2d4-80d00ed05efd&tenantId=ef9d67f2-bd3f-4e0c-84ba-3ffc81ab1c83).

| **Data**           | **Descrição da Atividade**   
---------------------|---------------------------
| 19/10| Unidade 1: Comunicação por meio do R: ambientação no R, RStudio, Git-Github e Rpubs; Hello R; RMarkdown.|
| 26/10| Unidade 2: Visualização de dados no R; estrutura de dados no R; tipos de dados, importação de base de dados, criação de objeto (vetores, matrizes, data frames), operadores aritméticos, de comparação e lógicos; visualização de informações gerenciais e científicas. |
| 09/11| Unidade 3: Manipulação e transformação de dados no R: funções para manipulação e tratamento de dados. Estatística descritiva e mineração de dados| 
| 16/11| Unidade 3: Manipulação e transformação de dados no R: funções para manipulação e tratamento de dados. Estatística descritiva e mineração de dados|
| 23/11| Unidade 4: Argumentos lógicos; ifelse, which, igual, maior, menor que, join; subconjuntos com argumentos lógicos| 
| **Total de Horas** | 30 horas    |

## Proposta de avaliação da aprendizagem

A aprendizagem na disciplina será avaliada por meio da consolidação de atividades alinhadas com os objetivos de aprendizagem (projetos incrementais) e por meio da elaboração de um projeto transversal aos objetivos (projeto integrador).

| Pontos | Entrega | Atividade                                                                                                                                                                                                                                                    |
|--------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 20 | 19/10 | Lab 1 – Introdução do R e IDE RStudio. RMarkdown. 
| 20 | 26/10 | Lab 2 – Tipos de dados e objetos no R. Visualização de dados – base ggplot2
| 20 | 09/11 | Lab 3 – Importação e introdução ao tratamento de dados no R. Tratamento de dados - dplyr. Junção de múltiplos dataframes
| 20 | 23/11 | Lab 4 – Argumentos lógicos - ifelse, which, igual, maior, menor que, join; subconjuntos com argumentos lógicos
| 5 | 19/10 | Atividade 1 
| 5 | 26/10 | Atividade 2 
| 5 | 09/11 | Atividade 3 
| 5 | 23/11 | Atividade 4 
| TOTAL: |         | 100 pontos

## Requisitos básicos e expectativas iniciais

Os participantes não precisam apresentar conhecimento prévio de computação, pacotes estatísticos ou manejo de conjuntos de dados. Se você é daquelas pessoas que, como eu há muito pouco tempo atrás, arrepia ao ver `códigos` na sua frente e tem certeza que nasceu sem a capacidade desenvolver quaisquer análises que envolvam `linha de comando`, você está no lugar certo! Fique tranquilo pois a proposta é que todos consigam acompanhar a disciplina e diferentes competências e inteligências são muito bem vindas! Vamos desconstruir essa ideia de que analistas, gestores e engenheiros não são formados para usar linguagem computacional.

Não quero que você se torne um desenvolvedor com este curso. Ele tem como proposta a ampliação das possibilidades de análise de sistemas organizacionais e suporte ao processo decisório. O `R` é uma linguagem acessível a todos.

A avaliação priorizará o esforço e a criatividade apresentados em detrimento da finalização das propostas e projetos. Ou seja, para encorajar todos os estudantes, códigos com erros, mas bem elaborados, são um ótimo produto a ser entregue ao longo da disciplina, como forma de encorajar estudantes iniciantes.

## Recursos necessários

Computador com Sistema Operacional à escolha do estudante, conexão à internet, câmera e microfone. Os softwares a serem instalados são:

-   R (Windows) - <https://cran.r-project.org/bin/windows/base/>
-   RStudio (Windows) - <https://rstudio.com/products/rstudio/download/>
-   Git - <https://git-scm.com/downloads>

Os alunos deverão ter uma conta gratuita na plataforma `github.com`. Recomendamos também que se cadastrem no [RPubs](https://rpubs.com/)

A turma virtual do SIGAA será utilizada para postagens de conteúdos e outras comunicações.

## Bibliografia recomendada sobre análise de dados aplicada a processos decisórios

-   FAWCETT, T; PROVOST, F. Data Science Para Negócios: O que você precisa saber sobre mineração de dados e pensamento analítico de dados. Edição: 1ª. Número de Páginas: 408 Editora Alta Books.
-   RAGSDALE, Cliff T. Modelagem de planilha e análise de decisão: uma introdução prática a business analytics. Revisão de João Luiz Becker. São Paulo: Saraiva, c2015. xi, 594 p., il. Inclui referências e índice. ISBN 9788522117741.
-   SHARDA, Ramesh. Business intelligence and analytics: systems for decision support. 10. ed. Boston: Pearson, c2015. xxx, 656 p., il. Inclui referências, glossário e índice. ISBN 9780133050905.
-   NISHISATO, S. Analysis of Categorical Data: Dual Scaling and Its Applications. Toronto: University of Toronto Press, Scholarly Publishing Division, 2018. ISBN 9781487578909. Disponível em: <http://search.ebscohost.com/login.aspx?direct=true&db=nlebk&AN=2027628&lang=pt-br&site=ehost-live>. Acesso em: 22 out. 2020.
- TSAY, Ruey S. Multivariate time series analysis: with R and financial applications. New Jersey: John Wiley & Sons, 2014.
- TROSSET, Michael W. An introduction to statistical inference and its applications with R. Boca Raton: Chapman and Hall/CRC, 2009.
- PARADIS, Emanuel. R for Beginners. Monpellier: Institut des Sciences de l’Evolution, 2005. Disponível em: https://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf. Acesso em: 12 nov. 2019.  
- TEETOR, Paul. R cookbook: Proven recipes for data analysis, statistics, and graphics. Sebastopol: O'Reilly Media, Inc., 2011.
- Zen do R - https://curso-r.github.io/zen-do-r/index.html


## Material adicional

[R Project](https://www.r-project.org/)   
[Reproductible research](https://cran.r-project.org/web/views/ReproducibleResearch.html)

## Comunicação

Toda comunicação individual com a docente deverá acontecer por meio do email institucional do docente, deve conter no campo "assunto" o texto `<R-PPGA>` e deve ser assinada com seu nome completo. Por favor, utilize o email institucional para comunicação com o docente: [renataoliveira@cefetmg.br](mailto:renataoliveira@cefetmg.br)

Se o seu email não contempla alguma questão pessoal/individual, mas sim questionamentos e dúvidas sobre as atividades deste curso, por favor:

1.  Verifique se a sua dúvida já foi respondida em algum post no `Teams`
2.  Se não houver discussões sobre o tópico em questão, faça um novo post no canal `discussão` no `Teams`.

> Compartilhar as dúvidas e responder os questionamentos dos colegas é um excelente meio de aprendizagem.

## Políticas institucionais e da disciplina

O comparecimento aos encontros síncronos é desejável. A participação nesses encontros faz com que os estudantes tenham melhor desempenho. Entretanto, considerando todos os desafios proporcionados pelo ensino remoto, todo o conteúdo do curso será disponibilizado nas plataformas adotadas para condução das atividades. Você poderá participar das atividades remotamente usando o canal `discussão` no `Teams`. 

1.  Resposta a perguntas postadas pelos estudantes no canal `discussão` no `Teams`.
2.  Participação em discussões e trabalhos em grupo na sala de aula.
3.  Identificação de problemas em relação à documentação apresentada.

Os estudantes e professores têm a responsabilidade de manter um ambiente de aprendizagem adequado e motivante. Aqueles que não aderirem a tais padrões de comportamento podem estar sujeitos ao regime disciplinar da instituição. A cortesia profissional e a sensibilidade são especialmente importantes no que diz respeito a indivíduos e discussões que lidam com diferenças de raça, cor, cultura, religião, credo, política, status de veterano, orientação sexual, gênero, identidade e expressão de gênero, idade, deficiência e nacionalidades. As listas de classes são fornecidas ao instrutor com o nome legal do aluno. Terei prazer em honrar seu pedido de dirigir-se a você por um nome alternativo ou pronome de gênero. Por favor, me informe essa preferência no início do semestre para que eu possa fazer as mudanças apropriadas em seus registros.

Não serão tolerados atos de discriminação ou assédio contra ou por qualquer funcionário ou estudante.

Honestidade acadêmica é um princípio fundamental desta disciplina. Desonestidade acadêmica configura-se por: cópias literais de textos ou ideias sem citação de fonte, fabricações e falsificações de qualquer natureza, plágio, mentira, suborno, comportamento ameaçador ou cumplicidade com desonestidade acadêmica em qualquer nível. Os estudantes que forem considerados em violação da política de integridade acadêmica estarão sujeitos tanto a sanções acadêmicas do membro docente quanto a sanções não acadêmicas. Se você tiver alguma dúvida sobre citações adequadas, configuração de plágio, etc., por favor, não hesite em perguntar!
