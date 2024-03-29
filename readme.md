# Criar pasta para a aplicação
mkdir projetoBackend

# Acessar pasta
cd projetoBackend

# Criar arquivo para documentar projeto
### touch readme.md
Arquivos com extensão .md, significam markdown, de marcação de texto. A ideia é marcar um texto informando o que é importante, o que é um tópico, o que são links e imagens, sem a necessidade de utilizar marcações mais complexas, como o HTML.

Utilizar este arquivo para descrever as ações executadas, de forma que facilite o entendimento

# Iniciar o gerenciador de pacotes Node
### npm init -y
Deverá ser criado um arquivo package.json na raíz do projeto

Imagem do resultado do comando no terminal

# Instalar os pacotes
### npm i express nodemon dotenv
express: framework web para construção da infraestrutura da API;
nodemon: monitora as mudanças nos arquivos do projeto e reinicia automaticamente o servidor Node;
dotenv: gerencia as variáveis de ambiente dentro do projeto;
A confirmação da instalação dos pacotes pode ser vista na chave 'dependencies' no arquivo package.json, conforme imagem abaixo

# Abrir o VSCode
code .

# Criar arquivo .gitignore
### nano .gitignore
Com o comando nano, podemos criar e editar um arquivo pelo terminal
Ctrl + o: Salvar o arquivo
Enter: Confirmar
Ctrl + x: Fechar o arquivo
Este arquivo é utilizado para ignorar o envio de pastas e arquivos pro gitHub

# Adicionar no arquivo .gitignore o nome da pasta criada após a instalação dos pacotes
### node_modules
Esta pasta node_modules não precisamos enviar pro gitHub, pois pode ser recriada com o comando 'npm install'
# Criar estrutura de arquivos e pastas
mkdir src

# Criar arquivos dentro da pasta src
### touch src/app.js
Arquivo responsável de criar a configuração da API
### touch src/server.js
Arquivo responsável em receber as configurações da aplicação e rodar a API

# Criar pastas dentro da pasta src
### mkdir src/config
Pasta para gerenciar a conexão com o banco de dados
### mkdir src/controllers
Pasta para gerenciar as requisições das rotas e conexão com banco de dados
### mkdir src/routes
Pasta para gerenciar as rotas da API

# Enviar estrutura do projeto para o gitHub
Inicializar o gerenciador de arquivos .git

# 2º Passo: Clonar o projeto do gitHub, criar configuração da API e testar

* Comando clone do git
* Configurar pacotes instalados
* Criar comando para rodar o servidor
* Testar servidor

#### Copiar a url do projeto

* Acessar repositório do projeto no gitHub
* Clicar no botão verde '<> Code'
* Clicar no ícone para copiar a URL, conforme a imagem

#### Clonar o repositório na sua máquina

* Abrir o gitBash em um local do computador
* Digitar o comando 'git clone' junto com a URL do seu repositório


git clone URL_REPOSITORIO

#### Acessar pasta
* Digitar o comando 'cd' e o nome do seu repositório
* cd (change directory): acessar outra pasta

cd NOME_REPOSITORIO

#### Reinstalar os pacotes da aplicação

npm i
* Este comando irá recriar a pasta node_modules no projeto

#### Criar arquivo .env na raiz do projeto
* Este arquivo é utilizada para armazenar as variáveis que serão reutilizadas na aplicação
* Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo
```
nano .env
```

#### Digitar no arquivo .env
```
PORT = 3008
```
* Variável que contém a porta que o servidor estará rodando
* Esta arquivo .env não enviamos pro gitHub, pois contém informações sensíveis do sistema

#### Adicionar arquivo .env no .gitignore
```
nano .gitignore

```
.env
```

#### Abrir o VSCode
```
code .
```

#### Criar arquivo de exemplo para para as variáveis necessárias da aplicação
* Como não enviamos o arquivo .env para o gitHub, precisamos criar o exemplo das variáveis necessárias da aplicação
* Este arquivo conterá apenas as variáveis, sem os valores correspondentes
```
nano .env.example
```

#### Adicionar no arquivo .env.example
```
PORT = 
```


#### Abrir o arquivo app.js e digitar o código
* Importar o pacote express (servidor)
```
const express = require('express');
```

* Importar o pacote dotenv, gerenciador de variáveis de ambiente
```
const dotenv = require('dotenv').config();
```

* Instanciar o express na variável app
```
const app = express();
```

* Setar a porta do servidor a partir do arquivo .env
* O operador condicional '||' significa 'OU', caso não tenha a variável PORT, será utilizado o valor '3333'
```
app.set('port', process.env.PORT || 3333);
```

* Exportar as configurações na variável app
```
module.exports = app;
```

#### Abrir o arquivo server.js e digitar os códigos
* Importar o arquivo app
```
const app = require('./app');
```

* Importar a porta do servidor
```
const port = app.get('port');
```

* Testar API com a função listen
* 1º parâmetro: passamos a porta do servidor
* 2º parâmetro: arrow function para retornar um console informando a porta que está rodando o servidor
```
app.listen(port, () => {
    console.log(`Running on port ${ port }!`);
});
```


## Depois de configurar os pacotes e o teste do servidor, vamos criar o comando para executar

#### Abrir o arquivo package.json e alterar a chave 'scripts'
* Substituir o comando 'test' pelo comando 'start' na linha 7
```
"start":"nodemon src/server.js"
```


#### Rodar o comando no termial com gitBash
```
npm run start
```

#### Atualizar projeto no gitHub
* Adicionar todos arquivos ao versionamento
```
git add .
```

* Salvar projeto e escrever comentário sobre o processo realizado
```
git commit -m 'configuração do projeto'
```

* Enviar os arquivos atualizados para o gitHub
```
git push
```

### Atualize a página no gitHub e verifique se os arquivos foram atualizados 
* Com o projeto no servidor remoto podemos remover os arquivos na nossa máquina
```
cd ..
```
* Comando para acessar uma pasta anterior
* Fechar o VSCode com o projeto aberto

```
rm -rf projetoBackend
```
* rm (remove): comando utilizado para apagar arquivo
* -r (recursive): apaga pastas e subpastas de forma recursiva
* -f (force): não pergunta confirmações
* projetoBackend: nome da pasta que contem os arquivos da aplicação