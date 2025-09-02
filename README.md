# CARE-PACKAGE
MEOW
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cat Quiz Game 🐾</title>
  <style>
    body {
      font-family: "Comic Sans MS", cursive, sans-serif;
      background: #fff8f0;
      text-align: center;
      padding: 40px;
    }
    h1 {
      color: #ff6600;
    }
    .question {
      font-size: 22px;
      margin: 20px 0;
    }
    .choices button {
      font-size: 18px;
      padding: 10px 20px;
      margin: 10px;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      background-color: #ffcc80;
      transition: 0.2s;
    }
    .choices button:hover {
      background-color: #ffa726;
    }
    #result {
      margin-top: 25px;
      font-size: 20px;
      font-weight: bold;
    }
    #reward {
      margin-top: 15px;
      font-size: 22px;
      color: #2e7d32;
    }
  </style>
</head>
<body>
  <h1>🐱 Cat Quiz Game</h1>
  <p>Answer the silly cat questions. Correct = reward 😻 Wrong = punishment 😾</p>

  <div id="quiz">
    <div class="question" id="question"></div>
    <div class="choices" id="choices"></div>
    <div id="result"></div>
    <div id="reward"></div>
  </div>

  <script>
    const quizData = [
      {
        question: "Will the meow scratch the human or hug the human?",
        options: ["Scratch 😾", "Hug 🤗"],
        correct: "Hug 🤗",
        reward: "🥩 Steak",
        punishment: "🧴 Forced bubble bath"
      },
      {
        question: "Does the cat drink tea, coffee, or milk?",
        options: ["Tea 🍵", "Coffee ☕", "Milk 🥛"],
        correct: "Milk 🥛",
        reward: "🥛 Fresh milk",
        punishment: "🍋 Sour lemon water"
      },
      {
        question: "What does the cat prefer: fruits or chocolates?",
        options: ["🍎 Fruits", "🍫 Chocolates"],
        correct: "🍫 Chocolates",
        reward: "🍫 Sweet chocolate bar",
        punishment: "🌶️ Spicy chili surprise"
      },
      {
        question: "Where will the cat sleep tonight?",
        options: ["On the bed 🛏️", "On the laptop 💻"],
        correct: "On the bed 🛏️",
        reward: "🤗 Warm hugs",
        punishment: "📦 Locked in cardboard box"
      },
      {
        question: "Will the cat chase the mouse or ignore it?",
        options: ["Chase 🐭", "Ignore 😼"],
        correct: "Chase 🐭",
        reward: "🥣 Yoghurt & Granola",
        punishment: "🥒 Cucumber scare"
      }
    ];

    let currentQuestion = 0;

    function loadQuestion() {
      if (currentQuestion < quizData.length) {
        document.getElementById("question").innerText = quizData[currentQuestion].question;
        const choicesDiv = document.getElementById("choices");
        choicesDiv.innerHTML = "";
        quizData[currentQuestion].options.forEach(option => {
          const btn = document.createElement("button");
          btn.innerText = option;
          btn.onclick = () => checkAnswer(option);
          choicesDiv.appendChild(btn);
        });
        document.getElementById("result").innerText = "";
        document.getElementById("reward").innerText = "";
      } else {
        document.getElementById("quiz").innerHTML = "<h2>🎉 The cat has finished the quiz! She is full of rewards 😻</h2>";
      }
    }

    function checkAnswer(answer) {
      const q = quizData[currentQuestion];
      if (answer === q.correct) {
        document.getElementById("result").innerText = "✅ Correct!";
        document.getElementById("reward").innerText = "Reward: " + q.reward;
      } else {
        document.getElementById("result").innerText = "❌ Wrong!";
        document.getElementById("reward").innerText = "Punishment: " + q.punishment;
      }
      currentQuestion++;
      setTimeout(loadQuestion, 2000);
    }

    loadQuestion();
  </script>
</body>
</html>
