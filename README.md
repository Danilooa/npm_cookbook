# npm cook book

### Concepts

**module** is a single js file that has an specific functionality.

**package** is a directory with many modules and a _package.json_ file. This file holds 
metadata about the package.

### Recipes

**working with starter projects**

clone the stater project from git (In this example we will be using the [react-starter-kit](https://github.com/kriasoft/react-starter-kit) project)  
$ `git clone https://github.com/kriasoft/react-starter-kit.git`

move inside the just cloned repository  
$ `cd react-starter-kit`

install the package  
$ `npm install`

check if there is an entry in the _package.json_ file for a start script, if yes, run it  
$ `npm start`

additionally, check if there is an entry in the _package.json_ file for a test script, if yes, run it  
$ `npm test`
