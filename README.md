# Hidden-quest
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Roborace Announcement</title>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
            radial-gradient(circle at top, #263238, #080b0d 65%);
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }

    .container {
        width: min(92%, 700px);
        text-align: center;
        position: relative;
        z-index: 2;
    }

    .robot {
        font-size: 80px;
        animation: float 2s ease-in-out infinite;
        margin-bottom: 25px;
    }

    @keyframes float {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-12px); }
    }

    .intro {
        font-size: clamp(20px, 5vw, 32px);
        color: #b0bec5;
        margin-bottom: 30px;
    }

    button {
        border: none;
        padding: 16px 32px;
        border-radius: 50px;
        font-size: 18px;
        font-weight: bold;
        cursor: pointer;
        background: white;
        color: #111;
        box-shadow: 0 0 25px rgba(255,255,255,.25);
        transition: .25s;
    }

    button:hover {
        transform: scale(1.07);
        box-shadow: 0 0 35px rgba(255,255,255,.5);
    }

    .reveal {
        display: none;
        animation: reveal .8s ease forwards;
    }

    @keyframes reveal {
        from {
            opacity: 0;
            transform: scale(.7);
        }
        to {
            opacity: 1;
            transform: scale(1);
        }
    }

    .small {
        color: #cfd8dc;
        font-size: 18px;
        margin-bottom: 12px;
    }

    .third {
        font-size: clamp(70px, 18vw, 150px);
        font-weight: 900;
        line-height: .9;
        color: #cd7f32;
        text-shadow:
            0 0 15px rgba(205,127,50,.5),
            0 0 40px rgba(205,127,50,.25);
    }

    .prize {
        font-size: clamp(32px, 9vw, 65px);
        font-weight: 900;
        margin-top: 15px;
        letter-spacing: 2px;
    }

    .roborace {
        margin-top: 20px;
        font-size: clamp(20px, 5vw, 30px);
        color: #90caf9;
    }

    .message {
        margin-top: 35px;
        font-size: 19px;
        color: #eceff1;
        line-height: 1.6;
    }

    .share {
        margin-top: 25px;
        background: #2196f3;
        color: white;
    }

    .confetti {
        position: fixed;
        width: 9px;
        height: 14px;
        top: -20px;
        animation: fall linear forwards;
        z-index: 1;
    }

    @keyframes fall {
        to {
            transform: translateY(110vh) rotate(720deg);
        }
    }

    .winner {
        margin-top: 30px;
        font-size: 16px;
        color: #90a4ae;
    }
</style>
</head>

<body>

<div class="container">

    <div id="intro">
        <div class="robot">🤖</div>

        <div class="intro">
            I have something to tell everyone...
        </div>

        <button onclick="revealWinner()">
            TAP TO REVEAL
        </button>
    </div>


    <div id="reveal" class="reveal">

        <div class="small">
            THE RESULT IS IN...
        </div>

        <div class="third">
            3rd
        </div>

        <div class="prize">
            PRIZE! 🏆
        </div>

        <div class="roborace">
            🤖 ROBORACE 🤖
        </div>

        <div class="message">
            After all the building, testing, fixing,
            debugging and racing...
            <br><br>

            <strong>WE DID IT!</strong>
        </div>

        <button class="share" onclick="shareResult()">
            SHARE THE NEWS
        </button>

        <div class="winner">
            🏁 RoboRace 2026
        </div>

    </div>

</div>


<script>

function revealWinner() {

    document.getElementById("intro").style.display = "none";
    document.getElementById("reveal").style.display = "block";

    launchConfetti();
}


function launchConfetti() {

    for (let i = 0; i < 120; i++) {

        const piece = document.createElement("div");

        piece.className = "confetti";

        piece.style.left = Math.random() * 100 + "vw";

        piece.style.animationDuration =
            (2 + Math.random() * 4) + "s";

        piece.style.animationDelay =
            Math.random() * 1.5 + "s";

        piece.style.transform =
            `rotate(${Math.random() * 360}deg)`;

        piece.style.background =
            `hsl(${Math.random() * 360}, 90%, 60%)`;

        document.body.appendChild(piece);

        setTimeout(() => {
            piece.remove();
        }, 6500);
    }
}


function shareResult() {

    const text =
        "🏆 I WON 3RD PRIZE IN ROBORACE! 🤖";

    if (navigator.share) {

        navigator.share({
            title: "Roborace Result",
            text: text
        });

    } else {

        navigator.clipboard.writeText(text);

        alert("Result copied! Send it to everyone 🚀");

    }
}

</script>

</body>
</html>
