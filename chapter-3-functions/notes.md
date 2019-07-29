### Functions

Functions are the bread and butter of JavaScript :)

#### Defining a Function

A function is created with an expression that starts with the keyword function. Functions have a set of parameters and a body contains the statements that are to be executed when the function is called.

The function body of a fucntion created must always be wrappred in braces, even when it consist of only single statement.

A function can have multiple parameters,

```js
const power = function(base, exponent) {
  let result = 1;
  for (let count = 0; count < exponent; count++) {
    result *= base;
  }
  return result;
};
```

Or no paramaters at all.

```js
const makeNoise = function() {
  console.log("Pliingg!");
};

makeNoise(); // Pliingg!
```

Some functions produce a value, and some don't whose only result is a side effect.

```js
const square = functions(x) {
    return x * x;
}

console.log(square(12)); // 144
```

#### Binding and Scopes

If you create bindings with let and const inside of a loop,
the code before and after the loop can not see it.

In pre-2015 bindings with var keyword are visible throughout the whole function that appear in out the global scope, if they are not in a function.

```js
let x = 10;
if (true) {
  let y = 20;
  var z = 30;
  console.log(x + y + z); // 60
}

console.log(y); // y is undefined
console.log(z); // 30
```

Each scope can *look out* into the scope around it. The exeption is when multiple bindings have same name code can see only the innermost one. 

For example, when code inside the *halve* function refers to n, it is seeing its own n, not the global one.

```js
const halve = function(n) {
    return n / 2;
}

let n = 10;
console.log(halve(100)); // 50
console.log(n); // 10
```

Each local scope can also see all he local scopes that contain it, and all scopes can see the global scope.
This aproach called *lexical scoping*.

#### Functions as Values

A function value can do all things that other values can do. It is possible to store a function value in a new binding, pass it an argument to a function and so on.

```js
let launchMissiles = function() {
    missilesSystem.launch('now');
}
if (safeMode) {
    launchMissiles = function() {
        // do nothing
    }
}
```
#### Declaration Notation

There is slightly shorter way to create a function binding, when the *function* keyword is used
at the start of a statement it works differently. It's slightly easier to write and does not require 
a semicolon after the function.

```js
function future() {
    return 'You will never have a flying car!';
}
```

### Arrow Function

Instead of the function keyword, it use an arrow (=>) made up of an equal sign and a greater than symbol.

```js
const power = (base, exponent) => {
    let result = 1;
    for (let i = 0; i < exponent; i++) {
        result *= base; 
    }
    return result;
}
```

When there is only one parameter, you can omit the parentheses around the parameter list.

```js
const square1 = (x) => { return x * x; }
const square2 = x => x * x;
```

#### Optional Arguments

JavaScript is extremely broad-minded about the number of arguments you pass to a function. 
If you pass too mnay, the extra ones are ignored.If you pass too few, missing parameters get assigned the value *undefined* or you can provide a default value.

```js
function power(base, exponent = 2) {
    let result = 1;
    for (let i = 0, i < exponent; i++) {
        result *= base;
    }
    return result;
}

console.log(power(4)); // 16 
console.log(power(2, 6)); // 64
```

#### Closure

Local bindings are created anew for every call, and different calls can not trample on one another's
local bindings. This feature is called *closure*.

```js
function wrapValue(n) {
    let local = n;
    return () => local;
}

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);

console.log(wrap1()); // 1
console.log(wrap2()); // 2
```

This behavioer not only frees from having to worry about litefimes of bindings but also makes it possible to use function values in some creative ways.

 

