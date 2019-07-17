# Creating a default structure for an API in NodeJS

Hi, in this tutorial we will create a default structure for any **API** project using **NodeJS**.

## Starting the project

- **yarn init -y**
    > This command will create the **package.json** file.

## Dependencies
- **yarn add express**
	> Using this command for install the server dependency.

## Dev Dependencies
- **yarn add sucrase -D**
    > An alternative to Babel, this dependency give agility in development. After install the **sucrase**, we can use the syntax **import**, better than the syntax **require**. In the section **Configuration** you can complete the instalation.
- **yarn add nodemon -D**
    > Install this dependency for the server show updates automatically in the browser.
 - **yarn add eslint -D**
     > This dependency is necessary to define default rules of codification. See the section **Configuration** for complete the installation.
- **yarn add prettier eslint-config-prettier eslint-plugin-prettier -D**
    > This dependencies are necessary do define default rules of codification too. Don't forget of see the section **Configuration** to complete the installation.

## Creating the folder structure
- Create the folder **src** in the root folder.
    > This folder have all the code of your application.
    - Inside the folder **src** you will create the followings files and folders:
		- app.js
			> Class using for start the application.
		- routes.js
            > File with all routes of the API.
		- server.js
            > Create this file to define information of the server.
    - Still inside the folder **src** we create the following folder structure.
		- config
            > Folder necessary to create all the configuration of the application.
		- database
            > Inside this folder, we include the file necessary to start the database of the application and the folders related with database such as **Migrations** and **Seeds**.
		- app
            > The folder **app** will contains all the business rules of the your application, inside this folder you wil create the following folders **Controllers**, **Models** and **Middlewares**.

## Configurations
- **sucrase**
    > 1. Create the file of configuration  of the dependency **nodemon** in the root folder, this file name is **nodemon.json**.
    > 2. Inside this file, insert the following line.
        > **{ "execMap" :  { "js":  "sucrase-node" } }**
        > Use this instructions to start the server with **sucrade-node**.
    > 3. Inside the package.json file, you insert the following instruction in the section **scripts**.
        > **{ "dev":  "nodemon src/server.js" }**
    > 4. Execute the command "**yarn dev**" to start the server.
	
- **eslint**
    > 1. To start the ESLINT configuration just execute the command **yarn eslint --init**
	> 2. Select the following options:
    
		- To check syntax, find problems, and enforce code style
        
		- JavaScript modules (import/export)
        
		- None of these
        
		- Using the space bar to unmark the option "browser" and mark the option "node".
        
		- Use a popular style guide
        
		- Airbnb (https://github.com/airbnb/javascript)
        
		- JavaScript
        
		- Accept the installation of the dependencies of Airbnb.
        
	> 3. Delete the file *package-lock.json* and execute the command **yarn**.
	> 4. In the IDE VSCode, open the extensions and install the extension of ESLint.
    > 5. Open the file of configuration of the VSCode and update for **true** the value of the attribute "**eslint.autoFixOnSave**".
	> 6. Update the attribute "**eslint.validate**" informing that the javascript,javascriptreact, typescript and typescriptreact will have the attribute "**autofix**" with the value **true**.
	> 7. Inside the file "**.eslintrc.js**" update the attribute **rules** adding the values "**class-methods-use-this**": "**off**", "**no-param-reassign**":  "**off**", **camelcase**:  "**off**", "**no-unused-vars**": **["error", { argsIgnorePattern:  "next" }]**

- **prettier**
	> 1. After install the prettier, you will edit the file "**.eslintrc.js**".
    
		Transform the attribute "extends" to an array with the values ["airbnb-base", "prettier"].
        
		Create or edit the attribute "plugins" and add the value ["prettier"].
        
		Inside the array "rules", add the value the following value: "prettier/prettier":  "error".
        
	> 2. In the root folder, create the file of configuration of the prettier called **.prettierrc**. This file will contains the following instruction: **{ "singleQuote":  true, "trailingComma":  es5" }**. This instruction override some rules of te prettier.

- **editorConfig**

    The editConfig is a plugin using for the IDE that maintain the rules of code configuration for all developers that work in this project.

	> 1. After install the plugin, click on the button right of the mouse in the root folder of the project and select the option **Generate .editorConfig** to create the editorConfig file.
	> 2. Finally you will update the values *trim_trailing_whitespace* e *insert_final_newline* for **true**.
