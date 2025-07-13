`html
<!DOCTYPE html>
<html>
<head>
  <title>Tic Tac Toe</title>
  <style>
    body { text-align: center; font-family: sans-serif; }
    table { margin: auto; border-collapse: collapse; }
    td {
      width: 80px; height: 80px; font-size: 2em;
      text-align: center; border: 1px solid #000;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Tic Tac Toe</h1>
  <table>
    <tr><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td></tr>
    <tr><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td></tr>
    <tr><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td><td onclick="makeMove(this)"></td></tr>
  </table>
  <p id="winner"></p>
  <script>
    let currentPlayer = 'X';
    function makeMove(cell) {
      if (cell.innerHTML !== '') return;
      cell.innerHTML = currentPlayer;
      if (checkWinner()) {
        document.getElementById('winner').innerText = currentPlayer + ' wins!';
        disableBoard();
      } else {
        currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
      }
    }
    function checkWinner() {
[13/07, 9:08 pm] ChatGPT: const cells = Array.from(document.querySelectorAll('td')).map(td => td.innerHTML);
      const wins = [
        [0,1,2], [3,4,5], [6,7,8],
        [0,3,6], [1,4,7], [2,5,8],
        [0,4,8], [2,4,6]
      ];
      return wins.some(indices => {
        const [a,b,c] = indices;
        return cells[a] && cells[a] === cells[b] && cells[a] === cells[c];
      });
    }
    function disableBoard() {
      document.querySelectorAll('td').forEach(td => td.onclick = null);
    }
  </script>
</body>
</html># My-Project