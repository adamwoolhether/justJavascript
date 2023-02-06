# Values
We can think of values as "floating" in our JS universe. They're not existing _inside_ the code,
but we can refer to them from our code.

Two main categories: _Primitive Values_ and _Objects & Functions_. In total, there are nin separate types.  
* Booleans
* Numbers
* BigInts
* Strings
* Symbols
* Objects
* Functions

Lonely values:
* `null` is the only value of `Null` type.
* `underfined` is the only value of the `Undefined` type.

Interesting, there is an old, unfixable bug in JS. Type `console.log(typeof(mull));` to find out!

## Primitive Values
Primitive values can be pointed to, but not created, destroyed, or modified.
```javascript
console.log(2);
console.log("hello");
console.log(undefined);
```
f
## Objects & Functions
Objects and functions can be manipulated.
Notice how the browser's console displays these differently:
```javascript
console.log({});
console.log([]);
console.log(x => x * 2);
```

**In JS, there are no other fundamental value types than the ones just mentioned.**
Everything else is an **object**. We can verify this with the following:
```javascript
console.log(typeof([])); // "object"
console.log(typeof(new Date())); // "object"
console.log(typeof(/(hello|goodbye)/)); // "object"
console.log(typeof(2)); // "number"
console.log(typeof("hello")); // "string"
console.log(typeof(undefined)); // "undefined"
```
Even if something like `"hi".toUppercase()` makes `"hi"`, seem like an object, JS will create a temporary object to do this.

## Expressions
Expressions are questions that JS can answer, and it answers those questions with values.
```javascript
console.log(2 + 2); // 4
console.log(typeof(2)); // "number"
```

# Values and Variables
Analyze this code snippet and say what I expect it to do:
```javascript
let reaction = 'yikes';
reaction[0] = 'l';
console.log(reaction);
```
Assign a string `yikes` to var `reaction`.  
Mutate first char in string (Aren't **primitive values immutable**???)  
Will either print `likes` or given an error when we try to mutate `reaction`.  
RESULT: No error, but as expected, the var in not mutable!!

## Primitive Values are Immutable
Although we can access an index of primitive vals, like `reaction` above, we can't mutate them, as they're not an array(which aren't primitive).

The below code wont' actually mutate the value. Whether an it silently refuses or throws an error depends on whether [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) is enabled or not.
```javascript
let fifty = 50;
fifty.shades = 'gray'; // No!
```

## Variable and Values
```javascript
let pet = 'Narwhal';
pet = 'The Kraken';
console.log(pet); // ?
```
This snippet will work, because we're not mutating the string, we're simply re-assigning a new value to `pet`.

## Variables are Wires
You can think of a variable as a wire that connects to a value.

### Rules of Assignment
1. The left side of an assignment must be a "wire", ie, the `pet` variable.
2. The right side must be an expression, always resulting in a value.

### Reading Values of Variables
```javascript
console.log(pet);
```