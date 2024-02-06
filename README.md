
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Инженерный Калькулятор</title>
    
</head>
<body>

    <input type="text" id="display" readonly>
    <br>
    <button onclick="clearDisplay()">C</button>
    <button onclick="backspace()">⌫</button>
    <button onclick="appendToDisplay('sin(')">sin</button>
    <button onclick="appendToDisplay('cos(')">cos</button>
    <button onclick="appendToDisplay('tan(')">tan</button>
    <br>
    <button onclick="appendToDisplay('log(')">log</button>
    <button onclick="appendToDisplay('exp(')">exp</button>
    <button onclick="appendToDisplay('sqrt(')">√</button>
    <button onclick="appendToDisplay('pi')">π</button>
    <button onclick="appendToDisplay('**')">^</button>
    <br>
    <button onclick="appendToDisplay('7')">7</button>
    <button onclick="appendToDisplay('8')">8</button>
    <button onclick="appendToDisplay('9')">9</button>
    <button onclick="appendToDisplay('+')">+</button>
    <button onclick="appendToDisplay('-')">-</button>
    <br>
    <button onclick="appendToDisplay('4')">4</button>
    <button onclick="appendToDisplay('5')">5</button>
    <button onclick="appendToDisplay('6')">6</button>
    <button onclick="appendToDisplay('*')">*</button>
    <button onclick="appendToDisplay('/')">/</button>
    <br>
    <button onclick="appendToDisplay('1')">1</button>
    <button onclick="appendToDisplay('2')">2</button>
    <button onclick="appendToDisplay('3')">3</button>
    <button onclick="appendToDisplay('('">(</button>
    <button onclick="appendToDisplay(')')">)</button>
    <br>
    <button onclick="appendToDisplay('0')">0</button>
    <button onclick="appendToDisplay('.')">.</button>
    <button onclick="calculate()">=</button>
    <button onclick="appendToDisplay('abs(')">|x|</button>
    <button onclick="appendToDisplay('!')">!</button>
    <button onclick="appendToDisplay('sinDeg(')">sinDeg</button>
    <button onclick="appendToDisplay('cosDeg(')">cosDeg</button>
    <button onclick="appendToDisplay('tanDeg(')">tanDeg</button>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function backspace() {
            var currentValue = document.getElementById('display').value;
            document.getElementById('display').value = currentValue.substring(0, currentValue.length - 1);
        }

        function calculate() {
            try {
                // Замена символа '**' на '^' перед вычислением
                var expression = document.getElementById('display').value.replace(/\*\*/g, '^');
                // Вычисление факториала
                expression = expression.replace(/(\d+)!/g, function(match, p1) {
                    return factorial(parseInt(p1));
                });
                var result = eval(expression);
                document.getElementById('display').value = result;
            } catch (error) {
                document.getElementById('display').value = 'Ошибка';
            }
        }

        function factorial(n) {
            if (n === 0 || n === 1) {
                return 1;
            }
            return n * factorial(n - 1);
        }
    </script>


