### Análise de Dados de Tickets de Suporte ao Cliente

Este projeto realiza análise de dados em um dataset público do Kaggle contendo informações sobre tickets de suporte ao cliente, utilizando Python e bibliotecas como Pandas para análise de dados e Qdrant para armazenamento de vetores.

### Objetivo

O projeto visa analisar dados de tickets de suporte ao cliente para extrair insights valiosos, incluindo:
- Distribuição percentual do status dos tickets
- Identificação dos clientes com maior número de tickets
- Análise de padrões e tendências nos dados de suporte

### Tecnologias Utilizadas

- Python 3.10
- Pandas para manipulação de dados
- Qdrant para armazenamento vetorial
- LangChain para processamento de linguagem natural
- OpenAI para geração de embeddings

### Estrutura do Projeto

```
projeto/
├── notebooks/
│   ├── 1-exemplo_inicial.ipynb
│   └── 2-embeddings.ipynb
├── data/
│   └── customer_support_tickets.csv
├── .env
└── README.md
```

### Configuração do Ambiente

1. Clone o repositório
2. Instale as dependências:
```bash
pip install pandas qdrant-client langchain openai python-dotenv
```
3. Configure as variáveis de ambiente:
   - Crie um arquivo `.env`
   - Adicione sua chave API do OpenAI

### Funcionalidades Principais

1. **Análise de Status dos Tickets**
   - Calcula a distribuição percentual dos status dos tickets
   - Visualiza os resultados através de gráficos

2. **Análise de Clientes**
   - Identifica clientes com maior número de tickets
   - Analisa padrões de uso do suporte

### Implementação

O projeto utiliza Qdrant para armazenamento vetorial e busca semântica:

```
client = QdrantClient(host="localhost", port=6333)
client.create_collection(
    collection_name="descomplicando_qdrant_tickets",
    vectors_config=VectorParams(size=1536, distance=Distance.COSINE),
)
```

### Sistema de Perguntas e Respostas

O projeto implementa um sistema de Q&A utilizando LangChain e OpenAI:

```
def qa_system(pergunta):
    resultado = qa({
        "query": pergunta
    })
    return {
        "resposta": resultado["result"],
        "fontes": resultado["source_documents"]
    }
```
### Como Usar

1. Carregue o dataset:
```
texto_chunks = quebrar_csv_helpdesk("customer_support_tickets.csv")
vectorstore.add_documents(texto_chunks)
```

2. Faça perguntas sobre os dados:
```
pergunta = "What percentage is the status of each ticket? return in percentage"
resultado = qa_system(pergunta)
print(resultado["resposta"])
```

### Exemplos de Análises

1. **Status dos Tickets**
   - Distribuição percentual por status
   - Visualização através de gráficos

2. **Análise de Clientes**
   - Ranking de clientes por número de tickets
   - Padrões de utilização do suporte

### Contribuição

Para contribuir com o projeto:
1. Faça um fork do repositório
2. Crie uma branch para sua feature
3. Faça commit das alterações
4. Envie um pull request

### Contato

Meu Linkedln: https://www.linkedin.com/in/airton-lira-junior-6b81a661/

### Agradecimentos

- Kaggle pela disponibilização do dataset
- Comunidade open source pelas ferramentas utilizadas
