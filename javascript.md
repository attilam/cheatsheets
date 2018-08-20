---
title: Javascripting
kind: cheatsheet
keywords: [code, cheatsheet]
created_at: 2015-aug-12 09:59:00
---

# Javascript

`console.log()` is your friend.  

`'use strict';` enables [strict mode](http://www.w3schools.com/js/js_strict.asp), use it!

## variables

Variable declarations are hoisted to the top of the enclosing scope always.

```js
// assigning something to a variable just like that makes it global!!!
blah = "hello"

// using 'var' makes the declaration local to the enclosing function
var blah = "hello"

// using 'let' makes the variable local to the block
let blah = "hello";

// 'const' makes the variable a constant (assignment only on declaration), local within block
const blah = "hello"
```

## strings

```js
var example = 'some string';
console.log(example.length);

var numToString = 0.5.toString();

var linesAsArray = myString.split('\n');
```

## Numbers

```js
var rounded = Math.round(0.5);

var num = Number('3.14');
```

## Operators

`==`, and `!=` only test for value equalty `5 == "5" // true`  
`===`, and `!==` operators test for value AND type `5 === "5" // false`

## Loops

```js
for(var i=0; i<10; i++) {
  console.log(i);
}
```

## Arrays

```js
var pets = ['cat', 'dog', 'elephant'];
pets.push('dolphin');

for(var i=0; i<pets.length; i++) {
  console.log(pets[i]);
}

var filtered = pets.filter(function(pet) {
  return (pet !== 'elephant');
});
```

## Objects

```js
var pizza = {
  toppings: ['cheese', 'sauce', 'pepperoni'],
  crust: 'deep dish',
  serves: 2
}

// two ways for accessors:
console.log(pizza.crust);
console.log(pizza['serves']);
```

## Functions

Functions are first class citizens in javascript.

Functions defined inside other functions have access to their parent function's scope.

```js
function multiply(x, mult) {
  return x*mult;
}

multiply(2, 4);
```

IIFE (Immediately Invoked Function Expression) is a common pattern for creating local scopes:

```js
(function() {
  // variables defined here can't be accessed outside
})(); // the function is immediately invoked
```