# npm cookbook

### Concepts

**module** is a single js file that has a specific functionality.

**package** is a directory with many modules and a _package.json_ file. This file holds 
metadata about the package.

**package.json** is the heart of the npm ecosystem and is responsible for holding metadata about the package. It defines things such as the author, modules, version, start script and test script of a package or project. 

**global packages** are packages that can be run in the command line. Also, they are available for every package in the machine without the need to be reinstalled in each package.  

**extraneous package** According to the [npm website](https://docs.npmjs.com/cli/prune), extraneous packages are packages that are not listed on the parent package's dependencies list.

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

to get help about _install_ or any other npm command type  
$ `npm install -h` 

to show a command's complete reference type  
$ `npm help install`  

to find all npm commands related to a specific subject, in this case _"documentation"_, type  
$ `npm help-search documentation`  
The result of the previous command will be a list of `npm help` calls, run any of them in the terminal.

**shorthands**

npm can be used with a bunch of different shorthands. For example, $ `npm install` is the same as
`npm i` since _i_ is a shorhand for _install_.

To find more about npm shorthands access [shorthands-and-other-cli-niceties](https://docs.npmjs.com/misc/config#shorthands-and-other-cli-niceties).

**creating a package.json**

to create a package.json answering manually the questions run  
$ `npm init`

to create a package.json giving default answers for the questions run  
$ `npm init -y`

You can set your own default answers. This way, every time you run $ `npm init`, you don't
have to give the same answers again. Run the following example to set _danilooa_ as the default author through the property _init-author-name_  
$ `npm set init-author-name 'danilooa'`  
To check the available properties access [https://docs.npmjs.com/misc/config](https://docs.npmjs.com/misc/config) and search for _'init-'_.

To check a default answer, in this example the default author name, run  
$ `npm get init-author-name`

To remove a default answer, in this example the default author name, run  
$ `npm config delete init-author-name`  

To check the current default answers in a Linux distribution access the file _.npmrc_. This file is created when the first answer is set and will be inside the user home.  
$ `less ~/.npmrc`

**installing packages**

To install a package, such as _vue_, run  
$ `npm i vue`
It is important to notice that the package's name, in this case _vue_, must be the _name_ written in the _package.json_ file of the desired package.

To install a package that will run in production run  
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

To install a package from a [github](https://github.com/) repository, just use the repository's url. It is important to notice that the repository must have a _package.json_ file. Additionally, this idea works with urls of any structure that has a _package.json_ file. Here comes a example  
$ `npm i https://github.com/vuejs/vue`

To install a package from a [gist](https://gist.github.com/) respository you must have the hash of the repository, the hash is that strange character sequence in the repository's url. It is important to remember that the gist repository must have a _package.json_ file. Here comes a example where _ab2bdbe3_ is the repository's hash  
$ `npm i gist:ab2bdbe3` 

To install a package from a folder or network directory you should guarantee that the folder has a _package.json_ file and run  
$ `npm i /anyPath/.../anyDirectory`  
The previous example will put a reference like the above in the _package.json_ file
```  
{  
...  
    "dependencies": {  
        ...  
            "the_package_name": "/anyPath/.../anyDirectory",  
        ...  
    }  
...  
}  
```  


**installing a specific package's version**

Fisrt, understand how _semantic versioning_ works clicking [here](https://docs.npmjs.com/getting-started/semantic-versioning).

For any of the following examples, if the flag `--save` is missing, the changes will not be reflected in the _package.json_ file. Additionally, if the flag `--save-exact` is missing, the package version imported will be equal or newer than the given version.

To install the last version of a package, in this case _vue_, run  
$ `npm install vue`

To install a specific path run  
$ `npm install vue@1.2.1 --save --save-exact`

To install the newest patch of a minor release run  
$ `npm install vue@1.2`

To install the newest minor release of a major release run  
$ `npm install vue@1`

To install the newest _vue_ minor release that is newer than 1.1 and older than 1.9 run  
$ `npm install vue@">1.1 <1.9"`

To install a package's beta version first edit the _package.json_ file like this   
```  
{  
...  
    "dependencies": {  
        ...  
            "any_package": "2.0.0-beta.0",    
        ...  
    }  
...  
}  
```  
Then run  
$ `npm install any_package@beta`    

**changing packages' versions **

1. remove the current package's version without changing the _package.json_ file  
$ `npm rm vue`  

2. edit the _package.json_ file in one of the following ways:  
    2.1 to get the latest major release  
    ```  
    {  
    ...  
        "dependencies": {  
            ...  
                "vue": "*",  
            ...  
        }  
    ...  
    }  
    ```
    
    2.2 to get the latest minor release, in this case the latest minor release of version _1_   
    ```  
    {  
    ...  
        "dependencies": {  
            ...  
                "vue": "^1.3.0",  
            ...  
        }  
    ...  
    }  
    ```
    
    2.3 to get the latest patch release, in this case the latest patch release of version _1.3_   
    ```  
    {  
    ...  
        "dependencies": {  
            ...  
                "vue": "~1.3.0",  
            ...  
        }  
    ...  
    }  
    ``` 
    
    2.4 to get exactly the version 1.3.2    
    ```  
    {  
    ...  
        "dependencies": {  
            ...  
                "vue": "1.3.2",  
            ...  
        }  
    ...  
    }  
    ```  
3. run the _install_ command  
$ `npm i`

**updating packages**

To get the latest versions of all the packages  
$ `npm update`  

To get the latest versions of the dev packages  
$ `npm update --dev`

To get the latest versions of the prod packages  
$ `npm update --prod`

To get the latest version of one specific package, in this case _vue_, run  
$ `npm update vue`

To get the latest version of the global packages  
$ `npm update -g`  

**listing installed packages**

If you have installed a package, it will be inside the directory _node_modules_ which lies in your project's home directory.
So, to list the packages you can run  
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

**finding a package**

If you need a package to solve a problem, go to [https://www.npmjs.com/](https://www.npmjs.com/), type the subject of your interest in the search box and hit the search button.  

To get _npm_ information about a package in _json_ format, go to your browser and type [http://registry.npmjs.org/angular](http://registry.npmjs.org/angular). Notice that in this example we are getting information about _angular_.  

If you know exactly the package that you are looking for, for example _angular_, you can go straight to [https://www.npmjs.com/angular](https://www.npmjs.com/angular)  

To access the repository of a specific package, in this case _angular_, run  
$ `npm repo angular`

**removing unnecessary/extraneous packages**  

First, check if there are extraneous packages by running  
$ `npm list --depth 0` 

If some package was listed with the _extraneous_ flag, run  
$ `npm prune`  

**running scripts**

Any _package.json_ file has a section like the following  
```  
{  
...  
    "scripts": {  
        ...  
            "start": "node running_any_js_file.js",  
        ...  
    }  
...  
}  
``` 
Based on the previous example, now the command $ `node running_any_js_file.js` can be run by _npm_ through its script indentifier like this  
$ `node start`

As _start_ in the previous example there are other default scripts idetifiers that you can check [here](https://docs.npmjs.com/misc/scripts). Also, a custom script identifier can be used, for example `do_something`,  and then _npm_ can run it just like it did with _start_. Here comes an example
```
{  
...  
    "scripts": {  
        ...  
           "do_something": "echo 'doing something`",  
        ...  
    }  
...  
}  
```

$ `npm do_something`  

**publishing a package on npm repository**  

1. Go to [https://www.npmjs.com/signup](https://www.npmjs.com/signup) and create an account and verify your email
2. Access you terminal and run $ `npm adduser` to add the account you just created  
3. Get inside the package's directory
4. Turn the package's directory into a git repository by running $ `git init`   
5. Go to [github](https://github.com/) and create a repository  
6. Define the origin of the local _git_ repository as the github repository by running $ `git remote add origin https://github.com/your_git_user_name/the_repository_created_on_github` 
7. Init the _npm_ package by running $ `npm init`. Answer the questions carrefully since them will be publish on _npm_  
8. Change the package files as desired  
9. Commit all the changes by running
    1. $ `git add .`
    2. $ `git commit -m "any comment"`
    3. $ `git push --set-upstream origin master`
10. Effectively publish you package on _npm_ by running $ `npm publish`
11. Tag your package by running
    1. $ `git tag the_version_from_the_package_json_file`
    2. $ `git push --tag`  
    3. Check if the tag was marked as a relase on _github_ by accessing `https://github.com/your_git_user_name/the_repository_created_on_github/releases`

**updating a package on npm repository**

1. Get into the package's directory
2. Change the package as desired
3. Create a commit by running
    1. $ `git add .`
    2. $ `git commit -m "any message"`
3. Use the rules described [here](https://docs.npmjs.com/getting-started/semantic-versioning) to define what kind of change was made
4. Run one of the following commands according to the kind of change made
    1. For patch releases run $ `npm version patch`
    2. For minor releases run $ `npm version minor`
    3. For major releases run $ `npm version major` 
5. Run $ `git push --tag` to send the new tag to _github_  
6. Run $ `git push` to send the change to _github_
7. Finally, run $ `npm publish` to update the package on _npm_

**releasing a beta version**

1. Get into the package's directory
2. Change the package as desired
3. If it is the first beta version, postfix the version in the _package.json_ file with `-beta.0` otherwise replace `0` with any other number. For example, if it is the first `v2.0.0` beta version, it will be   `v2.0.0-beta.0`, otherwise it will be something like `v2.0.0-beta.1`
4. Create a commit by running
    1. $ `git add .`
    2. $ `git commit -m "any message"`
5. Run one of the following commands according to the kind of change made
    1. For patch releases run $ `npm version patch`
    2. For minor releases run $ `npm version minor`
    3. For major releases run $ `npm version major` 
6. Run $ `git tag the_version_as_in_the_package_file`  
7. Run $ `git push --tag beta`
9. Run $ `git push`
8. Finally, run $ `npm publish`
