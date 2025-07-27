# scroll_back
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Scrollback – A Tribute to HCI</title>
  <style>
    body {
      margin: 0;
      font-family: monospace;
      background-color: #000;
      color: #00ff00;
      overflow-x: hidden;
    }
    header {
      text-align: center;
      padding: 2rem;
    }
    .orb {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background: radial-gradient(#00ffcc, #001111);
      margin: 0 auto;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.1); opacity: 0.8; }
      100% { transform: scale(1); opacity: 1; }
    }
    section {
      padding: 3rem;
      border-bottom: 1px solid #333;
    }
    .era {
      max-width: 800px;
      margin: auto;
    }
    .quote {
      font-style: italic;
      margin-top: 1rem;
      color: #ccc;
    }
    .papers a {
      display: block;
      color: #00ffcc;
      text-decoration: none;
      margin-top: 0.5rem;
    }
    .playground {
      margin-top: 2rem;
      background-color: #111;
      padding: 1rem;
      border: 1px solid #00ff00;
    }
    .terminal-input {
      width: 100%;
      background: #000;
      border: none;
      color: #0f0;
      font-size: 1rem;
      padding: 0.5rem;
    }
    #response {
      margin-top: 1rem;
      color: #0ff;
    }
    .mute-button {
      position: fixed;
      top: 1rem;
      right: 1rem;
      background: #111;
      color: #fff;
      border: none;
      padding: 0.5rem 1rem;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <button class="mute-button" onclick="toggleSound()">🔇 Mute</button>
  <header>
    <h1>Scrollback</h1>
    <p>A tribute to how we learned to speak in clicks, commands, and conversations.</p>
    <div class="orb"></div>
  </header>

  <section id="cli" class="era">
    <h2>🖥️ Command Line Era (1960s–1970s)</h2>
    <p>The dawn of human-computer interaction. Interfaces were textual, precise, and powerful — but demanded expertise.</p>
    <blockquote class="quote">"The best way to predict the future is to invent it." — Alan Kay</blockquote>
    <div class="papers">
      <a href="#">Engelbart’s 1968 Demo</a>
      <a href="#">UNIX Philosophy</a>
      <a href="#">As We May Think – Vannevar Bush</a>
    </div>
    <div class="playground">
      <label for="command">Try this: <code>sudo coffee</code></label>
      <input type="text" id="command" class="terminal-input" placeholder="Type a command..." onkeydown="if(event.key==='Enter') runCommand()">
      <div id="response"></div>
    </div>
  </section>

  <audio id="typeSound" src="https://cdn.pixabay.com/audio/2021/10/06/audio_c6b729bf58.mp3"></audio>

  <script>
    const responseBox = document.getElementById('response');
    const typeSound = document.getElementById('typeSound');
    let soundMuted = false;

    function runCommand() {
      const input = document.getElementById('command').value.toLowerCase();
      if (!soundMuted) typeSound.play();
      if (input === 'sudo coffee') {
        responseBox.textContent = '☕ Java delivered. Please caffeinate responsibly.';
      } else if (input === 'hello world') {
        responseBox.textContent = '👋 Hello, Earthling.';
      } else {
        responseBox.textContent = '🤖 Unknown command, but I like your spirit.';
      }
    }

    function toggleSound() {
      soundMuted = !soundMuted;
      document.querySelector('.mute-button').textContent = soundMuted ? '🔈 Unmute' : '🔇 Mute';
    }
  </script>
</body>
</html>
