<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Step Quest - 10,000 Steps Tracker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        button {
            padding: 10px;
            margin-top: 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Step Quest</h1>
        <p>Track your daily steps and stay on streak!</p>
        <label for="steps">Enter today's steps:</label>
        <input type="number" id="steps" min="0">
        <button onclick="logSteps()">Log Steps</button>
        <h3>Today's Progress: <span id="progress">0</span> steps</h3>
        <h3>Current Streak: <span id="streak">0</span> days</h3>
        <p id="challenge"></p>
    </div>

    <script>
        let steps = localStorage.getItem("steps") || 0;
        let streak = localStorage.getItem("streak") || 0;
        document.getElementById("progress").innerText = steps;
        document.getElementById("streak").innerText = streak;

        function logSteps() {
            let inputSteps = document.getElementById("steps").value;
            if (inputSteps >= 10000) {
                streak++;
                localStorage.setItem("streak", streak);
            } else {
                streak = 0;
                localStorage.setItem("streak", streak);
            }
            localStorage.setItem("steps", inputSteps);
            document.getElementById("progress").innerText = inputSteps;
            document.getElementById("streak").innerText = streak;
        }

        function generateChallenge() {
            const challenges = [
                "Walk 5,000 steps before noon!",
                "Take 1,000 steps in under 10 minutes!",
                "Explore a new street today!",
                "Complete 2,000 steps without stopping!"
            ];
            let challenge = challenges[Math.floor(Math.random() * challenges.length)];
            document.getElementById("challenge").innerText = "Today's Challenge: " + challenge;
        }

        generateChallenge();
    </script>
</body>
</html>
