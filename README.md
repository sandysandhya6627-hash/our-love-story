# our-love-story
<!DOCTYPE html>
<html>
<head>
<title>Our Love Story</title>
<style>
body {
  margin: 0;
  overflow: hidden;
  background: black;
  font-family: 'Courier New', monospace;
  color: white;
  text-align: center;
}

/* Star background */
canvas {
  position: fixed;
  top: 0;
  left: 0;
}

/* Story text */
#story {
  position: absolute;
  top: 50%;
  width: 100%;
  transform: translateY(-50%);
  font-size: 26px;
  opacity: 0;
  transition: opacity 1.5s ease;
}

/* Glow effect */
.glow {
  color: #ff4da6;
  text-shadow: 0 0 10px #ff4da6, 0 0 20px #ff1a8c;
}

/* Floating hearts */
.heart {
  position: absolute;
  color: #ff4da6;
  animation: floatUp 6s linear infinite;
}

@keyframes floatUp {
  0% { transform: translateY(100vh); opacity: 1; }
  100% { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>
<body>

<canvas id="stars"></canvas>
<div id="story"></div>

<script>
/* ---------- STAR BACKGROUND ---------- */
let canvas = document.getElementById("stars");
let ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let stars = [];
for (let i = 0; i < 200; i++) {
  stars.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    radius: Math.random() * 2
  });
}

function drawStars() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = "white";
  stars.forEach(star => {
    ctx.beginPath();
    ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
    ctx.fill();
  });
  requestAnimationFrame(drawStars);
}
drawStars();

/* ---------- STORY ---------- */
let story = [
  "Initializing Our_Story.exe ❤️",
  "A college bus passes by...",
  "He was walking on the road...",
  "Eyes met. Destiny triggered ✨",
  "Daily chats activated 📱",
  "First meeting at Scandy 🍦",
  "Sweet like the ice cream we shared 💕",
  "A whole night at a concert 🎶",
  "Music. Lights. Us.",
  "Football court laughter ⚽",
  "Under the night sky 🌌",
  "System Error: ArgumentDetected 🐞",
  "Emotions overflow...",
  "Recalculating priorities...",
  "Result: Love > Ego ❤️",
  "I'm sorry...",
  "You mean more than any fight.",
  "Let's build Version 2.0 together 💞"
];

let i = 0;
let storyDiv = document.getElementById("story");

function showStory() {
  if (i < story.length) {
    storyDiv.style.opacity = 0;
    setTimeout(() => {
      storyDiv.innerHTML = story[i];
      if (i >= story.length - 4) {
        storyDiv.classList.add("glow");
      }
      storyDiv.style.opacity = 1;
      i++;
    }, 1000);
    setTimeout(showStory, 4000);
  } else {
    createHearts();
    setTimeout(showFinalMessage, 5000);
  }
}

showStory();

/* ---------- FLOATING HEARTS ---------- */
function createHearts() {
  setInterval(() => {
    let heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (Math.random() * 20 + 15) + "px";
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 6000);
  }, 300);
}

/* ---------- FINAL TYPING MESSAGE ---------- */
function showFinalMessage() {
  let finalMessage = document.createElement("div");
  finalMessage.style.position = "absolute";
  finalMessage.style.bottom = "12%";
  finalMessage.style.width = "100%";
  finalMessage.style.fontSize = "28px";
  finalMessage.style.color = "#ff4da6";
  finalMessage.style.textShadow = "0 0 15px #ff4da6";
  document.body.appendChild(finalMessage);

  let text = "Forever loading… with you ❤️";
  let index = 0;

  function typeEffect() {
    if (index < text.length) {
      finalMessage.innerHTML += text.charAt(index);
      index++;
      setTimeout(typeEffect, 80);
    }
  }

  typeEffect();
}
</script>

</body>
</html>
