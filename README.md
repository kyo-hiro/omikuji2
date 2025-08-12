<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>ノベルティくじ</title>
<style>
  body {
    font-family: "Hiragino Kaku Gothic ProN", sans-serif;
    background: linear-gradient(135deg, #ffe4ec, #fbb1d1, #f9c5d1);
    background-size: 400% 400%;
    animation: bgMove 10s ease infinite;
    text-align: center;
    padding: 50px;
    color: #4a148c;
  }
  @keyframes bgMove {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }
  h1 {
    font-size: 2.5em;
    margin-bottom: 30px;
    color: #ad1457;
    letter-spacing: 2px;
  }
  .glass-card {
    backdrop-filter: blur(15px);
    background: rgba(255, 255, 255, 0.35);
    border-radius: 20px;
    box-shadow: 0 8px 32px rgba(0,0,0,0.15);
    padding: 30px;
    display: inline-block;
    width: 320px;
    transition: transform 0.3s;
  }
  .glass-card:hover {
    transform: scale(1.05);
  }
  button {
    background: linear-gradient(45deg, #ec407a, #f48fb1);
    color: white;
    font-size: 1.2em;
    border: none;
    border-radius: 30px;
    padding: 12px 30px;
    cursor: pointer;
    margin-top: 20px;
    transition: all 0.3s;
  }
  button:hover {
    background: linear-gradient(45deg, #d81b60, #f06292);
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
  }
  #result {
    font-size: 1.6em;
    font-weight: bold;
    margin-top: 20px;
    opacity: 0;
    transition: opacity 0.8s ease;
  }
  #prizeImage {
    width: 150px;
    height: auto;
    margin-top: 15px;
    opacity: 0;
    transition: opacity 0.8s ease;
  }
  .nav-links {
    margin-top: 30px;
  }
  .nav-links a {
    color: #880e4f;
    text-decoration: none;
    font-weight: bold;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.3s;
  }
  .nav-links a:hover {
    border-bottom: 2px solid #880e4f;
  }
</style>
</head>
<body>

<h1>ノベルティくじ</h1>
<div class="glass-card">
  <p>ご購入ありがとうございます🎁<br>ボタンを押してくじを引いてください。</p>
  <button onclick="drawPrize()">くじを引く</button>
  <div id="result"></div>
  <img id="prizeImage" src="" alt="">
</div>

<div class="nav-links">
  <a href="history.html">📜 履歴を見る</a>
</div>

<script>
const prizes = [
  { name: "A賞", color: "#d81b60", img: "https://i.imgur.com/hjD6gFp.png", msg: "高級コスメセット🎀" },
  { name: "B賞", color: "#8e24aa", img: "https://i.imgur.com/SZcVzj2.png", msg: "スペシャルハンドクリーム👐" },
  { name: "C賞", color: "#3949ab", img: "https://i.imgur.com/xvZZhYy.png", msg: "リップスティック💄" },
  { name: "D賞", color: "#00897b", img: "https://i.imgur.com/k59QnGw.png", msg: "化粧ポーチ👜" }
];

function drawPrize() {
  const randomIndex = Math.floor(Math.random() * prizes.length);
  const prize = prizes[randomIndex];
  
  const resultEl = document.getElementById("result");
  const imgEl = document.getElementById("prizeImage");

  // フェードアウト
  resultEl.style.opacity = 0;
  imgEl.style.opacity = 0;

  setTimeout(() => {
    resultEl.textContent = `${prize.name} - ${prize.msg}`;
    resultEl.style.color = prize.color;
    resultEl.style.opacity = 1;

    imgEl.src = prize.img;
    imgEl.style.opacity = 1;

    saveHistory(prize);
  }, 300);
}

function saveHistory(prize) {
  const now = new Date();
  const dateStr = now.toLocaleString("ja-JP");
  const entry = `${dateStr} - ${prize.name} (${prize.msg})`;

  let history = JSON.parse(localStorage.getItem("prizeHistory")) || [];
  history.unshift(entry);
  if (history.length > 50) history.pop();
  localStorage.setItem("prizeHistory", JSON.stringify(history));
}
</script>

</body>
</html>


<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>抽選履歴</title>
<style>
  body {
    font-family: "Hiragino Kaku Gothic ProN", sans-serif;
    background: linear-gradient(135deg, #fce4ec, #f8bbd0);
    text-align: center;
    padding: 40px;
    color: #4a148c;
  }
  h1 {
    font-size: 2em;
    margin-bottom: 20px;
    color: #ad1457;
  }
  ul {
    background: rgba(255,255,255,0.8);
    backdrop-filter: blur(10px);
    list-style: none;
    padding: 20px;
    border-radius: 15px;
    max-width: 500px;
    margin: auto;
    text-align: left;
    box-shadow: 0 8px 32px rgba(0,0,0,0.15);
  }
  li {
    padding: 8px 0;
    border-bottom: 1px solid rgba(0,0,0,0.1);
  }
  a {
    display: inline-block;
    margin-top: 20px;
    color: #880e4f;
    text-decoration: none;
    font-weight: bold;
  }
</style>
</head>
<body>

<h1>抽選履歴</h1>
<ul id="historyList"></ul>
<a href="index.html">⬅ くじ引きに戻る</a>

<script>
function renderHistory() {
  const historyListEl = document.getElementById("historyList");
  const history = JSON.parse(localStorage.getItem("prizeHistory")) || [];
  historyListEl.innerHTML = "";
  history.forEach(item => {
    const li = document.createElement("li");
    li.textContent = item;
    historyListEl.appendChild(li);
  });
}
renderHistory();
</script>

</body>
</html>
