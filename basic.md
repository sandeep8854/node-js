## What is Node.js?

Node.js an open-source , cross-plateform javascript runtime envirnment.

- open source:- source code is publicly available for sharing and modification.

- Cross plateform- Available on Mac, Windows and Linux.

- Javascript runtime environment-?

#### Why learn Node.js?

- Build end-in-end JavaScript applications.
- A number of major companies like LinkedIn,Netfilx, PayPal have al migrated from other backend technologies to Node.js.
- Full stack delevelopment is the one of the most sought out skill sets by companies.
- Huge community supports.

```
console.log("Hello World");
run it:- node filename.js
Hello World
```

### Browser vs Node.js

- In the browser, most of the time what are doing is interacting with the DOM, or other Web Platform APIs like Cookies. You dont have the document, window and all other objects that are provided by the broswer.
- In the browser, we dont have all the nice API that Node.js provides througth its modules. For example the filesystem access functionality.

- With Node.js you control the envirnment.
- With a broswer, you are at the mercy of what the users choose.

### Modules

A module is an encapsulated and reusable chunk of code that has its own context in Node.js, each file is treated as a separate modules.

### Types of Modules

- **Local modules** - Modules that we create in our applicatios

- **Build-in modules** Modules that Node.js ships with out of the box.

- **Third party modules** Modules written by other developers that we can use in our applicatios.

Local modules:- Moduules that we create and use
in our application.

### CommonJS

- CommanJS is a standard that states how a modules should be structured and shared.

- Node.js adopted CommonJS when it started out and is what you will see in code bases.

```
fileName :- add.js
function add(a,b){
    return a+b;
}
console.log(add(4,5)); // 9
```

```
fileName:- index.js
require("./add.js);
console.log("Hello from index.js");

if you run this program, output  will be 9 and  Hello from index.js

if you run node index.js
// 9 will print from add.js and Hello from index.js will print index.js
because of require modules.

```

### Local Modules Summary

- In node.js, each file is a module that is isolated by default.
- To load a module into another file, we use require function
- When index.js is executed, the code in the module is also executed.
- if the file we are requiring is a javascript file, we can skip specifying the extension and node.js will infer it on our behalf.

### Module Exports

```
function add(a, b) {
  return a + b;
}
module.exports = add;
```

another file i have index.js

```
console.log("Hello from index.js");
const add1 = add(4, 5);
const add2 = add(5, 5);
console.log(add1);
console.log(add2);
```

Output will be like as:-

```
Hello from index.js
9
10
```

**Note** You can use multiple time of add functions

### Module Scope

- **fileName :- batman.js**

```
const superHero = "Batman";
console.log(superHero);
```

- **fileName:- superman.js**

```
const superman = "Superman";
console.log(superman);

```

- **fileName:- index.js**

```
require("./batman");
require("./superman");
```

- **Output**

```
Batman
Superman
```

**Note** each module in node.js has a own scope.

```
(function () {
  const superHero = "Superman";
  console.log(superHero);
})();
(function () {
  const superHero = "Batman";
  console.log(superHero);
})();
```

- **Output**

```
Superman
Batman
```

#### Immediately Invoked Function (IIFE) in Node.js

```
(function(){
    // module code actualy lives in here.
})
```

- Before a module's code is executed, Node.js will wrap it with a function wrapper that provides scope.

- This saves us from having to worry about conflicting variables or functions.

- This is proper eccapsulatios and reusability is unaffected.

### Module Wrapper

- Every module in node.js get wrapped in an IIFE before being loaded.

- IIFE helps keep top level variables scoped to the modules rather than the global object.

- The IIFE that wraps every modules contains 5 parameters which are pretty important for the functioning of a module.

```
(function (message) {
  const superHero = "Superman";
  console.log(message, superHero);
})("Hello");
(function (message) {
  const superHero = "Batman";
  console.log(message, superHero);
})("Hey");
```

```
node iife.js
Hello Superman
Hey Batman
```

```
(function (exports, require, module, __filename, __dirname) {
  const superHero = "Batman";
  console.log(superHero);
})();
```

**Before a module's code is executed node.js will wrap it with a functions that contain five parameter namely exports,requre,module,filename,dirname.**

### Module Caching

```
class SuperHero {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
  setName(name) {
    this.name = name;
  }
}
module.exports = SuperHero;
```

```
const SuperHero = require("./super-hero");

const batman = new SuperHero("Batman");
console.log(batman.getName());
batman.setName("Bruce Wayan");
console.log(batman.getName());

const newSuperHero = new SuperHero("Superman");
console.log(newSuperHero.getName());
```

```
node index.js
Batman
Bruce Wayan
Superman
```

**Note** When you create new superhero the module are not going to function because module already caching in previous supername of name.
That is called module caching come to the picture.

### Emport Export pattern.

<!-- // ![screensort](./imageName.png) -->

**There are five ways to import and export pattern in javascript**

**1** - In first way to create a module as a single functions. using **module.export=functionName**

**Example**

![screen](./images/1-mod.png)

![screen](./images/1mod.1.png)

**2 Pattern**

Here we just put directly module.exports in the function name. and all remaining are same.

![screen](./images/2Me.png)
![screen](./images/1mod.1.png)

**3rd Pattern**

We are going to export two function, one is add and second is subtruct.
In this program we are retuning as a object, then object you have to call .(dot) operator.

![screen](./images/3me.png)
![screen](./images/index3M.png)

**4th Pattern**

:- We are going to directly in the function name like as module.export.functionName
means, how to attach the module.exports in the function?

![screen](./images/4th.png)
![screen](./images/4thIn.png)

**5th Pattern**

:- IIFE node.js module recieved 5 modules in javascript
name as like as when you call IIFE function. In export function have already a module , so no need to putting modules.exports instead of exports.functionName.

![screen](./images/5th.png)
![screen](./images/4thIn.png)

Why are you putting exports.add instead of moudule.exports.add

![screen](./images/iife.png)

### Importing Json

- JavaScript object Notation
- A data interchange format commonly used with web server.

![screen](./images/json1.png)
![screen](./images/json2.png)

You can print any data based on your requirement.

### Watch mode in node.js

js server using the --watch flag, run the node command with the --watch flag followed by the name of the file you want to restart when Node detects changes. The command will watch your server. js file and restart the Node. js server when it detects changes made in the file

![screen](./images/watchmode.png)

If any require to change in your code then no need to run command watch mode detect automatically your code. and give the output based on your function call.
**Just save it.**

![screen](./images/watchmode2.png)

### Build-in-Module

Modules that node.js ships with Also referred to as core modules

Import the module before you can use it.

- path
- events
- fs
- stream
- http

### 1- Path module

The path module provides utilities for working with file and directory path.

![screen](./images/path.png)

In this above example **filename give us to absolute path and **dirname give us absolute dirctory name.

Differnce method available in path module.

![screen](./images/pathMethod.png)

In this above example if you run this program you will find a baseName of the file name which are using **path.basename(\_\_filename)**

and **path.extname(\_\_filename)** give us the extension of file name but directory name does not have any extension, he will given to empty.

and **path.parse(\_\_filename)** method give us to inform of object every information of the pathname.

and **path.format(path.parse(\_\_filename))** give us the absolute path of filename.

Some remaining method are:-

![screen](./images/pathMethod2.png)

In above example have isAsolute method which are given is it absolute are not.

and join method also there to join all arguments and normalize the resulting path.

**Last and important method**

![screen](./images/resolve.png)

**Both these methods accept a sequence of paths or path segments.**

**The path.resolve() method resolves a sequence of paths or path segments into an absolute path.**

**The path.join() method joins all given path segments together using the platform specific separator as a delimiter, then normalizes the resulting path.**
