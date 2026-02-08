# Math-game
<!DOCTYPE html>
<html>
<head>
  <title>Zombie Math Escape 🧟‍♂️</title>
</head>

<body style="text-align:center; font-family:Arial;">

  <h1>🧟‍♂️ Zombie Math Escape 🧠</h1>

  <p id="scene">🧍‍♀️ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 🧟‍♂️</p>
  <p id="question"></p>

  <input type="number" id="answer">
  <button onclick="check()">أجاوب</button>

  <p id="status"></p>
  <p id="lives"></p>

  <script>
    let distance = 5;
    let wrong = 0;

    function newQuestion() {
      let a = Math.floor(Math.random() * 10) + 1;
      let b = Math.floor(Math.random() * 10) + 1;
      correct = a + b;
      document.getElementById("question").innerHTML =
        "حل بسرعة: " + a + " + " + b;
    }

    function updateScene() {
      let person = "🧍‍♀️";
      let zombie = "🧟‍♂️";
      let space = "&nbsp;".repeat(distance * 3);
      document.getElementById("scene").innerHTML =
        person + space + zombie;
    }

    function check() {
      let user = document.getElementById("answer").value;

      if (user == correct) {
        distance++;
        document.getElementById("status").innerHTML = "هربتي 😌";
      } else {
        wrong++;
        distance--;
        document.getElementById("status").innerHTML = "غلط! الزومبي قرب 😱";
      }

      document.getElementById("lives").innerHTML =
        "محاولات خاطئة: " + wrong + " / 3";

      if (wrong >= 3) {
        document.getElementById("status").innerHTML =
          "💀 الزومبي مسكهم! GAME OVER";
        return;
      }

      updateScene();
      newQuestion();
      document.getElementById("answer").value = "";
    }

    newQuestion();
    updateScene();
  </script>

</body>
</html>
