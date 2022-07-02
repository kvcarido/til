# Spread Operator

The spread operator `...` gives us the ability to expand an iterable like an array in places where 1+ arguments are expected. Syntax is the same when using the [rest parameter](https://www.geeksforgeeks.org/javascript-rest-operator/) but does the complete opposite.

It can be used in place of the `.concat()` method:

```javascript
let arr = [1, 2, 3]
let arr2 = [4, 5]

let arr = arr.concat(arr2)
> console.log(arr)
// [1, 2, 3, 4, 5]
```

```javascript
let arr = [1, 2, 3]
let arr2 = [4, 5]

let spreadArr = [...arr, ...arr2]
> console.log(spreadArr)
// [1, 2, 3, 4, 5]
```

Using the spread operator can also come in handy when you want to utilize the Math object and it's properties, such as finding the minimum value of an array.

```javascript
let arr = [1, 2, 3, -1]
> console.log(Math.min(arr))
// NaN
```

```javascript
let arr = [1, 2, 3, -1]
> console.log(Math.min([...arr]))
// -1
```