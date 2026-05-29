<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <title>ESP32 Control</title>
  <link rel="manifest" href="data:application/manifest+json,{%22name%22:%22ESP32%20Control%22,%22short_name%22:%22ESP32%22,%22start_url%22:%22.%22,%22display%22:%22standalone%22,%22background_color%22:%22%23111111%22,%22theme_color%22:%22%23111111%22,%22icons%22:[{%22src%22:%22data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%2096%2096'%3E%3Crect%20width='96'%20height='96'%20rx='20'%20fill='%23111'/%3E%3Ccircle%20cx='48'%20cy='48'%20r='22'%20fill='none'%20stroke='%2322c55e'%20stroke-width='4'/%3E%3Ccircle%20cx='48'%20cy='48'%20r='10'%20fill='%2322c55e'/%3E%3C/svg%3E%22,%22sizes%22:%22any%22,%22type%22:%22image/svg+xml%22}]}">
  <meta name="theme-color" content="#111111">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <meta name="apple-mobile-web-app-title" content="ESP32">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
    :root {
      --bg: #111;
      --card: #1a1a1a;
      --border: #2a2a2a;
      --text: #f0f0f0;
      --muted: #555;
      --green: #22c55e;
      --red: #ef4444;
      --amber: #f59e0b;
    }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      min-height: 100dvh;
      display: flex;
      flex-direction: column;
      padding: 24px 16px 32px;
      max-width: 420px;
      margin: 0 auto;
      gap: 24px;
    }
    header {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    #dot {
      width: 9px; height: 9px;
      border-radius: 50%;
      background: var(--red);
      flex-shrink: 0;
      transition: background 0.3s;
    }
    #dot.on { background: var(--green); }
    #dot.busy { background: var(--amber); animation: blink 1s infinite; }
    @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }
    #status { font-size: 13px; color: var(--muted); flex: 1; }
    #connect-btn {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text);
      font-size: 13px;
      padding: 7px 16px;
      border-radius: 999px;
      cursor: pointer;
      transition: border-color 0.2s, color 0.2s;
      font-family: inherit;
    }
    #connect-btn:hover { border-color: var(--green); color: var(--green); }
    #connect-btn.connected { border-color: var(--red); color: var(--red); }
    #connect-btn:disabled { opacity: 0.35; cursor: default; }
    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      flex: 1;
      align-content: start;
    }
    .toggle {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 28px 12px 24px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 12px;
      cursor: pointer;
      transition: background 0.15s, border-color 0.15s, transform 0.1s;
      min-height: 140px;
      justify-content: center;
      font-family: inherit;
    }
    .toggle:active { transform: scale(0.95); }
    .toggle.on { background: rgba(34,197,94,0.08); border-color: var(--green); }
    .toggle:disabled { opacity: 0.3; cursor: default; }
    .toggle:disabled:active { transform: none; }
    .indicator {
      width: 12px; height: 12px;
      border-radius: 50%;
      background: var(--border);
      transition: background 0.2s, box-shadow 0.2s;
    }
    .toggle.on .indicator {
      background: var(--green);
      box-shadow: 0 0 8px rgba(34,197,94,0.5);
    }
    .label {
      font-size: 15px;
      font-weight: 500;
      color: var(--muted);
      transition: color 0.2s;
    }
    .toggle.on .label { color: var(--text); }
    .state {
      font-size: 11px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--muted);
      transition: color 0.2s;
    }
    .toggle.on .state { color: var(--green); }
    #log {
      font-size: 11px;
      color: var(--muted);
      font-family: 'Courier New', monospace;
      min-height: 18px;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <div id="dot"></div>
    <span id="status">Disconnected</span>
    <button id="connect-btn">Connect</button>
  </header>

  <div class="grid">
    <button class="toggle" data-i="0" disabled>
      <div class="indicator"></div>
      <span class="label">Output 1</span>
      <span class="state">off</span>
    </button>
    <button class="toggle" data-i="1" disabled>
      <div class="indicator"></div>
      <span class="label">Output 2</span>
      <span class="state">off</span>
    </button>
    <button class="toggle" data-i="2" disabled>
      <div class="indicator"></div>
      <span class="label">Output 3</span>
      <span class="state">off</span>
    </button>
    <button class="toggle" data-i="3" disabled>
      <div class="indicator"></div>
      <span class="label">Output 4</span>
      <span class="state">off</span>
    </button>
  </div>

  <div id="log"></div>

  <script>
    const SERVICE_UUID = '4fafc201-1fb5-459e-8fcc-c5c9c331914b';
    const CHAR_UUID    = 'beb5483e-36e1-4688-b7f5-ea07361b26a8';

    const dot        = document.getElementById('dot');
    const statusEl   = document.getElementById('status');
    const connectBtn = document.getElementById('connect-btn');
    const logEl      = document.getElementById('log');
    const toggles    = document.querySelectorAll('.toggle');

    let device = null;
    let char   = null;
    let state  = 0;          // bitmask — bit 0 = output 1, etc.
    let intentionalDisconnect = false;

    function log(msg) {
      logEl.textContent = msg;
    }

    function setStatus(text, cls) {
      statusEl.textContent = text;
      dot.className = cls || '';
    }

    function setConnected(yes) {
      connectBtn.textContent = yes ? 'Disconnect' : 'Connect';
      connectBtn.classList.toggle('connected', yes);
      toggles.forEach(t => t.disabled = !yes);
      if (!yes) { state = 0; renderToggles(); }
    }

    function renderToggles() {
      toggles.forEach((t, i) => {
        const on = (state >> i) & 1;
        t.classList.toggle('on', !!on);
        t.querySelector('.state').textContent = on ? 'on' : 'off';
      });
    }

    async function send() {
      if (!char) return;
      try {
        await char.writeValue(new Uint8Array([state]));
      } catch(e) {
        log('Write failed — ' + e.message);
      }
    }

    toggles.forEach(t => {
      t.addEventListener('click', async () => {
        const i = parseInt(t.dataset.i);
        state ^= (1 << i);
        renderToggles();
        await send();
      });
    });

    async function attemptConnect(dev) {
      const server  = await dev.gatt.connect();
      const service = await server.getPrimaryService(SERVICE_UUID);
      char = await service.getCharacteristic(CHAR_UUID);
    }

    async function onDisconnected() {
      char = null;
      if (intentionalDisconnect) {
        setStatus('Disconnected');
        setConnected(false);
        log('');
        return;
      }
      setStatus('Reconnecting…', 'busy');
      log('Connection lost — retrying…');
      // Keep trying until it works or user disconnects
      while (!intentionalDisconnect) {
        try {
          await attemptConnect(device);
          setStatus(device.name || 'ESP32', 'on');
          setConnected(true);
          log('Reconnected');
          return;
        } catch(e) {
          await new Promise(r => setTimeout(r, 2000));
        }
      }
    }

    async function connect() {
      try {
        setStatus('Scanning…', 'busy');
        connectBtn.disabled = true;
        log('');

        device = await navigator.bluetooth.requestDevice({
          filters: [{ services: [SERVICE_UUID] }]
        });

        device.addEventListener('gattserverdisconnected', onDisconnected);
        intentionalDisconnect = false;

        setStatus('Connecting…', 'busy');
        await attemptConnect(device);

        setStatus(device.name || 'ESP32', 'on');
        setConnected(true);
        log('Connected ✓');
      } catch(e) {
        if (e.name !== 'NotFoundError' && e.name !== 'NotAllowedError') {
          log(e.message);
        }
        setStatus('Disconnected');
        setConnected(false);
        device = null;
      } finally {
        connectBtn.disabled = false;
      }
    }

    connectBtn.addEventListener('click', () => {
      if (connectBtn.classList.contains('connected')) {
        intentionalDisconnect = true;
        device?.gatt.disconnect();
      } else {
        connect();
      }
    });

    if (!navigator.bluetooth) {
      setStatus('Bluetooth not supported');
      connectBtn.disabled = true;
      log('Open this page in Chrome on Android');
    }
  </script>
</body>
</html>
