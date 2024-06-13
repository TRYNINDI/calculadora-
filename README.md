<!DOCTYPE html>
<html>
<head>
  <title>HTML Calculator</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      font-family: "Helvetica Neue", sans-serif;
      box-sizing: border-box;
    }
    body {
      background-color: #8bc6ec;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .container {
      background: #000000;
      padding: 25px;
      width: 350px;
      border-radius: 10px;
    }
    .calc-text {
      margin-bottom: 20px;
      padding-left: 5px;
    }
    .calc-text p {
      width: 100%;
      font-size: 3.5rem;
      text-align: end;
      background: transparent;
      color: #fff;
      border: none;
      outline: none;
      word-wrap: break-word;
      word-break: break-all;
    }
    button {
      background: #333333;
      color: #fff;
      font-size: 1.5rem;
      border: none;
      border-radius: 70%;
      cursor: pointer;
      height: 65px;
      width: 65px;
    }
    button:active, button:focus {
      filter: brightness(120%);
    }
    .calc-keys {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-row-gap: 15px;
      grid-column-gap: 10px;
    }
    .key-zero {
      grid-column: span 2;
      width: 100%;
      border-radius: 30px;
    }
    .key-operate {
      background: #ff9501;
    }
    .key-others {
      background: #a6a6a6;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="calc-text">
      <p name="user-input" id="user-input">0</p>
    </div>
    <div class="calc-keys">
      <button type="button" class="numbers">7</button>
      <button type="button" class="numbers">8</button>
      <button type="button" class="numbers">9</button>
      <button type="button" class="key-operate operations">/</button>
      <button type="button" class="numbers">4</button>
      <button type="button" class="numbers">5</button>
      <button type="button" class="numbers">6</button>
      <button type="button" class="key-operate operations">*</button>
      <button type="button" class="numbers">1</button>
      <button type="button" class="numbers">2</button>
      <button type="button" class="numbers">3</button>
      <button type="button" class="key-operate operations">-</button>
      <button type="button" class="key-zero numbers">0</button>
      <button type="button" class="numbers">.</button>
      <button type="button" class="key-operate operations">=</button>
      <button type="button" class="key-operate operations">+</button>
      <button type="button" class="key-others">AC</button>
      <button type="button" class="key-others">DEL</button>
    </div>
  </div>
  <script>
    const inputValue = document.getElementById("user-input");
    const number = document.querySelectorAll(".numbers");
    const calculate = document.querySelectorAll(".operations");
    let lastValue = "";

    number.forEach(function(item) {
      item.addEventListener("click", function(e) {
        if (inputValue.innerText === "NaN") {
          inputValue.innerText = "";
        }
        if (inputValue.innerText === "0") {
          inputValue.innerText = "";
        }
        inputValue.innerText += e.target.innerHTML.trim();
      });
    });

    calculate.forEach(function(item) {
      item.addEventListener("click", function(e) {
        if (e.target.innerHTML === "=") {
          inputValue.innerText = eval(inputValue.innerText);
        } else if (e.target.innerHTML === "AC") {
          inputValue.innerText = 0;
        } else if (e.target.innerHTML === "DEL") {
          inputValue.innerText = inputValue.innerText.substring(0, inputValue.innerText.length - 1);
          if (inputValue.innerText.length == 0) {
            inputValue.innerText = 0;
          }
        } else {
          lastValue = inputValue.innerText.substring(inputValue.innerText.length - 1, inputValue.innerText.length);
          if (!isNaN(lastValue)) {
            inputValue.innerText += e.target.innerHTML;
          }
        }
      });
    });
  </script>
</body
