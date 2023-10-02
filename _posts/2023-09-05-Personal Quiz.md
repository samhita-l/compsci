---
toc: true
comments: false
layout: post
title: Personal Quiz
description: Learn more about Samhita
type: hacks
courses: { compsci: {week: 1} }

---

<html>
<head>
    <title>Quiz</title>
</head>
<body>
    <h1>Quiz</h1>
    
    <div id="questions">
        <!-- Question 1 -->
        <div class="question">
            <p>What is my favorite food?</p>
            <div class="options">
                <input type="checkbox" id="q1-option1" data-correct="true"> <label for="q1-option1">pasta</label><br>
                <input type="checkbox" id="q1-option2"> <label for="q1-option2">chicken sandwich</label><br>
                <input type="checkbox" id="q1-option3"> <label for="q1-option3">pizza</label><br>
                <input type="checkbox" id="q1-option4"> <label for="q1-option4">cucumber</label><br>
            </div>
            <div class="result"></div>
        </div>

        <!-- Question 2 -->
        <div class="question">
            <p>Who is my favorite singer?</p>
            <div class="options">
                <input type="checkbox" id="q2-option1"> <label for="q2-option1">Olivia Rodrigo</label><br>
                <input type="checkbox" id="q2-option2"> <label for="q2-option2">Lana Del Rey</label><br>
                <input type="checkbox" id="q2-option3" data-correct="true"> <label for="q2-option3">Taylor Swift</label><br>
                <input type="checkbox" id="q2-option4"> <label for="q2-option4">SZA</label><br>
            </div>
            <div class="result"></div>
        </div>

        <!-- Question 3 -->
        <div class="question">
            <p>Where was I born?</p>
            <div class="options">
                <input type="checkbox" id="q3-option1"> <label for="q3-option1">California</label><br>
                <input type="checkbox" id="q3-option2"> <label for="q3-option2">New York</label><br>
                <input type="checkbox" id="q3-option4"> <label for="q3-option4">Michigan</label><br>
                <input type="checkbox" id="q3-option3" data-correct="true"> <label for="q3-option3">Tennessee</label><br>
            </div>
            <div class="result"></div>
        </div>
    </div>

    <script>
        const checkboxes = document.querySelectorAll('input[type="checkbox"]');
        checkboxes.forEach(checkbox => {
            checkbox.addEventListener('change', () => {
                checkAnswer(checkbox);
            });
        });

        function checkAnswer(checkbox) {
            const questionDiv = checkbox.closest('.question');
            const correctCheckbox = questionDiv.querySelector('input[data-correct="true"]');
            const resultElement = questionDiv.querySelector('.result');

            if (checkbox.isEqualNode(correctCheckbox)) {
                if (checkbox.checked) {
                    resultElement.textContent = "Correct";
                } else {
                    resultElement.textContent = "";
                }
            } else {
                if (checkbox.checked) {
                    resultElement.textContent = "Incorrect";
                } else {
                    resultElement.textContent = "";
                }
            }
        }
    </script>
</body>
</html>

