# Using the Set Object to Remove Duplicates

The `Set` Object is an easy way to store a **unique** collection of values, which can be a primitive value or object references.

A value in the Set has to be unique, which means it can only occur once.

While working through a CodeWars challenge, the task was to sort through a string with duplicate words and only return each word once.

```javascript
const example = "alpha alpha alpha beta gamma gamma delta delta delta"

let arr = example.split(" ")
let words = new Set(arr)
let removeDuplicates = [...words].join(" ")

> console.log(removeDuplicates)
// "alpha beta gamma delta"
```