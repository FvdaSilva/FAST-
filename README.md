# FAST-
Coleta de dados da API
                 | 
              Python 
                 | 
        Limpeza e Formatação
                 | 
             Criação de
         novas colunas, se necessário
                 | 
            Conversão para
                JSON
                 | 
     Conexão com o Banco de Dados
                 | 
             MongoDB 

Python

import requests
import pymongo
import json

# Coletando dados da API
response = requests.get('http://api.example.com/data')
data_from_api = response.json()

# Operações de limpeza e formatação
# Suponha que você tenha um dicionário chamado cleaned_data após a limpeza e formatação
cleaned_data = clean_and_format_data(data_from_api)

# Criação de novas colunas, se necessário
cleaned_data['new_column'] = 'new_value'

# Conversão para JSON
data_json = json.dumps(cleaned_data)

# Conexão com o banco de dados MongoDB
myclient = pymongo.MongoClient("mongodb://localhost:27017/")
mydb = myclient["mydatabase"]
mycollection = mydb["mycollection"]

# Inserindo os dados no MongoDB
mycollection.insert_one(json.loads(data_json))
