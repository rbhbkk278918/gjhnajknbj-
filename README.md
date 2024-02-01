
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шахматы</title>
    <style>
        .chessboard {
            display: grid;
            grid-template-columns: repeat(8, 50px);
            grid-template-rows: repeat(8, 50px);
        }

        .square {
            width: 50px;
            height: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            background-color: #eee;
        }

        .white {
            background-color: #fff;
        }

        .draggable {
            cursor: pointer;
            user-select: none;
        }
    </style>
</head>
<body>

<div id="chessboard" class="chessboard"></div>

<script>
    document.addEventListener('DOMContentLoaded', function () {
        const chessboard = document.getElementById('chessboard');

        // Создаем шахматную доску
        for (let row = 0; row < 8; row++) {
            for (let col = 0; col < 8; col++) {
                const square = document.createElement('div');
                square.className = `square ${((row + col) % 2 === 0) ? 'white' : ''}`;
                square.dataset.row = row;
                square.dataset.col = col;

                chessboard.appendChild(square);
            }
        }

        // Задаем начальное расположение фигур с перемешиванием
        setStartingPosition();

        // Добавляем обработчики событий для перемещения фигур
        document.querySelectorAll('.square').forEach((square) => {
            square.addEventListener('mousedown', startDrag);
        });
    });

    function setStartingPosition() {
        const pieces = ['♜', '♞', '♝', '♛', '♚', '♝', '♞', '♜'];
        const shuffledPieces = shuffleArray(pieces);

        document.querySelectorAll('.square').forEach((square, index) => {
            const row = Math.floor(index / 8);
            const col = index % 8;

            if (row === 0 || row === 7) {
                square.textContent = shuffledPieces[col];
                square.classList.add('draggable');
            }

            if (row === 1 || row === 6) {
                square.textContent = '♟';
                square.classList.add('draggable');
            }
        });
    }

    function shuffleArray(array) {
        // Простой алгоритм перемешивания массива
        for (let i = array.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]];
        }
        return array;
    }

    let draggedPiece = null;

    function startDrag(event) {
        const square = event.target;
        if (square.classList.contains('draggable')) {
            draggedPiece = square;
            document.addEventListener('mousemove', dragPiece);
            document.addEventListener('mouseup', endDrag);
        }
    }

    function dragPiece(event) {
        if (draggedPiece) {
            const mouseX = event.clientX - draggedPiece.clientWidth / 2;
            const mouseY = event.clientY - draggedPiece.clientHeight / 2;

            draggedPiece.style.position = 'absolute';
            draggedPiece.style.zIndex = 1000;
            draggedPiece.style.left = mouseX + 'px';
            draggedPiece.style.top = mouseY + 'px';
        }
    }

    function endDrag() {
        if (draggedPiece) {
            const mouseX = event.clientX;
            const mouseY = event.clientY;

            // Найти клетку, над которой находится фигура
            const targetSquare = document.elementFromPoint(mouseX, mouseY);

            // Проверяем, что targetSquare — клетка доски и она не пуста
            if (targetSquare && targetSquare.classList.contains('square') && targetSquare.textContent === '') {
                targetSquare.textContent = draggedPiece.textContent;
                draggedPiece.textContent = ''; // очищаем исходную клетку
                draggedPiece.style.position = '';
                draggedPiece.style.zIndex = '';
                draggedPiece.style.left = '';
                draggedPiece.style.top = '';

                document.removeEventListener('mousemove', dragPiece);
                document.removeEventListener('mouseup', endDrag);

                draggedPiece = null;
            } else {
                // Возвращаем фигуру на исходное место
                draggedPiece.style.position = '';
                draggedPiece.style.zIndex = '';
                draggedPiece.style.left = '';
                draggedPiece.style.top = '';
            }
        }
    }
</script>


