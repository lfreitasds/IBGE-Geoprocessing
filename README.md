# Bem-vindo à Análise de Dados dos Municípios e Unidades de Conservação
<img src="img/banner.png">

---
## Sumário

[1 - Business Problem](https://github.com/lfreitas16/Sales-Prediction-Rossmann#1---business-problem-)

* [1.1 - Description](https://github.com/lfreitas16/Sales-Prediction-Rossmann#11---description)
* [1.2 - Data Overview](https://github.com/lfreitas16/Sales-Prediction-Rossmann#12---data-overview)

[2 - Business Assumptions](https://github.com/lfreitas16/Sales-Prediction-Rossmann#2---business-assumptions)

[3 - Solution Strategy](https://github.com/lfreitas16/Sales-Prediction-Rossmann#3---solution-strategy)

* [Step 01 - Data Description](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-01---data-description)
* [Step 02 - Feature Engineering](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-02---feature-engineering)
* [Step 03 - Filtering Variables](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-03---filtering-variables)
* [Step 04 - Exploratory Data Analysis](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-04---exploratory-data-analysis)
* [Step 05 - Data Preparation](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-05---data-preparation)
* [Step 06 - Feature Selection](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-06---feature-selection)
* [Step 07 - Machine Learning Modeling](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-07---machine-learning-modeling)
* [Step 08 - Hyperparameter Fine Tuning](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-08---hyperparameter-fine-tuning)
* [Step 09 - Performance Evaluation](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-09---performance-evaluation)
* [Step 10 - Model Deployment](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-10---model-deployment)
* [Step 11 - Telegram Bot](https://github.com/lfreitas16/Sales-Prediction-Rossmann#step-11---telegram-bot)

[4 - Business Results](https://github.com/lfreitas16/Sales-Prediction-Rossmann#4---business-results)

[5 - Conclusions](https://github.com/lfreitas16/Sales-Prediction-Rossmann#5---conclusions)

[6 - Next Steps to Improve](https://github.com/lfreitas16/Sales-Prediction-Rossmann#6---next-steps-to-improve)

[7 - Technologies](https://github.com/lfreitas16/Sales-Prediction-Rossmann#7---technologies)

[8 - Author](https://github.com/lfreitas16/Sales-Prediction-Rossmann#8---author)

---

## 1 - Descrição do Projeto

Usar dados de geolocalização dos municípios e unidades de conservação do Brasil para obter qual percentual da área dos municípios corresponde à área de conservação.

## 2 - Conjunto de Dados

### 2.1 - Municípios
Malha municipal digital com 5572 geocódigos, sendo: 5568 Municípios,  1 Distrito Federal (Brasília – DF), 1 Distrito Estadual (Fernando de Noronha – PE), 2 Áreas Estaduais Operacionais (Lagoa dos Patos e Lagoa Mirim, ambas atribuídas ao Rio Grande do Sul).

<img src="img/ibge_map_br.png" width="500">

Autor: Instituto Brasileiro de Geografia e Estatistica (IBGE)
Última atualização: 01/03/2021

[Download](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/malhas-territoriais/15774-malhas.html?=&t=downloads)

### 2.2 - Unidades de Conservação
Dados geoespaciais de 334 Unidades de Conservação Federais.

<img src="img/icmbio_map_br.png" width="500">

[Download Mapa Temático](https://www.gov.br/icmbio/pt-br/servicos/geoprocessamento/mapa-tematico-e-dados-geoestatisticos-das-unidades-de-conservacao-federais/copy_of_mapa_oficial_08_2021_150.pdf)

Autor: Instituto Chico Mendes de Conservação da Biodiversidade (ICMBio).
Última atualização: 15/08/2022
[Download](https://www.gov.br/icmbio/pt-br/servicos/geoprocessamento/mapa-tematico-e-dados-geoestatisticos-das-unidades-de-conservacao-federais)

## 3 - Considerações
AAAA

## 4 - Estratégia de Solução

### Passo 01 - Instalar biblioteca Geopandas
O GeoPandas permite operações espaciais em DataFrames com tipos de dados geométricos no Python.

### Passo 02 - Importar bibliotecas
* *pandas*: manipulação de dataframes
* *matplotlib.pyplot*: criação de mapas
* *geopandas*: manipulação de dados geoespaciais 
* *fiona*: leitura e escrita de formatos vetoriais
* *seaborn*: visualização de dados

### Passo 03 - Carregar os dados
Usar Geopandas para criar um GeoDataFrame com os dados geográficos armazenados em formato shapefile.
### Passo 04 - Separar os municípios por região
Para facilitar a análise.
### Passo 05 - Calcular áreas dos municípios e unidades de conservação
Utilizar o atributo *area*, que devolve a área do polígono para cada uma das linhas dos conjuntos de dados.
### Passo 06 - Visualizar os dados
Plotar gráficos para comparar as quantidades de municípios/unidades de conservação e as respectivas áreas em cada região.
### Passo 07 - Plotar mapa do Brasil
Mostrando a divisão dos municípios e as unidades de conservação.
### Passo 08 - Criar GeoDatraFrame de sobreposição
Por meio da função overlay da biblioteca de geopandas, obter os locais onde os conjuntos de dados do IBGE e do iCMBio se sobrepõem.
### Passo 09 - Salvar o GeoDataFrame de Sobreposição
Em formato vetorial GeoJSON para poder carregar os dados sem a necessidade de executar novamente a função overlay cujo processamento é um pouco demorado.
### Passo 10 - Calcular as áreas de sobreposição
Utilizar o atributo *area*, que devolve a área do polígono para cada uma das linhas dos conjuntos de dados.
### Passo 11 - Calcular o percentual de área de sobreposição
### Passo 12 - Salvar relatório final

| Coluna | Descrição | 
| :----- | :----- | 
| CD_MUN | código do município | 
| NM_MUN | nome do município |
| SIGLA | estado do município |
| REGIAO_MUN | região do município |
| AREA_MUN | área do município |
| CNUC | código da unidade de conservação |
| NM_UC | nome da unidade de conservação |
| REGIAO_UC	| região da unidade de conservação |
| AREA_UC | área da unidade de conservação |
| AREA_SOBREP | área de sobreposição |
| PERC_SOBREP | percentual de área de sobreposição |
| PERC_TOTAL | área de sobreposição total do município |

Você pode abrir o relatório aqui: [report_br.csv](https://github.com/lfreitasds/IBGE-Geoprocessing/blob/main/report_br.csv)  

## 5 - Resultados
Analisando todos os municípios:
| Região | Quantidade de Municípios | Percentual de Sobreposição |
| :-----: | :-----: | :-----: |
| Norte | 450 | 16,49% |
| Nordeste | 1792  | 4,80% | 
| Sul | 1193 | 2,75% | 
| Sudeste | 1668 | 2,71% | 
| Centro-Oeste | 467 | 2,36% | 
| **Total:** | **5572** | **9,13%** |

Analisando somente os municípios que fazem intersecção com unidades de conservação:
| Região | Quantidade de Municípios | Percentual de Sobreposição |
| :-----: | :-----: | :-----: |
| Norte | 160 | 22,76% |
| Nordeste | 253 | 19,50% | 
| Sul | 105 | 16,14% | 
| Sudeste | 202 | 16,41% | 
| Centro-Oeste | 61 | 10,21% | 
| **Total:** | **781** | **20,72%** |

## 6 - Conclusões
* AAAA

## 7 - Próximos Passos
No próximo ciclo do CRISP...

## 8 - Tecnologias
[![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white)](https://www.anaconda.com/)
[![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white)](https://www.canva.com/)
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-%23#ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=white)](https://matplotlib.org/)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/python/plotly-express/)

## 9 - Author
Leonardo de Freitas  
Cientista de Dados
[Portfolio](https://lfreitasds.github.io/portfolio/)

---
[Return to the table of contents](https://github.com/lfreitas16/Sales-Prediction-Rossmann#table-of-contents)

---