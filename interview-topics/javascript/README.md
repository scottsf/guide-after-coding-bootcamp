# JavaScript

* [Lexical environment](#lexical-environment)
* [Strict mode](#strict-mode)
* [Sloppy mode](#sloppy-mode)
* [Hoisting](#hoisting)
* [Variable scope](#variable-scope)
* [Difference Between *var*, *let*, and *const*](#difference-between-var,-let,-and-const)
* [IIFE](#iife)
* [Closure](#closure)
* [Curring](#curring)
* [Call, apply and bind methods](#call-apply-bind-methods)
* [Generator functions](#generator-functions)

## Lexical environment
  How a parser resolves variable names when functions are nested. The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Nested functions have access to variables declared in their outer scope.

  source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures

  [[↑] Back to top](#JavaScript)
  
## Strict mode
  Strict Mode is a feature that allows you to place a program, or a function, in a “strict” operating context. This strict context prevents certain actions from being taken and throws more exceptions. The statement “use strict”; instructs the browser to use the Strict mode, which is a reduced and safer feature set of JavaScript.
  
  * Strict mode eliminates some JavaScript silent errors by changing them to throw errors.
  * Strict mode fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that’s not strict mode.
  * Strict mode prohibits some syntax likely to be defined in future versions of ECMAScript.
  * It prevents, or throws errors, when relatively “unsafe” actions are taken (such as gaining access to the global object).
  * It disables features that are confusing or poorly thought out.
  * Strict mode makes it easier to write “secure” JavaScript.
      
  Strict mode can be used in two ways – used in global scope for the entire script and can be applied to individual functions. Strict mode doesn’t work with block statements enclosed in {} braces.
  
  source: https://www.geeksforgeeks.org/strict-mode-javascript/
  
  [[↑] Back to top](#JavaScript)
  
## Sloppy mode
  The normal, non-strict mode of JavaScript is sometimes referred to as sloppy mode. 
  It sloppy mode, assigning to an undeclared variable creates a global variable. 
  
  ```javascript
  function check() {
    var declared = 'local variable';  
    undeclared = 'global variable';   // undeclared variable
    return `I'm a ${declared}, I'm a ${undeclared}.`;
  }

  console.log(check());

  console.log(undeclared); // return 'global variable'
  console.log(declared)    // return ReferenceError
  ```
  
  If you use strict mode in the above example undeclared will cause an error because pitfall is not declared.
  
  [[↑] Back to top](#JavaScript)
  
## Hoisting 
  Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Inevitably, this means that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local.

Source: https://scotch.io/tutorials/understanding-hoisting-in-javascript

[[↑] Back to top](#JavaScript)

## Variable scope
  Scope in JavaScript refers to the current context of code, which determines the accessibility of variables to JavaScript. The two types of scope are local and global:

  * Global variables are those declared outside of a block
  * Local variables are those declared inside of a block
    
  source: https://www.digitalocean.com/community/tutorials/understanding-variables-scope-hoisting-in-javascript
  
  [[↑] Back to top](#JavaScript)
  
## Difference Between *var*, *let*, and *const*
  The differences between the three are based on scope, hoisting, and reassignment.
  
  <img width="755" alt="screen shot 2019-01-08 at 1 46 44 pm" src="https://user-images.githubusercontent.com/43653189/50860883-ed867e00-134b-11e9-81fc-c519a9e92e03.png">

  source: https://www.digitalocean.com/community/tutorials/understanding-variables-scope-hoisting-in-javascript
  
  [[↑] Back to top](#JavaScript)

## IIFE
  An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.

  ```javascript
  (function () {
      statements
  })();
  ```

  It is a design pattern which is also known as a Self-Executing Anonymous Function and contains two major parts. The first is the anonymous function with lexical scope enclosed within the Grouping Operator (). This prevents accessing variables within the IIFE idiom as well as polluting the global scope.

  The second part creates the immediately executing function expression () through which the JavaScript engine will directly interpret the function.
  
  source: https://developer.mozilla.org/en-US/docs/Glossary/IIFE
  
  #### helpful article: https://medium.com/@vvkchandra/essential-javascript-mastering-immediately-invoked-function-expressions-67791338ddc6

  [[↑] Back to top](#JavaScript)
  
## Closure 
  A *closure* is the combination of a function and the lexical environment within which that function was declared. 
  Closures capture the local variables and can use them as private state. 
  ```javascript
  let scope = "global scope";         // A global variable
  function findNemo(name) {
    let scope = "local scope";        // A local variable
    return function f() { 
      return `${name} in ${scope}`;   // Return the value in scope 
    }   
  } 
  
  findNemo('Nemo')();                 // => "local scope"

  let  inc = (function () {
    let number = 0;
    return function () { 
        return number += 1;
    }
  }());
  inc();       // Return 1
  inc();       // Return 2
  ```
  ##### More info: [MDN Closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
  ##### Helpful article: [Medium](https://medium.com/koderlabs/javascript-scope-chain-and-execution-context-simplified-ffb54fc6ad02)
  
  [[↑] Back to top](#JavaScript)
  
  ## Call, Apply and Bind methods
  Traditionally object has properties and methods. In JavaScript, you can write method separately and attach it to different objects with call, apply and bind methods. Simply, you can write common methods for various objects. For example:
  
  ``` javascript
  // we have an object called a student
  let student = {
    name: 'Harry Potter',
  }
  
  let hasWand = function(bool) {
    return `Does ${this.name} has a wand? Answer: ${bool}`
  }
  
  // using call method
  hasWand.call(student, true) //returns "Does this.name has a wand? Answer: false"
  
  ---

  let getBirthday = function(month, day, year) {
    return `${this.name} was born on ${month}/${day}/${year}`
  }
  
  let birthday = ['October', 16, 1998];
  
  // difference between appy and call is apply accepts array property
  getBirthday.apply(student, birthday) //returns "Harry Potter was born at October/16/1998"
  
  ---
  
  // Bind method binds the method with the object and it returns a function
  let bound = hasWand.bind(student)
  bound(true) // returns "Does Harry Potter has a wand? Answer: true"
  
  ```
  
  ## Generator functions 
  Generator functions return generator object. It can be exited and re-entered later. Their context will be saved. It is a powerful tool, especially combined with promises. It eliminates callback hell. 
  Super useful for asynchronous programming. Which async built on top of it. It doesn’t execute the body immediately. The generator functions body executed until the first *yield* expression. It delegates to another function. 
  Depends on the next() method returns an object with a value (containing the yielded value) and done property contains (true, false)
  Calling next() method with the argument will resume the generator function execution replacing the yield expression where execution was paused with the argument from next() method.

  source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*
  
  [[↑] Back to top](#JavaScript)

