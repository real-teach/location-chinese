<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>我的房间 — Опиши комнату</title>

<style>
:root {
  --blue:#547fc4;
  --light:#edf3ff;
  --bg:#f5f7fb;
  --text:#29364b;
  --border:#dce4ef;
}

* { box-sizing:border-box; }

html {
  scroll-behavior:smooth;
}

body {
  margin:0;
  background:var(--bg);
  color:var(--text);
  font:16px/1.6 Arial,sans-serif;
}

header {
  padding:35px 15px;
  text-align:center;
  background:linear-gradient(135deg,#dceaff,#f4e8ff);
}

header h1 { font-size:38px; margin:0; }
header p { margin:7px 0 0; }

/* ИСПРАВЛЕННОЕ ВЕРХНЕЕ МЕНЮ */
nav {
  position:sticky;
  top:0;
  z-index:9999;
  display:flex;
  gap:8px;
  overflow-x:auto;
  padding:10px;
  background:white;
  border-bottom:1px solid var(--border);
  pointer-events:auto;
  -webkit-overflow-scrolling:touch;
}

nav a {
  position:relative;
  z-index:10000;
  display:inline-block;
  flex-shrink:0;
  text-decoration:none;
  background:var(--light);
  color:#315b9b;
  padding:8px 13px;
  border-radius:20px;
  font-size:14px;
  cursor:pointer;
  pointer-events:auto;
  white-space:nowrap;
}

nav a:active {
  background:#d3e2fb;
}

main {
  max-width:1050px;
  margin:25px auto;
  padding:0 14px 50px;
}

section {
  scroll-margin-top:85px;
  background:white;
  border:1px solid var(--border);
  border-radius:17px;
  padding:22px;
  margin-bottom:20px;
  box-shadow:0 4px 14px #263b5a0b;
}

h2 { margin:0 0 15px; font-size:24px; }

button {
  background:var(--blue);
  color:white;
  border:0;
  border-radius:9px;
  padding:10px 15px;
  cursor:pointer;
  font-size:15px;
}

button:hover { opacity:.88; }

button.secondary {
  background:#e9eef6;
  color:#34445e;
}

input[type=text] {
  width:100%;
  max-width:550px;
  padding:11px;
  border:1px solid #bdc9d8;
  border-radius:9px;
  font-size:16px;
}

textarea {
  width:100%;
  min-height:140px;
  padding:12px;
  border:1px solid #bdc9d8;
  border-radius:10px;
  font:16px Arial;
}

.note {
  background:#f0f5ff;
  border-left:4px solid var(--blue);
  padding:13px 15px;
  border-radius:8px;
  margin:15px 0;
}

.grid {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(210px,1fr));
  gap:10px;
}

.word {
  border:1px solid var(--border);
  border-radius:11px;
  padding:11px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:8px;
}

.word strong { font-size:21px; }
.word small { display:block; color:#68778d; }
.speak { padding:6px 9px; flex-shrink:0; }

table {
  width:100%;
  border-collapse:collapse;
}

td,th {
  padding:10px;
  text-align:left;
  border-bottom:1px solid var(--border);
}

th { background:#f1f5fb; }

.room-photo {
  display:block;
  width:100%;
  max-width:736px;
  height:auto;
  margin:0 auto;
  border-radius:12px;
  border:1px solid #dce4ef;
}

.quiz {
  border:1px solid var(--border);
  border-radius:11px;
  padding:13px;
  margin:12px 0;
}

.quiz p {
  margin:0 0 9px;
  font-weight:bold;
}

.feedback {
  font-size:14px;
  margin-top:7px;
}

.correct { color:#187344; }
.wrong { color:#b43b31; }

.options {
  display:flex;
  flex-wrap:wrap;
  gap:12px;
}

.options label {
  background:#f1f4f9;
  padding:8px 12px;
  border-radius:8px;
}

footer {
  text-align:center;
  color:#758196;
  padding:15px;
}

@media(max-width:600px) {
  section { padding:15px; }
  header h1 { font-size:30px; }
}
</style>
</head>

<body>

<header>
  <h1>我的房间 🏠</h1>
  <p>Опиши комнату — предметы и их расположение</p>
</header>

<!-- ВЕРХНЕЕ МЕНЮ -->
<nav id="topMenu">
  <a href="#vocab">Словарь</a>
  <a href="#positions">方位词</a>
  <a href="#picture">Картинка</a>
  <a href="#questions">Вопросы</a>
  <a href="#build">Предложения</a>
  <a href="#errors">Ошибки</a>
  <a href="#speaking">Говорение</a>
</nav>

<main>

<!-- 1. СЛОВАРЬ -->
<section id="vocab">
<h2>1. Словарь по картинке 📚</h2>
<p>Повтори слова. Нажми на 🔊, чтобы услышать произношение.</p>
<div class="grid" id="vocabGrid"></div>
</section>

<!-- 2. 方位词 -->
<section id="positions">
<h2>2. Где находится предмет? 方位词</h2>

<table>
<tr>
<th>中文</th><th>Перевод</th>
<th>中文</th><th>Перевод</th>
</tr>
<tr><td>里面</td><td>внутри</td><td>后面</td><td>позади</td></tr>
<tr><td>前面</td><td>перед</td><td>上面 / 上</td><td>сверху, на</td></tr>
<tr><td>下面 / 下</td><td>снизу, под</td><td>左边</td><td>слева</td></tr>
<tr><td>右边</td><td>справа</td><td>中间</td><td>посередине</td></tr>
<tr><td>旁边</td><td>рядом</td><td></td><td></td></tr>
</table>

<div class="note">
<b>Модель предложения:</b><br>
Предмет + 在 + место + 方位词。<br><br>

<b>笔记本电脑在书桌上。</b><br>
Ноутбук находится на письменном столе.<br><br>

<b>椅子在书桌前面。</b><br>
Стул находится перед письменным столом.
</div>

<button class="secondary"
onclick="speak('笔记本电脑在书桌上。椅子在书桌前面。')">
🔊 Послушать примеры
</button>
</section>

<!-- 3. ФОТОГРАФИЯ -->
<section id="picture">
<h2>3. Рассмотри комнату 🏠</h2>
<p>Внимательно рассмотри фотографию. Найди предметы и запомни, где они находятся.</p>

<img
  src="https://i.pinimg.com/1200x/3d/82/d8/3d82d87fd267ba4dfe77dc6c16e59f6a.jpg"
  alt="我的房间 — фотография комнаты"
  class="room-photo"
>

<div class="note">
<b>Подсказки:</b><br><br>
床 — слева от письменного стола.<br>
书桌 — справа от кровати.<br>
椅子 — перед письменным столом.<br>
书架 — справа в комнате.<br>
地毯 — на полу перед письменным столом.<br>
空调 — слева от окна.<br>
百叶窗 — на окне.<br>
海报 — на стене.
</div>
</section>

<!-- 4. ВОПРОСЫ -->
<section id="questions">
<h2>4. Ответь на вопросы по картинке ✍️</h2>
<p>Напиши полное предложение, обязательно используя 在.</p>
<div id="questionList"></div>
<button onclick="checkInputs('questionList')">Проверить ответы</button>
</section>

<!-- 5. СОСТАВЬ ПРЕДЛОЖЕНИЯ -->
<section id="build">
<h2>5. Составь предложения по подсказкам 🧩</h2>
<p>Составь предложение из предложенных слов.</p>

<div class="note">
<b>Пример:</b><br>
笔记本电脑 / 书桌 / 上<br>
Ответ: 笔记本电脑在书桌上。
</div>

<div id="buildList"></div>
<button onclick="checkInputs('buildList')">Проверить ответы</button>
</section>

<!-- 6. НАЙДИ ОШИБКУ -->
<section id="errors">
<h2>6. Найди ошибку 🔎</h2>
<p>Прочитай предложение и выбери, соответствует ли оно фотографии.</p>
<div id="errorList"></div>
<button onclick="checkErrors()">Проверить ответы</button>
</section>

<!-- 7. ГОВОРЕНИЕ -->
<section id="speaking">
<h2>7. Расскажи о своей комнате 🗣️</h2>

<p>
Представь, что это твоя комната. Опиши её в 5–6 предложениях.
Используй минимум пять разных слов местоположения.
</p>

<div class="note">
<b>Опоры для рассказа:</b><br><br>
我的房间……<br>
床在……<br>
书桌在……<br>
……在……上。<br>
……在……旁边。<br>
……在……里面。<br>
……在……前面。
</div>

<textarea placeholder="Напиши свой рассказ на китайском языке..."></textarea>

<p>
<button class="secondary"
onclick="speak('我的房间很漂亮。床在房间左边。书桌在床的右边。椅子在书桌前面。书在书架里面。地毯在房间中间。')">
🔊 Послушать пример рассказа
</button>
</p>
</section>

</main>

<footer>
我的房间 · Индивидуальная практика китайского языка
</footer>

<script>

/* НАВИГАЦИЯ — ОБРАБОТЧИК КЛИКОВ */
document.getElementById('topMenu').addEventListener('click', function(event) {
  const link = event.target.closest('a[href^="#"]');

  if (!link) return;

  const targetId = link.getAttribute('href').substring(1);
  const target = document.getElementById(targetId);

  if (!target) return;

  event.preventDefault();

  target.scrollIntoView({
    behavior:'smooth',
    block:'start'
  });

  history.replaceState(null, '', '#' + targetId);
});


/* СЛОВАРЬ */
const vocab = [
['房间','fángjiān','комната'],
['床','chuáng','кровать'],
['枕头','zhěntou','подушка'],
['被子','bèizi','одеяло'],
['玩具熊','wánjùxióng','плюшевый мишка'],
['台灯','táidēng','настольная лампа'],
['书桌','shūzhuō','письменный стол'],
['笔记本电脑','bǐjìběn diànnǎo','ноутбук'],
['电子钟','diànzǐzhōng','электронные часы'],
['花瓶','huāpíng','ваза'],
['花','huā','цветы'],
['椅子','yǐzi','стул'],
['地毯','dìtǎn','ковёр'],
['书架','shūjià','книжный стеллаж'],
['书','shū','книги'],
['抽屉','chōuti','ящик'],
['窗户','chuānghu','окно'],
['百叶窗','bǎiyèchuāng','жалюзи'],
['空调','kōngtiáo','кондиционер'],
['海报','hǎibào','постер, плакат'],
['相机','xiàngjī','фотоаппарат']
];


/* ОЗВУЧИВАНИЕ */
function speak(text) {
  if (!('speechSynthesis' in window)) {
    alert('В этом браузере нет функции озвучивания.');
    return;
  }

  speechSynthesis.cancel();

  const utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = 'zh-CN';
  utterance.rate = 0.85;

  speechSynthesis.speak(utterance);
}


/* КАРТОЧКИ СЛОВ */
document.getElementById('vocabGrid').innerHTML =
vocab.map(word => `
<div class="word">
  <div>
    <strong>${word[0]}</strong>
    <small>${word[1]} · ${word[2]}</small>
  </div>
  <button class="speak" onclick="speak('${word[0]}')">🔊</button>
</div>
`).join('');


/* ВОПРОСЫ ПО ФОТОГРАФИИ */
const questions = [
['床在哪里？','床在书桌左边。'],
['玩具熊在哪里？','玩具熊在床上。'],
['笔记本电脑在哪里？','笔记本电脑在书桌上。'],
['电子钟在哪里？','电子钟在书桌上。'],
['花瓶在哪里？','花瓶在笔记本电脑旁边。'],
['椅子在哪里？','椅子在书桌前面。'],
['地毯在哪里？','地毯在房间中间。'],
['书架在哪里？','书架在房间右边。'],
['书在哪里？','书在书架里面。'],
['空调在哪里？','空调在窗户左边。'],
['百叶窗在哪里？','百叶窗在窗户上。'],
['台灯在哪里？','台灯在书桌上。']
];


/* СОСТАВЬ ПРЕДЛОЖЕНИЯ */
const builds = [
['玩具熊 / 床 / 上','玩具熊在床上。'],
['枕头 / 玩具熊 / 后面','枕头在玩具熊后面。'],
['椅子 / 书桌 / 前面','椅子在书桌前面。'],
['书 / 书架 / 里面','书在书架里面。'],
['地毯 / 房间 / 中间','地毯在房间中间。'],
['花瓶 / 笔记本电脑 / 旁边','花瓶在笔记本电脑旁边。'],
['床 / 书桌 / 左边','床在书桌左边。'],
['书架 / 房间 / 右边','书架在房间右边。']
];


/* СОЗДАНИЕ ПОЛЕЙ ДЛЯ ОТВЕТОВ */
function makeInputs(id, data) {
  document.getElementById(id).innerHTML =
  data.map((item,i) => `
    <div class="quiz">
      <p>${i+1}. ${item[0]}</p>
      <input
        type="text"
        data-answer="${item[1]}"
        placeholder="Напиши предложение по-китайски"
      >
      <div class="feedback"></div>
      <button class="secondary" onclick="showHint(this)">
        Показать ответ
      </button>
    </div>
  `).join('');
}

makeInputs('questionList', questions);
makeInputs('buildList', builds);


/* НОРМАЛИЗАЦИЯ ОТВЕТА */
function normalize(text) {
  return text.replace(/[。.!！?？\s]/g,'').trim();
}


/* ПРОВЕРКА ОТВЕТОВ */
function checkInputs(id) {
  document.querySelectorAll('#'+id+' .quiz').forEach(item => {
    const input = item.querySelector('input');
    const feedback = item.querySelector('.feedback');

    if (!input.value.trim()) {
      feedback.textContent = 'Сначала напиши ответ.';
      feedback.className = 'feedback wrong';
      return;
    }

    const correct =
      normalize(input.value) === normalize(input.dataset.answer);

    feedback.textContent = correct
      ? 'Верно! ✓'
      : 'Проверь порядок слов и наличие 在. Можно посмотреть подсказку.';

    feedback.className = 'feedback ' + (correct ? 'correct' : 'wrong');
  });
}


/* ПОКАЗАТЬ ОТВЕТ */
function showHint(button) {
  const item = button.closest('.quiz');
  const answer = item.querySelector('input').dataset.answer;
  const feedback = item.querySelector('.feedback');

  feedback.textContent = 'Возможный ответ: ' + answer;
  feedback.className = 'feedback';
}


/* НАЙДИ ОШИБКУ */
const errors = [
['笔记本电脑在床上。',false,'笔记本电脑在书桌上。'],
['玩具熊在床上。',true,''],
['椅子在书桌前面。',true,''],
['花瓶在书桌下面。',false,'花瓶在笔记本电脑旁边。'],
['书架在房间右边。',true,''],
['地毯在房间中间。',true,''],
['空调在窗户右边。',false,'空调在窗户左边。'],
['床在书桌右边。',false,'床在书桌左边。']
];

document.getElementById('errorList').innerHTML =
errors.map((item,i) => `
<div class="quiz">
  <p>${i+1}. ${item[0]}</p>
  <div class="options">
    <label>
      <input type="radio" name="error${i}" value="true">
      Верно
    </label>
    <label>
      <input type="radio" name="error${i}" value="false">
      Неверно
    </label>
  </div>
  <div class="feedback"></div>
</div>
`).join('');


/* ПРОВЕРКА «НАЙДИ ОШИБКУ» */
function checkErrors() {
  let score = 0;

  errors.forEach((item,i) => {
    const selected = document.querySelector(
      'input[name="error'+i+'"]:checked'
    );

    const feedback = document.querySelectorAll(
      '#errorList .feedback'
    )[i];

    if (selected && selected.value === String(item[1])) {
      score++;
      feedback.textContent = item[2]
        ? 'Правильно! Исправление: ' + item[2]
        : 'Правильно! ✓';
      feedback.className = 'feedback correct';
    } else {
      feedback.textContent = 'Попробуй ещё раз.';
      feedback.className = 'feedback wrong';
    }
  });

  let result = document.getElementById('errorScore');

  if (!result) {
    result = document.createElement('p');
    result.id = 'errorScore';
    document.getElementById('errorList').appendChild(result);
  }

  result.innerHTML =
    '<b>Результат: ' + score + ' из ' + errors.length + '</b>';
}

</script>

</body>
</html>
