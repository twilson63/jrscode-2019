# Functional JavaScript Day 3

https://fpjs.now.sh

---

## Day 3

* Exercise Review
* Concept Review
* Map, Filter
* Reduce
* The Reducer Function
* Create a compose function with reduce
* Cybertron

---

## Exercise Review

In this exercies you were tasked to work through 
callback canyon implementing the following functions

* exists
* propEq
* map
* isNil, not
* pluck
* toUpper, toLower

## Bonus

* capitalize

---

## Concept Review

* What is the difference between a procedure and function?
* What is a pure function?
* What is a higher order function?
* What is immutability mean?
* What is a closure?
* What is partial application?
* What is currying?
* What is auto-curry?
* What is compose?
* What direction does a compose apply values to the function arguments?
* What two functions can be combined to create a propEquals function?
* What two functions can combined to create a pluck function?

---

## Map Review

```js
function map(mapperFn, list) {
  var result = []
  for(var i = 0; i < list.length; i++) {
    result.push(mapperFn(list[i]))
  }
  return result
}
```

```js
function map(mapperFn, list) {
  return list.map(mapperFn)
}
```

## Why do we want to use our own map function?

---

## Why map?

### Why abstract the array.map?

```js
const map = curry(function(mapperFn, list) { return list.map(mapperFn) })
```

So that we can curryify it and then compose it later.

```js
const transform = map(compose(toUpper, prop('name')))
const results = transform([{name: 'Tom'}, {name: 'Trip'}])
console.log(results)
```

---

# Filter

Filter takes a list of values and applys a unary predicate function
on each value, if the result is true, then the function keeps the 
item, if the function is false it discards the item into a new 
array.

```js
function filter(predicateFn, list) {
  var results = []
  for(var i = 0; i < list.length; i++) {
    if (predicateFn(list[i]) === true) {
      results.push(list[i])
    }
  }
  return results
}
```

---

## Filter 

```js
const filter = curry(function (predicateFn, list) {
  return list.filter(predicateFn)
})
```

```js
const oddNumbers = filter(isOdd)
const results = oddNumbers([1,2,3,4,5])
console.log(results)
```

---

## Reduce

A reduce function is a function that takes a reducer function, 
an initial value and an array, and returns a new value.

```js
function add(a,b) { return a + b }

const sum = function(...list) {
  return list.reduce(add, 0)
}
```

The reduce takes a reducer function, and initial value and a list of values.

---

## Reducer function

The reducer function is a function that has two arguments:

* accumulator
* value

The accumulator is the previous value returned by the reducer function
or if it is the first time the reducer is called it is the initial value

The value is the value from the array that is available for each iteration.

### Questions?

* Can a reduce function return a string or integer?
* Can a reduce function return an array?
* Can a reduce function return an object?

> A lot of iterator functions can be constructed by reduce.

---

## Example

```js
const count = reduce(inc, 0)
console.log(count([1,2,3,4,5,6])
```

> Step through the code using the tutor

---

## Cybertron

* Work through Level 5

---

* Work through Level 4 (if time)
