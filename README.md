
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Инженерный Калькулятор</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }

        input {
            width: 200px;
            font-size: 18px;
            padding: 5px;
            margin-bottom: 10px;
        }

        button {
            font-size: 16px;
            padding: 10px;
            margin: 5px;
        } <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }

        input {
            width: 240px;
            font-size: 20px;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #fff;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        button {
            font-size: 18px;
            padding: 15px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background-color: #4caf50;
            color: #fff;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        button:hover {
            background-color: #45a049;
        }

        .row {
            display: flex;
            justify-content: center;
        }

        .column {
            flex: 20%;
        }

        .calculator-container {
            max-width: 400px;
            margin: 0 auto;
        }
  
    </style>
</head>
<body>
    <input type="text" id="display" readonly>
    <br>
    <button onclick="clearDisplay()">C</button>
    <button onclick="backspace()">⌫</button>
    <button onclick="appendToDisplay('customSin(')">sin</button>
    <button onclick="appendToDisplay('customCos(')">cos</button>
    <button onclick="appendToDisplay('customTan(')">tan</button>
    <br>
    <button onclick="appendToDisplay('Math.log(')">log</button>
    <button onclick="appendToDisplay('Math.exp(')">exp</button>
    <button onclick="appendToDisplay('customSqrt(')">√</button>
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
    <button onclick="appendToDisplay('customSin(Math.PI/180*')">sinDeg</button>
    <button onclick="appendToDisplay('customCos(Math.PI/180*')">cosDeg</button>
    <button onclick="appendToDisplay('customTan(Math.PI/180*')">tanDeg</button>

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
                var expression = document.getElementById('display').value.replace(/\*\*/g, '^');
                expression = expression.replace(/(\d+)!/g, function(match, p1) {
                    return factorial(parseInt(p1));
                });

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

        function customSin(value) {
            var radians = value * Math.PI / 180;
            return Math.sin(radians);
        }

        function customCos(value) {
            var radians = value * Math.PI / 180;
            return Math.cos(radians);
        }

        function customTan(value) {
            var radians = value * Math.PI / 180;
            return Math.tan(radians);
        }

        function customSqrt(value) {
            if (value < 0) {
                return 'Ошибка: Квадратный корень из отрицательного числа';
            }
            return Math.sqrt(value);
        }

        // Keyboard input handling
        document.addEventListener('keydown', function(event) {
            // Allow numbers, operators, and some special keys
            if (/[\d\+\-\*\/\(\)\.\^]/.test(event.key)) {
                appendToDisplay(event.key);
            } else if (event.key === 'Enter') {
                calculate();
            } else if (event.key === 'Backspace') {
                backspace();
            }
        });
    </script>
  
<li> ВНИМАНИЕ  для Работоспособность калькулятора при выполнении функции  sin cos tg  корень из числа 
 нужно  при вписании  цифры  закрыть скобку </li>
<img src="https://img5.lalafo.com/i/posters/api/b3/09/96/8b3342a4ea85af14b775c85842.jpeg.jpg" alt="Описание изображения">
<img src="https://i.ytimg.com/vi/LRaLsVDTh8U/hqdefault.jpg.jpg" alt="Описание изображения">
<img src="https://sun9-14.userapi.com/c9375/g18539923/a_3ea5be04.jpg.jpg" alt="Описание изображения">
<img src="https://www.sostav.ru/articles/rus/2010/28.06/news/images/Baltika-3_Outdoor_m.jpg.jpg" alt="Описание изображения">
    <p>&copy; 2024 Разработчик  Dylan9332789Z Все права защищены. | <span id="companyLink"></span></p>
    

