
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Простой калькулятор</title>
    <style>
        input, button {
            width: 50px;
            height: 50px;
            font-size: 180px;
            margin: 50px;
        }
    </style>
</head>
<body>
    
  
<div id="calendar"></div>


    <h2>Калькулятор</h2>

    <input type="text" id="result" disabled>

    <br>

    <button onclick="appendToResult('1')">1</button>
    <button onclick="appendToResult('2')">2</button>
    <button onclick="appendToResult('3')">3</button>
    <button onclick="appendToResult('+')">+</button>

    <br>

    <button onclick="appendToResult('4')">4</button>
    <button onclick="appendToResult('5')">5</button>
    <button onclick="appendToResult('6')">6</button>
    <button onclick="appendToResult('-')">-</button>

    <br>

    <button onclick="appendToResult('7')">7</button>
    <button onclick="appendToResult('8')">8</button>
    <button onclick="appendToResult('9')">9</button>
    <button onclick="appendToResult('*')">*</button>

    <br>

    <button onclick="clearResult()">C</button>
    <button onclick="appendToResult('0')">0</button>
    <button onclick="calculateResult()">=</button>
    <button onclick="appendToResult('/')">/</button>

    <script>
        function appendToResult(value) {
            document.getElementById('result').value += value;
        }

        function clearResult() {
            document.getElementById('result').value = '';
        }

        function calculateResult() {
            try {
                document.getElementById('result').value = eval(document.getElementById('result').value);
            } catch (error) {
                document.getElementById('result').value = 'Error';
            }
        }
    </script>
    <nav>
        <ul>
            <ul><a href="#about">О нас</a></ul>
            <ul><a href="#services">Услуги</a></ul>
            <ul><a href="#contact">Контакты</a></ul>
        </ul>
    </nav>
  


    <section id="services">
        <h2>Услуги</h2>
        <li> информация о предостав
