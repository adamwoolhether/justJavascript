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

# Studying from the Inside
In our model we won't worry about the lower level details of how the language is implemented. We won't concern
with a string being a "pointer", or "memory address". **A value is good enough**  
❗️The foundation of this mental model is values.

# Meeting the Primitive Values

## Undefined
This type has only one value: `undefined`.
```js
console.log(typeof(undefined)); // "undefined"
```
Undefined can cause trouble. Reading a property from it will break your program:
```js
let person = undefined;
console.log(person.mood); // TypeError!
```
Why does it exist? It represents **an unintentionally missing values**. Ex: an unassigned var will point to `undefined`:
```js
let bandersnatch;
console.log(bandersnatch); // undefined
```
Note, `undefined` doesn't simply mean "a var that isn't defined yet". It's an actual primitive value like 2 or "hello".  
To demonstrate: try reading a var that _actually_ wasn't defined:
```js
console.log(jabberywocky); // ReferenceError
```

## Null
You can consider `null` as `undefined`'s sister. There is **only one value for this type**: `null`. It behaves similarly too:
```js
let mimsy = null;
console.log(mimsy.mood); // TypeError!
```
Null is used for **intentionally missing values**.

## Booleans
Only two values (of course):
```js
console.log(typeof(true)); // "boolean"
console.log(typeof(false)); // "boolean"
```
Logical operations:
```js
let isSad = true;
let isHappy = !isSad; // The opposite
let isFeeling = isSad || isHappy; // Is at least one of them true?
let isConfusing = isSad && isHappy; // Are both true?
```

## Numbers
JS number types only have on type:
```js
console.log(typeof(28)); // "number"
console.log(typeof(3.14)); // "number"
console.log(typeof(-140)); // "number"
```
### Math for Computers
Floating point precision still applies:
```js
console.log(0.1 + 0.2 === 0.3); // false
console.log(0.1 + 0.2 === 0.30000000000000004); // true
```

### Colors and Numbers
JS uses numbers with **limited precision**. You can imagine numbers on an axis: The closer to 0, the more precise the number.

To demonstrate the loss of precision:
```js
console.log(Number.MAX_SAFE_INTEGER);     // 9007199254740991
console.log(Number.MAX_SAFE_INTEGER + 1); // 9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 2); // 9007199254740992 (again!)
console.log(Number.MAX_SAFE_INTEGER + 3); // 9007199254740994
console.log(Number.MAX_SAFE_INTEGER + 4); // 9007199254740996
console.log(Number.MAX_SAFE_INTEGER + 5); // 9007199254740996 (again!)
```

### Special Numbers
```js
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```
The type of `NaN` might be confusing. It technically is a number.
```js
console.log(typeof(NaN)); // "number"
```

### BigInts
Bigints allows us to represent large integers with precision, usefule for financial calculations where precision is needed.  
There are an **infinite number of BigInts, one for each integer in math.**   
Demonstrate the use of arbitrary precision:
```js
let alot = 9007199254740991n; // n at the end makes it a BigInt!
console.log(alot + 1n); // 9007199254740992n
console.log(alot + 2n); // 9007199254740993n
console.log(alot + 3n); // 9007199254740994n
console.log(alot + 4n); // 9007199254740995n
console.log(alot + 5n); // 9007199254740996n
```
## Strings
Three ways to write in JS: single quotes, double quotes, & backticks. The result in the same value:
```js
console.log(typeof("こんにちは")); // "string"
console.log(typeof('こんにちは')); // "string"
console.log(typeof(`こんにちは`)); // "string"
console.log(typeof('')); // "string"
```
### Strings Aren't Objects
While strings have some built-in properties (methods in other lang), they aren't objects!
```js
let cat = 'Cheshire';
console.log(cat.length); // 8
console.log(cat[0]); // "C"
console.log(cat[1]); // "h"
```

### A Value for Every Conceivable String
💡**There is a distinct value for every conceivable string.**  
Question: does this code create a string, or _summon_ a string that already exists?
```js
// Try it in your console
let answer = prompt('Enter your name');
console.log(answer); // ?
```
To keep our mental model simple: **all conceivable string values already exist from the beginning—one value for every distinct string**.

### Symbols
Symbols allow hiding information inside an object and controlling which parts of code can access it. They're quite rare, so we'll skip them.
```js
let alohomora = Symbol();
console.log(typeof(alohomora)); // "symbol"
```

# Objects and Functions
These are types that let us make our own values.

## Objects
Includes arrays, dates, regex, etc.:
```js
console.log(typeof({})); // "object"
console.log(typeof([])); // "object"
console.log(typeof(new Date())); // "object"
console.log(typeof(/\d+/)); // "object"
console.log(typeof(Math)); // "object"
```

Objects are **not** primitive values, and are therefore mutable. Properties can be accessed with dot `.` or bracket `[]` notation:
```js
let rapper = { name: 'Malicious' };
rapper.name = 'Malice'; // Dot notation
rapper['name'] = 'No Malice'; // Bracket notation
```

### Making Our Own Objects
We can make new objects with the bracket literal: `{}`.
```js
let shrek = {};
let donkey = {};
```

Because JS is a GC language, we can't explicitly "destroy" an object.
```js
let junk = {};
junk = null; // Doesn't really "destry" the object.
```

Functions in JS are first-class objects, we can assign them to a var. The below code will print out seven unique object values:
```js
for (let i = 0; i < 7; i++) {
  console.log({});
}
```

### Calling a Function
Guess what this prints:
```js
let countDwarves = function() { return 7; };
let dwarves = countDwarves;
console.log(dwarves); // ƒ () {return 7;}
```
Note that the above snippet doesn't actually call the function, it points `dwarves` to the function.  
But this does, it points `dwarves` to the values that `countDwarves` returns:
```js
let countDwarves = function() { return 7; };
let dwarves = countDwarves(); // () is a function call
console.log(dwarves); // 7
```
