
from sys import displayhook
import pandas as pd
# importando os arquivos
vendas_df = pd.read_csv(r'C:\Users\Usuario\OneDrive\Desktop\pandas analise de dados\Contoso - Vendas  - 2017.csv', sep=';')
produtos_df = pd.read_csv(r'C:\Users\Usuario\OneDrive\Desktop\pandas analise de dados\Contoso - Cadastro Produtos.csv', sep=';')
lojas_df = pd.read_csv(r'C:\Users\Usuario\OneDrive\Desktop\pandas analise de dados\Contoso - Lojas.csv', sep=';')
clientes_df = pd.read_csv(r'C:\Users\Usuario\OneDrive\Desktop\pandas analise de dados\Contoso - Clientes.csv', sep=';')

# limpando apenas as colunas que queremos
clientes_df = clientes_df[['ID Cliente', 'E-mail']]
produtos_df = produtos_df[['ID Produto']]
lojas_df = lojas_df[['ID Loja', 'Nome da Loja']]

# mesclando e renomeando os dataframes
vendas_df = vendas_df.merge(produtos_df, on='ID Produto')
vendas_df = vendas_df.merge(lojas_df, on='ID Loja')
vendas_df = vendas_df.merge(clientes_df, on='ID Cliente').rename(columns={'E-mail': 'E-mail do Cliente'})
displayhook(vendas_df)
