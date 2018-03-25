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
