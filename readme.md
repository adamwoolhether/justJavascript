# Values
We can think of values as "floating" in our JS universe. They're not existing _inside_ the code,
but we can refer to them from our code.

Two main categories: _Primitive Values_ and _Objects & Functions_. In total, there are nin separate types.  
Lonely values:
* `null` is the only value of `Null` type.
* `underfined` is the only value of the `Undefined` type.

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