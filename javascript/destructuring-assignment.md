# Destructuring Assignment

Destructuring allows us to "unpack" objects or arrays into a bunch of variables for convenience.

```javascript
let a, b, rest
[a, b] = [10, 20]

console.log(a) // 10
console.log(b) // b

[a, b, ...rest] = [10, 20, 30, 40, 50]

console.log(rest) // [30, 40, 50]
```