<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Simulated Debt Payoff Celebration!</title>
<style>
    body {
        margin: 0;
        font-family: 'Comic Sans MS', cursive, sans-serif;
        background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        color: #333;
        overflow: hidden;
    }

    h1 {
        font-size: 3rem;
        margin-bottom: 20px;
        text-align: center;
    }

    .container {
        background: rgba(255,255,255,0.8);
        border-radius: 10px;
        padding: 20px;
        max-width: 400px;
        text-align: center;
        box-shadow: 0 0 20px rgba(0,0,0,0.1);
        transition: transform 0.5s, opacity 0.5s;
        z-index: 2;
    }

    label {
        display: block;
        margin: 15px 0 5px;
        font-weight: bold;
    }

    input[type="text"],
    input[type="number"] {
        width: 100%;
        padding: 10px;
        border: 2px solid #ddd;
        border-radius: 5px;
        font-size: 1rem;
    }

    button {
        margin-top: 20px;
        padding: 15px;
        background: linear-gradient(to right, #ff9966, #ff5e62);
        border: none;
        border-radius: 30px;
        color: #fff;
        font-size: 1.2rem;
        cursor: pointer;
        box-shadow: 0 0 10px rgba(0,0,0,0.3);
        transition: 0.3s;
    }

    button:hover {
        transform: scale(1.05);
    }

    .celebration {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #fff;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        padding: 20px;
        box-sizing: border-box;
        opacity: 0;
        pointer-events: none;
        transition: opacity 1s ease;
        z-index: 10;
    }

    .celebration.show {
        opacity: 1;
        pointer-events: auto;
    }

    .celebration h2 {
        font-size: 4rem;
        margin: 20px 0;
        color: #ff5e62;
        text-shadow: 2px 2px #fff;
    }

    .celebration .info {
        font-size: 1.5rem;
        color: #333;
        margin-bottom: 30px;
    }

    /* Confetti styles */
    .confetti {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
        pointer-events: none;
    }

    .confetti-piece {
        position: absolute;
        width: 10px;
        height: 20px;
        background-color: #f2c14e;
        opacity: 0.8;
        animation: fall 3s linear infinite;
        transform: rotateZ(15deg);
    }

    .confetti-piece:nth-child(odd) {
        background-color: #c34a36;
    }

    .confetti-piece:nth-child(3n) {
        background-color: #009fb7;
    }

    @keyframes fall {
        0% {
            transform: translateY(-100px) rotateZ(0deg);
        }
        50% {
            opacity: 1;
        }
        100% {
            transform: translateY(calc(100vh + 100px)) rotateZ(360deg);
            opacity: 0;
        }
    }
</style>
</head>
<body>

<h1>Simulated Debt Payoff Party!</h1>
<div class="container" id="form-container">
    <form onsubmit="handleFormSubmit(event)">
        <label for="firstName">Your First Name:</label>
        <input type="text" id="firstName" required placeholder="e.g. Alex">

        <label for="debtName">Debt Paid Off:</label>
        <input type="text" id="debtName" required placeholder="e.g. Credit Card">

        <label for="lastPayment">Simulated Last Payment Amount:</label>
        <input type="number" id="lastPayment" required placeholder="e.g. 700">

        <button type="submit">Make Final Payment!</button>
    </form>
</div>

<div class="celebration" id="celebration">
    <div class="confetti" id="confetti-container"></div>
    <h2>Congratulations!</h2>
    <div class="info" id="info"></div>
    <p style="font-size:1.2rem;">You’ve just reached a huge milestone. Enjoy the feeling of freedom and keep rocking your financial journey!</p>
</div>

<script>
    function handleFormSubmit(event) {
        event.preventDefault();
        const firstName = document.getElementById('firstName').value;
        const debtName = document.getElementById('debtName').value;
        const lastPayment = document.getElementById('lastPayment').value;

        // Hide the form container
        const formContainer = document.getElementById('form-container');
        formContainer.style.transform = 'scale(0.5)';
        formContainer.style.opacity = '0';

        setTimeout(() => {
            formContainer.style.display = 'none';
            showCelebration(firstName, debtName, lastPayment);
        }, 500);
    }

    function showCelebration(firstName, debtName, lastPayment) {
        const celebration = document.getElementById('celebration');
        const info = document.getElementById('info');
        info.textContent = `${firstName}, you just crushed your final payment of $${lastPayment} on your ${debtName}!`;

        celebration.classList.add('show');
        launchConfetti();
    }

    function launchConfetti() {
        const container = document.getElementById('confetti-container');
        const confettiCount = 200;
        for (let i = 0; i < confettiCount; i++) {
            const piece = document.createElement('div');
            piece.classList.add('confetti-piece');
            piece.style.left = Math.random() * 100 + '%';
            piece.style.backgroundColor = randomColor();
            piece.style.animationDelay = (Math.random() * 3) + 's';
            container.appendChild(piece);
        }
    }

    function randomColor() {
        const colors = ['#f2c14e', '#c34a36', '#009fb7', '#ff5e62', '#ff9966', '#f7b801'];
        return colors[Math.floor(Math.random() * colors.length)];
    }
</script>

</body>
</html>
