<!DOCTYPE html><html lang="en"><head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ashish Windows 11</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      overflow: hidden;
      font-family: 'Segoe UI', sans-serif;
      background: url('https://wallpaperaccess.com/full/5651994.jpg') no-repeat center center fixed;
      background-size: cover;
    }
    #boot {
      position: fixed;
      width: 100%;
      height: 100%;
      background: black;
      color: white;
      font-size: 2em;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }
    #login-screen {
      display: none;
      position: fixed;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }
    #desktop {
      display: none;
      width: 100%;
      height: 100%;
      position: relative;
    }
    .icon {
      width: 80px;
      text-align: center;
      color: white;
      margin: 20px;
      cursor: pointer;
    }
    .icon i {
      font-size: 2em;
    }
    .window {
      position: absolute;
      width: 600px;
      height: 400px;
      background: white;
      border: 2px solid #0078D7;
      display: none;
      flex-direction: column;
      z-index: 1000;
    }
    .window-header {
      background: #0078D7;
      color: white;
      padding: 10px;
      display: flex;
      justify-content: space-between;
      cursor: move;
    }
    .window-content {
      flex: 1;
      padding: 10px;
      overflow: auto;
    }
    #taskbar {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 50px;
      background: rgba(0, 0, 0, 0.7);
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: white;
      padding: 0 20px;
    }
    #start-menu {
      display: none;
      position: absolute;
      bottom: 60px;
      left: 20px;
      background: white;
      width: 250px;
      padding: 10px;
      border-radius: 10px;
    }
    #start-menu button {
      width: 100%;
      padding: 10px;
      margin-bottom: 5px;
      border: none;
      background: #f0f0f0;
      cursor: pointer;
      text-align: left;
    }
    textarea {
      width: 100%;
      height: 100%;
    }
  </style>
</head><body>
  <div id="boot">Booting Ashish Windows 11...</div>  <div id="login-screen">
    <h2 style="color:white">Welcome</h2>
    <input type="password" id="login-password" placeholder="Enter Password" />
    <button onclick="login()">Login</button>
  </div>  <div id="desktop">
    <div style="position:absolute;top:20px;left:20px;display:flex;flex-direction:column;">
      <div class="icon" onclick="openWindow('notepad')">
        <i class="fas fa-file-alt"></i>
        <div>Notepad</div>
      </div>
      <div class="icon" onclick="openWindow('calculator')">
        <i class="fas fa-calculator"></i>
        <div>Calculator</div>
      </div>
    </div><div id="notepad" class="window">
  <div class="window-header">
    <span>Notepad</span>
    <button onclick="closeWindow('notepad')">✖</button>
  </div>
  <div class="window-content">
    <textarea placeholder="Write something..."></textarea>
  </div>
</div>

<div id="calculator" class="window">
  <div class="window-header">
    <span>Calculator</span>
    <button onclick="closeWindow('calculator')">✖</button>
  </div>
  <div class="window-content">
    <input type="text" id="calc-display" readonly style="width:100%;font-size:1.5em;margin-bottom:10px;" />
    <div>
      <button onclick="calc('1')">1</button>
      <button onclick="calc('2')">2</button>
      <button onclick="calc('+')">+</button>
      <button onclick="calc('=')">=</button>
    </div>
  </div>
</div>

<div id="taskbar">
  <button onclick="toggleStartMenu()">Start</button>
  <div id="clock"></div>
</div>

<div id="start-menu">
  <button onclick="openWindow('notepad')">📝 Notepad</button>
  <button onclick="openWindow('calculator')">🧮 Calculator</button>
</div>

  </div>  <script>
    // Boot sequence
    setTimeout(() => {
      document.getElementById('boot').style.display = 'none';
      document.getElementById('login-screen').style.display = 'flex';
    }, 3000);

    function login() {
      document.getElementById('login-screen').style.display = 'none';
      document.getElementById('desktop').style.display = 'block';
    }

    function toggleStartMenu() {
      const menu = document.getElementById('start-menu');
      menu.style.display = menu.style.display === 'block' ? 'none' : 'block';
    }

    function openWindow(id) {
      document.getElementById(id).style.display = 'flex';
    }

    function closeWindow(id) {
      document.getElementById(id).style.display = 'none';
    }

    let expr = "";
    function calc(val) {
      if (val === '=') {
        try {
          document.getElementById('calc-display').value = eval(expr);
          expr = "";
        } catch {
          expr = "";
          document.getElementById('calc-display').value = 'Error';
        }
      } else {
        expr += val;
        document.getElementById('calc-display').value = expr;
      }
    }

    function updateClock() {
      const now = new Date();
      document.getElementById('clock').innerText = now.toLocaleTimeString();
    }
    setInterval(updateClock, 1000);
    updateClock();
  </script></body></html>
