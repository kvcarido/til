# String.substring() vs String.slice()

Both string methods essentially have the same functionality, which is to return a specific portion of the string variable. While reviewing JavaScript during my daily Anki spaced repetition review, my brain often confused the two.

### String.substring()

When using `substring`, the method takes 2 parameters: the `starting index`, and the `terminating index` (exclusive), or until the end of the string.

```javascript
const str = "Mozilla"

> console.log(str.substring(1, 3))
// "oz"

> console.log(str.substring(2))
// "zilla"
```

### String.slice()

Using the `slice` method extracts a section of the string without modifying the original string. It also accepts two parameters of `starting index` and `terminating index` (exclusive).

```javascript
const phrase = "Queens get the money"

> console.log(phrase.slice(0,6))
// "Queens"

> console.log(phrase.slice(7))
// "get the money"
```

#### TL;DR

When in doubt, use `String.slice()` to avoid confusion. 

Based on my surface-level research between the two, `String.substr()` is deprecated, and you can't go wrong with creating a copy instead of modifying the original variable. 