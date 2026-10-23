<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>RoboRace Result</title>

    <style>
        html, body {
            margin: 0;
            padding: 0;
            width: 100%;
            min-height: 100%;
        }

        body {
            background: #111827;
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
        }

        .page {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            box-sizing: border-box;
        }

        .box {
            width: 100%;
            max-width: 650px;
        }

        .robot {
            font-size: 80px;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 32px;
            margin: 10px 0;
        }

        p {
            font-size: 20px;
            color: #cbd5e1;
        }

        button {
            margin-top: 25px;
            padding: 16px 30px;
            font-size: 18px;
            font-weight: bold;
            border: 0;
            border-radius: 12px;
            background: white;
            color: #111827;
            cursor: pointer;
        }

        button:active {
            transform: scale(0.95);
        }

        #result {
            display: none;
        }

        .number {
            font-size: 110px;
            font-weight: bold;
            color: #f59e0b;
            margin: 10px 0;
        }

        .prize {
            font-size: 48px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .race {
            font-size: 28px;
            color: #38bdf8;
            font-weight: bold;
        }

        .message {
            margin-top: 30px;
            font-size: 21px;
            line-height: 1.5;
            color: white;
        }

        .again {
            background: #38bdf8;
            color: black;
        }
    </style>
</head>

<body>

<div class="page">

    <div class="box" id="start">

        <div class="robot">🤖</div>

        <h1>I've got something to tell everyone...</h1>

        <p>After all the work, testing and racing...</p>

        <button onclick="showResult()">
            REVEAL THE RESULT
        </button>

    </div>


    <div class="box" id="result">

        <div class="robot">🤖</div>

        <p>THE RESULT IS...</p>

        <div class="number">3rd</div>

        <div class="prize">PRIZE 🏆</div>

        <div class="race">
            ROBORACE
        </div>

        <div class="message">
            WE ACTUALLY DID IT! 🎉
            <br><br>
            All that building, fixing, testing
            and racing was worth it.
        </div>

        <button class="again" onclick="shareResult()">
            SHARE THE NEWS
        </button>

    </div>

</div>


<script>

function showResult() {

    document.getElementById("start").style.display = "none";

    document.getElementById("result").style.display = "block";

}


function shareResult() {

    var message = "🏆 I WON 3RD PRIZE IN ROBORACE! 🤖";

    if (navigator.share) {

        navigator.share({
            title: "RoboRace Result",
            text: message
        });

    } else {

        navigator.clipboard.writeText(message);

        alert("Copied! Now send it to everyone 😎");

    }

}

</script>

</body>
</html>
