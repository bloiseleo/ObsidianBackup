 xJavaScript is a script language which evolved to be a full featured language. Even if, as any "old" language, it has its counter parts, it's also a pretty good language. It's a interpreted or just-in-time compiled programming language with first-class functions. Besides, it's a prototype-based, multi-paradigm  and single-threaded. It supports P.O.O, imperative and declarative.

JavaScript's standards are defined by the ECMAScript language specification and ECMAScript Internationalization API specification.
#### First-Class Function
It means that functions are treated like any other variable. It's possible to inform functions as parameters, it can be returned by another function and can be assigned as as value to a variable.
#### Prototype-Based
It means that we do not need to define classes in order to create an object. We can simply create an empty object or an object that already exists and add properties and methods to this object.
## Pure Function
A pure function is a function that does not change any value that existed before its call. In this case, imagine that we have a function that perform math operations and take two parameters as input. Now, you perform your calculations and return the value. But, before realizing the calculations, it changed the value in the memory (it's not pure). It would be pure if the parameters had not changed.
Other thing is: given the same input, you would obtain the same result.

> You should take this approach in consideration when programming functionally.
## Node Js
Node Js is a runtime environment that powers javascript outside the browser. It was created by Ryan Dahl in 2009 and in 2010 the version 0.1.14 was launched It was adopted by Microsoft, Yahoo! and LinkedIn. The OpenJS Foundation was created to maintain and evolve node js. In 2015, the node js adopted ecma script standards.  
### How it works? 
Node Js relys on the JavaScript engine to execute the javascript code. Node js uses the V8, that is used by the Google Chrome to execute javascript. Then, the creator created the libuv, which is the layer written in C++ that executes the event loop and interacts with the operational system.
## Projects
Every node.js project must contains the `package.json` file inside a folder. This folder is also called `workspace`. In order to create a pure node.js project, you should execute `npm init` in the terminal pointing to the root folder of your `workspace`.
The command `npm init` executes and waits for your input to determine some required information for the nodejs project. They are: package name, version, description, entry point, test command, git repository, keywords, author and license. If you want it to be fulfilled with the default information, you can use `npm init -y`.
- `name` is the name of the project.
- `version` is the version of the project. By default, it follows the semantic versioning, but you can use any version system you want.
- `description` is the description of the project.
- `main` is the entrypoint file of the project. It means that this file will be the file that will be executed first.
- `keywords` is an array of words that it would be used to look for this project in npm or any repository that supports nodejs.
- `license` is the license used by the project.
- `scripts` dictionary that contains key-value pairs of information. The key is the name of a lifecycle event of the project or an arbitrary name. The value is the command that will be run. To run this scripts, you can execute them with `npm run [script-name]`
	- The lifecycle scripts are named as: prepare, prepublish, prepublishOnly, postpack, dependencies.
	- The `prepare` runs before the package is packed, for example, during `publish` and `pack`. Besides, it also runs on `npm install`. 
	- The `prepublishOnly` runs when the package is prepared and packed, ONLY on `npm publish`.
	- Etc...
	- If you want, you can create `pre` or `post` scripts for any script you have. In order to do this, you can do this:
		```
		{
			"scripts": {
				"precompress": "",
				"compress": "",
				"postcompress"
			}
		}
		```
### Running the Project
If you want to run the project, you can execute it directly as `node file.js`. Besides, you can also create a script called `start` and put as a value to `node file.js`. But, every change will require a restart in your application, but you can add a flag called `--watch`. To do this, you can do `node --watch file.js`. Now, when you change the code that you're watching, node will automatically restart and re-execute your application.
## Modules
Modules are a way to organize and separate your code into different files. There are two manners of doing this: CommonJS and ECMAScript Modules.
### CommonJS
This is the default modules that nodejs uses when you create your project. Its syntax uses the object `module` to exports objects, functions and other stuff. 
- It's sync by default.
- It's mainly used by the node.js server side.
- It uses the `module.exports` to exports objects and the function `require`.
- It loads the modules dynamically.
Every javascript file is considered as a javascript module. A module can exports functions, objects and variables to make them available to another javascript file. For example, let's imagine that you have a file that contains functions related to product processing:
```
product.js
-----------------------------------------------------------------------------------
async function getFullName(codeId, productName) {
	return `${codeId} - ${productName}`
}
module.exports = {
	getFullName
};
```
Now, in another file, you can import this file in another file:
```
main.js
-----------------------------------------------------------------------------------
const { getFullName } = require('./product.js'); // This way, I'm using the
// desestructing, but I could do this way:
const products = require('./product.js');
//In this case, I would need to product.getFullName...
```
### ECMAScript Modules
This is the new module that nodejs uses when you set on your package.json to `type: module`. Its syntax uses `import` and `export` to control what is exposed and what is not. It's supported by the browsers.
Again, every javascript file is a module. Then, if you want something that is inside a module to be exported to another module, you should do something like the example below:
```
database.js
-----------------------------------------------------------------------------------
async function connect() {
	//...
}

export default connect;
```

In this way, you're only exporting the function `connect`. If you have more stuff inside this module, it will not be exported. To use it, you should do something like that:
```
main.js
-----------------------------------------------------------------------------------
import connect from './database.js';

connect();
```

If you want to export more things, you can do something like this:
```
database.js
-----------------------------------------------------------------------------------
async function connect() {
	//...
}

async function otherStuff() {
	// ....
}

export {
	connect,
	otherStuff
}
```

In order to import these stuff, you should do something like it:
```
import * as database from './database.js'

database.connect();
database.otherStuff();
```
But, if you want to only import some stuff, you can do something like it:
```
import { connect } from './database.js';
connect();
```

# TypeScript
TypeScript is a superset of Javascript that adds new features on top of javascript. The main new feature is a type system that provides safer development and better development experience.
## Node JS Flags
- `--env-file`: This flag accepts a path to a `.env` file. This file will be dumped inside the `process.env` object and it would be available to your application.