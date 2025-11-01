# Executando Tarefas Automatizadas com AWS Lambda Function e S3

Este repositório foi criado para o **desafio da DIO - Executando Tarefas Automatizadas com AWS Lambda Function e S3**.  
O objetivo é demonstrar, de forma **didática e teórica**, como automatizar tarefas na nuvem utilizando **funções Lambda** em conjunto com o **Amazon S3**.

---

## Objetivo do Desafio

Este desafio tem como propósito consolidar o entendimento sobre como o **AWS Lambda** pode ser utilizado para **automatizar processos baseados em eventos**, como o envio, leitura ou exclusão de arquivos em **buckets S3**.

---

##  Conceitos Aprendidos

- **AWS Lambda** — serviço serverless para execução de código sob demanda.  
- **Amazon S3** — serviço de armazenamento de objetos altamente escalável.  
- **Eventos S3 + Lambda** — integração que permite acionar funções automaticamente.  

---


### 🧩 Exemplo de Função Lambda (Didática)

Abaixo está um exemplo **teórico** de função Lambda que é acionada quando um arquivo é enviado para um bucket S3.  
Essa função apenas imprime o nome do arquivo e o bucket simulando uma automação simples.

```python
import json

def lambda_handler(event, context):
    # Extrai informações do evento enviado pelo S3
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']

    print(f"Novo arquivo detectado no bucket: {bucket}")
    print(f"Nome do arquivo: {key}")

    
    return {
        'statusCode': 200,
        'body': json.dumps('Tarefa automatizada executada com sucesso!')
    }
