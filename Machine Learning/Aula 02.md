# Aula 02 – NumPy e Pandas para Machine Learning

## Preparando os Dados para a Inteligência Artificial

**Carga Horária:** 4 horas

---

# Objetivos da Aula

Ao final desta aula você será capaz de:

✅ Entender o que é NumPy.

✅ Criar vetores e matrizes.

✅ Manipular dados utilizando Pandas.

✅ Ler arquivos CSV.

✅ Filtrar informações.

✅ Tratar dados ausentes.

✅ Preparar dados para Machine Learning.

---

# Relembrando a Aula Anterior

Na aula passada aprendemos:

```text
Dados → Algoritmo → Modelo → Previsão
```

Mas existe um problema...

Na vida real os dados nunca vêm organizados.

Imagine uma planilha assim:

| Nome  | Idade | Salário |
| ----- | ----- | ------- |
| João  | 25    | 3000    |
| Maria |       | 4500    |
| Pedro | 40    |         |
| Ana   | 22    | 2800    |

Observe:

❌ Idade faltando

❌ Salário faltando

❌ Dados incompletos

Antes de ensinar uma IA precisamos organizar tudo.

É exatamente isso que faremos hoje.

---

# 1. O que é NumPy?

NumPy significa:

```text
Numerical Python
```

É uma biblioteca criada para trabalhar com números e matrizes.

Praticamente todas as bibliotecas de IA utilizam NumPy internamente.

---

## Analogia

Imagine uma calculadora comum.

Ela faz:

```text
2 + 2
```

Agora imagine uma calculadora capaz de realizar milhões de cálculos por segundo.

Essa é a ideia do NumPy.

---

# Importando o NumPy

```python
import numpy as np
```

## Explicação

### import

Importa uma biblioteca.

### numpy

Nome da biblioteca.

### as np

Apelido utilizado mundialmente.

---

# 2. Criando Arrays

Em Machine Learning quase tudo é armazenado em Arrays.

---

## Lista Python

```python
idades = [18, 22, 30, 40]
```

---

## Array NumPy

```python
import numpy as np

idades = np.array([18, 22, 30, 40])

print(idades)
```

Resultado:

```text
[18 22 30 40]
```

---

# O que é um Array?

Um Array é semelhante a uma lista.

Porém:

✅ Mais rápido

✅ Menos memória

✅ Melhor para cálculos matemáticos

---

# 3. Operações Matemáticas

Lista Python:

```python
numeros = [1,2,3]

print(numeros * 2)
```

Resultado:

```text
[1,2,3,1,2,3]
```

A lista foi repetida.

---

Com NumPy:

```python
numeros = np.array([1,2,3])

print(numeros * 2)
```

Resultado:

```text
[2 4 6]
```

Cada elemento foi multiplicado.

---

# Analogia

Imagine uma sala com 40 alunos.

Você deseja aumentar todas as notas em 1 ponto.

Sem NumPy:

```text
Aluno por aluno...
```

Com NumPy:

```text
Todos ao mesmo tempo.
```

---

# 4. Matrizes

Machine Learning trabalha principalmente com matrizes.

---

## Criando uma matriz

```python
dados = np.array([
    [18, 1500],
    [25, 3000],
    [35, 5000]
])

print(dados)
```

Resultado:

```text
[[  18 1500]
 [  25 3000]
 [  35 5000]]
```

---

## Visualizando

| Idade | Salário |
| ----- | ------- |
| 18    | 1500    |
| 25    | 3000    |
| 35    | 5000    |

---

# 5. Acessando Posições

```python
dados = np.array([
    [18,1500],
    [25,3000],
    [35,5000]
])

print(dados[0])
```

Resultado:

```text
[18 1500]
```

Primeira linha.

---

## Linha e Coluna

```python
print(dados[1,1])
```

Resultado:

```text
3000
```

---

## Explicação

```text
dados[linha, coluna]
```

---

# 6. Conhecendo Melhor o Pandas

Na aula anterior criamos DataFrames.

Hoje vamos manipulá-los.

---

# Criando uma tabela

```python
import pandas as pd

dados = {
    "nome": ["João", "Maria", "Pedro"],
    "idade": [25, 30, 40]
}

df = pd.DataFrame(dados)

print(df)
```

---

Resultado

| nome  | idade |
| ----- | ----- |
| João  | 25    |
| Maria | 30    |
| Pedro | 40    |

---

# 7. Informações da Tabela

```python
df.info()
```

Resultado:

```text
Quantidade de linhas
Quantidade de colunas
Tipo dos dados
```

---

# Analogia

É como olhar a ficha técnica de um carro.

---

# 8. Estatísticas Básicas

```python
df.describe()
```

Resultado:

```text
Média
Máximo
Mínimo
Desvio padrão
```

---

Exemplo:

| idade        |
| ------------ |
| Média = 31,6 |
| Máximo = 40  |
| Mínimo = 25  |

---

# Por que isso é importante?

Antes de treinar uma IA precisamos conhecer os dados.

---

# 9. Lendo Arquivos CSV

Grande parte dos datasets vêm em CSV.

CSV significa:

```text
Comma Separated Values
```

Valores separados por vírgulas.

---

## Exemplo

arquivo.csv

```csv
nome,idade,salario
João,25,3000
Maria,30,4500
Pedro,40,5000
```

---

## Lendo o arquivo

```python
import pandas as pd

df = pd.read_csv("arquivo.csv")

print(df)
```

---

# Explicando o read_csv()

### read

Ler

### csv

Arquivo CSV

---

# 10. Visualizando Dados

Primeiras linhas:

```python
df.head()
```

Resultado:

```text
Mostra as 5 primeiras linhas
```

---

Últimas linhas:

```python
df.tail()
```

Resultado:

```text
Mostra as 5 últimas linhas
```

---

# Analogia

É como abrir uma apostila e olhar a primeira e a última página.

---

# 11. Filtrando Dados

Tabela:

| Nome  | Idade |
| ----- | ----- |
| João  | 18    |
| Ana   | 25    |
| Pedro | 35    |

---

Mostrar somente maiores de idade acima de 20 anos:

```python
print(df[df["idade"] > 20])
```

Resultado:

| Nome  | Idade |
| ----- | ----- |
| Ana   | 25    |
| Pedro | 35    |

---

# Entendendo

```python
df["idade"] > 20
```

Produz:

```text
False
True
True
```

O Pandas utiliza esse resultado para filtrar.

---

# 12. Dados Faltando

Problema muito comum.

---

Tabela:

| Nome  | Idade |
| ----- | ----- |
| João  | 25    |
| Maria |       |
| Pedro | 40    |

---

## Verificando valores vazios

```python
df.isnull()
```

Resultado:

```text
True
False
```

---

## Quantidade de vazios

```python
df.isnull().sum()
```

Exemplo:

```text
idade    1
```

---

# 13. Removendo Dados Vazios

```python
df = df.dropna()
```

---

## Explicação

### drop

Remover

### na

Not Available

(Dado indisponível)

---

# 14. Preenchendo Dados Vazios

Em vez de apagar:

```python
df["idade"] = df["idade"].fillna(df["idade"].mean())
```

---

## O que acontece?

Se a média for:

```text
30
```

Maria recebe:

```text
30
```

automaticamente.

---

# Analogia

Imagine uma pesquisa com 100 pessoas.

Uma delas esqueceu de informar a idade.

Podemos usar a média do grupo para completar.

---

# 15. Preparando Dados para IA

Tabela original:

| Nome  | Idade | Salário | Comprou |
| ----- | ----- | ------- | ------- |
| João  | 25    | 3000    | Sim     |
| Maria | 40    | 5000    | Sim     |
| Pedro | 18    | 1500    | Não     |

---

Separando entradas:

```python
X = df[["idade", "salario"]]
```

---

Separando resposta:

```python
y = df["comprou"]
```

---

Agora os dados estão prontos para treinamento.

---

# Exercício Prático

Crie um DataFrame com:

| Nome  | Nota |
| ----- | ---- |
| Ana   | 8    |
| João  | 5    |
| Pedro | 9    |
| Maria | 7    |

Depois:

1. Mostre a tabela.
2. Exiba apenas alunos com nota maior que 7.
3. Mostre a média das notas.

---

# Exercícios

## Exercício 1

Explique a diferença entre:

```python
lista = [1,2,3]
```

e

```python
np.array([1,2,3])
```

---

## Exercício 2

O que faz:

```python
import numpy as np
```

---

## Exercício 3

Explique:

```python
df.head()
```

---

## Exercício 4

Explique:

```python
df.describe()
```

---

## Exercício 5

Qual a função de:

```python
df.dropna()
```

---

# Desafio da Aula

Crie uma tabela com:

| Horas Estudo | Nota |
| ------------ | ---- |
| 2            | 4    |
| 3            | 5    |
| 5            | 7    |
| 6            | 8    |
| 8            | 10   |

Utilize Pandas para:

* Criar o DataFrame.
* Mostrar estatísticas.
* Exibir apenas notas maiores que 7.

---

# Resumo

Hoje aprendemos:

✅ O que é NumPy

✅ Arrays e matrizes

✅ Operações matemáticas vetorizadas

✅ O que é Pandas

✅ DataFrame

✅ Leitura de CSV

✅ Filtros

✅ Tratamento de dados faltantes

✅ Preparação dos dados para Machine Learning

### Próxima Aula

**Treinamento e Teste de Modelos**

Você aprenderá:

* `train_test_split()`
* Treino e teste
* Overfitting
* Underfitting
* Primeira avaliação de um modelo de Machine Learning com dados reais.
