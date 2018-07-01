# npm cook book

### Concepts

**module** is a single js file that has an specific functionality.

**package** is a directory with many modules and a _package.json_ file. This file holds 
metadata about the package.

**package.json** is the heart of the npm ecosystem and is responsible for holding metadata about the package. It defines things such as the author, modules, version, start script and test script of a package or project. 

### Recipes

**working with starter projects**

clone the stater project from git (In this example we will be using the [react-starter-kit](https://github.com/kriasoft/react-starter-kit) project)  
$ `git clone https://github.com/kriasoft/react-starter-kit.git`

get inside the just cloned repository  
$ `cd react-starter-kit`

install the package  
$ `npm install`

check if there is an entry in the _package.json_ file for a start script, if yes, run it  
$ `npm start`

additionally, check if there is an entry in the _package.json_ file for a test script, if yes, run it  
$ `npm test`

**Getting help**

_help_ is the command responsible for giving help about the npm usage.
To show an overview on _help_ type  
$ `npm -h`

to get help about install or any other npm command type  
$ `npm install -h` 

to show a command's complete reference, in this example install, type  
$ `npm help install`  

to find all npm commands related to a specific subject, in this case _"documentation"_, type  
$ `npm help-search documentation`  
The result of the previous command will be a list of `npm help` calls, run any of them in the terminal.

**Shorthands**

npm can be used with a bunch of different shorthands. For example, $ `npm install` can run in this way
`npm i` since _i_ is a shorhand for _install_.

To find more about npm shorthands access [shorthands-and-other-cli-niceties](https://docs.npmjs.com/misc/config#shorthands-and-other-cli-niceties).


**Creating a package.json**

to create a package.json answering manually the questions run  
$ `npm init`

to create a package.json giving automatically default answers for the questions  
$ `npm init -y`


