# npm cookbook

### Concepts

**module** is a single js file that has an specific functionality.

**package** is a directory with many modules and a _package.json_ file. This file holds 
metadata about the package.

**package.json** is the heart of the npm ecosystem and is responsible for holding metadata about the package. It defines things such as the author, modules, version, start script and test script of a package or project. 

**global packages** are packages that can be run in the command line. Also, they are available for every package in the machine without the need to be installed in each package.

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

**getting help**

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

**creating a package.json**

to create a package.json answering manually the questions run  
$ `npm init`

to create a package.json giving default answers for the questions run  
$ `npm init -y`

You can set your own default answers. This way, every time you run $ `npm init` you don't
have to give the same answers over and over. Run the following example to set _danilooa_ as the default author through the property _init-author-name_  
$ `npm set init-author-name 'danilooa'`  
To check the available properties access [https://docs.npmjs.com/misc/config](https://docs.npmjs.com/misc/config) and search for _'init-'_.

To check a default answer, in this example the author name, run  
$ `npm get init-author-name`

To remove a default answer, in this example the author name, run  
$ `npm config delete init-author-name`  

To check the current default answers in a Linux distribution access the file _.npmrc_. This file is created when the first answer is set and will be inside in the user home.  
$ `less ~/.npmrc`

**installing packages**

To install a package, in this example _vue_, run  
$ `npm i vue`
It is important to notice that the name of the package, in this case _vue_, must be the _name_ written in the _package.json_ file of the package being installed.

To install a package that will run in production along with your application run  
$ `npm i vue -S`  
This will also write the version of the installed package inside your _package.json_ as the following  
```  
{  
...  
    "dependencies": {  
        ...  
            "vue": "^2.5.16",  
        ...  
    }  
...  
}  
```  

To install a package that will be used only during development time run  
$ `npm i opn-cli -D`  

```  
{  
...  
    "devDependencies": {  
        ...  
            "opn-cli": "^3.1.0",  
        ...  
    }  
...  
}  
```  

To install a global package, in this case _karma_, run  
$ `npm i karma -g`  

**installing a specific version of a package**

Fisrt, understand how _semantic versioning_ works clicking [here](https://docs.npmjs.com/getting-started/semantic-versioning).

For any of the following examples, if the flag `--save` is missing, the changes will not be reflected in the _package.json_ file. Additionally, if the flag `--save-exact` is missing, the package version imported will be equal or newer than the given version.

To install the last version of a package, in this case _vue_,  run
$ `npm install vue`

To install a specific path run  
$ `npm install vue@1.2.1 --save --save-exact`

To install the newest patch of a minor release run  
$ `npm install vue@1.2`

To install the newest minor release of a major release run  
$ `npm install vue@1`

To install the newest _vue_ minor release that is newer than 1.1 and older than 1.9 run  
$ `npm install vue@">1.1 <1.9"`

**listing installed packages**

If you have installed a package, it will be inside the directory _node_modules_ in your package home directory.
So, to list the packages run  
$ `ls ./node_modules/`  

To show the dependency tree of your package run  
$ `npm list`  

To limit the depth of the dependency tree, in this case to 1, run  
$ `npm list --depth 1`  

To show the global packages run  
$ `npm list --global true`  

To show the package along with their details run  
$ `npm list --long true`  

To show the dependency tree in _json_ format run  
$ `npm list --json true`  

**uninstalling packages**  

To uninstall a package, in this case _vue_, run any of the following commands  
$ `npm uninstall vue --save`  
$ `npm rm vue`  
$ `npm un vue`  
$ `npm r vue`  

To uninstall a global package just add the flag `g` to the previous commands, for example  
$ `npm r vue -g`
