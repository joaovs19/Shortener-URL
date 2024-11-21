# Shortener-URL  

Um encurtador de URLs totalmente **serverless** construído com tecnologias da **AWS** e **Java 17**. Esta aplicação permite criar, armazenar e acessar URLs encurtadas, incluindo a funcionalidade de expiração de links.  

## 🛠️ Tecnologias Utilizadas  
- **Java 17**: Implementação da lógica de negócios.  
- **AWS Lambda**: Funções serverless para processamento backend.  
- **API Gateway**: Criação e gestão de endpoints RESTful.  
- **S3**: Armazenamento seguro das URLs em formato JSON.  
- **Insomnia**: Testes de APIs e configuração do tempo de expiração das URLs.  

---

## 🚀 Funcionalidades  
1. **Encurtamento de URL**:  
   - Envie uma URL para encurtar através do endpoint `/codigoGerado`.  
   - Informe um tempo de expiração (em segundos) junto à URL.  

2. **Redirecionamento**:  
   - Acesse a URL encurtada gerada para ser redirecionado ao link original.  
   - Caso o tempo de expiração tenha passado, uma mensagem de "Link Expirado" será exibida.  

---

## 🎯 Como Funciona  

### Fluxo da Aplicação  
1️⃣ O usuário envia uma **URL original** e o **tempo de expiração** através do **endpoint `/codigoGerado`**.  
   - Exemplo de corpo da requisição:  
     ```json
     {
       "url": "https://meusite.com",
       "expiration": 3600
     }
     ```  

2️⃣ Uma **função Lambda** processa a requisição:  
   - Gera um código único para a URL encurtada.  
   - Armazena os dados no **AWS S3** em formato JSON.  

3️⃣ Para acessar a URL encurtada:  
   - O usuário insere o código no endpoint, que ativa outra **função Lambda**.  
   - Essa função verifica se o tempo de expiração foi atingido.  
     - Se válido, redireciona para a URL original.  
     - Caso contrário, retorna uma mensagem de "Link Expirado".  

---

## 🔗 Link da API  
Acesse a API do projeto no seguinte endereço:  
**[URL da API](https://api-seuprojeto.com](https://nez82ioq87.execute-api.eu-north-1.amazonaws.com))**  

## 🔧 Configuração do Projeto  

### Pré-requisitos  
- **Conta na AWS** com permissões para Lambda, API Gateway e S3.  
- **JDK 17+** instalado.  
- **Insomnia** ou ferramenta similar para testes de API.  

### Passos para Configurar  
1. Clone este repositório:  
   ```bash
   git clone https://github.com/seu-usuario/Shortener-URL.git
