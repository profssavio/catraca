# ESTRATÉGIA DE IMPORTAÇÃO (SEMESTRAL)

O arquivo modelo está no projeto **modelo.csv**

> **!Importante:** Os valores de **matrícula** e **cpf** não podem ter mascaras.
> 
> **!Importante:** Os campos **matrícula** e **cpf** tem que ser do tipo texto para não peder o zero inicial.

## IMPORTAÇÃO 

- Fazer a importação de todos os estudantes via arquivo .csv

> **!Importante:** As colunas **dateStartLimit	dateLimit** definir a data do semestre

Exemplo:
```
dateStartLimit	dateLimit
20/03/2018	25/03/2018
20/03/2018	25/03/2018
```

# RETIRAR ACENTOS DO ARQUIVO COLUNA *NAME*

- Em Python

```
import pandas as pd
import unicodedata

def remover_acentos(nome):
    # Normaliza a string para decompor os caracteres acentuados
    nome_normalizado = unicodedata.normalize('NFD', nome)
    # Filtra apenas os caracteres que não são acentos
    nome_sem_acento = ''.join(c for c in nome_normalizado if unicodedata.category(c) != 'Mn')
    return nome_sem_acento

# Carregar o arquivo CSV
df = pd.read_csv('Importacao.csv')

# Remover acentos da coluna 'name'
df['name'] = df['name'].apply(remover_acentos)

# Salvar o DataFrame de volta em um novo arquivo CSV
df.to_csv('Importacao_sem_acento.csv', index=False)

```
