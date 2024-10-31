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
