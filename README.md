# ESTRATÉGIA DE IMPORTAÇÃO (SEMESTRAL)

## 1ª IMPORTAÇÃO 

- Fazer a importação de todos os estudantes via arquivo .csv e se possível guardar no local determinado.

## 2ª IMPORTAÇÃO

- Pegar o arquivo da importação anterior e colocar na **coluna INATIVO** o valor **Sim** e realizar a importação.
- > **!Importante:** Se por acaso não tem mais o arquivo, a opção e fazer a exportação do sistema e arrumar as colunas.
- Pegar o **novo arquivo** e fazer a importação

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

# NA COLUNA *dateStartLimit	dateLimit*

- Definir a data do semestre

Exemplo:

```
dateStartLimit	dateLimit
20/03/2018	25/03/2018
20/03/2018	25/03/2018
```
