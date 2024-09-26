# ADS
aula ads - 4 - 1 e 2 semestre 
Explicação do Código:
# Gerar os dados: O código cria um DataFrame fictício com os dados das compras 
(ID, data, produto, quantidade, valor, unidade, total e setor). 
Salvar como CSV: O arquivo CSV é gerado automaticamente no Colab, 
sem a necessidade de upload manual. Função carregar_csv(): Lê o arquivo CSV e 
retorna como um DataFrame. Função mostrar_compras_por_setor(df): Exibe os setores disponíveis. 
Mostra a contagem de compras por setor com o value_counts(). 
Cria um gráfico de barras usando seaborn e matplotlib para melhor visualização dos dados. 
Exibir os dados: O código exibe o DataFrame e as contagens de compras por setor de forma interativa.
---------------------------------------------------------------------------------------------------------
# Instale as bibliotecas necessárias
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from IPython.display import display

# Definir os dados para o CSV
data = {
    'ID': [1, 2, 3, 4],
    'DATA': ['01/01/2024', '10/02/2024', '30/05/2024', '29/06/2024'],
    'PRODUTO': ['TOALHA', 'SABONETE', 'MOUSE', 'TECLADO'],
    'QNT': [6, 5, 3, 2],
    'VALOR': ['R$ 35,00', 'R$ 3,00', 'R$ 10,00', 'R$ 38,00'],
    'UNIDADE': ['R$ 210,00', 'R$ 15,00', 'R$ 30,00', 'R$ 76,00'],
    'TOTAL': ['R$ 210,00', 'R$ 15,00', 'R$ 30,00', 'R$ 76,00'],
    'SETOR': ['MesaBanho', 'Perfumaria', 'Informática', 'Informática']
}

# Criar o DataFrame a partir dos dados
df = pd.DataFrame(data)

# Salvar o DataFrame como CSV (você não precisa fazer upload manualmente)
df.to_csv('compras.csv', index=False)

# Função para ler e exibir o CSV em um DataFrame
def carregar_csv():
    df = pd.read_csv('compras.csv')
    return df

# Função para mostrar a contagem de compras por setor com gráfico
def mostrar_compras_por_setor(df):
    # Exibir os setores únicos
    print("Setores disponíveis no arquivo:")
    print(df['SETOR'].unique())

    # Contar quantas compras cada setor tem
    compras_por_setor = df['SETOR'].value_counts()
    print("\nNúmero de compras por setor:")
    display(compras_por_setor)

    # Visualizar os dados com um gráfico de barras
    plt.figure(figsize=(8, 6))
    sns.barplot(x=compras_por_setor.index, y=compras_por_setor.values, hue=compras_por_setor.index, palette="viridis", legend=False)
    plt.title("Compras por Setor")
    plt.xlabel("Setor")
    plt.ylabel("Número de Compras")
    plt.xticks(rotation=45)
    plt.show()

# Carregar o CSV e exibir
df = carregar_csv()
print("Dados do CSV:")
display(df)

# Mostrar compras por setor com gráfico
mostrar_compras_por_setor(df)
