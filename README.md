# Veganism
What is Veganism??
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Veganism Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f6f6f6;
    }
    .quiz-box {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      width: 350px;
      margin: auto;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    h2 {
      margin-bottom: 10px;
    }
    button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      background: #4caf50;
      color: white;
    }
    .option {
      display: block;
      padding: 10px;
      background: #eee;
      margin: 10px 0;
      border-radius: 8px;
      cursor: pointer;
    }
    #result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="quiz-box">
    <h2 id="question"></h2>
    <div id="options"></div>
    <button onclick="nextQuestion()">Next</button>
    <p id="result"></p>
  </div>  <script>
    const quiz = [
      {
        q: "Is Egg Vegan?",
        options: ["Yes", "No"],
        correct: 1
      },
      {
        q: "Is Honey Vegan?",
        options: ["Yes", "No"],
        correct: 1
      },
      {
        q: "Is Milk Vegan?",
        options: ["Yes", "No"],
        correct: 1
      }
    ];

    let index = 0;
    let score = 0;

    function loadQuestion() {
      document.getElementById("question").innerText = quiz[index].q;
      const optionsDiv = document.getElementById("options");
      optionsDiv.innerHTML = "";

      quiz[index].options.forEach((opt, i) => {
        const btn = document.createElement("div");
        btn.className = "option";
        btn.innerText = opt;
        btn.onclick = () => selectOption(i);
        optionsDiv.appendChild(btn);
      });
    }

    function selectOption(selected) {
      if (selected === quiz[index].correct) {
        score++;
      }
      nextQuestion();
    }

    function nextQuestion() {
      index++;
      if (index < quiz.length) {
        loadQuestion();
      } else {
        document.getElementById("question").innerText = "Quiz Completed!";
        document.getElementById("options").innerHTML = "";
        document.getElementById("result").innerText = `Your Score: ${score} / ${quiz.length}`;
      }
    }

    loadQuestion();
  </script></body>
</html>
