# Getters and Setters with Objects

`Objects` are a data structure that can hold properties (`variables`) and methods (`functions`).

```javascript
let person = {
    firstName: "John",
    lastName: "Doe",
	fullName() {
		return `${this.firstName} ${this.lastName}`
	}
}
```
Although `person.fullName()` is correct syntax, there are a few limitations that can get in the way when formatted as a method. You'd have to call it like a function with the parenthases `()` at the end, and in this form you won't be able to change it's value.

- **Getters** give you the ability to access properties
- **Setters** allow you to change, or mutate them

To format a getter, use the keyword `get` in front of the original method:

```javascript
let person = {
	firstName: "John",
	lastName: "Doe",
	get fullName() {
		return `${this.firstName} ${this.lastName}`
	}
}

> person.fullName // "John Doe"
// no need to invoke the method with parentheses at the end
```

The same can be done with the keyword `set` in order to be able to manipulate it. Setters also take in a parameter (`value`):

```javascript
let person = {
	firstName: "John",
	lastName: "Doe",
	set fullName(value) {
		let names = value.split(' ')
		this.firstName = names[0]
		this.lastName = names[1]
	}
}

// no more parentheses!
> person.fullName = "Tobe Bryant"
> person.firstName
// "Tobe
> person.lastName
// "Bryant"
```

This tidbit was made possible through the insightful teachings of Mosh found in [this video](https://www.youtube.com/watch?v=bl98dm7vJt0).