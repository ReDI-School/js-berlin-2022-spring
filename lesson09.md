<!-- .slide: id="lesson9" -->

# Basic Frontend - Spring 2022

Lesson 9, Thursday, 2022-04-14

---

### Recap

What do you remember from last lesson?

---

### Task

The easter bunny goes digital and needs your help!

Write a HTML page with 5 buttons and an image (you can choose an image from e.g. https://giphy.com/explore/easter-eggs). Make sure you set `hidden=true`.

```html
<iframe hidden=true id="easterEgg" src="https://giphy.com/embed/GL9C4Dpmc2Ig1Bq9FT" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
```

4 of the buttons do nothing.

1 of the buttons shows the image (e.g. set `hidden` to `false`).

---

### Bonus

Every time the page loads, a different button should reveal the easter egg.

To get a random number between zero and 4, you can use:

```js
function getRandomInt() {
  return Math.floor(Math.random() * 4);
}
```

---

### Solution

```html
<button onclick="showEasterEgg(0)">Easter Egg?</button>
<button onclick="showEasterEgg(1)">Easter Egg?</button>
<!-- and so on -->
```

```js
let randomIndex = getRandomInt(); // from slide before
let easterEgg = document.getElementById("easterEgg");

function showEasterEgg(index) {
    if (index === randomIndex) {
        easterEgg.hidden = false;
    } else {
        easterEgg.hidden = true;
    }
}
```
