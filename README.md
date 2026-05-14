# codealpha_calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic Calculator</title>
  <style>
    body {
      background: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      font-family: 'Segoe UI', sans-serif;
    }

    .calculator {
      background: #222;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0,0,0,0.3);
    }

    #display {
      width: 100%;
      height: 60px;
      font-size: 24px;
      text-align: right;
      margin-bottom: 15px;
      border: none;
      border-radius: 8px;
      padding: 10px;
      background: #fff;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 70px);
      gap: 10px;
    }

    .btn {
      background: #333;
      color: #fff;
      font-size: 20px;
      border: none;
      border-radius: 8px;
      padding: 15px;
      cursor: pointer;
      transition: background 0.3s;
    }

    .btn:hover {
      background: #555;
    }

    .equal {
      background: #ff9500;
      color: white;
    }

    .equal:hover {
      background: #ffa733;
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled>
    <div class="buttons">
      <button class="btn" onclick="clearDisplay()">C</button>
      <button class="btn" onclick="deleteLast()">⌫</button>
      <button class="btn" onclick="appendValue('/')">÷</button>
      <button class="btn" onclick="appendValue('*')">×</button>

      <button class="btn" onclick="appendValue('7')">7</button>
      <button class="btn" onclick="appendValue('8')">8</button>
      <button class="btn" onclick="appendValue('9')">9</button>
      <button class="btn" onclick="appendValue('-')">−</button>

      <button class="btn" onclick="appendValue('4')">4</button>
      <button class="btn" onclick="appendValue('5')">5</button>
      <button class="btn" onclick="appendValue('6')">6</button>
      <button class="btn" onclick="appendValue('+')">+</button>

      <button class="btn" onclick="appendValue('1')">1</button>
      <button class="btn" onclick="appendValue('2')">2</button>
      <button class="btn" onclick="appendValue('3')">3</button>
      <button class="btn equal" onclick="calculate()">=</button>

      <button class="btn zero" onclick="appendValue('0')">0</button>
      <button class="btn" onclick="appendValue('.')">.</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function appendValue(value) {
      display.value += value;
    }

    function clearDisplay() {
      display.value = '';
    }

    function deleteLast() {
      display.value = display.value.slice(0, -1);
    }

    function calculate() {
      try {
        display.value = eval(display.value);
      } catch {
        display.value = 'Error';
      }
    }

    // Keyboard support
    document.addEventListener('keydown', (event) => {
      const key = event.key;
      if (!isNaN(key) || ['+', '-', '*', '/', '.'].includes(key)) {
        appendValue(key);
      } else if (key === 'Enter') {
        calculate();
      } else if (key === 'Backspace') {
        deleteLast();
      } else if (key.toLowerCase() === 'c') {
        clearDisplay();
      }
    });
  </script>
</body>
</html>
