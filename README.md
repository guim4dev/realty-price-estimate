# EEL891 - 2021.1 - Relatório do Trabalho 2
Regressão Multivariável - estimar o preço de um imóvel a partir de suas características

Aluno: Thiago Guimarães

## Sobre o Repositório

Nesse repositório podem ser encontrados um [`notebook`](https://github.com/guim4dev/realty-price-estimate/blob/main/notebook.ipynb), que foi utilizado
para realizar o pré-processamento dos dados e o treinamento do modelo, além da geração de um arquivo [`submission.csv`](https://github.com/guim4dev/realty-price-estimate/blob/main/submission.csv), que é o arquivo entregado no Kaggle. Há também uma pasta [`data`](https://github.com/guim4dev/realty-price-estimate/tree/main/data), na qual estão armazenados os datasets fornecidos e afins.

## Pré-processamento

Por meio da análise dos dados utilizando pandas e das informações fornecidas no kaggle, foram mapeadas colunas inúteis que poderiam ser descartadas, colunas que precisariam passar por um processo de one_hot_encoding, fora outros processamentos. As colunas que sofreram tais tipos de alteração estão mapeadas detalhadamente no arquivo de [`anotações](https://github.com/guim4dev/realty-price-estimate/blob/main/anotacoes.txt).
Em resumo temos:

**1. Colunas removidas:**

```
'Id',
'diferenciais',
's_jogos',
's_ginastica'
```

**2. Colunas que são binarizadas:**

```
'tipo_vendedor'
```

**3. Colunas que sofrem one_hot_encode:**

```
'tipo',
'bairro'
```

**4. Outras alterações:**

Além disso, para remover bias de algumas variáveis numéricas quantitativas, foi utilizado um processo de MinMaxScaling, sendo estas colunas:

```
'quartos',
'suites',
'vagas',
'area_util',
'area_extra'
```

## Implementação do modelo classificador

Tendo tanto o dataframe de teste como o de treino em mãos, foram treinados diversos modelos, dentre estes: RandomForest, AdaBoost, NaiveBayes, KNN e GradientBoosting. Após uma grande quantidade de testes, o melhor modelo em questão de performance foi o Gradient Boosting. Assim, foi realizado um processo de fine tuning dos hiperparâmetros deste modelo, de forma a encontrar o melhor resultado para sua accuracy. Como foram feitos diversos testes e para facilitar o processo de leitura do notebook, estes testes de modelos diferentes foram retirados no Notebook para despoluí-lo.


## Resultados

Assim
O modelo encontrou um rmspe de 0.2559 no teste utilizando train_test_split. Já no kaggle, o rmspe encontrado foi de 0.27142.