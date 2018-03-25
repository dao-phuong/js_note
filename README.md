# JS Note
Some important note about JavaScript

## Data types
7 type: <br>
+ undefined<br>
+ null<br>
+ boolean<br>
+ symbol<br>
+ number<br>
+ object<br>

## Some note about 'this'
https://viblo.asia/p/this-trong-javascript-gAm5ywe8Zdb?utm_source=newsletter&utm_medium=email&utm_campaign=weekly_digest


## for ...of
```
for (let value of array) {
  // do something with value
}
```

## for ...in
```
for (let property in object) {
  // do something with object property
}
```

## The && and || operators
The && and || operators use short-circuit logic, which means whether they will execute their second operand is dependent on the first. This is useful for checking for null objects before accessing their attributes:
```
var name = o && o.getName();
```
Or for caching values (when falsy values are invalid):
```
var name = cachedName || (cachedName = getName());
```

## Array
Note that array.length isn't necessarily the number of items in the array. Consider the following:
```
var a = ['dog', 'cat', 'hen'];
a[100] = 'fox';
a.length; // 101
```
Remember — the length of the array is one more than the highest index.

If you query a non-existent array index, you'll get a value of undefined in return:
```
typeof a[90]; // undefined
```

## 4 way to iterate through array

### for loop
```
for (var i = 0; i < a.length; i++) {
  // Do something with a[i]
}
```

### for...of
```
for (const currentValue of a) {
  // Do something with currentValue
}
```

### for...in NOT RECOMMEND
You could also iterate over an array using a for...in loop. But if someone added new properties to Array.prototype, they would also be iterated over by this loop. Therefore this loop type is not recommended for arrays.

### forEach()
```
['dog', 'cat', 'hen'].forEach(function(currentValue, index, array) {
  // Do something with currentValue or array[index]
});
```

## Functions
```
function add() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i < j; i++) {
    sum += arguments[i];
  }
  return sum;
}

add(2, 3, 4, 5); // 14
```
This is pretty useful, but it does seem a little verbose.To diminish this code a bit more we can look at substituting the use of the arguments array through Rest parameter syntax.
```
function avg(...args) {
  var sum = 0;
  for (let value of args) {
    sum += value;
  }
  return sum / args.length;
}

avg(2, 3, 4, 5); // 3.5
```

The avg() function takes a comma-separated list of arguments — but what if you want to find the average of an array? You could just rewrite the function as follows:
```
function avgArray(arr) {
  var sum = 0;
  for (var i = 0, j = arr.length; i < j; i++) {
    sum += arr[i];
  }
  return sum / arr.length;
}

avgArray([2, 3, 4, 5]); // 3.5
```
But it would be nice to be able to reuse the function that we've already created. Luckily, JavaScript lets you call a function with an arbitrary array of arguments, using the apply() method of any function object.
```
avg.apply(null, [2, 3, 4, 5]); // 3.5
```

JavaScript lets you create anonymous functions.
```
var a = 1;
var b = 2;

(function() {
  var b = 3;
  a += b;
})();

a; // 4
b; // 2
```

JavaScript allows you to call functions recursively. This is particularly useful for dealing with tree structures, such as those found in the browser DOM.
```
function countChars(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += countChars(child);
  }
  return count;
}
```

This highlights a potential problem with anonymous functions: how do you call them recursively if they don't have a name? JavaScript lets you name function expressions for this. You can use named IIFEs (Immediately Invoked Function Expressions) as shown below:
```
var charsInBody = (function counter(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += counter(child);
  }
  return count;
})(document.body);
```
The name provided to a function expression as above is only available to the function's own scope. This allows more optimizations to be done by the engine and results in more readable code. The name also shows up in the debugger and some stack traces, which can save you time when debugging.
