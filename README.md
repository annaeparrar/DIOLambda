# DIOLambda
Este projeto implementa uma solução serverless na AWS para automação de tarefas usando a integração nativa entre Amazon S3 e AWS Lambda Functions. A solução configura um gatilho de evento (s3:ObjectCreated:Put) em um bucket S3, que dispara uma Lambda Function ([Linguagem utilizada, ex: Python]) sempre que um novo objeto é carregado.
