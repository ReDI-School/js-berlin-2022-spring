<!-- .slide: id="lesson7" -->

# Basic Frontend - Spring 2022

Lesson 7, Thursday, 2022-04-07

---

### Recap

```js
let x = 1 + 2 * 3;
```

What is the value of `x`?

7 (multiplication has higher precedence than addition)
<!-- .element: class="fragment" -->

---

### Recap

```js
1 + 2 + 3;
```

What is computed first, `1 + 2` or `2 + 3`?

1 + 2 (Addition operator has left-to-right associativity)
<!-- .element: class="fragment" -->

---

### Recap

```js
x = y = z;
```

What is computed first, `x = y` or `y = z`?

y = z (Assignment operator has right-to-left associativity)
<!-- .element: class="fragment" -->

---

### Lesson overview

* `let` vs `const` vs `var`
* JavaScript comments
* `undefined`
* Compound assignment operators
* HTML and functions
* Objects

---

### `let` vs `const` vs `var`

So far, we **defined** variables using the `let` keyword. `const` defines a **constant**, which means that the value cannot be changed:

```js
const x = 42;
x = 43; // error
```

The `var` keyword is *old* JavaScript. It is not recommended. Use `let` instead.

---

### Comments

In JavaScript (and in programming in general) comments are short texts to add explanations to our code.

Comments are meant only for developers of the code.

They are ignored by JavaScript:

```js
// Average: divide the sum of a set of numbers by the number of values
// for example, if we have 4 numbers, we have to divide the sum by 4
let average = (2 + 6 + 3 + 9) / 4;
```

---

### Commenting our code

Two types of comments:

```js
// this is a one line comment
// another one line comment
// anything after // is ignored by JavaScript

/*
    This is
    a multi-line
    comment
*/

let a = 5; // I can put comments mostly everywhere
```

- Use comments to add important information that is not already clear from reading the code.
- Good comments explain the **why** and not the **what**

---

### Data Type: Undefined

* **Undefined** has only one value: `undefined`
* It indicates the unintentional absence of any value
* `undefined` is automatically assigned to variables
* `undefined` is automatically returned by functions without a `return` statement

---

### Undefined example

```js
let x;  // no value is assigned to x
console.log(x); // undefined
console.log(typeof x); // "undefined"
console.log(x === undefined); // true

function silly() { /* no return statement */ }
let y = silly(); // y is undefined
```

---

### Compound assignment operators

| Compound operator | Same as |
| ----------------- | ------  |
| `x += 42` | `x = x + 42` |
| `x -= 42` | `x = x - 42` |
| `x /= 42` | `x = x / 42` |
| `x *= 42` | `x = x * 42` |
| `x **= 42` | `x = x ** 42` |

Compound assignment operators are shorter ways of applying an operator on the variable and assigning the result back to the variable.

---

### HTML and JavaScript

HTML Buttons have a `onclick` attribute that executes JavaScript when the button is clicked:

```html
<button onclick="console.log('I was clicked!')">Click me!</button>
```

However, writing JavaScript in `onclick` is rather tedious. Can you think of a better way?

---

### HTML and JavaScript

How about calling a function instead?

```html
<button onclick="handleButtonClick()">Click me!</button>
```

In JavaScript:

```js
function handleButtonClick() { /* TODO */ }
```

---

### Changing the background color

The browser provides a variable `document.body.style.backgroundColor`.

We can assign a value to `document.body.style.backgroundColor` to change the background color of our HTML page.

```js
// change the current color:
document.body.style.backgroundColor = "red";
// print the current color to console
console.log("The current color:", document.body.style.backgroundColor);
```

---

### Task

Create a webpage with three buttons, "red", "green", "blue".

When you press the button, set `document.body.style.backgroundColor` to that color.

BONUS:

* If you press the button again, change the color back to white.
* Solve the task with only one single `function` and one single `if/else` statement.

---

### Solution

HTML:
```html
<button onclick="changeColor('red')">red</button>
```

JS:
```js
function changeColor(color) {
    if (document.body.style.backgroundColor === color) {
        document.body.style.backgroundColor = "white";
    } else {
        document.body.style.backgroundColor = color;
    }
}
```

---

<!-- .slide: id="objects" -->

# Objects

---

### Problem with simple values

Let's imagine you need to describe three friends:

```js
let friend1Name = "Mellina";
let friend1IsTeacher = true;
let friend2Name = "Woytek";
let friend2IsTeacher = true;
let friend3Name = "Matt";
let friend3IsTeacher = true;
```

We need _a lot_ of variables.

---

### Problem with function parameters

Now imagine a function that operates on 2 people:

```js
function introduce(person1Name, person1Age, person1IsTeacher, person2Name, person2Age, person2IsTeacher) {
  console.log("Hello", person1Name, ", let me introduce you to", person2Name);
  // ...
}
```

The parameter list gets rather long, and if you'd like to introduce another variable, it gets messy.

---

Wouldn't it be nicer if we could group information that belongs together somehow?

---

### Objects

An **object**, in Javascript, is a group of *key* / *value* pairs

We can think of key/value pairs as words in a dictionary

* a word is the **key**
* the definition is the **value**

![Dictionary](images/dictionary.jpg) <!-- .element width="500" style="display: block; margin: 0 auto;" -->

---

### Objects

Example:

```js
let person = {
  firstName: 'Carlo',
  lastName: 'Trimarchi',
  age: 39
};
```

Can you guess how we can create an object?

---

### Objects

key/value pairs are also referred to as **properties**

```js
let person = {
  firstName: 'Carlo', // comma
  age: 39,            // comma
  isVegetarian: true  // comma is optional
};
```
* can you name all the properties in this **person** object?
* and its keys?
* and its values?

---

### Objects: examples

```js
let book = {
  title: 'The Lord of the Rings',
  author: 'J. R. R. Tolkien',
  publicationYear: 1954,
  pages: 1216
};
```

---

### Task: Introduction

Define a variable called `me` and initialize it with an object containing the following information about you:

* name
* favorite food
* hair color
* eye color

---

### Objects: accessing properties

Now we know how to create objects, what can we do with it?

```js
let me = {
    name: "Mellina",
    age: 19
};

// we can access the value of a property using the . operator
let myName = me.name; // myName points to "Mellina"

// we can also change the value
me.age = 20;
```

---

### Task

Write a function that takes an object as parameter and introduces that person to `console.log`.

Example output:

```js
"Hi, I am Harald and my favorite food is pizza".
```

---

### Task

Now create another object called `friend` with the same properties as `me`.

Introduce your friend to `console.log`.

Example output:

```js
"Hi, I am Owen and my favorite food is hamburger".
```
