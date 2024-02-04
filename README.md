<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }

        #stopwatch {
            text-align: center;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
        }

        #display {
            font-size: 2em;
            color: #333;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            margin: 10px;
            cursor: pointer;
            background-color: #4CAF50;
            color: #fff;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #45a049;
        }

        #laps {
            margin-top: 20px;
            text-align: left;
        }

        #lapList {
            list-style-type: none;
            padding: 0;
            margin: 0;
            max-height: 150px;
            overflow-y: auto;
        }

        .lapTime {
            margin-bottom: 5px;
            padding: 5px;
            background-color: #f2f2f2;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
    </style>
    <title>Colored Stopwatch with Laps</title>
</head>
<body>

<div id="stopwatch">
    <h1 style="color: #333;">Colored Stopwatch with Laps</h1>
    <p id="display">00:00:00</p>
    <button id="startStopButton" onclick="startStop()">Start</button>
    <button onclick="reset()">Reset</button>

    <div id="laps">
        <h2>Lap Times</h2>
        <ul id="lapList"></ul>
    </div>
</div>

<script>
    let timer;
    let isRunning = false;
    let seconds = 0, minutes = 0, hours = 0;
    let lapCounter = 1;

    function startStop() {
        if (isRunning) {
            clearInterval(timer);
            document.getElementById('startStopButton').textContent = 'Start';
        } else {
            timer = setInterval(updateTime, 1000);
            document.getElementById('startStopButton').textContent = 'Stop';
        }

        isRunning = !isRunning;
    }

    function updateTime() {
        seconds++;

        if (seconds === 60) {
            seconds = 0;
            minutes++;

            if (minutes === 60) {
                minutes = 0;
                hours++;
            }
        }

        const display = document.getElementById('display');
        display.textContent = formatTime(hours) + ':' + formatTime(minutes) + ':' + formatTime(seconds);
    }

    function formatTime(value) {
        return value < 10 ? '0' + value : value;
    }

    function reset() {
        clearInterval(timer);
        isRunning = false;
        seconds = 0;
        minutes = 0;
        hours = 0;
        lapCounter = 1;

        const display = document.getElementById('display');
        display.textContent = '00:00:00';

        document.getElementById('startStopButton').textContent = 'Start';

        // Clear lap times
        const lapList = document.getElementById('lapList');
        lapList.innerHTML = '';
    }

    function lap() {
        const lapTime = formatTime(hours) + ':' + formatTime(minutes) + ':' + formatTime(seconds);
        const lapList = document.getElementById('lapList');

        const lapItem = document.createElement('li');
        lapItem.classList.add('lapTime');
        lapItem.textContent = 'Lap ' + lapCounter + ': ' + lapTime;

        lapList.insertBefore(lapItem, lapList.firstChild);
        lapCounter++;
    }
</script>

</body>
</html>
- 👋 Hi, I’m @mohammadnikhatparveen
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
mohammadnikhatparveen/mohammadnikhatparveen is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
