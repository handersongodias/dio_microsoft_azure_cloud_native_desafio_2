# Desafio DIO com Microsoft Azure Cloud Native
# Cria um blog , hospedar na Azure , criar imagem docker e subir para o ACR

Este projeto foi desenvolvido com docker , azure, azure acr, que permite executar um blog com container , criando uma imagem e depois executando

---

## 🚀 Funcionalidades

-  Cadastrar assuntos no Blog
 
---

## 🧰 Tecnologias e Bibliotecas

- Visual Studio Code
- Azure-cli
- Docker Desktop

---

## 📦 Instalação

### 1. Crie uma pasta local para o projeto que sera utilizada no visual code
      crie o arquivo dockerfile
      crie mais uma pasta chamada Blog
      cria mais uma pasta chamada Html dentro da pasta Blog
      dentro da pasta Html crie 3 arquivos create-post.html, index.html, post-detail.html
      
### 2. Crie os arquivos conforme etapa 1
    html/ -> o blog
    blog/ -> arquivos de configuração do ambiente
    dockerfile -> executa todos os scripts do projeto gerando a imagem no docker file
    
    
### 3. Instale as bibliotecas
    faça o download do Azure-cli e instale
    faça o download do Docker desktop e instale
      
### 4. Execute os comandos no terminal
    Criar a imagem:
     docker build -t nome-da-imagem-do-blog:latest .
    Testar se esta funcionando , acesse no browser http://localhost apos executar esse codigo
     docker run -d -p 80:80 nome-da-imagem-do-blog:latest 
    
### 5. Os comandos de configuração e implantação no Azure
  #### Comando para criar uma imagem do blog
    docker build -t nomdaimagem:latest .

  ### Comando para executar a imagem do blog
    docker run -d -p 80:80 nomdaimagem:latest 
---
### Depois de criar a imagem e executar o container, vamos subir a imagem para o Azure Container Registry (ACR) e criar um Container App.
   #### Para isso, siga os passos abaixo:
   #### Instale o Azure CLI
   #### https://docs.microsoft.com/pt-br/cli/azure/install-azure-cli

### efetue o login no azure
   #### Use o Azure CLI to log in
    az login

### Criar o resource group
    az group create --name nomedorgroup --location eastus

### Criar Container Registry
    az acr create --resource-group nomedorgroup --name nomedoacr --sku Basic

### Efetue o login no azure container registry
    az acr login --name nomedoacr

### Crie uma Tag para a imagem
    docker tag nomedaimagem:latest nomedoacr.azurecr.io/nomedaimagem:latest


### Push da imagem no Azure Container Registry
    docker push nomedoacr.azurecr.io/nomedaimagem:latest

### Criar variaveis de ambiente para o container app
    az containerapp env create  --name nomedavariavel-env --resource-group nomedorgroup --location eastus 

### Criar o container app 
### coloque o codigo em uma linha só, caso esteja usando o terminal do windows
### ou quebre em várias linhas com a barra invertida no final de cada linha, caso esteja usando o terminal do Linux ou MacOS.

    az containerapp create --name nomedoapp-app 
      --resource-group nomedorgroup 
      --image nomedoacr.azurecr.io/nomedaimagem:latest 
      --environment nomedavariavel-env 
      --target-port 80 --ingress external 
      --registry-username nomedousarionocontainer 
      --registry-password informarasenhadocontainer 
      --registry-server nomedoacr.azurecr.io
    
### Caso apresente o erro abaixo 
    Subscription xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is not registered for the Microsoft.OperationalInsights resource provider.  
    
### Execute o comando para registrar o resource provider do log analytics, e depois execute novamente o comando acima para criar o container app
     az provider register -n Microsoft.OperationalInsights --wait

### Apos criar o container app, você pode acessar o endereço do app no navegador.
    O endereço será algo como: https://nomedoapp-app.nomedorgroup.eastus.azurecontainerapps.io/ ,que estara no log do terminal. na propriedade "latestRevisionFqdn"


## 📸 Telas da aplicação e configuração do Azure 
      na pasta arquivos

