# Sportybet-aviator-view-

<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SportyBet Aviator Tracker</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
    .overlay {
      position: fixed;
      top: 10px;
      left: 10px;
      background: rgba(0, 0, 0, 0.7);
      color: #fff;
      padding: 12px;
      border-radius: 8px;
      z-index: 9999;
      max-width: 250px;
    }
    .overlay h4 {
      margin: 0 0 10px 0;
      font-size: 16px;
    }
    .overlay p {
      margin: 4px 0;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <iframe src="https://www.sportybet.com/gh/m/games"></iframe>  <div class="overlay" id="tracker">
    <h4>Aviator Tracker</h4>
    <p>Last crash: <span id="lastCrash">Loading...</span></p>
    <p>Next prediction: <span id="prediction">Calculating...</span></p>
    <p>Cashout Alert: <span id="alert">Waiting...</span></p>
  </div>  <script>
    // Simulated crash values and predictor (randomized)
    const crashHistory = [];

    function simulateCrash() {
      const crash = (Math.random() * 50 + 1).toFixed(2);
      crashHistory.unshift(crash);
      if (crashHistory.length > 10) crashHistory.pop();
      return crash;
    }

    function predictNextCrash() {
      if (crashHistory.length < 2) return (Math.random() * 5).toFixed(2);
      const avg = crashHistory.reduce((a, b) => a + parseFloat(b), 0) / crashHistory.length;
      return (avg + (Math.random() - 0.5)).toFixed(2);
    }

    setInterval(() => {
      const crash = simulateCrash();
      const prediction = predictNextCrash();

      document.getElementById("lastCrash").innerText = `${crash}x`;
      document.getElementById("prediction").innerText = `${prediction}x`;

      if (parseFloat(prediction) > 2.0) {
        document.getElementById("alert").innerText = "Prepare to cash out!";
      } else {
        document.getElementById("alert").innerText = "Wait...";
      }
    }, 5000);
  </script></body>
</html>
