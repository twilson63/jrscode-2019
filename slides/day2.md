# JRS Code Workshop Day 2

https://fpjs.now.sh

---

## Agenda

* Day 2 - Currying and Composition

---

# Review Day 1

* Understanding Functions
* What is the difference between a procedure and function?
* What is a pure function?
* What is a higher order function?
* What is immutability mean?
* What is a closure?

---

## What is currying?

---

Currying is the process of only supplying on value of a function at a time until 
all values are supplied then the function algorithm is executed. 

Currying is the process of converting a function with n arguments into n functions
with single arguments.

> Partial application, is where you may apply some of the arguments, followed up
with the rest of the arguments at a later time.
> AutoCurrying does both partial application and currying.

---

## Lets see some examples:

Manual Curry

```js
function add(a) {
  return function (b) {
    return a + b
  }
}
```

```js
function subtract(a) {
  return function (b) {
    return a - b
  } 
}
```

---

## Curryify functions

Taking a function with n arguments and if that function is called with 1 argument, 
return a function asking for the other argument, and so on.

```js
function curry2(fn) {
  let values = []
  return function doCurry(...args) {
    values = values.concat(args)
    if (values.length >= 2) {
      return fn(...values)
    }
    return doCurry
  }
}

function basicAdd(a,b) {
  return a + b
}

const add = curry2(basicAdd)
console.log(add(1,2))
console.log(add(1)(2))

```

---

## CurryN

CurryN is a function that wraps around a normal function and asks for the number
arguments at the time that function is called.

```js
function curryN(n, fn) {
  let values = []
  return function doCurry(...args) {
    values = values.concat(args)
    if (values.length >= n) {
      return fn(...values)
    }
    return doCurry
  }
}

function _add(a,b) { return a + b }

export default const add = curryN(2, _add)

```

---

## CurryN with 3 arguments

```js

function _reduce(reducer, initialValue, list) {
  return list.reduce(reducer, initialValue)
}

export default const reduce = curryN(3, _reduce)
```

---

## Use a library

Don't write your own curry, use a library like `ramda` or `lodash/fp` and
wrap your functions with curry to convert all of your binary and variatic 
functions into unary functions.

---

## Composition

The act of combining one or more functions to create a more complex function:

```
f(g(x)) = compose(f,g)(x)
```

If we have a value and call a function that returns a value then we pass that 
in to another function that returns a value, we can leverage math to understand 
that if we combine or compose those methods together we can create a very nice 
abstration to declaratively represent passing a value from one function and the 
result of that function being passed to another function.

This gives us that lego like feel when building complex algorithms.

```js
function compose2(fn1, fn2) {
  return function (v) {
    v = fn2(v)
    return fn1(v)
  }
}

// 1 + 1 - 2
const subtract2 = subtract(2)
const add1 = add(1)
const add1andsubtract2 = compose2(subtract2, add1)
const result = subtract(2, add(1, 2)) === add1andsubtract2(1)
console.log(result)
```

---



```js
const colors = [{name: 'blue'}, {name: 'green'}, {name: 'red'}]

const uppercaseColorName = compose(toUpper, prop)
const transformColors = map(uppercaseColorName)
const results = transformColors(colors)
```

Lets transform them but keep the property in the object

```js
TODO
```

---

Lets work through Callback Canyon and identify opportunities to compose and curry.





