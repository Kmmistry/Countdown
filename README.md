# Countdown

<!DOCTYPE html>
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Party Countdown</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

/* PARTY BACKGROUND */
body {
  min-height: 100vh;
  background: radial-gradient(circle at top, #ff0080, #7928ca, #2b1055);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

/* Floating lights */
body::before {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-radial-gradient(
    circle at random,
    rgba(255,255,255,0.15) 0,
    transparent 10%
  );
  animation: sparkle 6s linear infinite;
}

@keyframes sparkle {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* MAIN CARD */
.party-box {
  position: relative;
  z-index: 2;
  background: rgba(0, 0, 0, 0.45);
  backdrop-filter: blur(12px);
  padding: 40px 45px;
  border-radius: 20px;
  box-shadow: 0 0 50px rgba(255, 0, 200, 0.7);
  text-align: center;
  color: #fff;
}

/* TITLE */
.party-box h1 {
  font-size: 34px;
  margin-bottom: 12px;
  letter-spacing: 2px;
  text-transform: uppercase;
  animation: glow 2s infinite alternate;
}

@keyframes glow {
  from { text-shadow: 0 0 10px #ff00ff; }
  to { text-shadow: 0 0 25px #00eaff; }
}

.party-sub {
  font-size: 16px;
  opacity: 0.9;
  margin-bottom: 25px;
}

/* TIMER */
#demo {
  display: flex;
  gap: 18px;
  justify-content: center;
  flex-wrap: wrap;
}

/* TIME BOX */
.time {
  background: linear-gradient(145deg, #ff0080, #7928ca);
  padding: 18px 20px;
  border-radius: 14px;
  min-width: 90px;
  box-shadow: 0 0 20px rgba(255,0,200,0.8);
  animation: bounce 1s infinite alternate;
}

@keyframes bounce {
  from { transform: translateY(0); }
  to { transform: translateY(-8px); }
}

.time span {
  display: block;
  font-size: 44px;
  font-weight: 700;
}

.time small {
  font-size: 13px;
  letter-spacing: 1px;
  text-transform: uppercase;
}

/* EXPIRED PARTY */
.expired {
  font-size: 38px;
  font-weight: 800;
  animation: explode 1s infinite alternate;
  text-shadow: 0 0 30px gold;
}

@keyframes explode {
  from { transform: scale(1); }
  to { transform: scale(1.15); }
}

/* MOBILE */
@media(max-width: 480px) {
  .party-box h1 {
    font-size: 26px;
  }
  .time span {
    font-size: 36px;
  }
}
</style>
</head>

<body>

<div class="party-box">
  <h1>🎉 It's Christmas 🎉</h1>
  <div class="party-sub">The celebration starts in…</div>
  <div id="demo"></div>
</div>

<script>
var countDownDate = new Date("Dec 25, 2025 01:05:25").getTime();

var x = setInterval(function () {
  var now = new Date().getTime();
  var distance = countDownDate - now;

  var days = Math.floor(distance / (1000 * 60 * 60 * 24));
  var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  var seconds = Math.floor((distance % (1000 * 60)) / 1000);

  document.getElementById("demo").innerHTML = `
    <div class="time"><span>${days}</span><small>Days</small></div>
    <div class="time"><span>${hours}</span><small>Hours</small></div>
    <div class="time"><span>${minutes}</span><small>Minutes</small></div>
    <div class="time"><span>${seconds}</span><small>Seconds</small></div>
  `;

  if (distance < 0) {
    clearInterval(x);
    document.getElementById("demo").innerHTML =
      '<div class="expired">🎊 PARTY TIME 🎊</div>';
  }
}, 1000);
</script>

</body>
</html>
