
# Tratando a imensidão dos dados

Através dessa atividade realizei a limpeza de um conjunto de
dados, tornando-o apto a ser usado em tarefas de mineração/análise de
dados.

### Contextualização:
Como Analista de Dados, você recebeu, em um novo projeto, um conjunto de dados. Sua principal tarefa é tratar os dados desse a fim de que possam ser utilizados para a descoberta de conhecimento através de sua posterior análise e interpretação. Para tal tarefa, você deverá utilizar a linguagem Python e a biblioteca Pandas.

### Procedimentos
1-	Para essa atividade, tive obrigatoriamente, utilizar o conjunto de dados fornecido anteriormente, na seção “Contextualização”.
Após ler um conjunto de dados, fornecidos no enunciado da entrega, compostos pelas conlunas ID;Duration;Date;Pulse;Maxpulse;Calories devemos desenvolver a seguinte programação:


## Uso/Exemplos

```import pandas as pd

# 1. Leitura do CSV
df = pd.read_csv('seu_arquivo.csv')

# 2. Verificação da importação dos dados
print("Informações gerais do DataFrame:")
print(df.info())

print("\nPrimeiras 5 linhas:")
print(df.head())

print("\nÚltimas 5 linhas:")
print(df.tail())

# 3. Criação de uma cópia do DataFrame original
df_copy = df.copy()

# 4. Tratamento de valores nulos na coluna 'Calories'
df_copy['Calories'].fillna(0, inplace=True)
print("\nDataFrame após substituir nulos na coluna 'Calories' por 0:")
print(df_copy)

# 5. Tratamento de valores nulos na coluna 'Date'
df_copy['Date'].fillna('1900/01/01', inplace=True)
print("\nDataFrame após substituir nulos na coluna 'Date' por '1900/01/01':")
print(df_copy)

# 6. Tentativa de conversão para datetime e tratamento de erros
try:
    df_copy['Date'] = pd.to_datetime(df_copy['Date'], format='%Y/%m/%d')
except Exception as e:
    print(f"Erro ao converter 'Date': {e}")

# 7. Correção do erro na conversão de datetime
df_copy['Date'].replace('1900/01/01', pd.NA, inplace=True)
df_copy['Date'] = pd.to_datetime(df_copy['Date'], errors='coerce')

# Tratamento do valor incorreto '20201226'
df_copy['Date'] = df_copy['Date'].replace('20201226', '2020/12/26')
df_copy['Date'] = pd.to_datetime(df_copy['Date'], format='%Y/%m/%d')

print("\nDataFrame após correções na coluna 'Date':")
print(df_copy)

# 8. Remoção de registros com valores nulos na coluna 'Date'
df_copy.dropna(subset=['Date'], inplace=True)

print("\nDataFrame final após todas as transformações:")
print(df_copy)

```

