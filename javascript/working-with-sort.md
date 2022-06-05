# Working with arr.sort() Method

When using `sort` it accepts a callback function with two arguments, also known as a [Compare Function](https://www.w3schools.com/js/js_array_sort.asp "Compare Function"). The purpose of this function is to define an alternative way to sort the order of the array.

```javascript
function(a, b) { return a - b}
```

The function will return a value that is either positive, negative, or zero.

- If the result is **negative**, `a` is sorted before `b`
- If the result is **positive**, `b` is sorted before `a`
- If the result is **zero**, no changes are done with the sort order of the two values

This behavior works with numbers, but when trying to sort strings you must define the behavior:

```javascript
let names = ["Ironman", "Captain America", "Black Widow", "Hulk", "Thor"]

let sortedAvengers = names.sort((a, b) => {
	if (a < b) return -1
	return 1
})

> console.log(sortedAvengers)
// ["Black Widow", "Captain America", "Hulk", Ironman", "Thor"]
```