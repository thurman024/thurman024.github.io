---
layout: post
title:      "Javascript - Hoisting and Scopes"
date:       2018-06-25 23:01:05 +0000
permalink:  javascript_-_hoisting_and_scopes
---


A confusing nuance for beginners in Javascript are the concepts of hoisting and scope.  I won't try to redefine the basic concepts here, as I'm sure there are dozens of explanations available that would be better than mine. Instead, this blog post will take a look at a few complex cases when applying other concepts.

**Variable definition (var, let, const)**

As you've learned in ES6, there are three ways to define a variable.  Var and Let differ in scope - but only scopes created by code blocks such as loops.  Within a function's scope, Var and Let perform the same

```
// Global Scope
function firstFunc() {
  // First scope
  var testVar = "hello"
	let testLet = "world"
}
testVar; // => undefined
testLet; // => undefined
```

As you see here, our two variables are locally scoped within our `firstFunc()`.  Const and Let are identical in all scopes, but using const prevents the value of the variable from being reassigned.

**Anonymous Functions**

You may remember that function declarations are hoisted, meaning the following code still prints "Hello".

```
sayHello();

function sayHello() {
  console.log("Hello");
};
```

However, when a function is created anonymously, we run into a unique error. Consider the following code:

```
sayHello();

var sayHello = function () {
  console.log("Hello");
};
```

The `sayHello` variable is hoisted, but remember *only the declaration is hoisted.*  Meaning that `sayHello` is essentially an empty (no value assigned to it) variable at the time when it is invoked.  So the error we get in response is that `sayHello` is not a function.

**Arrow Functions**

One behavior of arrow functions is that they do not pass `this` to the newly defined scope.  Here we have a `person` object with a `name` attribute and two `hello()` methods using different function constructors to illustrate the difference.  

```
window.name = "global scope"

var person = {
  name: "stephen",

  hello: function () {
      console.log("my name is ", this.name);
  },
  hello2: () => {
      console.log("my name is ", this.name);
  }
};
```

Invoking person.hello() will return the intended phrase "my name is stephen".  Intuitively, we can follow `this` is referenced back to `person`, so the value of `person.name` is rendered in the console.

But invoking person.hello2() will not behave the same way.  Because `this` is not bound to the local scope of the person object, `this.name` refers back to the enclosing scope of `person`.  So our return value is "my name is global scope".
