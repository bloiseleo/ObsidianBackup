The main build tool used in the javascript ecosystem is called Node Package Manager.  This build tool is installed alongside nodejs when you install it.
## Package
A package is a bunch of related code that aims to do only one thing. In this way, the code can focus on doing something really well. This package is stored in the cloud and, if another application wants to use this code, it can simply download and use this package of code. 

In order to do these stuff, javascript uses the `node package manager`. It will be responsible to manage, download and organize the packages that your applications needs.
### Package Repository
In order to download the packages, you will need to download these packages from somewhere else. The javascript package repository is called `NPM JS Repository`. It will store the packages and make them available for downloading and usage.
## Kinds of Dependencies
There are two kinds of dependencies:
- Pure Dependency
- Development Dependency
The pure dependency, also called as dependency, is something that your application needs to run. If it's removed , the entire application will stop functioning. The development dependency is a dependency only needed for development.
In the `package.json`file, you will find those kinds of dependencies in two separated sections:
```
{
	"dependencies": {
		//...
	},
	"devDependencies": {
		//...
	}
}
```
### Command Line
In order to install a node js package, you can use the command: `npm install <package-name>`. It will download and install the dependencies needed. This way you're installing a pure dependency. So, it will appear in the `dependencies` object. Besides, it will have a semantic versioning to determine what version is being used. For example:
```
{
  "name": "nodejslearn",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
    "chalk": "^5.3.0"
  }
}
```
The `chalk` dependency is installed as pure dependency. Besides, it will always install a version that is bigger or equal to 5.3.0. The files of the package are stored inside the `node_modules` folder. IT WILL NEVER BE VERSIONED, because you can reinstall all dependencies simply using the `npm install` command.

> When you install your dependencies, it will generate the `package-lock.json`. It will be the file that registers the dependencies of your dependencies. You will not need to change this file, but it needs to be versioned by git.

To install development dependencies, you should add the flag `-D` when installing the dependency. For example:
```
npm install -D chalk
```
This command would install `chalk` as a development package.

In order to remove a dependency, you should execute:
```
npm uninstall <package-name>
```

### Dependency Tree
In order to see the dependency tree, you must use the command `npm fund`. Besides of showing from where the dependencies where downloaded, it will show u all the dependencies of your dependencies.
### Updating Dependencies
To update your dependencies, you should use  the command `npm update <package-name>`.
## NPM Scripts
Inside the package.json file, there's a property called `scripts`. These scripts are commands that are executed in a given phase or moment of your project to achieve a given result. There're pre-defined scripts that, if you create, it will affect the functionality of your application. Otherwise, you can create scripts that were made to be called for the user whenever it wants to call it.
The property `scripts` is a dictionary in which the key is the name of the script and, the value, it's the command itself. Then, if you want to run a given script, you need to do something like this:
```
package.json
-----------------------------------------------------------------------------------
"scripts": {
	"start": "node index.js"
}
```
Now, in your terminal, you should do:
```
npm run start
```
