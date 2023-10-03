# CodeClauseIntern_Timer
<!DOCTYPE html>
<html>
<head>
  <title>Stopwatch</title>
  <style>
    body {
      background-color: #362417; 
      font-family: Arial, sans-serif;
      text-align: center;
      color: #fff; /* Text Color */
    }
    {
      font-size: 36px;
      font-weight: bold;
      margin: 20px 0;
    }
   {
      margin: 10px 0;
    }
    button {
      background-color: #795548; 
      color: #fff; 
      border: none;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      margin: 5px;
      border-radius: 5px;
    }
    button:hover {
      background-color: #5d4037; 
    }
  </style>
</head>
<body>
  <h1>Stopwatch</h1>
  <div id="stopwatch">00:00:00</div>
  <div id="controls">
    <button onclick="startStopwatch()">Start</button>
    <button onclick="stopStopwatch()">Stop</button>
    <button onclick="resetStopwatch()">Reset</button>
  </div>
  
  <script>
    let stopwatchInterval;
    let stopwatchSeconds = 0;
    let stopwatchMinutes = 0;
    let stopwatchHours = 0;
    let running = false;

    function startStopwatch() {
      if (!running) {
        clearInterval(stopwatchInterval);
        stopwatchInterval = setInterval(updateStopwatch, 1000);
        running = true;
      }
    }

    function stopStopwatch() {
      clearInterval(stopwatchInterval);
      running = false;
    }

    function resetStopwatch() {
      clearInterval(stopwatchInterval);
      stopwatchSeconds = 0;
      stopwatchMinutes = 0;
      stopwatchHours = 0;
      updateStopwatch();
      running = false;
    }

    function updateStopwatch() {
      stopwatchSeconds++;
      if (stopwatchSeconds >= 60) {
        stopwatchSeconds = 0;
        stopwatchMinutes++;
        if (stopwatchMinutes >= 60) {
          stopwatchMinutes = 0;
          stopwatchHours++;
        }
      }

      const formattedTime = `${stopwatchHours.toString().padStart(2, '0')}:${stopwatchMinutes.toString().padStart(2, '0')}:${stopwatchSeconds.toString().padStart(2, '0')}`;
      document.getElementById('stopwatch').textContent = formattedTime;
    }
  </script>
</body>
</html>
