<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Daily Quiz Earn</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<h1>🎮 Daily Quiz Earn</h1>

<div id="game">
  <h2 id="question">Question appears here</h2>

  <div class="options">
    <button onclick="checkAnswer(0)">Option 1</button>
    <button onclick="checkAnswer(1)">Option 2</button>
    <button onclick="checkAnswer(2)">Option 3</button>
    <button onclick="checkAnswer(3)">Option 4</button>
  </div>

  <p id="score">Score: 0</p>
</div>

<p class="footer">Share your referral ID & earn rewards!</p>

<script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f2f2f2;
  padding: 20px;
}

h1 {
  color: #ff5722;
}

#game {
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  max-width: 400px;
  margin: 20px auto;
}

button {
  display: block;
  margin: 10px auto;
  padding: 12px;
  width: 80%;
  font-size: 16px;
  border-radius: 8px;
  border: none;
  background-color: #2196f3;
  color: #fff;
  cursor: pointer;
}

button:hover {
  background-color: #0b7dda;
}

.footer {
  margin-top: 20px;
  font-size: 14px;
  color: #777;
}
let questions = [
  {
    question: "भारत की राजधानी क्या है?",
    options: ["मुंबई", "दिल्ली", "कोलकाता", "चेन्नई"],
    answer: 1
  },
  {
    question: "2 + 2 = कितना?",
    options: ["3", "4", "5", "6"],
    answer: 1
  },
  {
    question: "भारत के प्रधानमंत्री कौन हैं?",
    options: ["राहुल गांधी", "नरेंद्र मोदी", "योगी", "केजरीवाल"],
    answer: 1
  },
  {
    question: "सन 2026 में कौन सा साल है?",
    options: ["वर्ष 2025", "वर्ष 2026", "वर्ष 2027", "वर्ष 2024"],
    answer: 1
  }
];

let currentQuestion = 0;
let score = 0;

let questionEl = document.getElementById("question");
let buttons = document.getElementsByTagName("button");
let scoreEl = document.getElementById("score");

function loadQuestion() {
  if (currentQuestion < questions.length) {
    let q = questions[currentQuestion];
    questionEl.innerText = q.question;
    for (let i = 0; i < buttons.length; i++) {
      buttons[i].innerText = q.options[i];
      buttons[i].style.display = "block";
    }
  } else {
    questionEl.innerText = "🎉 Game Over!";
    for (let i = 0; i < buttons.length; i++) {
      buttons[i].style.display = "none";
    }
  }
  scoreEl.innerText = "Score: " + score;
}

function checkAnswer(selected) {
  if (selected === questions[currentQuestion].answer) {
    score++;
    alert("✅ सही जवाब!");
  } else {
    alert("❌ गलत जवाब!");
  }
  currentQuestion++;
  loadQuestion();
}

loadQuestion();
