---
title: "Eleições 2022 - Segundo Turno - Análise de dados"
date: 2023-02-24T11:38:52+01:00
draft: true
authors: [Bruno Geronimo]
summary: "Vamos analisar os dados das urnas nas eleições 2022."
---

Pouco depois das eleições, eu escrevi uma [thread][tweet] no Twitter analisando os dados fornecidos pelo TSE sobre
as eleições presidenciais de 2022. Decidi transformar o que eu encontrei na minha análise em um post.

O TSE possui uma plataforma chamada [Dados Abertos][dados_abertos]. Nela, é possível baixar CSVs contendo dados de
todas as eleições que ocorreram no Brasil desde [1933](https://dadosabertos.tse.jus.br/dataset/?_tags_limit=0&tags=Ano+1933).

Para analisar os dados das últimas eleições, também faremos algumas comparações com dados de 2010, 2014, 2018 e 2022.

## Primeiros passos

Para trabalhar com os dados do TSE, eu optei por importar todos os CSVs em um banco de dados MySQL. A ideia era de facilitar
o trabalho de pesquisar nos dados. Como o CSV possui muitas linhas, um banco de dados facilitaria o trabalho na hora de
filtrar pelas informações que explorarei neste artigo.

Como eu peguei dados de muitas eleições, criei uma tabela para cada um, diminuindo assim o tempo para executar os comandos
no banco de dados.

Feito isso, eu decidi verificar se os dados contidos nos CSVs batem com os valores informados pela apuração dos votos.
Para isso, eu pesquisei na internet pelos números da época das eleições e comparei os divulgados pela mídia com as totalizações
dos CSVs.

Caso você siga os mesmos nomes utilizados pelo TSE e faça o processo descrito acima, eu utilizei a seguite query
para verificar os dados:

```sql
select ANO_ELEICAO, NR_VOTAVEL, sum(qt_votos) as somatoria
from votacao_secao_<ano>
where NR_TURNO = 2
  and NR_VOTAVEL in (<número dos partidos do segundo turno>)
group by ANO_ELEICAO, nr_votavel
order by somatoria desc;
```

### 2010 - Dilma vs Serra (2º Turno)
Fonte: https://g1.globo.com/especiais/eleicoes-2010/noticia/2010/11/tse-conclui-apuracao-dos-votos-do-segundo-turno.html

Votos em Dilma: 55.752.529 (56,05%)
Votos em José Serra: 43.711.388 (43,95%)

Valores do banco de dados:

| ANO_ELEICAO | NR_VOTAVEL | somatoria  |
|-------------|------------|------------|
| 2010        | 13         | 55.752.529 |
| 2010        | 45         | 43711388   |

### 2014 - Dilma vs Aécio (2º Turno)

Fonte: https://g1.globo.com/politica/eleicoes/2014/apuracao-votos-presidente.html

Votos em Dilma: 54.501.118 (51,64%)
Votos em Aécio: 51.041.155 (48,36%)

Valores do banco de dados:

| ANO_ELEICAO | NR_VOTAVEL | somatoria  |
|-------------|------------|------------|
| 2014        | 13         | 54.501.118 |
| 2014        | 45         | 51.041.155 |

### 2018 - Bolsonaro vs Haddad (2º Turno)

Fonte: https://g1.globo.com/politica/eleicoes/2018/apuracao/presidente.ghtml

Votos em Bolsonaro: 57.797.847 (55,13%)
Votos em Haddad: 47.040.906 (44,87%)

Valores do banco de dados:

| ANO_ELEICAO | NR_VOTAVEL | somatoria  |
|-------------|------------|------------|
| 2018        | 17         | 57.797.847 |
| 2018        | 13         | 47.040.906 |

### 2022 - Lula vs Bolsonaro (2º Turno)

Fonte: https://www.tse.jus.br/comunicacao/noticias/2022/Outubro/100-das-secoes-totalizadas-confira-como-ficou-o-quadro-eleitoral-apos-o-2o-turno

Votos em Lula: 60.345.999 (50,90%)
Votos em Bolsonaro: 58.206.354 (49,10%)

Valores do banco de dados:

| ANO_ELEICAO | NR_VOTAVEL | somatoria  |
|-------------|------------|------------|
| 2022        | 13         | 60.345.999 |
| 2022        | 22         | 58.206.354 |

Como vimos acima, todos os CSVs conferem com os dados de apuração das urnas.





[tweet]: <https://twitter.com/BrunoGeronimo/status/1589220721280323588>
[dados_abertos]: <https://dadosabertos.tse.jus.br/>
[apuracao_2010]: <https://g1.globo.com/especiais/eleicoes-2010/noticia/2010/11/tse-conclui-apuracao-dos-votos-do-segundo-turno.html>

