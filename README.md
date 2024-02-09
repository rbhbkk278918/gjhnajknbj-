

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
    <button onclick="appendToDisplay('Math.sin(')">sin</button>
    <button onclick="appendToDisplay('Math.cos(')">cos</button>
    <button onclick="appendToDisplay('Math.tan(')">tan</button>
    <br>
    <button onclick="appendToDisplay('Math.log(')">log</button>
    <button onclick="appendToDisplay('Math.exp(')">exp</button>
    <button onclick="appendToDisplay('Math.sqrt(')">√</button>
    <button onclick="appendToDisplay('Math.PI')">π</button>
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
    <button onclick="appendToDisplay('Math.abs(')">|x|</button>
    <button onclick="appendToDisplay('!')">!</button>
    <button onclick="appendToDisplay('Math.sin(Math.PI/180*')">sinDeg</button>
    <button onclick="appendToDisplay('Math.cos(Math.PI/180*')">cosDeg</button>
    <button onclick="appendToDisplay('Math.tan(Math.PI/180*')">tanDeg</button>

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
            
            // Добавленные алгоритмы
            expression = expression.replace(/Math.sin\(/g, 'customSin(');
            expression = expression.replace(/Math.cos\(/g, 'customCos(');
            expression = expression.replace(/Math.tan\(/g, 'customTan(');
            expression = expression.replace(/Math.sqrt\(/g, 'customSqrt(');

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

    // Добавленные функции для кастомных вычислений
    function customSin(value) {
        return Math.sin(value);
    }

    function customCos(value) {
        return Math.cos(value);
    }

    function customTan(value) {
        return Math.tan(value);
    }

    function customSqrt(value) {
        return Math.sqrt(value);
    }
</script>

