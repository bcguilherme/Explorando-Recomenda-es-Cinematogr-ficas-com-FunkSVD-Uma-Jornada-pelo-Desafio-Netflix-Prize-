# Explorando-Recomenda-es-Cinematogr-ficas-com-FunkSVD-Uma-Jornada-pelo-Desafio-Netflix-Prize-


# Recomendação Cinematográfica com FunkSVD 🎥🍿

Este projeto utiliza o algoritmo FunkSVD para criar um sistema de recomendação de filmes. O FunkSVD é uma técnica poderosa de fatoração de matriz, notável por seu sucesso no desafio Netflix Prize de 2006.

## Sobre o Projeto

O objetivo deste projeto é explorar a recomendação de filmes com base nas avaliações de usuários, utilizando o conjunto de dados do MovieLens.

## Como Usar


```python
# Carregar bibliotecas
import pandas as pd
import numpy as np

# Carregar avaliações dos usuários
df_ratings = pd.read_parquet('ratings.parquet')

# Carregar metadados dos filmes
df_items = pd.read_parquet('movies.parquet')

from funk_svd import SVD

# Definir hiperparâmetros
lr = 0.001
reg = 0.005
n_epochs = 100
n_factors = 30

# Criar modelo
model = SVD(lr=lr, reg=reg, n_epochs=n_epochs, n_factors=n_factors)

# Treinar o modelo
model.fit(X=df_ratings)

# Avaliar o modelo
model.evaluate(X=df_ratings)

# Gerar recomendações para um usuário específico
user_id = 123
item_ids = df_items['item_id'].unique()
recommendations = model.recommend_n_items(user_id, item_ids, n=10)
print(recommendations)

Contribuições

Contribuições são bem-vindas! Se você encontrar melhorias ou tiver sugestões, sinta-se à vontade para abrir uma issue ou enviar um pull request.
