<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Quotex Signal Dashboard</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #1e1e2f;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .signal-box {
      background: #2c2c3e;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0, 255, 150, 0.2);
      text-align: center;
    }
    .signal {
      font-size: 48px;
      font-weight: bold;
      margin-top: 20px;
      color: #00ff96;
    }
  </style>
</head>
<body>
  <div class="signal-box">
    <h1>Quotex Signal Dashboard</h1>
    <p class="signal" id="signal">Loading...</p>
  </div>

  <script>
    async function fetchSignal() {
      try {
        const response = await fetch("signal.txt?_=" + new Date().getTime());
        const text = await response.text();
        document.getElementById("signal").textContent = text.trim();
      } catch (e) {
        document.getElementById("signal").textContent = "No signal found.";
      }
    }
    fetchSignal();
    setInterval(fetchSignal, 5000);
  </script>
</body>
</html>
