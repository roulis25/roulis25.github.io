<html lang="el">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Πρόκληση Ενωμοτιών</title>

    <style>
        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, Arial;
            margin: 0;
            background: #f1f4f8;
        }

        .container {
            max-width: 500px;
            margin: auto;
            padding: 20px;
            background: white;
            min-height: 100vh;
        }

        h1 {
            text-align: center;
            margin-bottom: 5px;
        }

        .question {
            background: #e8eef7;
            padding: 15px;
            border-radius: 12px;
            font-size: 1.1rem;
            text-align: center;
            margin-bottom: 20px;
            color: #2b2d42;
        }

        label {
            font-weight: 600;
            margin-bottom: 5px;
            display: block;
        }

        select,
        input {
            width: 100%;
            padding: 12px;
            font-size: 1rem;
            border-radius: 10px;
            border: 1px solid #ccc;
            margin-bottom: 15px;
        }

        button {
            width: 100%;
            padding: 12px;
            background: #3366ff;
            color: white;
            border-radius: 999px;
            font-size: 1.1rem;
            border: none;
            cursor: pointer;
        }

        .message {
            text-align: center;
            margin-top: 10px;
            font-weight: 600;
        }

        .error {
            color: #d90429;
        }

        .success {
            color: #2f9e44;
        }

        .image-wrapper {
            display: none;
            margin-top: 20px;
            text-align: center;
        }

        .image-wrapper img {
            max-width: 100%;
            border-radius: 14px;
            border: 3px solid #2f9e44;
        }
    </style>
</head>

<body>
    <div class="container">

        <h1>Πρόκληση Ενωμοτιών</h1>

        <!-- ΕΔΩ ΕΙΝΑΙ Η ΕΡΩΤΗΣΗ -->
        <div id="questionText" class="question">
            ./../--/.-/.../-/.//....//-.-/.-/.-../-.--/-/./.-./....//./-./.--/--/---/-/../.-//
        </div>

        <form id="quizForm">

            <label for="patrolSelect">Διάλεξε Ενωμοτία</label>
            <select id="patrolSelect" required>
                <option value="">-- Διάλεξε --</option>
                <option value="lion">Λιοντάρια</option>
                <option value="wolf">Λύκοι</option>
                <option value="eagle">Αετοί</option>
                <option value="dolphin">Δελφίνια</option>
            </select>

            <label for="answerInput">Απάντηση</label>
            <input type="text" id="answerInput" placeholder="Γράψε την απάντηση..." autocomplete="off" required>

            <button type="submit">Έλεγχος</button>
        </form>

        <div id="message" class="message"></div>

        <div id="imageWrapper" class="image-wrapper">
            <img id="patrolImage" src="αγια φωτεινη.png" alt="Εικόνα Ενωμοτίας">
        </div>

    </div>

    <script>
        // ΟΛΕΣ οι ενωμοτίες έχουν ΤΗΝ ΙΔΙΑ ΕΡΩΤΗΣΗ.
        // Εδώ βάζεις τη σωστή απάντηση:
        const correctAnswer = "είμαστε η καλύτερη ενωμοτία";

        // Εικόνες ανά ενωμοτία
        const patrolImages = {
            lion: "αγια φωτεινη.png",
            wolf: "αγια φωτεινη.png",
            eagle: "αγια φωτεινη.png",
            dolphin: "αγια φωτεινη.png"
        };

        const form = document.getElementById('quizForm');
        const patrolSelect = document.getElementById('patrolSelect');
        const answerInput = document.getElementById('answerInput');
        const messageDiv = document.getElementById('message');
        const imageWrapper = document.getElementById('imageWrapper');
        const patrolImage = document.getElementById('patrolImage');

        form.addEventListener('submit', function (e) {
            e.preventDefault();

            const patrol = patrolSelect.value;
            const answer = answerInput.value.trim().toLowerCase();

            if (!patrol) {
                messageDiv.textContent = "Διάλεξε πρώτα ενωμοτία!";
                messageDiv.className = "message error";
                imageWrapper.style.display = "none";
                return;
            }

            if (answer === correctAnswer.toLowerCase()) {
                messageDiv.textContent = "Σωστή απάντηση! 🎉";
                messageDiv.className = "message success";

                // Δείξε εικόνα
                patrolImage.src = patrolImages[patrol];
                imageWrapper.style.display = "block";

            } else {
                messageDiv.textContent = "Λάθος απάντηση – προσπάθησε ξανά!";
                messageDiv.className = "message error";

                imageWrapper.style.display = "none";

                // ΚΑΘΑΡΙΣΜΟΣ ΠΕΔΙΟΥ
                answerInput.value = "";

                // Εστίαση ξανά στο input
                answerInput.focus();
            }
        });

    </script>

</body>

</html>
