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
  
    


## 📸 Telas da aplicação e configuração do Azure 
      na pasta arquivos

