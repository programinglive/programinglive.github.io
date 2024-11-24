---
title: Map in JavaScript
layout: default
parent: JavaScript
grand_parent: Web Development
description: "Map in JavaScript"
---

# JavaScript `map()` Function

The `map()` function is a built-in method in JavaScript that creates a new array by applying a given function to each
element in the original array. It is often used for transforming data in arrays without modifying the original array.

---

## Table of Contents

- [What is `map()`?](#what-is-map)
- [Syntax of `map()`](#syntax-of-map)
- [How the `map()` Function Works](#how-the-map-function-works)
- [Examples of Using `map()`](#examples-of-using-map)
- [Chaining `map()`](#chaining-map)
- [When to Use `map()`](#when-to-use-map)
- [Conclusion](#conclusion)

---

## What is `map()`?

The `map()` function is used to iterate over an array and perform a transformation on each element. It does not change
the original array but returns a **new array** with the results of applying the callback function to each element.

This method is ideal when you want to process each item in an array and return a new array with the modified results.

---

## Syntax of `map()`

```javascript
let newArray = array.map(function (currentValue, index, array) {
	// return transformed element
}, thisArg);
```

- **currentValue**: The current element being processed in the array.
- **index** *(optional)*: The index of the current element in the array.
- **array** *(optional)*: The array that the `map()` method is called upon.
- **thisArg** *(optional)*: Value to use as `this` when executing the callback function.

---

## How the `map()` Function Works

1. **Creates a new array**: The original array remains unchanged, and a new array is returned with the transformed
   elements.
2. **Iterates through all elements**: The callback function is applied to every element of the array in order.
3. **Callback execution**: The callback function executes once for each element, and the transformed result is added to
   the new array.

---

## Examples of Using `map()`

### Example 1: Doubling the Values in an Array

```javascript
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(function (num) {
	return num * 2;
});
console.log(doubled); // [2, 4, 6, 8, 10]
```

### Example 2: Extracting Specific Properties from Objects in an Array

```javascript
let users = [
	{name: 'Alice', age: 25},
	{name: 'Bob', age: 30},
	{name: 'Charlie', age: 35}
];

let names = users.map(function (user) {
	return user.name;
});
console.log(names); // ['Alice', 'Bob', 'Charlie']
```

### Example 3: Using Arrow Functions with `map()`

```javascript
let numbers = [1, 2, 3, 4, 5];
let squared = numbers.map(num => num ** 2);
console.log(squared); // [1, 4, 9, 16, 25]
```

---

## Chaining `map()`

You can chain multiple `map()` calls to perform multiple transformations on the array elements:

```javascript
let numbers = [1, 2, 3, 4, 5];
let result = numbers
	.map(num => num * 2)      // Double the numbers
	.map(num => num + 1);     // Add 1 to each doubled number

console.log(result); // [3, 5, 7, 9, 11]
```

---

## When to Use `map()`

- **Transforming data**: When you need to apply a transformation to each element in an array, such as modifying the
  values or extracting specific properties.
- **Creating a new array**: When you want to generate a new array without modifying the original.
- **Performing calculations**: Useful when performing mathematical operations on arrays, such as scaling values,
  summing, or squaring elements.

---

## Conclusion

The `map()` function is a powerful method for creating new arrays based on existing ones while applying a
transformation. Its immutability, flexibility, and the ability to chain operations make it a valuable tool in functional
programming in JavaScript. Use `map()` whenever you need to transform the elements of an array and generate a new array
with the results!