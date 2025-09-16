# Ebac-com

# Importando as bibliotecas necessárias
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Conteúdo do arquivo gasolina.csv
csv_content = """dia,venda
1,5.11
2,4.99
3,5.02
4,5.21
5,5.07
6,5.09
7,5.13
8,5.12
9,4.94
10,5.03
"""

# Criando o arquivo .csv
with open('gasolina.csv', 'w') as file:
    file.write(csv_content)

print("Arquivo 'gasolina.csv' criado com sucesso.")

# Lendo o arquivo .csv com pandas
df = pd.read_csv('gasolina.csv')

# Criando o gráfico de linha com seaborn
sns.set_style("whitegrid")
plt.figure(figsize=(10, 6))
sns.lineplot(data=df, x='dia', y='venda', marker='o', color='b', linewidth=2.5)

# Adicionando título e rótulos aos eixos
plt.title('Preço Médio de Venda da Gasolina em São Paulo - Julho/2021', fontsize=16, fontweight='bold')
plt.xlabel('Dia', fontsize=12)
plt.ylabel('Preço Médio de Venda (R$)', fontsize=12)

# Adicionando rótulos de dados
for index, row in df.iterrows():
    plt.text(row.dia, row.venda + 0.02, f'{row.venda}', ha='center', va='bottom', fontsize=10)

# Salvando o gráfico em um arquivo .png
plt.savefig('gasolina.png')
print("Gráfico 'gasolina.png' salvo com sucesso.")

# O código que gera o gráfico também será salvo em um arquivo .py
python_code = """
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

def gerar_grafico():
    # Carregando os dados do arquivo CSV
    try:
        df = pd.read_csv('gasolina.csv')
    except FileNotFoundError:
        print("Erro: Arquivo 'gasolina.csv' não encontrado. Certifique-se de que ele está no mesmo diretório.")
        return

    # Criando o gráfico de linha
    sns.set_style("whitegrid")
    plt.figure(figsize=(10, 6))
    sns.lineplot(data=df, x='dia', y='venda', marker='o', color='b', linewidth=2.5)

    # Adicionando título e rótulos
    plt.title('Preço Médio de Venda da Gasolina em São Paulo - Julho/2021', fontsize=16, fontweight='bold')
    plt.xlabel('Dia', fontsize=12)
    plt.ylabel('Preço Médio de Venda (R$)', fontsize=12)
    
    # Adicionando rótulos de dados
    for index, row in df.iterrows():
        plt.text(row.dia, row.venda + 0.02, f'{row.venda}', ha='center', va='bottom', fontsize=10)

    # Salvando o gráfico em um arquivo PNG
    plt.savefig('gasolina.png')
    plt.show()

if __name__ == "__main__":
    gerar_grafico()
"""

with open('gasolina.py', 'w') as file:
    file.write(python_code)
print("Arquivo 'gasolina.py' criado com sucesso.")



!git checkout -b develop

!git add gasolina.csv gasolina.py gasolina.png
!git commit -m "Atualizacao do exercicio de gasolina na branch develop"


!git push origin develop
