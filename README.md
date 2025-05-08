# Protection-BASMAGA
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>امتحان Protective Relaying</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f5f5f5;
        }
        .quiz-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 800px;
            margin: auto;
        }
        .question {
            margin-bottom: 20px;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .options {
            margin-top: 10px;
        }
        button {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
        }
        button:hover {
            background: #45a049;
        }
        #result {
            font-weight: bold;
            margin-top: 20px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>امتحان Protective Relaying MCQs</h1>
        <div id="quiz"></div>
        <button onclick="calculateScore()">احسب النتيجة</button>
        <div id="result"></div>
    </div>

    <script>
        // الأسئلة والإجابات (تم اختصارها للتوضيح)
        const questions = [
            {
                question: "1. What is protective relaying?",
                options: [
                    "A. One of the several features of power system design for protection",
                    "B. An energy generator",
                    "C. Transmission lines",
                    "D. A type of power transformer"
                ],
                answer: 0 // الإجابة الصحيحة (A)
            },
            {
                question: "2. What is the purpose of protective relaying in the power system?",
                options: [
                    "A. To protect only certain parts of the power system",
                    "B. To minimize the damage to the equipment and service interruptions when electrical failure occurs",
                    "C. To increase equipment ratings",
                    "D. To maximize the damage and service interruptions when electrical failure occurs"
                ],
                answer: 1 // الإجابة الصحيحة (B)
            },
            // ... (أضف بقية الأسئلة هنا بنفس الهيكل)
        ];

        // عرض الأسئلة
        function loadQuiz() {
            const quizContainer = document.getElementById('quiz');
            questions.forEach((q, index) => {
                const questionDiv = document.createElement('div');
                questionDiv.className = 'question';
                questionDiv.innerHTML = `
                    <h3>${q.question}</h3>
                    <div class="options">
                        ${q.options.map((option, i) => `
                            <label>
                                <input type="radio" name="q${index}" value="${i}">
                                ${option}
                            </label><br>
                        `).join('')}
                    </div>
                `;
                quizContainer.appendChild(questionDiv);
            });
        }

        // حساب النتيجة
        function calculateScore() {
            let score = 0;
            questions.forEach((q, index) => {
                const selectedOption = document.querySelector(`input[name="q${index}"]:checked`);
                if (selectedOption && parseInt(selectedOption.value) === q.answer) {
                    score++;
                }
            });
            document.getElementById('result').innerHTML = `
                نتيجتك: ${score} من ${questions.length}
                <br>النسبة: ${((score / questions.length) * 100).toFixed(1)}%
            `;
        }

        // تحميل الامتحان عند فتح الصفحة
        window.onload = loadQuiz;
    </script>
</body>
</html>
