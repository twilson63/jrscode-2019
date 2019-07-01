# JRS Code Workshop

https://fpjs.now.sh

---

# Agenda

* Day 1 - Understanding functions
* Day 2 - Currying and Composition
* Day 3 - Reduce and Reducers

---

# Day 1 - Understanding functions

* What is a function?
* Functions as values
* Pure functions
* Side Effects
* Declarative Coding
* Immutability
* Closures and Higher Order Functions

---

# What is a function?

---

### What is a function?

A function is a procedure that can take 0 or more parameters and returns value as output.

A function when called/invoked/initiated/executed will create an execution context for the 
statements and expressions to run in.

---

### How to define/declare a function?

```js
function functionName() {

}
```

```js
const functionName = function() {

}
```

```js
const functionName = () => {}
```

---

# Functions as values

What does this mean?

---

In JavaScript a function can be passed to another function as an argument:

```js
function hello() {
  return 'hello'
}

function greeting(fn, name) {
  return fn() + name
}

greeting(hello, 'Class')

```

> NOTE: when parenthesis are to the right of a function name in a statement, 
> this instructs javascript to execute the function, when parenthesis are 
> not to the right of a function name then the function is being passed as 
> reference.

---

# Pure functions

---

### Pure function

A function that returns the same output value when called with the same input value.

```js
function identity(value) {
  return value
}
```

---

### What is an impure function

A function that has side effects.

What are side effects?

---

```
                             +---------+
                             |   SE    |
    +------------------------------------------------------+
    |  App                   |         |                   |
    |                        +---------+                   |
    |                                                      |
    |            +-----------------------------+           |
    |            |                             |           |
    |            |   Core                      |           |
+--------+       |                             |           |
|   |    |       |   Business Logic            |           |
|   | SE |       |                             |           |
|   |    |       |                             |           |
|   |    |       |                             |           |
+--------+       |                             |           |
    |            |                             |           |
    |            |                             |           |
    |            +-----------------------------+           |
    |                                                      |
    |                                                      |
    |                                                      |
    |                                                      |
    |                                                      |
    +------------------------------------------------------+
```

---

### Examples

```js
function greeting() {
  console.log('Hello World')
}

function alert() {
  setTimeout(function() {
    alert('Beep')
  }, 1000)
}

function write(text) {
  const el = document.createElement('div')
  el.innerText = text
  document.body.appendChild(el)
}
```

---

# Declarative Coding

When coding, it is more effective to tell the program what you 
want for it to do, versus how to do it. In this case, we can 
talk about map, the map function is `declarative` compared to
a for loop, which is imperative. The for loop tells the program
how to iterate over an array, where the map function tells the 
program to iterate over the array.

---

# Immutability

https://fpjs.now.sh/docs/immutability

---

# Closures and Higher Order Functions

https://fpjs.now.sh/docs/closures

---

In functional programming you can create small declarative functions
that do one thing then compose these functions together to create
more complex algorithms. 

> Exercise: Callback Canyon

In this exercise you are going to pair together and create a git
repository forked from callback canyon, and will work on creating
some callback functions. All of these functions will be pure 
functions and focused on one thing.

---

## Pairing rules

* Driver/Navigator
* Switch every 10 minutes
  - Driver commit changes to repo with descriptive message
  - New Driver pull changes from repo and continue down the list

> Driver must not provide instruction, they must do what the navigator says.
> Navigator must use their words to instruct the driver to add the correct logic.

> Important: If you are the driver, and the navigator tells you to do something
that is wrong, continue to do it, do not offer any advice, until the test fails.
> In order, to fix, swap roles and then as the Navigator verbally walk the 
driver through the fix.

---

## Test Driven Development

When creating code, it is good practice to create a test on how you expect it 
to work, then create a test on how you expect it not to work. Then use that 
test to confirm that your test work. In this exercise, we are going to use
tests to verify that our functions work.

```js
import { test } from 'test-modern'
import equals from './equals'

test('two arguments if equal should return true', assert => {
  const result = equals(42, 42)
  assert.equal(result, true, '42 should equal 42')
})

test('two arguments if not equal should return false', assert => {
  const result = equals(43, 44)
  assert.equal(result, false, '43 does not equal 44')
})

test('How can I break it?', assert => {
  // do you best!
})
```

---

## Testing asserts (All you need to know)

* ok - `assert.ok(actual, expected, msg)`
* equal - `assert.ok(actual, expected, msg)`
* throws - `assert.throws(() => throw new Error('Error'), 'Error was thrown')`

---

## Lets walk through a few

* Equals
* Add
* Subtract





