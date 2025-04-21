<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>水果攤加法樂</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #ff6347;
        }
        #game-container {
            max-width: 600px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        #fruit-display {
            display: flex;
            justify-content: space-around;
            font-size: 2em;
            margin: 20px 0;
        }
        #question {
            font-size: 1.5em;
            margin: 10px 0;
        }
        #answer-input {
            padding: 10px;
            font-size: 1.2em;
            width: 100px;
            margin: 10px;
        }
        #submit-btn {
            padding: 10px 20px;
            font-size: 1.2em;
            background-color: #32cd32;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        #submit-btn:hover {
            background-color: #228b22;
        }
        #feedback {
            font-size: 1.2em;
            margin: 10px 0;
            color: #ff4500;
        }
        #score {
            font-size: 1.2em;
            color: #4682b4;
        }
    </style>
</head>
<body>
    <h1>水果攤加法樂</h1>
    <div id="game-container">
        <div id="fruit-display"></div>
        <div id="question"></div>
        <input type="number" id="answer-input" placeholder="輸入答案">
        <button id="submit-btn" onclick="checkAnswer()">提交</button>
        <div id="feedback"></div>
        <div id="score">得分：0</div>
    </div>

    <script>
        let num1, num2, correctAnswer, score = 0;

        // 初始化遊戲
        function startGame() {
            // 隨機生成兩個數字（1到10）
            num1 = Math.floor(Math.random() * 10) + 1;
            num2 = Math.floor(Math.random() * 10) + 1;
            correctAnswer = num1 + num2;

            // 顯示水果（使用 emoji）
            const fruit1 = "🍎".repeat(num1);
            const fruit2 = "🍌".repeat(num2);
            document.getElementById("fruit-display").innerHTML = `${fruit1} + ${fruit2}`;

            // 顯示問題
            document.getElementById("question").innerText = `${num1} + ${num2} = ?`;
            document.getElementById("answer-input").value = "";
            document.getElementById("feedback").innerText = "";
        }

        // 檢查答案
        function checkAnswer() {
            const userAnswer = parseInt(document.getElementById("answer-input").value);
            const feedback = document.getElementById("feedback");

            if (userAnswer === correctAnswer) {
                feedback.innerText = "答對了！好棒！";
                feedback.style.color = "#32cd32";
                score++;
                document.getElementById("score").innerText = `得分：${score}`;
                setTimeout(startGame, 1000); // 1秒後進入下一題
            } else {
                feedback.innerText = "答錯了，再試一次！";
                feedback.style.color = "#ff4500";
            }
        }

        // 按 Enter 鍵提交
        document.getElementById("answer-input").addEventListener("keypress", function(event) {
            if (event.key === "Enter") {
                checkAnswer();
            }
        });

        // 遊戲開始
        startGame();
    </script>
</body>
</html>
