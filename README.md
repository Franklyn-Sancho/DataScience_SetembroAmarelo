<h1 align="center"> Analisando a taxa de suicídio do mundo com DataScience<h1>

<h5 align="center">Não tem sido fácil analisar esses dados, não só pela parte técnica, mas principalmente pelo assunto abordado. Falar sobre suícidio não é simples, mas precisamos. A cada resultado analisado, levanto da minha cadeira e tiro alguns minutos para respirar e refletir sobre o mundo que estamos construíndo.</h5>

### 1 - Ferramentas usadas nesta análise**
* Eu fiz pelo Google Colab, por uma questão de simplicidade. Não precisa instalar absolutamente nada. 
* Mas caso você queeira trabalhar diretamente no pc. Lá vamos: 
* Python
* Pandas
* Matplotlib
* seaborn
* numpy
* Anaconda e Jupyter também seria uma ótima opção. 

### 2 - Importanto as ferramentas e preparando o ambiente inicial**
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

NossosDados = pd.read_csv('https://raw.githubusercontent.com/carlosfab/data_science/master/datasets/suicide_rates.csv')
```
Primeiro importamos as nossas bibliotecas de análise: Pandas, matplotlib, numpy, seaborn; depois damos um nome para o nosso Dataset (o que desejar. Eu, por exemplo, chamei de "NossosDados"). Invocamos o Pandas, modo leitura, o tipo de arquivo (CSV) e o link do CSV. A fonte Dataset é o banco mundial e a organização das nações unidas. Quero reforçar que muito além de analisar gráficos, números e tabelas, estamos aqui para compreender os resultados. Como cientistas de dados, entendemos o problema e encontramos soluções

## 3 - Vamos iniciar a jornada**

**3.1 - Entendo as variáveis**
* country: 101 países no total
* year: Entre 1985 até 2016
* sex: Masculino e Feminino (baseado no Dataset)
* age: 5-14 anos | 15-24 anos | 25-34 anos | 35-54 anos | 55-74 anos | 75+ anos
* suicides_no: Numero total de suícidio
* population: população
* suicides/100k pop: Suícidio por 100 mil habidades
* country_year: identificador contendo country + year
* HDI for year: IDH para o ano
* gdp_for_year: PIB para o ano
* gdp_per_capita: PIB per capita 

**3.2 - Enxengando o nosso Dataset**

```python
print(NossosDados.head())
```
Será chamado os 5 primeiros registros do nosso dataset

id   |country  |   year |  ... | gdp_per_capita ($) | generation    |
-----|---------|--------|------|--------------------|---------------|
0    | Albania |  1987  |  ... |          796       |Generation X   |
1    | Albania |  1987  |  ... |          796       |   Silent      |
2    | Albania |  1987  |  ... |          796       |Generation X   |
3    | Albania |  1987  |  ... |          796       |G.I. Generation|
4    | Albania |  1987  |  ... |          796       |   Boomers|






**3.3 - Analisando as taxas entre 1985 a 2016**<br>

Antes de prosseguir, vamos criar um outro DataSet apenas com os dados do Brasil. Isso será bem interessante, já que poderemos fazer comparações entre os números totais no mundo e do Brasil. Lembrando que pelas informações que temos em mãos, podemos obter diversos tipos de informações. Sem mais delongas, vamos prosseguir aqui com as nossas funções. 

```python
dados_brasil = NossosDados[NossosDados.country == "Brazil"].copy() 
# Aqui criamos um Dataset apenas com os valores relacionados ao Brasil
```
Agora que temos os dois datasets em mãos, podemos continuar. Para começar, vamos analisar as taxas mundiais entre 1985 até 2016. Para facilitar a nossa visualização, vamos plotar o nosso lindo gráfico em linha. Como pretendemos comparar com as taxas brasileiras, podemos deixar na função e deṕois só chamar

```python
anos = dados_brasil.year.unique()
suicides_world_mean = dados.groupby('year')['suicides/100k pop'].mean()

ax = sns.lineplot(x=anos, y = suicides_world_mean, label='mundo')
```


<img src="https://github.com/Franklyn-Sancho/DataScience_SetembroAmarelo/blob/main/LineYellow.jpg">
O pico foi em 1995 (Vamos analisar as possíveis causas). 

**3.4 - Comparando a taxa brasileira e mundial temos**
```python
anos = dados_brasil.year.unique()
suicides_brasil_mean = dados_brasil.groupby('year')['suicides/100k pop'].mean()
suicides_world_mean = dados.groupby('year')['suicides/100k pop'].mean()

ax = sns.lineplot(x=anos, y = suicides_world_mean, label='mundo')
ax = sns.lineplot(x=anos, y = suicides_brasil_mean, label = 'brasil')
```

<img src="https://github.com/Franklyn-Sancho/DataScience_SetembroAmarelo/blob/main/MundoBrasil.jpg">

Comparando os resultados, enquanto a taxa mundial tem caído após o pico em 1995, no Brasil, a taxa só começa a cair em 1997 mais ou menos. Logo após os anos 2000 temos um gráfico que lembra muito uma função seno, crescendo lentamente de 2005 até 2014, quando explode em 2015. Vemos que o Brasil enfrenta um grande problema, já que as taxas tem aumentado gradativamente, diferente das taxas mundiais, que tem diminuído. Lembrando que estamos falando sobre suícidio, então qualquer caso é uma tragédia. 

**3.5 - As taxas, os anos e as idades.**

<img src="https://github.com/Franklyn-Sancho/DataScience_SetembroAmarelo/blob/main/TaxaFaixaIdade.jpg">
