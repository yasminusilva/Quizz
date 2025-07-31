<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Quizziz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 50px auto;
      padding: 20px;
      background: #f4f4f9;
      color: #333;
    }
    h1 {
      text-align: center;
      color: #2c3e50;
    }
    .question {
      margin-bottom: 15px;
    }
    .answers button {
      display: block;
      margin: 8px 0;
      padding: 10px;
      width: 100%;
      font-size: 16px;
      cursor: pointer;
      background: #3498db;
      border: none;
      color: white;
      border-radius: 4px;
      transition: background 0.3s;
    }
    .answers button:hover {
      background: #2980b9;
    }
    #result {
      font-size: 22px;
      text-align: center;
      margin-top: 25px;
      font-weight: bold;
      color: #27ae60;
    }
  </style>
</head>
<body>

  <h1>Quiz: Crimes virtuais</h1>

  <div id="quiz-container">
    <div id="question" class="question"></div>
    <div id="answers" class="answers"></div>
  </div>

  <div id="result"></div>

  <script>
    const quiz = [
      {
        question: "O que é phishing?",
        answers: [
          "Uma técnica para obter dados pessoais fingindo ser uma entidade confiável",
          "Um tipo de vírus que se espalha pelo computador",
          "Um programa para acelerar a internet",
          "Um ataque físico a servidores"
        ],
        correct: 0
      },
      {
        question: "Qual a principal forma de evitar fraudes online?",
        answers: [
          "Compartilhar senhas com amigos",
          "Clicar em links desconhecidos",
          "Usar senhas fortes e não repetir em vários sites",
          "Baixar programas de fontes não confiáveis"
        ],
        correct: 2
      },
      {
        question: "O que é ransomware?",
        answers: [
          "Um programa que protege seu computador",
          "Um malware que sequestra arquivos e pede resgate para liberá-los",
          "Um tipo de firewall",
          "Um sistema de backup"
        ],
        correct: 1
      }
    ];

    let currentQuestion = 0;
    let score = 0;

    const questionEl = document.getElementById('question');
    const answersEl = document.getElementById('answers');
    const resultEl = document.getElementById('result');

    function showQuestion() {
      const q = quiz[currentQuestion];
      questionEl.textContent = q.question;
      answersEl.innerHTML = '';

      q.answers.forEach((answer, index) => {
        const button = document.createElement('button');
        button.textContent = answer;
        button.onclick = () => checkAnswer(index);
        answersEl.appendChild(button);
      });
    }

    function checkAnswer(selected) {
      if(selected === quiz[currentQuestion].correct) {
        score++;
      }
      currentQuestion++;
      if(currentQuestion < quiz.length) {
        showQuestion();
      } else {
        showResult();
      }
    }

    function showResult() {
      questionEl.style.display = 'none';
      answersEl.style.display = 'none';
      resultEl.textContent = `Você acertou ${score} de ${quiz.length} perguntas!`;
    }

    showQuestion();
  </script>

</body>
</html>
