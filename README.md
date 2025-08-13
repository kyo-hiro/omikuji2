

<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ノベルティくじ</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&family=Poppins:wght@500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans JP', 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #fff;
            text-align: center;
        }
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
            background-color: #ff6f91;
            color: #fff;
        }
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
        }
        .nav a {
            color: #fff;
            text-decoration: none;
            margin-left: 1rem;
        }
        .main {
            padding: 2rem;
        }
        .intro h1 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
        }
        .intro p {
            font-size: 1.1rem;
            color: #555;
        }
        .draw-button, .retry-button {
            background-color: #ff6f91;
            color: white;
            padding: 1rem 2rem;
            border: none;
            font-size: 1.2rem;
            border-radius: 8px;
            cursor: pointer;
            margin-top: 1rem;
        }
        .draw-button:hover, .retry-button:hover {
            background-color: #ff4f73;
        }
        .result {
            margin-top: 2rem;
        }
        .prize-name {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }
        .prize-description {
            font-size: 1.2rem;
            margin-bottom: 1rem;
        }
        .prize-image {
            max-width: 200px;
            margin-bottom: 1rem;
        }
        .footer {
            background-color: #333;
            color: white;
            padding: 1rem;
            margin-top: 2rem;
        }
        .social-links a {
            color: white;
            margin: 0 0.5rem;
            text-decoration: none;
        }
        /* アニメーション */
        .fade-in {
            animation: fadeIn 1s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <!-- ===== ヘッダー ===== -->
    <header class="header">
        <div class="logo">ノベルティくじ</div>
        <nav class="nav">
            <a href="history.html" class="history-link">📜 履歴を見る</a>
        </nav>
    </header>

    <!-- ===== メインコンテンツ ===== -->
    <main class="main">
        <!-- 説明文 -->
        <section class="intro">
            <h1>ご購入ありがとうございます</h1>
            <p>ボタンを押してくじを引いてください。</p>
            <small>※ノベルティは数量限定です</small>
        </section>

        <!-- 抽選ボタン -->
        <section class="draw-section">
            <button id="drawButton" class="draw-button">くじを引く</button>
        </section>

        <!-- 結果表示エリア -->
        <section id="result" class="result hidden">
            <h2 id="prizeName" class="prize-name"></h2>
            <p id="prizeDescription" class="prize-description"></p>
            <img id="prizeImage" src="" alt="賞の画像" class="prize-image">
            <button id="retryButton" class="retry-button">もう一度引く</button>
        </section>
    </main>

    <!-- ===== フッター ===== -->
    <footer class="footer">
        <p>© 2025 Cosmetic Store</p>
        <div class="social-links">
            <a href="#" aria-label="Instagram">📷</a>
            <a href="#" aria-label="LINE">💬</a>
        </div>
    </footer>

    <script>
        // 賞データ定義
        const prizes = [
            {
                name: "A賞",
                description: "高級コスメセット🎀",
                image: "images/a.png",
                bgColor: "#f8c8dc", // ピンク系
                sound: "sounds/a.mp3"
            },
            {
                name: "B賞",
                description: "保湿クリーム＆ローションセット💧",
                image: "images/b.png",
                bgColor: "#c8e6f8", // 水色系
                sound: "sounds/b.mp3"
            },
            {
                name: "C賞",
                description: "リップ＆チークセット💄",
                image: "images/c.png",
                bgColor: "#f8e1c8", // ベージュ系
                sound: "sounds/c.mp3"
            },
            {
                name: "D賞",
                description: "ハンドクリーム👐",
                image: "images/d.png",
                bgColor: "#e0f8c8", // グリーン系
                sound: "sounds/d.mp3"
            }
        ];

        // HTML要素取得
        const drawButton = document.getElementById("drawButton");
        const retryButton = document.getElementById("retryButton");
        const resultSection = document.getElementById("result");
        const prizeNameEl = document.getElementById("prizeName");
        const prizeDescriptionEl = document.getElementById("prizeDescription");
        const prizeImageEl = document.getElementById("prizeImage");

        // 抽選ボタンイベント
        drawButton.addEventListener("click", () => {
            const prize = getRandomPrize();
            showResult(prize);
            saveHistory(prize);
        });

        // もう一度引くボタン
        retryButton.addEventListener("click", () => {
            resultSection.classList.add("hidden");
            document.body.style.backgroundColor = "#fff";
        });

        // ランダム抽選関数
        function getRandomPrize() {
            const index = Math.floor(Math.random() * prizes.length);
            return prizes[index];
        }

        // 結果表示
        function showResult(prize) {
            prizeNameEl.textContent = prize.name;
            prizeDescriptionEl.textContent = prize.description;
            prizeImageEl.src = prize.image;
            prizeImageEl.alt = prize.name;
            
            // 背景色変更
            document.body.style.backgroundColor = prize.bgColor;

            // 効果音再生
            const audio = new Audio(prize.sound);
            audio.play();

            // フェードイン表示
            resultSection.classList.remove("hidden");
            resultSection.classList.add("fade-in");
        }

        // 履歴保存
        function saveHistory(prize) {
            const history = JSON.parse(localStorage.getItem("lotteryHistory")) || [];
            const timestamp = new Date().toLocaleString("ja-JP");
            history.unshift({
                date: timestamp,
                name: prize.name,
                description: prize.description,
                image: prize.image
            });
            localStorage.setItem("lotteryHistory", JSON.stringify(history));
        }
    </script>
</body>
</html>
