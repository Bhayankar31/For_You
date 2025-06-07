<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Calculator App</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
  />
  <style>
    /* Remove number input arrows */
    input[type="text"]::-webkit-inner-spin-button,
    input[type="text"]::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
    input[type="text"] {
      -moz-appearance: textfield;
    }
  </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen p-4">
  <div class="bg-white rounded-xl shadow-lg w-full max-w-md">
    <div class="p-6">
      <h1 class="text-3xl font-bold text-center mb-6 text-gray-800">Calculator</h1>
      <input
        type="text"
        id="display"
        class="w-full text-right text-4xl font-mono p-4 rounded-lg border border-gray-300 mb-6 focus:outline-none focus:ring-2 focus:ring-indigo-500"
        readonly
        aria-label="Calculator display"
        value="0"
      />
      <div class="grid grid-cols-4 gap-4">
        <button
          type="button"
          class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-semibold py-4 rounded-lg transition"
          data-action="clear"
          aria-label="Clear"
        >
          C
        </button>
        <button
          type="button"
          class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-semibold py-4 rounded-lg transition"
          data-action="backspace"
          aria-label="Backspace"
        >
          <i class="fas fa-backspace"></i>
        </button>
        <button
          type="button"
          class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-semibold py-4 rounded-lg transition"
          data-action="percent"
          aria-label="Percent"
        >
          %
        </button>
        <button
          type="button"
          class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-4 rounded-lg transition"
          data-action="operator"
          data-value="/"
          aria-label="Divide"
        >
          &divide;
        </button>

        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="7"
          aria-label="Seven"
        >
          7
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="8"
          aria-label="Eight"
        >
          8
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="9"
          aria-label="Nine"
        >
          9
        </button>
        <button
          type="button"
          class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-4 rounded-lg transition"
          data-action="operator"
          data-value="*"
          aria-label="Multiply"
        >
          &times;
        </button>

        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="4"
          aria-label="Four"
        >
          4
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="5"
          aria-label="Five"
        >
          5
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="6"
          aria-label="Six"
        >
          6
        </button>
        <button
          type="button"
          class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-4 rounded-lg transition"
          data-action="operator"
          data-value="-"
          aria-label="Minus"
        >
          &minus;
        </button>

        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="1"
          aria-label="One"
        >
          1
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="2"
          aria-label="Two"
        >
          2
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="3"
          aria-label="Three"
        >
          3
        </button>
        <button
          type="button"
          class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-4 rounded-lg transition"
          data-action="operator"
          data-value="+"
          aria-label="Plus"
        >
          +
        </button>

        <button
          type="button"
          class="col-span-2 bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="number"
          data-value="0"
          aria-label="Zero"
        >
          0
        </button>
        <button
          type="button"
          class="bg-gray-100 hover:bg-gray-200 text-gray-900 font-semibold py-4 rounded-lg transition"
          data-action="decimal"
          aria-label="Decimal point"
        >
          .
        </button>
        <button
          type="button"
          class="bg-green-600 hover:bg-green-700 text-white font-semibold py-4 rounded-lg transition"
          data-action="equals"
          aria-label="Equals"
        >
          =
        </button>
      </div>
    </div>
  </div>

  <script>
    (() => {
      const display = document.getElementById("display");
      let currentInput = "0";
      let lastInput = null;
      let operator = null;
      let resetNext = false;

      function updateDisplay() {
        display.value = currentInput;
      }

      function clearAll() {
        currentInput = "0";
        lastInput = null;
        operator = null;
        resetNext = false;
        updateDisplay();
      }

      function backspace() {
        if (resetNext) {
          clearAll();
          return;
        }
        if (currentInput.length > 1) {
          currentInput = currentInput.slice(0, -1);
        } else {
          currentInput = "0";
        }
        updateDisplay();
      }

      function appendNumber(num) {
        if (resetNext) {
          currentInput = num;
          resetNext = false;
          updateDisplay();
          return;
        }
        if (currentInput === "0") {
          currentInput = num;
        } else {
          currentInput += num;
        }
        updateDisplay();
      }

      function appendDecimal() {
        if (resetNext) {
          currentInput = "0.";
          resetNext = false;
          updateDisplay();
          return;
        }
        if (!currentInput.includes(".")) {
          currentInput += ".";
          updateDisplay();
        }
      }

      function setOperator(op) {
        if (operator && !resetNext) {
          calculate();
        }
        lastInput = parseFloat(currentInput);
        operator = op;
        resetNext = true;
      }

      function calculate() {
        if (operator === null || resetNext) return;
        const current = parseFloat(currentInput);
        let result = 0;
        switch (operator) {
          case "+":
            result = lastInput + current;
            break;
          case "-":
            result = lastInput - current;
            break;
          case "*":
            result = lastInput * current;
            break;
          case "/":
            if (current === 0) {
              alert("Error: Division by zero");
              clearAll();
              return;
            }
            result = lastInput / current;
            break;
          default:
            return;
        }
        currentInput = String(result);
        operator = null;
        lastInput = null;
        resetNext = true;
        updateDisplay();
      }

      function percent() {
        let num = parseFloat(currentInput);
        num = num / 100;
        currentInput = String(num);
        updateDisplay();
      }

      document.querySelectorAll("button").forEach((btn) => {
        btn.addEventListener("click", () => {
          const action = btn.getAttribute("data-action");
          const value = btn.getAttribute("data-value");
          switch (action) {
            case "clear":
              clearAll();
              break;
            case "backspace":
              backspace();
              break;
            case "number":
              appendNumber(value);
              break;
            case "decimal":
              appendDecimal();
              break;
            case "operator":
              setOperator(value);
              break;
            case "equals":
              calculate();
              break;
            case "percent":
              percent();
              break;
          }
        });
      });

      // Keyboard support
      window.addEventListener("keydown", (e) => {
        if (
          (e.key >= "0" && e.key <= "9") ||
          e.key === "." ||
          e.key === "+" ||
          e.key === "-" ||
          e.key === "*" ||
          e.key === "/" ||
          e.key === "Enter" ||
          e.key === "Backspace" ||
          e.key === "Escape" ||
          e.key === "%"
        ) {
          e.preventDefault();
          if (e.key >= "0" && e.key <= "9") {
            appendNumber(e.key);
          } else if (e.key === ".") {
            appendDecimal();
          } else if (e.key === "+" || e.key === "-" || e.key === "*" || e.key === "/") {
            setOperator(e.key);
          } else if (e.key === "Enter") {
            calculate();
          } else if (e.key === "Backspace") {
            backspace();
          } else if (e.key === "Escape") {
            clearAll();
          } else if (e.key === "%") {
            percent();
          }
        }
      });
    })();
  </script>
</body>
</html>
