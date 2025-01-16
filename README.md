<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hidden Folder Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f9;
    }

    .calculator {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      width: 300px;
    }

    .calculator input {
      width: 100%;
      height: 50px;
      margin-bottom: 10px;
      text-align: right;
      font-size: 1.5rem;
      padding: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    .calculator .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    .calculator button {
      height: 50px;
      background: #007bff;
      color: #fff;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
    }

    .calculator button:hover {
      background: #0056b3;
    }

    .hidden-folder {
      display: none;
      margin-top: 20px;
      padding: 10px;
      background: #f9f9f9;
      border: 1px dashed #007bff;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="result" placeholder="0" readonly>
    <div class="buttons">
      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button onclick="appendValue('/')">/</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button onclick="appendValue('*')">*</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button onclick="appendValue('-')">-</button>

      <button onclick="appendValue('0')">0</button>
      <button onclick="clearResult()">C</button>
      <button onclick="calculateResult()">=</button>
      <button onclick="appendValue('+')">+</button>
    </div>

    <!-- Hidden folder message -->
    <div id="hiddenFolder" class="hidden-folder">
      Hidden Folder Unlocked!
    </div>
  </div>

  <script>
    let resultInput = document.getElementById("result");

    function appendValue(value) {
      resultInput.value += value;
    }

    function clearResult() {
      resultInput.value = "";
    }

    function calculateResult() {
      try {
        // Evaluate the expression safely
        const result = Function("return " + resultInput.value)();
        resultInput.value = result;

        // Trigger hidden folder if specific condition is met
        if (result === 42) { // Example: If the result is 42
          document.getElementById("hiddenFolder").style.display = "block";
        } else {
          document.getElementById("hiddenFolder").style.display = "none";
        }
      } catch (error) {
        alert("Invalid calculation");
        clearResult();
      }
    }
  </script>
</body>
</html>
# calculator
