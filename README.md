<h1 align="center"> Analisando a taxa de suicídio do mundo com DataScience<h1>

<h5 align="center">Não tem sido fácil analisar esses dados, não só pela parte técnica, mas principalmente pelo assunto abordado. Falar sobre suícidio não é simples, mas precisamos. A cada resultado analisado, levando da minha cadeira e tiro alguns minutos para respirar e refletir sobre o mundo que estamos construíndo.</h5>

**1 - Ferramentas usadas nesta análise**
* Eu fiz pelo Google Colab, por uma questão de simplicidade. Não precisa instalar absolutamente nada. 
* Mas caso você queeira trabalhar diretamente no pc. Lá vamos: 
* Python
* Pandas
* Matplotlib
* seaborn
* numpy
* Anaconda e Jupyter também seria uma ótima opção. 

**2 - Importanto as ferramentas e preparando o ambiente inicial**
```python
import pandas as pd
import matplotlib as plt
import numpy as np
import seaborn as sns

dados = pd.read_csv('https://raw.githubusercontent.com/carlosfab/data_science/master/datasets/suicide_rates.csv')
```
Primeiro importamos as nossas bibliotecas de análise: Pandas, matplotlib, numpy, seaborn; depois damos um nome para o nosso dataset, chamamos o pandas, modo leitura, o tipo de arquivo (no caso CSV) e o link dos dados. No nosso caso, este sobre as taxas de suícidio no mundo

**3 - Vamos iniciar a nossa analise**

***Vamos entender as nossas variáveis:***
* country: 101 países no total
* year: Entre 1985 até 2016
* sex: Masculino e Feminino (baseado no registro
* age: 5-14 anos | 15-24 anos | 25-34 anos | 35-54 anos | 55-74 anos | 75+ anos
* suicides_no: Numero total de suícidio
* population: população
* suicides/100k pop: Suícidio por 100 mil habidades
* country_year: identificador contendo country + year
* HDI for year: IDH para o ano
* gdp_for_year: PIB para o ano
* gdp_per_capita: PIB per capita 


**3.1 - Vamos analisar agora como estão os números entre os anos de 1985 até 2016**<br>

Para isso, vamos chamar o nosso clássico histograma. 
```python
dados.hist('year')
```
<b>Teremos o seguinte dado ao executar essa função:</b>

<img src="https://github.com/Franklyn-Sancho/DataScience_Titanic/blob/main/Anos.jpg">
Podemos ver claramente, que infelizmente, os números só aumentaram. Apesar de correto, este gráfico não está tão preciso quanto aos resultados. Mas conforme vamos analisando, teremos números ainda maisa claros e melhores.
