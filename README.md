<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>2004Scape Landscape</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: #000;
      height: 100vh;
      width: 100vw;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    #game-frame {
      width: 100vw;
      height: 100vh;
      border: none;
      display: block;
      transform-origin: center;
    }
    /* Force landscape on iPhone */
    @media (orientation: portrait) {
      body {
        transform: rotate(90deg);
        transform-origin: center;
        width: 100vh;
        height: 100vw;
        position: fixed;
        top: 0;
        left: 0;
      }
      #game-frame {
        width: 100vh;
        height: 100vw;
      }
    }
    @media (orientation: landscape) {
      #game-frame {
        width: 100vw;
        height: 100vh;
      }
    }
    /* Prevent keyboard and zoom issues */
    html, body {
      -webkit-text-size-adjust: none;
      text-size-adjust: none;
      overscroll-behavior: none;
    }
  </style>
</head>
<body>
  <iframe id="game-frame" src="https://2004.lostcity.rs/client?world=2&detail=high&method=0" allowfullscreen></iframe>
  <script>
    // Attempt to lock orientation to landscape
    if (screen.orientation && screen.orientation.lock) {
      screen.orientation.lock('landscape').catch(err => console.log('Orientation lock failed:', err));
    }
    // Prevent pinch-to-zoom and pull-to-refresh
    document.addEventListener('touchmove', (e) => {
      if (e.touches.length > 1) e.preventDefault();
    }, { passive: false });
    document.addEventListener('touchstart', (e) => {
      if (e.touches.length === 1 && window.scrollY === 0) {
        e.preventDefault();
      }
    }, { passive: false });
    // Log iframe load status
    const iframe = document.getElementById('game-frame');
    iframe.onload = () => console.log('Iframe loaded');
    iframe.onerror = () => console.log('Iframe failed to load');
  </script>
</body>
</html>