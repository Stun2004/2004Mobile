<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>2004Scape Stretched</title>
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
      color: white;
      font-family: Arial, sans-serif;
    }
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
    }
    html, body {
      -webkit-text-size-adjust: none;
      text-size-adjust: none;
      overscroll-behavior: none;
    }
  </style>
</head>
<body>
  <p>Redirecting to stretched 2004Scape client...</p>
  <script>
    window.location.replace("https://2004.lostcity.rs/client?world=2&detail=high&method=0");
    if (screen.orientation && screen.orientation.lock) {
      screen.orientation.lock('landscape').catch(err => console.log('Orientation lock failed:', err));
    }
    document.addEventListener('touchmove', (e) => {
      if (e.touches.length > 1) e.preventDefault();
    }, { passive: false });
    document.addEventListener('touchstart', (e) => {
      if (e.touches.length === 1 && window.scrollY === 0) {
        e.preventDefault();
      }
    }, { passive: false });
  </script>
</body>
</html>