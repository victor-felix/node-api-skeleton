# Criando uma estrutura padrão para uma API com Node

Oi, neste tutorial vamos criar uma estrutura padrão para iniciar qualquer **API** em **Node**.

## Iniciando projeto

- **yarn init -y**
	> Comando utilizado para criar o arquivo **package.json**.

## Dependências
- **yarn add express**
	> Comando utilizado para baixar a dependência do express que será utilizado para iniciar o servidor do projeto.

## Dependências de desenvolvimento
- **yarn add sucrase -D**
	> Dependência alternativa ao Babel que dá agilidade ao desenvolvimento. PS: Ao instalar  o **sucrase**, podemos utilizar a sintaxe de **import** ao invés de **require**. Após instalar esta dependência siga para a sessão de configurações para configurar o sucrase.
- **yarn add nodemon -D**
 	> Instale este dependência para habilitar um servidor que reinicia automaticamente sempre que houver alguma alteração no código.
 - **yarn add eslint**
	 > Dependência necessária para padronizar o código da aplicação. Após a instalação do eslint, siga para a sessão de configurações para concluir a instalação do eslint.

## Criando estrutura de pastas
- Criar pasta **src** na raiz do projeto
	> Pasta contento todo o código fonte da nossa aplicação.
	- Dentro da pasta **src** serão criandos os seguintes arquivos:
		- app.js
			>Classe principal para a inicialização da aplicação.
		- routes.js
			>Arquivo que conterá todas as rotas da aplicação.
		- server.js
			>Arquivo que vai conter  a inicialização e as informações do servidor.

## Configurações
- **sucrase**
  1. Criar arquivo de configuração do **nodemon** na raiz do projeto, o arquivo deve se chamar **nodemon.json**.
	2. Dentro desse arquivo, deve ser inserido a linha abaixo.
	> **{ "execMap" :  { "js":  "sucrase-node" } }**
	> Com este comando eu estou dizendo que ao executar o nodemon, o node deverá utilizar o sucrase-node ao invés do nodemon.
	3. Dentro do arquivo package.json deve ser inserida a linha abaixo.
	> **"scripts" : { "dev":  "nodemon src/server.js" }**
	4. Executar o comando "**yarn dev**".
	
- **eslint**
	1. Para iniciar a configuração do eslint basta executar o comento **yarn eslint --init**
	2. Selecionar as opções:
  
	2.1 *To check syntax, find problems, and enforce code style*
  
	2.2 *JavaScript modules (import/export)*
  
	2.3 *None of these*
  
	2.4 Utilizando a barra de espaço, desmarcar a opção do *browser* e marcar a opção **node**.
  
	2.5 Use a popular style guide
  
	2.6 Airbnb (https://github.com/airbnb/javascript)
  
	2.7 JavaScript
  
	2.8 Aceitar a instalação das dependências do Airbnb.
  
	2.9 Deletar arquivo *package-lock.json* e executar o comando **yarn**.
