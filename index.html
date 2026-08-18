<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Пазл (клик-обмен) → Гифка</title>
<style>
  :root { --size: 360px; --n: 3; }
  * { box-sizing: border-box; }
  body {
    margin: 0; min-height: 100vh;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    gap: 16px; padding: 20px;
    font-family: system-ui, sans-serif;
    background: #0f1226; color: #e9ecff;
  }
  h1 { font-size: 20px; margin: 0; }
  .panel {
    display: flex; flex-wrap: wrap; gap: 14px;
    justify-content: center; align-items: center;
    background: #1a1e3c; padding: 14px 18px; border-radius: 12px;
  }
  .field { display: flex; flex-direction: column; gap: 4px; font-size: 12px; color: #aab2e6; }
  input[type=file] { font-size: 12px; color: #e9ecff; max-width: 200px; }

  .stage {
    position: relative;
    width: var(--size); height: var(--size);
    border-radius: 14px; overflow: hidden;
    box-shadow: 0 20px 50px rgba(0,0,0,.45);
    background: #11142b;
  }

  /* Единое поле */
  #board {
    position: absolute; inset: 0;
    display: grid;
    grid-template-columns: repeat(var(--n), 1fr);
    grid-template-rows: repeat(var(--n), 1fr);
    gap: 2px;
  }
  .tile {
    background-size: var(--size) var(--size);
    background-repeat: no-repeat;
    cursor: pointer;
    transition: transform .12s ease, filter .12s ease, outline-color .12s;
    outline: 0 solid transparent;
  }
  .tile:hover { filter: brightness(1.12); }
  .tile.selected {
    outline: 3px solid #5b6cff;
    outline-offset: -3px;
    transform: scale(.94);
    z-index: 2;
  }

  /* Результат — гифка / анимация после победы */
  #result {
    position: absolute; inset: 0;
    background-size: cover; background-position: center;
    opacity: 0; transform: scale(.96);
    transition: opacity .5s ease, transform .5s ease;
    pointer-events: none;
  }
  .stage.solved #board { opacity: 0; transition: opacity .4s ease; }
  .stage.solved #result { opacity: 1; transform: scale(1); }

  .controls { display: flex; gap: 10px; align-items: center; }
  button {
    background: #5b6cff; color: #fff; border: 0;
    padding: 9px 16px; border-radius: 10px; font-size: 14px; cursor: pointer;
  }
  button:hover { background: #4757f0; }
  .stat { font-size: 13px; color: #aab2e6; }
  .msg { height: 20px; font-size: 14px; color: #8affc1; }
  .hint { font-size: 12px; color: #8189bd; max-width: 380px; text-align: center; }
</style>
</head>
<body>
  <h1>🧩 Пазл — меняй плитки кликом</h1>

  <div class="panel">
    <label class="field">🖼 Картинка для пазла
      <input type="file" id="imgInput" accept="image/*">
    </label>
    <label class="field">🎞 Гифка после сборки
      <input type="file" id="gifInput" accept="image/gif,image/*">
    </label>
    <label class="field">Сложность
      <select id="grid">
        <option value="3" selected>3 × 3</option>
        <option value="4">4 × 4</option>
        <option value="5">5 × 5</option>
      </select>
    </label>
  </div>

  <div class="stage" id="stage">
    <div id="board"></div>
    <div id="result"></div>
  </div>

  <div class="controls">
    <button id="shuffle">Перемешать</button>
    <span class="stat">Ходы: <b id="moves">0</b></span>
  </div>
  <div class="msg" id="msg"></div>
  <p class="hint">Кликни одну плитку, затем другую — они поменяются местами. Расставь все по местам, и запустится гифка (или анимация картинки, если гифку не загрузил).</p>

<script>
const SIZE = 360;
const stage  = document.getElementById('stage');
const board  = document.getElementById('board');
const result = document.getElementById('result');
const msg    = document.getElementById('msg');
const movesEl= document.getElementById('moves');

let N = 3;
let imgURL = defaultImage();
let gifURL = null;
let order = [];          // order[позиция] = индекс правильного кусочка
let selected = null;     // выбранная позиция
let moves = 0;
let hasGif = false;

document.getElementById('grid').addEventListener('change', e => { N = +e.target.value; init(); });
document.getElementById('shuffle').addEventListener('click', init);

document.getElementById('imgInput').addEventListener('change', e => {
  const f = e.target.files[0]; if (!f) return;
  imgURL = URL.createObjectURL(f);
  init();
});
document.getElementById('gifInput').addEventListener('change', e => {
  const f = e.target.files[0]; if (!f) return;
  gifURL = URL.createObjectURL(f);
  hasGif = true;
});

function init() {
  stage.classList.remove('solved');
  msg.textContent = '';
  selected = null; moves = 0; movesEl.textContent = '0';
  document.documentElement.style.setProperty('--n', N);

  result.style.backgroundImage = `url("${gifURL || imgURL}")`;

  // перемешиваем (не допускаем уже собранного)
  do {
    order = [...Array(N*N).keys()];
    for (let i = order.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [order[i], order[j]] = [order[j], order[i]];
    }
  } while (isSolved());

  render();
}

function render() {
  const tile = SIZE / N;
  board.innerHTML = '';
  order.forEach((pieceIdx, pos) => {
    const row = Math.floor(pieceIdx / N), col = pieceIdx % N;
    const div = document.createElement('div');
    div.className = 'tile' + (selected === pos ? ' selected' : '');
    div.style.backgroundImage = `url("${imgURL}")`;
    div.style.backgroundSize = `${SIZE}px ${SIZE}px`;
    div.style.backgroundPosition = `-${col*tile}px -${row*tile}px`;
    div.addEventListener('click', () => onClick(pos));
    board.appendChild(div);
  });
}

function onClick(pos) {
  if (selected === null) {
    selected = pos;                 // выбрали первую
  } else if (selected === pos) {
    selected = null;                // отмена выбора
  } else {
    [order[selected], order[pos]] = [order[pos], order[selected]]; // обмен
    selected = null;
    moves++; movesEl.textContent = moves;
  }
  render();
  if (isSolved()) win();
}

function isSolved() {
  return order.every((v, i) => v === i);
}

function win() {
  stage.classList.add('solved');
  if (!hasGif) {
    result.animate(
      [{ transform:'scale(1)' }, { transform:'scale(1.04) rotate(.6deg)' }, { transform:'scale(1)' }],
      { duration: 2500, iterations: Infinity, easing: 'ease-in-out' }
    );
  }
  msg.textContent = hasGif
    ? `🎉 Собрано за ${moves} ходов! Гифка запущена.`
    : `🎉 Собрано за ${moves} ходов! Картинка ожила.`;
}

/* Картинка по умолчанию, пока не загрузили свою */
function defaultImage() {
  const svg = `
  <svg xmlns='http://www.w3.org/2000/svg' width='360' height='360'>
    <defs><linearGradient id='g' x1='0' y1='0' x2='1' y2='1'>
      <stop offset='0' stop-color='#6dd5ff'/><stop offset='1' stop-color='#ff7eb3'/>
    </linearGradient></defs>
    <rect width='360' height='360' fill='url(#g)'/>
    <circle cx='270' cy='90' r='40' fill='#ffd84d'/>
    <path d='M0 280 Q90 240 180 280 T360 280 V360 H0 Z' fill='#7bd389'/>
    <text x='180' y='190' font-size='40' text-anchor='middle' fill='#fff'
      font-family='sans-serif'>🧩 PUZZLE</text>
  </svg>`;
  return 'data:image/svg+xml;utf8,' + encodeURIComponent(svg);
}

init();
</script>
</body>
</html>
