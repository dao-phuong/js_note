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

