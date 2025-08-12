<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>おみくじアプリ</title>
<style>
  body {
    font-family: "Hiragino Kaku Gothic ProN", sans-serif;
    text-align: center;
    margin-top: 50px;
    transition: background-color 0.5s ease;
  }
  h1 {
    font-size: 2em;
    margin-bottom: 30px;
  }
  button {
    padding: 10px 20px;
    font-size: 1.2em;
    cursor: pointer;
    background-color: #ff6347;
    border: none;
    border-radius: 8px;
    color: white;
  }
  button:hover {
    background-color: #e5533d;
  }
  #result {
    margin-top: 30px;
    font-size: 2.5em;
    font-weight: bold;
  }
  #message {
    margin-top: 20px;
    font-size: 1.2em;
    color: #333;
  }
  #image {
    margin-top: 20px;
    width: 150px;
    height: auto;
  }
</style>
</head>
<body>

<h1>おみくじ</h1>
<button onclick="drawOmikuji()">引く！</button>

<div id="result"></div>
<img id="image" src="" alt="" style="display:none;">
<div id="message"></div>

<!-- 効果音 -->
<audio id="sound-daikichi" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>
<audio id="sound-chuukichi" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3"></audio>
<audio id="sound-shoukichi" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"></audio>
<audio id="sound-suekichi" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3"></audio>

<script>
function drawOmikuji() {
  const fortunes = [
    { 
      text: "大吉", 
      color: "red", 
      bgColor: "#ffe4e1", 
      img: "https://i.imgur.com/jQ7PcdU.png", 
      msg: "今日は最高の一日になりそう！行動力UP！", 
      soundId: "sound-daikichi"
    },
    { 
      text: "中吉", 
      color: "orange", 
      bgColor: "#fff5e6", 
      img: "https://i.imgur.com/9sz0V0L.png", 
      msg: "まずまず順調。チャンスを逃さないで！", 
      soundId: "sound-chuukichi"
    },
    { 
      text: "小吉", 
      color: "green", 
      bgColor: "#e6ffe6", 
      img: "https://i.imgur.com/f4eZyXb.png", 
      msg: "小さな幸せに気づける日です。感謝を忘れずに。", 
      soundId: "sound-shoukichi"
    },
    { 
      text: "末吉", 
      color: "blue", 
      bgColor: "#e6f0ff", 
      img: "https://i.imgur.com/7k6V76B.png", 
      msg: "焦らずコツコツ進めましょう。", 
      soundId: "sound-suekichi"
    }
  ];

  const randomIndex = Math.floor(Math.random() * fortunes.length);
  const selected = fortunes[randomIndex];

  // 要素取得
  const resultEl = document.getElementById("result");
  const imageEl = document.getElementById("image");
  const messageEl = document.getElementById("message");

  // 表示更新
  resultEl.textContent = selected.text;
  resultEl.style.color = selected.color;
  imageEl.src = selected.img;
  imageEl.style.display = "block";
  messageEl.textContent = selected.msg;

  // 背景色変更
  document.body.style.backgroundColor = selected.bgColor;

  // 効果音再生（他の音を停止）
  document.querySelectorAll("audio").forEach(audio => {
    audio.pause();
    audio.currentTime = 0;
  });
  document.getElementById(selected.soundId).play();
}
</script>

</body>
</html>
