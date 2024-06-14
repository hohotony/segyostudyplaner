<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Segyo Study Planer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            width: 100%;
            margin-bottom: 20px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #f9f9f9;
        }
        .stopwatch, .notes, .calendar {
            margin-bottom: 20px;
        }
        .calendar input, .notes textarea {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
        }
        .calendar input[type="date"] {
            padding: 5px;
        }
    </style>
</head>
<body>

<div class="container stopwatch">
    <h2>Stopwatch</h2>
    <div id="display">00:00:00</div>
    <button onclick="startStopwatch()">Start</button>
    <button onclick="stopStopwatch()">Stop</button>
    <button onclick="resetStopwatch()">Reset</button>
</div>

<div class="container notes">
    <h2>Notes</h2>
    <textarea id="notes" rows="10"></textarea>
</div>

<div class="container calendar">
    <h2>Calendar</h2>
    <input type="date" id="event-date">
    <input type="text" id="event-name" placeholder="Event Name">
    <button onclick="addEvent()">Add Event</button>
    <div id="event-list"></div>
</div>

<script>
    let stopwatchInterval;
    let stopwatchTime = 0;

    function startStopwatch() {
        stopwatchInterval = setInterval(() => {
            stopwatchTime++;
            document.getElementById('display').innerText = new Date(stopwatchTime * 1000).toISOString().substr(11, 8);
        }, 1000);
    }

    function stopStopwatch() {
        clearInterval(stopwatchInterval);
    }

    function resetStopwatch() {
        clearInterval(stopwatchInterval);
        stopwatchTime = 0;
        document.getElementById('display').innerText = '00:00:00';
    }

    function addEvent() {
        const date = document.getElementById('event-date').value;
        const name = document.getElementById('event-name').value;
        const eventList = document.getElementById('event-list');
        const eventItem = document.createElement('div');
        eventItem.innerText = `${date}: ${name}`;
        eventList.appendChild(eventItem);
    }
</script>

</body>
</html>
