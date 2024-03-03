<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reaction Tester</title>
    <style>
        body {
            background-color: red;
            margin: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: Arial, sans-serif;
        }

        #container {
            background-color: white;
            position: relative;
            width: 1000px;
            height: 600px; /* corrected height */
            border: 2px solid #000;
            overflow: hidden;
            margin-top: 20px;
        }

        #shape {
            position: absolute;
            width: 200px;
            height: 200px;
            background-color: red;
        }

        #timer {
            position: absolute;
            top: -40px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 24px;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Reaction Tester</h1>
    <p>Click on the shapes as soon as you can!</p>
    <div id="timer"></div>
    <div id="container">
        <div id="shape"></div>
    </div>
    
    <script>
        var container = document.getElementById("container");
        var shape = document.getElementById("shape");
        var timerDisplay = document.getElementById("timer");
        var start; // Declaring start in the outer scope

        function getRandomColor() {
            var letters = '012345679ABCDEF';
            var color = '#';
            for(var i = 0; i < 6; i++) {
                color += letters[Math.floor(Math.random() * 16)];
            }
            return color;
        }

        function moveShape() {
            var left = Math.random() * (container.offsetWidth - shape.offsetWidth);
            var top = Math.random() * (container.offsetHeight - shape.offsetHeight);
            var wh = ((Math.random() * 200) + 100);

            shape.style.left = left + "px";
            shape.style.top = top + "px";
            shape.style.width = wh + "px";
            shape.style.height = wh + "px";
            shape.style.backgroundColor = getRandomColor();
            shape.style.display = "block";
            start = new Date().getTime(); // Update start here
        }

        moveShape();

        shape.onclick = function() {
            var end = new Date().getTime();
            var timeTaken = (end - start) / 1000;
            console.log("Time taken: " + timeTaken.toFixed(2) + " seconds");
            timerDisplay.textContent = "Time taken: " + timeTaken.toFixed(2) + " seconds";
            alert(timeTaken);
            moveShape();
        }
    </script>
</body>
</html>
