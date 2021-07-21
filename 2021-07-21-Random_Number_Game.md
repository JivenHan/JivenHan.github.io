# Random Number Game

##조건은 다음과 같다

- Find a random number on a range between 0 and a number defined by the user.
- Update the range value in real time.
- Only play after the user chooses a number.
- Notify the user if the game is lost or won.

```html
<body>
    <h1>Random Number Game</h1>
    <form id="start">
      <h2>
        Generate a number between 0 and
        <input required type="number" min="1" id="setRange" />
      </h2>
      <h3>
        Guess the number:
        <input required type="number" id="guess" min="0" />
        <input type="submit" value="Play!" />
      </h3>
      <h3 id="status"></h3>
      <h3 id="result"></h3>
    </form>
    <script src="slot.js"></script>
  </body>
```

```js

const start = document.querySelector("#start");
const setRange = document.querySelector("#setRange");
const guess = document.querySelector("#guess");
const status = document.querySelector("#status");
const result = document.querySelector("#result");

function check(event) {
  event.preventDefault();
  const randomNumber = Math.round(Math.random()*setRange.value);
  const guessNumber = parseInt(guess.value);
  status.textContent = `You chose: ${guessNumber}, the machine chose: ${randomNumber}`;
  if (guessNumber === randomNumber) {
    result.textContent = "You win!";
  } else {
    result.textContent = "You lost!";
  }
}

start.addEventListener("submit", check);
```

