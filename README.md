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
 - **yarn add eslint -D**
	 > Dependência necessária para padronizar o código da aplicação. Após a instalação do eslint, siga para a sessão de configurações para concluir a instalação do eslint.
- **yarn add prettier eslint-config-prettier eslint-plugin-prettier -D**
    > Também são dependências necessárias para padronização do código da aplicação, após o término da instalação siga para a sessão de configurações do **prettier**.

## Criando estrutura de pastas
- Criar pasta **src** na raiz do projeto
	> Pasta contento todo o código fonte da nossa aplicação.
	- Dentro da pasta **src** serão criandos os seguintes arquivos e pastas:
		- app.js
			>Classe principal para a inicialização da aplicação.
		- routes.js
			>Arquivo que conterá todas as rotas da aplicação.
		- server.js
			>Arquivo que vai conter  a inicialização e as informações do servidor.
	- Ainda dentro da pasta **src** vamos criar a seguinte estrutura de pastas.
		- config
			>Pasta que irá conter a maioria das configurações da nossa aplicação.
		- database
			> Dentro da pasta database vamos criar o arquivo **index.js** que será o arquivo de inicialização da nossa conexão com o banco de dados, também teremos as pastas de **migrations** e **seeds**.
		- app
			> A pasta **app** conterá toda regra de negócio da nossa aplicação, dentro dessa pasta vamos criar as pastas **controllers**, **models** e **middlewares**.

## Configurações
- **sucrase**
	> 1. Criar arquivo de configuração do **nodemon** na raiz do projeto, o arquivo deve se chamar **nodemon.json**.
	> 2. Dentro desse arquivo, deve ser inserido a linha abaixo.
		> **{ "execMap" :  { "js":  "sucrase-node" } }**
		> Com este comando eu estou dizendo que ao executar o nodemon, o node deverá utilizar o sucrase-node ao invés do nodemon.
	> 3. Dentro do arquivo package.json deve ser inserida a linha abaixo.
		> **"scripts" : { "dev":  "nodemon src/server.js" }**
	>4. Executar o comando "**yarn dev**".
	
- **eslint**
	> 1. Para iniciar a configuração do eslint basta executar o comento **yarn eslint --init**
	> 2. Selecionar as opções:
    
		- To check syntax, find problems, and enforce code style
        
		- JavaScript modules (import/export)
        
		- None of these
        
		- Utilizando a barra de espaço, desmarcar a opção do browser e marcar a opção node.
        
		- Use a popular style guide
        
		- Airbnb (https://github.com/airbnb/javascript)
        
		- JavaScript
        
		- Aceitar a instalação das dependências do Airbnb.
        
	> 3. Deletar arquivo *package-lock.json* e executar o comando **yarn**.
	> 4. No VSCode abrir a aba de extensões e instalar a extensão do ESLint
	> 5. Abrir o arquivo de configuração do VSCode e modificar o valor do atributo "**eslint.autoFixOnSave**" para **true**.
	> 6. Também modificar o atributo "**eslint.validate**" informando que o javascript, javascriptreact, typescript e typescriptreact terão o atributo "**autofix**" com o valor true para forçar o eslint a fazer o autofix.
	> 7. Dentro do arquivo "**.eslintrc.js**" modificar o atributo **rules** adicionando os valores "**class-methods-use-this**": "**off**", "**no-param-reassign**":  "**off**", **camelcase**:  "**off**", "**no-unused-vars**": **["error", { argsIgnorePattern:  "next" }]**

- **prettier**
	> 1. Após instalar o prettier, vamos editar o arquivo "**.eslintrc.js**".
    
		Transformar o atributo extends em um array com o valor ["airbnb-base", "prettier"].
        
		Adicionar uma nova propriedade chamada plugins com o valor ["prettier"].
        
		Dentro da propriedade rules, adicionar a linha "prettier/prettier":  "error".
        
	> 2. Na raiz do projeto, criar o arquivo json de configuração do prettier chamado **.prettierrc**, e adicionar o conteúdo **{ "singleQuote":  true, "trailingComma":  es5" }**. Com este arquivo estamos sobrescrevendo algumas regras do prettier que são definidas por padrão.

- **editorConfig**

    O editorConfig é um plugin do VSCode que tem por objetivo manter o padrão de código configurado inicialmente para todas as interfaces de desenvolvimento.

	> 1. Após instalar o plugin no VSCode, clique com o botão direito do mouse na raiz do projeto e em seguida clique em **Generate .editorConfig**.
	> 2. Após o VSCode criar o arquivo de configuração do editorConfig, modifique os valores dos atributos *trim_trailing_whitespace* e *insert_final_newline* para **true**.
