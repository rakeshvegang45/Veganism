<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Vegan Quiz</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background: #f2f2f2; }
    .box { background: white; padding: 20px; max-width: 350px; margin: auto; border-radius: 10px; }
    .option { background: #e6e6e6; padding: 10px; margin: 8px 0; border-radius: 8px; cursor: pointer; }
    .option:hover { background: #d4d4d4; }
    button { padding: 10px; width: 100%; border-radius: 8px; border: none; background: green; color: white; font-size: 16px; margin-top: 10px; }
  </style>
</head>
<body><div class="box">
  <h2 id="question"></h2>
  <div id="options"></div>
  <button onclick="nextQ()">Next</button>
  <p id="result"></p>
</div><script>
  const quiz = [
    { q: "Is Egg Vegan?", options: ["Yes", "No"], correct: 1 },
    { q: "Is Honey Vegan?", options: ["Yes", "No"], correct: 1 },
    { q: "Is Milk Vegan?", options: ["Yes", "No"], correct: 1 }
  ];

  let i = 0;
  let score = 0;

  function loadQ() {
    document.getElementById("question").innerText = quiz[i].q;
    const optDiv = document.getElementById("options");
    optDiv.innerHTML = "";

    quiz[i].options.forEach((opt, index) => {
      const div = document.createElement("div");
      div.className = "option";
      div.innerText = opt;
      div.onclick = () => choose(index);
      optDiv.appendChild(div);
    });
  }

  function choose(selected) {
    if (selected === quiz[i].correct) score++;
    nextQ();
  }

  function nextQ() {
    i++;
    if (i < quiz.length) {
      loadQ();
    } else {
      document.getElementById("question").innerText = "Quiz Finished!";
      document.getElementById("options").innerHTML = "";
      document.getElementById("result").innerText = "Your Score: " + score + " / " + quiz.length;
    }
  }

  loadQ();
</script></body>
</html>
