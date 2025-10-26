
# Analise-Dataset

## Instruções de Uso

### Pré-requisitos

É necessário ter o Python e as seguintes bibliotecas instaladas:
```bash
pip install pandas numpy scikit-learn seaborn matplotlib kagglehub
````

Além disso, é necessário configurar sua chave de API do Kaggle no ambiente para que o download do dataset funcione corretamente.

### Carregamento do Dataset

O repositório contém o código completo que executa o download direto do Kaggle, garantindo que a versão correta do dataset seja utilizada:

```python
# Instala as dependências do kagglehub
!pip install kagglehub -q 

# Importa a biblioteca
import kagglehub
import os

# Download do dataset "gregorut/videogamesales"
path = kagglehub.dataset_download("gregorut/videogamesales")
print("Path to dataset files:", path)

# Carrega o DataSet
if 'path' in locals() and os.path.isdir(path):
    csv_file_path = os.path.join(path, 'vgsales.csv')
    
    # Verifica se o arquivo CSV existe no caminho esperado
    if os.path.exists(csv_file_path):
        df_games = pd.read_csv(csv_file_path)
        print(f"Dataset carregado de: {csv_file_path}")
    else:
        print(f"Erro: O arquivo 'vgsales.csv' não foi encontrado em {path}")
else:
    print("Erro: O caminho do dataset baixado não foi encontrado ou não é um diretório.")
```

### Execução

1.  Salve o código Python completo fornecido na Seção 2 em um arquivo, por exemplo, `analise_vendas.py`.
2.  Execute o script no seu ambiente Python.

<!-- end list -->

```bash
python analise_vendas.py
```

O script realizará automaticamente todo o pipeline: download, limpeza, engenharia de features, treinamento e avaliação dos modelos.
