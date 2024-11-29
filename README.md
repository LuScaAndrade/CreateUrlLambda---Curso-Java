# CreateUrlLambda - Curso-Java
## Encurtador de URLs

Este projeto implementa um serviço de encurtamento de URLs utilizando AWS Lambda e Amazon S3.

## 📋 Descrição

O código recebe uma URL original e um tempo de expiração, gera um código curto exclusivo e armazena os dados no S3.

---

## 🚀 Funcionalidades

1. Recebe um corpo JSON contendo:
   - `OriginalUrl`: A URL a ser encurtada.
   - `expirationTime`: O tempo de expiração em segundos.
2. Gera um código único de 8 caracteres para a URL curta.
3. Salva os dados no Amazon S3 em formato JSON.

---

## 🛠️ Tecnologias Utilizadas

- **Java** com AWS Lambda
- **Amazon S3** para armazenamento
- **Jackson** para serialização JSON
- **Lombok** para simplificação de código

---

## 📝 Requisitos

- Configurar o nome do bucket no seguinte trecho:
  ```java
  PutObjectRequest request = PutObjectRequest.builder()
      .bucket("SEU_BUCKET_NAME")
      .key(shortUrlCode + ".json")
      .build();
  ```
- Ter as dependências necessárias para o projeto:
  - software.amazon.awssdk
  - com.fasterxml.jackson.databind
  - lombok

---

## 🗂️ Estrutura do Código
- Main: Classe principal que processa a solicitação e salva os dados no S3.
- UrlData: Classe que representa os dados da URL.

---

## 📥 Exemplo de Entrada
  ```json
  {
    "body": "{\"OriginalUrl\": \"https://example.com\", \"expirationTime\": \"3600\"}"
  }
  ```

## 📥 Exemplo de Saída
  ```json
  {
    "code": "a1b2c3d4"
  }
  ```
--- 
## 🛠️ Como Executar
1. Configure as permissões necessárias na AWS para Lambda e S3.
2. Compile o código e faça o deploy na AWS Lambda.
3. Faça chamadas HTTP para o Lambda com o JSON no corpo da requisição.
