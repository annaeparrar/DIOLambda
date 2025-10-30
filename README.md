# Automatizando Tarefas com AWS Lambda e Amazon S3

## Desafio de Projeto - Digital Innovation One (DIO)

Este repositório documenta a implementação prática de uma solução **Serverless** na **Amazon Web Services (AWS)**, utilizando a integração entre o **Amazon S3** (Simple Storage Service) e o **AWS Lambda Function** para automatizar tarefas em resposta a eventos de upload de arquivos.

O objetivo é consolidar o conhecimento em **tarefas automatizadas**, documentando a experiência e os insights adquiridos, servindo como material de apoio e demonstração de proficiência técnica.

---

## Objetivo da Automação

**O que o projeto faz:**

* **Serviço de Origem (Trigger):** Amazon S3 (Bucket: `DioLambda`)
* **Evento:** `s3:ObjectCreated:Put` 
* **Função:** AWS Lambda Function (`LambdaFun`)
* **Ação Automatizada:** Quando um novo arquivo é carregado no S3, a função Lambda é acionada para... **Emitir alerta**.

---

## Tecnologias e Conceitos Aplicados

| Serviço / Conceito | Descrição e Aplicação no Projeto |
| :--- | :--- |
| **AWS Lambda** | Serviço de computação Serverless. Utilizado para executar o código **[Linguagem: Python/Node.js]** em resposta ao evento S3, sem a necessidade de gerenciar servidores. |
| **Amazon S3** | Serviço de armazenamento de objetos escalável. Configurado como **gatilho de evento** para iniciar o fluxo de automação. |
| **IAM (Identity and Access Management)** | Usado para criar uma **Role de Execução (Execution Role)** com as permissões mínimas necessárias para a Lambda: logs no CloudWatch e acesso de leitura/escrita no S3. |
| **CloudFormation (Opcional)** |  |
| **CloudWatch** | Utilizado para monitorar e registrar os logs de execução da função Lambda, garantindo a rastreabilidade e o debug da automação. |

---

## Estrutura e Implementação do Projeto

### 1. Pré-requisitos
* Conta AWS ativa.
* Conhecimento básico em Python.
* Configuração do AWS CLI .

### 2. Arquivos no Repositório

| `README.md` | Este documento. |

### 3. Código da Função Lambda

O código (`Lambdatest`) é responsável por analisar o evento S3 recebido e executar a lógica principal.
```python
def lambda_handler(event, context):
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    print(f"Novo objeto criado no bucket: {bucket} com chave: {key}")
      return {
        'statusCode': 200,
        'body': 'Processamento concluído com sucesso!'
    }
