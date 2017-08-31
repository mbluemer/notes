# Scopes and Closures



## 2 | Lexical Scope

**Lexical scope** is where a name refers to its local lexical environment thus it's scope is defined at lex time in the compilation process.

* Name lookup will start in the most local scope and continue searching upward until a match is found
* Allows the same identifier to exist at multiple scope levels, a term called *shadowing*
* Lexical scope is defined only by where a function is declared, not where it is called (this only refers to local scope and says nothing about outer scopes)



There are two ways to cheat lexical scope (often frowned upon):

1. `eval(..)` function takes a string and evaluates it as if it was there at author time. This allows for the dynamic insertion of code, thus dynamically modifying the lexical scope environment.
   * note: in *strict-mode* eval generates it's own lexical scope and doesn't modify the one around it.
2. `with` (now deprecated) takes an object and treats that object as if it is a wholly separate lexical scope
   * note: in *strict-mode* with just isn't allowed

Both of those cheating methods can provide dangerous side-effects and cause the compiler to skip optimizations because it can't fully predict the outcomes, causing overall worse performance.



## 3 | Function vs. Block Scope

It's often very useful to hide functionality and variables in a scope bubble because:

* it prevents external tampering through hiding of private details
* it helps avoid naming collisions
* it often leads to concrete and well-defined interfaces



If we want to scope something with a function but don't want to pollute the current lexical scope with an extra function name we can use an **IIFE** (Immediately Invoked Function Expression):

```javascript
(function foo() {
    var a = 3;
  console.log(a);
})();
```

* note: There's debate over whether anonymous functions or named function expressions are better. Anonymous functions have no identification in stack traces and make recursion difficult but function expressions can be accidently hoisted into the enclosing scope in IE. Douglas Crockford recommends using function expressions but [this article](http://kangax.github.io/nfe/) goes into more detail. In modern browsers these issues should be non-existent.



Strictly speaking Javascript doesn't support **block scope** but there are certain constructs that allow it:

* in a `try/catch` the catch block is scoped so anything declared in that block will not exist outside
* ES6 introduced the `let` keyword that allows block-scoped variables to be defined
* ES6 also introduced the `const` key which creates a block-scope consant
  * These are huge helpers when it comes to garbage collection because the scope of where certain variables are needed is much more explicit



## 4 | Hoisting

