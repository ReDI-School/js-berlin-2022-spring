<!-- .slide: id="lesson8" -->

# Basic Frontend - Spring 2022

Lesson 8, Tuesday, 2022-04-12

---

### Lesson overview

* Object properties
* Variable lifetime
* Manipulate HTML Elements from JavaScript

---

### Recap

Can you explain the following?

```js
let me = {
    name: "Mariana",
    isTeacher: true,
    age: 21
};
```

How would you access Mariana's age?
<!-- .element: class="fragment" -->

```js
let marianaAge = me.age;
```
<!-- .element: class="fragment" -->


---

### Object Properties

Objects consist of key-value pairs (also called properties).

Keys point to values.

Mariana's object consists of three properties, pointing to a string, a boolean and a number. What other data types can we use?

---

```js
let me = {
    name: "Harald",
    address: {
        street: "Invalidenstraße",
        city: "Berlin"
    }
};
```

How many properties does the object above have? How can you access the `city` in the `me` variable above?

```js
let myCity = me.address.city;
```
<!-- .element: class="fragment" -->

---

```js
let me = {
    name: "Harald",
    greeting: function() {
        if (dayOfWeek === "Monday") {
            return "Get out of my face";
        } else {
            return "Hi, how are you?";
        }
    }
};
```

How would you call the greeting function?

```js
let greeting = me.greeting();
```
<!-- .element: class="fragment" -->

---

### Methods

A function inside an object is also called **method**:

```js
// I am a function!
function hi() { return "Hi!"; }

let me = {
    // I'm a method!
    hi: function() { return "Hi!"; }
};
```

---

### Variable lifetime

```js
console.log(x); // 1
{
    console.log(x); // 2
    let x = 42;
    console.log(x); // 3
}
console.log(x); // 4
```

Which of the `console.log` above are valid?

Only 3. 1, 2, and 4 throw errors.
<!-- .element: class="fragment" -->

---

### Variable lifetime

When you open a scope with `{`, e.g. for `if` statements or `function`, the variables you define inside the curly braces only exist within that block.

Variables you define outside any curly braces exist during the entire lifetime of your html page:

```js
// I exist as long as the html page exists!
let clickCount = 0;

function onButtonClick() {
    clickCount += 1;
}
```

---

### Manipulate HTML Elements from JavaScript

Let's say we have a HTML element:

```html
<div>Total Price: 0 EUR</div>
```

Wouldn't it be nice if we could dynamically change that from JavaScript?

---

### document.getElementById

One way to obtain a variable pointing to a HTML element is `document.getElementById()`:

HTML:

```html
<div id="totalPrice">Total Price: 0 EUR</div>
```

JavaScript

```js
let priceDiv = document.getElementById("totalPrice");
```

---

`priceDiv` is a variable, and its type is `object`.

How do we know which properties/methods the object has?

We could try the browser's developer tools.

Or we could check MDN:

https://developer.mozilla.org/en-US/docs/Web/API/HTMLDivElement


---

Let's try some properties, see what happens:

```js
let priceDiv = document.getElementById("totalPrice");
// choose from below:
// priceDiv.textContent = "Hi from JavaScript";
// priceDiv.hidden = true;
// priceDiv.style.backgroundColor = "red";
// priceDiv.remove();
```

---

### Task 1

In HTML, create a `div` element and a `button`.

When the user clicks the button, set the background color of the `div` to red.

---

### Task 2

In HTML, create a `button` and a `div` element.

When the user clicks the button, update the `textContent` of the `div` element with the amount of times the user has clicked the button.

Example: "You clicked 12 times"

---

### Task 3

We're creating a web shop selling hummus (or chocolate, or eba and egusi soup)!

Create a number input field in HTML that lets the user choose the amount of hummus:

```html
Choose the amount of hummus servings:
<input type="number" id="amount" min="0" value="0" oninput="amountChanged()">
```

Use the `valueAsNumber` property of the number input to get the amount that the user selected in your `amountChanged` function. Output the total price the user has to pay to a `div` element.

---

### Task 4 (Bonus)

Extend your webshop to sell two products (e.g. hummus _and_ chocolate).

Every product has a different price. Update the total price in the `div` element every time the user changes the amount of hummus and chocolate.

---

### Task 5 (Bonus)

There's a special sale - if the user buys products for more than 20 EUR, they get 10% rebate.

---

### Solution Task 1

HTML:

```html
<button onclick="changeColor()">Click me!</button>
<div id="myDiv">Hello</div>
<script>
    function changeColor() {
        let myDiv = document.getElementById("myDiv");
        myDiv.style.backgroundColor = "red";
    }
</script>
```

---

### Solution Task 2

```html
<button onclick="count()">Click me!</button>
<div id="myDiv">You clicked 0 times</div>
<script>
    let clickCount = 0;
    function count() {
        clickCount += 1;
        let myDiv = document.getElementById("myDiv");
        myDiv.textContent = "You clicked " + clickCount + " times";
    }
</script>
```

---

### Solution Task 3

```html
<input type="number" id="amount" min="0" value="0" oninput="amountChanged()">
<div id="priceDiv">0 EUR</div>
<script>
    let hummusPrice = 5;
    function amountChanged() {
        let amountElement = document.getElementById("amount");
        let priceDiv = document.getElementById("priceDiv");
        let amount = amountElement.valueAsNumber;
        let totalPrice = hummusPrice * amount;
        priceDiv.textContent = totalPrice + " EUR"
    }
</script>
```
